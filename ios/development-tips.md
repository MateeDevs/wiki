# Matee Wiki - iOS - Development tips based on often mistakes

## User interface
- Whenever you're writing code for the UI, stick to the provided design
    - Your UI can differ in some minor areas, but always make sure that you have a good reason for it, which you should explain, for example, in the PR description
- Always make sure that your UI is well-designed **for all screen sizes** and **both light modes** – it is a good practice to test your UI on the 1st gen iPhone SE and on some larger iPhone
- If your task is focused on the UI creation only, it is appropriate to also provide an empty view model ready for the connection to use cases
    - All your UI components should also be ready to be connected, so that the next developer connecting the UI to use cases doesn't have to bother with the UI at all
- Whenever you need to create a new UI component, always check that such a component hasn't already been created in the app, or that such a component isn't provided by the system or some library that we're using
- Whenever you're displaying a set of data that comes in `Pages`, make sure to handle that correctly
- All of these rules can be broken sometimes, but there must be a good reason for it

## Localization, fonts and styles
- Do not use hard-coded strings in places where you should use localization instead
    - Hard coded strings are allowed in previews and mocks
- When you find yourself needing to add a new string to Twine, always make sure that such a string hasn't been added already and try to coordinate yourself with the Android team
    - Make sure to always push your Twine changes, so that other devs and the CI/CD can see them
- When you're using fonts and styles that are used in more places in the app, don't specify them explicitly in your views, but use the defined fonts and styles
    - If you're designing some new components and their styles, consider defining some of that stuff in Assets, AppTheme, etc.
    - If some fonts and styles are specific for your view only, it's OK to specify them explicitly in your views

## Edge cases, loading, and errors
- Always test how your implementation handles edge cases, such as:
    - Bad internet connection
    - No internet connection
    - Unstable internet connection (disabled during some execution etc.)
    - Interacting with the UI unexpectedly
    - Executing your functionalities with edge values
    - ...
- Make sure that your views display loading indicators correctly, test it with a slow internet connection
- Also, make sure that your views handle errors correctly – whenever some use case fails, the user should be informed (Whisper, Alert, ...), and they should be able to carry on

## Naming and hierarchy
- Make sure to keep consistent naming and place your newly created files correctly into the file hierarchy
- Files with classes should have the same name as the class defined in that file
- Remember that each class needs to have a unique name in the package, so name your classes with that in mind, for example – you may want to define an input field for onboarding views, but a different input field for some form in settings, so the naming should be `OnboardingInputFieldView` and `SettingsInputFieldView`
    - The same goes for your subviews – if you want to create a subview for your `LoginView`, it should be named `LoginSubview` and not just `Subview`, because that subview belongs only to the `LoginView`
- If you're not sure where to place your implementation, always seek inspiration in other files, because you'll probably find answers there

## Layer responsibility
- Make sure that you implement your code in the correct layer in the clean architecture to avoid stuff like:
    - Using localization in the Domain Layer (localization is a responsibility of the Presentation Layer)
    - Writing extensions used in different layers (you can have an extension to a single type in each layer if necessary)
    - Using third-party libraries outside of the Data Layer
        - This obviously doesn't apply to UI frameworks, dependency injection (`Resolver`), `RxSwift`, and some other stuff

## Access control
- Always make sure you're using the correct access modifiers:
    - Stuff defined in a class and used only by it should be private
    - Stuff used within a package should be internal
    - Stuff used outside of a package should be public (open if subclassing is allowed)
    - ...