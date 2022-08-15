# Development rules & recommendations

- Here, you can find information about managing JIRA issues, git repos, GitHub pull requests, etc.
- Mainly, you will find information about our codebase here

## JIRA tasks
- Our projects usually have a JIRA project associated with it
- Creating issues and managing them can differ from project to project

## Git & GitHub
- We usually create a git branch for every JIRA issue, e.g. `git checkout -b feature/MUV-XXX-some-title` (`MUV` being the project code on JIRA)
- Depending on whether the task corresponds to a fix or a feature, the branch usually has a prefix `fix/` or `feature/`
- The branch name usually contains the JIRA issue number `MUV-XXX` so that CI/CD can automatically manage the issue state etc.
- In order to keep your branch up-to-date with the base branch, we prefer `git rebase`
- Try to follow the recommendations for git commit messages, such as writing them in do-forms and keeping them informative, very specific information [here](https://cbea.ms/git-commit/)
- Once you are finished with the implementation, you can create a Pull Request on GitHub

### GitHub Pull Requests
- Try to stick with the naming style `[MUV-XXX] <Pull request title>`
- We have a template for our pull request descriptions, which you will be able to fill out as soon as you create the pull request
- Try to fill out the entire template accordingly:
    - **Description**: Try to sum up what the PR introduces
    - **What's new**: Describe what this PR changes
    - **What's missing**: Try to sum up stuff related to the PR that you feel should be further developed or what you didn't have time for
    - **References**: Add links to the stuff that your PR is related to, usually it's at least the JIRA issue and chili tasks, if available
    - You can add more sections if you see fit.
- Once you're done with the PR description, you can add reviewers – these would usually be the people who are working on the project with you
- Always try to react to the reviewers' messages so that they can later see how you handled them
- When you're done with all the review comments, request a re-review, so that the reviewers can see that you've fixed all their comments and that the code is ready for a re-review
- Once the PR is ready to be merged, it should be merged by you, the PR creator

## Architecture

- The goal for our projects is to follow the clean architecture and to use Kotlin Multiplatform Mobile
- We have recently [started using advanced modularisation](https://github.com/MateeDevs/devstack-native-app/pull/31)

### Presentation Layer
- Our presentation layer follows the MVI architecture
- ViewModel has its state and intents, which are then used in a relevant SwiftUI View
- Asynchronous work is represented via native async/await

#### Flow Controllers
- Flow controllers control the flow of the app
- All feature parts of the app should have their own flow controller, such as `OnboardingFlowController`, `HomeFlowController` etc.
- `AppFlowController` is the top-level flow controller, and it's defined in the application layer
- All flow controllers are a subclass of the `FlowController` class, which provides a common interface for all flow controllers
- Flow controllers therefore inherit the `handleFlow(_:)` method, which should be used in the view models to handle the flow
- `handleFlow(_:)` takes a parameter of type `Flow`, which is just an empty protocol, but all subflow enums (`OnboardingFlow`, `HomeFlow`, ...), which come with the feature flow controllers (`OnboardingFlowController`, `HomeFlowController`, ...), conform to this protocol, so that they can be used as the parameter of that `handleFlow(_:)` method
- Flow enum example:
```
enum OnboardingFlow: Flow, Equatable {
    case login(Login)
    case registration(Registration)
    
    enum Login: Equatable {
        case dismiss
        case showRegistration
    }
    
    enum Registration: Equatable {
        case dismiss
        case pop
    }
}
```
- In this example, we then implement how the `OnboardingFlowController` handles specific flows:
```
override public func handleFlow(_ flow: Flow) {
    guard let onboardingFlow = flow as? OnboardingFlow else { return }
    switch onboardingFlow {
    case .login(let loginFlow): handleLoginFlow(loginFlow)
    case .registration(let registrationFlow): handleRegistrationFlow(registrationFlow)
    }
}
```

#### Views and View Models
- New features usually contain creating new views for the user
- Once you have a reasonable UI structure, you can create a view in the correct directory, such as `Login/LoginView.swift`
- Top views or other views, that are handled by flow controllers or contain some business logic, should always come with a view model, such as `LoginViewModel.swift`
- Reusable views that can be used anywhere in the app, such as customized buttons following the app theme, should be defined in the `UIToolKit` package
    - Same goes for styles etc.
- Try to separate your views into logic components (subviews), which can be defined outside of your view in a `Views` subfolder
- Also, try not to exceed \~100 lines of code in a view body
- View example:
```
struct SomeView: View {

    @ObservedObject private var viewModel: SomeViewModel

    init(viewModel: SomeViewModel) {
        self.viewModel = viewModel
    }

    var body: some View {
        SomeBackgroundView {
            VStack {
                SomeSubview(someInput: Binding<String>(
                    get: { viewModel.state.someInput },
                    set: { string in viewModel.onIntent(.changeInput(to: string)) }
                ))

                Button("Click Me!") {
                    viewModel.onIntent(.confirm)
                }

                Button("Cancel") {
                    viewModel.onIntent(.cancel)
                }
            }
        }
        .lifecycle(viewModel)
    }
}
```
- It is necessary to add the `.lifecycle(viewModel)` modifier (to the top-level view only!), so that lifecycle methods, such as `onAppear()` will be propagated to the view model
- One of the advantages of using SwiftUI is the ability to see live previews – in order to make them work, you need to:
    - Have the feature scheme selected as the scheme you build, otherwise the pre-build actions may cause the preview build to fail
    - Register mocked use cases of the ones you use in your view model in the `registerUseCaseMocks()` function, which is defined in the `SharedDomainMocks` source of the `SharedDomain` package
- You can also switch localizations by setting `Environment.locale`, because our `swiftgen-strings.stencil` generates localization according to it 
```
#if DEBUG
import Resolver
import SharedDomainMocks
import Utilities

struct SomeView_Previews: PreviewProvider {
    static var previews: some View {
    	Environment.locale = .init(identifier: "cs")
        Resolver.registerUseCaseMocks()
        
        let vm = SomeViewModel(flowController: nil)
        return PreviewGroup() {
            SomeView(viewModel: vm)
        }
    }
}
#endif
```
- View Model structure:
```
final class SomeViewModel: BaseViewModel, ViewModel, ObservableObject {

    // MARK: Dependencies

    private weak var flowController: FlowController?

    @Injected private var someUseCase: SomeUseCase
    @Injected private var someAnalyticsUseCase: SomeAnalyticsUseCase

    init(flowController: FlowController?) {
        self.flowController = flowController
        super.init()
    }

    // MARK: Lifecycle

    override func onAppear() {
        super.onAppear()
        someAnalyticsUseCase.execute(SomeAnalytics.onAppear.analyticsEvent) 
    }

    // MARK: State

    struct State {
        var isLoading = false
        var items: [SomeDomainModel] = []
        var someInput = ""
        var whisper: WhisperData?
    }

    @Published private(set) var state: State = State()

    // MARK: Intent

    enum Intent {
        case changeInput(to string: String)
        case confirm
        case cancel
    }

    @discardableResult
    func onIntent(_ intent: Intent) -> Task<Void, Never> {
        executeTask(Task {
            switch intent {
            case .changeInput(let string): changeInput(to: string)
            case .confirm: await confirm()
            case .cancel: cancel()
            }
        })
    }

    private func changeInput(to string: String) {
        state.someInput = string
    }

    private func confirm() async {
        state.isLoading = true
        do {
            let items = try await someUseCase.execute(withSomeInput: state.someInput)
            state.items = items
        } catch {
            state.whisper = .init(error: error.apiMessage ?? error.localizedDescription)
        }
        state.isLoading = false
    }

    private func cancel() {
        flowController?.handleFlow(OnboardingFlow.login(.dismiss))
    }
}
```
- the `executeTask(_:)` function serves to handle tasks in each view model, so that all tasks will be cancelled when the view disappears

### Domain Layer
- Reflects the whole business logic of the application via DomainModels and UseCases
- It also defines protocols for repositories
- It is separated into logical parts (`Auth`, `User`, `Analytics`, ...)

#### Domain Models
- We use domain models as the standard way to represent objects in the application
- These models are used when passing data between layers
- We should only use these domain models and not models from some third-party libraries, as that would make our app strictly dependent on those specific libraries
- We define these models under the `Models` directory for each logical part
- Conversion between domain models and some DTO objects is not the responsibility of the domain layer, therefore is not and cannot be defined here
- Domain model example:
```
public struct User {
    public let name: String
    public let surname: String
    public let gender: Gender
    public let title: Title?

    public init(
        name: String,
        surname: String,
        gender: Gender,
        title: Title? = nil
    ) {
        self.name = name
        self.surname = surname
        self.gender = gender
        self.title = title
    }
}
```

#### Use Cases and their implementations
- Use cases represent the business logic functionalities
- The presentation layer only calls these use cases, and that's where its responsibility ends
- Use cases can call repository functions and other use cases
- Each Use Case is represented by a protocol defining the `execute` function, allowing us to create more implementations, mocks, etc.
- Dependency Injection is then responsible for selecting the correct use case implementation
- The main implementation is usually defined in the same file as the use case protocol
- We define use cases under `UseCases` directory of each logical part
- Use Case example:
```
public protocol LoginUseCase {
    func execute(username: String, password: String) async throws
}

public struct LoginUseCaseImpl: LoginUseCase {

    private let authRepository: AuthRepository
    private let someOtherUseCase: SomeOtherUseCase

    public init(
        authRepository: AuthRepository,
        someOtherUseCase: SomeOtherUseCase
    ) {
        self.authRepository = AuthRepository
        self.someOtherUseCase = someOtherUseCase
    }

    public func execute(username: String, password: String) async throws {
        try await someOtherUseCase.execute()
        try await authRepository.login(username: username, password: password)
    }
}
```
- You can then register your use case in the application layer in `DependencyInjection/UseCase+Injection.swift`
```
public extension Resolver {
    static func registerUseCases() {

        // ...

        register { LoginUseCaseImpl(authRepository: resolve(), someOtherUseCase: resolve()) as LoginUseCase }

        // ...
    }
}
```

#### Repositories
- We define repositories under the `Repositories` directory in each logical part
- The domain layer defines protocols for these repositories – functions and their interfaces
- You should use CRUD naming for repository functions that handle objects
- Repository example:
```
public protocol AuthRepository {
    func login(username: String, password: String) async throws
    func logout() async throws
    func register(username: String, password: String) async throws
}
```
- The data layer provides repository implementations, as those are dependent on more data-level stuff

### Data Layer
- Provides required data via Repositories and Providers from database / network / etc.
- Our data layer is separated into `Toolkits` and `Providers`
- There is a toolkit for every logical part of the domain layer defining a repository protocol
- These toolkits provide repository implementations and relevant `NetworkModels`, `DatabaseModels`, `NetworkEndpoints`, etc.
- `Providers` define provider protocols and implementations
- You should also stick with CRUD naming in the entire data layer

#### Providers and their implementations
- We use providers for handling each data source
- A provider is defined as a protocol
- Each provider can have multiple implementations, for example, one using a third-party library, and another one using our own custom implementation
- Dependency Injection is again responsible for selecting the correct implementation
- Provider example:
```
public protocol DatabaseProvider {
    func read<T>(_ type: T.Type, id: Int) throws -> T
    func update<T>(_ object: T, model: UpdateModel) throws –> T
    func delete<T>(_ object: T) throws
    func deleteAll() throws
}
```
- Provider implementation example:
```
public struct RealmDatabaseProvider {

    // ... some setup and context ...
}

extension RealmDatabaseProvider: DatabaseProvider {
    public func read<T>(_ type: T.Type, id: Int) throws -> T {
        // ...
        if let object = realm.object(ofType: realmType.self, forPrimaryKey: id) as? T {
            return object
        } else {
            throw SomeError
        }
    }

    // ...
}
```
- Just like with use cases, you register the provider implementation in the application layer in `DependencyInjection/Providers+Injection.swift`

#### Repository implementations
- Repository implementations use providers and add some business logic
- They're independent of the specific provider implementation
- Repository implementation example:
```
public struct AuthRepositoryImpl {

    private let databaseProvider: DatabaseProvider
    private let networkProvider: NetworkProvider

    public init(
        databaseProvider: DatabaseProvider,
        networkProvider: NetworkProvider
    ) {
        self.databaseProvider = databaseProvider
        self.networkProvider = networkProvider
    }
}

extension AuthRepositoryImpl: AuthRepository {
    public func login(username: String, password: String) async throws {
        let endpoint = AuthAPI.login(username: Username, password: Password)
        try await netowrk.request(endpoint)
    }

    public func logout() async throws {
        try database.deleteAll()
    }

    // ...
}
```
- And again, you register the repository implementation in the application layer in `DependencyInjection/Repositories+Injection.swift`

#### DTO models
- DTO Models used for networking, database etc. are defined under `NetworkModels`, `DatabaseModels`, ...
- If needed, we also define conversions between them and their domain model equivalents in the same file
- DTO model example:
```
struct NETUser {
    let t_name: String
    let t_surname: String
    let t_gender: Gender
    let t_title: Title?
}

// Conversion from NetworkModel to DomainModel
extension NETUser: DomainRepresentable {
    typealias DomainModel = User

    var domainModel: DomainModel {
        User(
            name: t_name,
            surname: t_surname,
            gender: t_gender,
            title: t_title
        )
    }
}

// Conversion from DomainModel to NetworkModel
extension User: NetworkRepresentable {
    typealias NetworkModel = NETUser

    ver networkModel: NetworkModel {
        NETUser(
            t_name: name,
            t_surname: surname,
            t_gender: gender,
            t_title: title
        )
    }
}
```
