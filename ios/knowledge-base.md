# Matee Wiki - iOS - Knowledge base

## Introduction
- This a curated list of links to articles, blogposts and examples related to the iOS part of [Matee DevStack](https://github.com/MateeDevs/devstack-native-app).
- Those marked with :star: are a must-read for everybody! :nerd_face:
- Pull Requests are always welcomed. :wave:

## Swift
- :star: [Swift 3 Access Controls](https://useyourloaf.com/blog/swift-3-access-controls/) - Basics of access control in Swift
- :star: [Swift Guide to Map Filter Reduce](https://useyourloaf.com/blog/swift-guide-to-map-filter-reduce/) - Nice guide to basic functional operators
- :star: [Capturing Self with Swift 4.2](https://benscheirman.com/2018/09/capturing-self-with-swift-4-2/) - What is a retain cycle and how to avoid them
- [Automatic Reference Counting](https://docs.swift.org/swift-book/LanguageGuide/AutomaticReferenceCounting.html) - Memory management in Swift
- [You don’t (always) need [weak self]](https://medium.com/flawless-app-stories/you-dont-always-need-weak-self-a778bec505ef) - When to use [weak self]
- [The Official raywenderlich.com Swift Style Guide](https://github.com/raywenderlich/swift-style-guide) - Our default Swift style guide
- [Swift Documentation](https://nshipster.com/swift-documentation/) - How to properly document your code

## Async / await
- :star: [Async await in Swift](https://www.avanderlee.com/swift/async-await) - Introduction into async / await in Swift
- :star: [Using the MainActor attribute](https://www.swiftbysundell.com/articles/the-main-actor-attribute) - Introduction to `@MainActor` attribute
- [RxSwift Concurrency](https://github.com/ReactiveX/RxSwift/blob/main/Documentation/SwiftConcurrency.md) - How to consume RxSwift using async / await

## App architecture
- :star: [Good iOS Application Architecture](https://slideslive.com/38897361/good-ios-application-architecture-en) - Overview of commonly used app architectures ([updated version from 2018](https://youtu.be/PdkWjdKOqfo))
- :star: [Clean Architecture and MVVM on iOS](https://tech.olx.com/clean-architecture-and-mvvm-on-ios-c9d167d9f5b3) - Introduction into Clean Architecture principles
- :star: [SwiftUI is Model View Intent (MVI)](https://zoewave.medium.com/swiftui-is-model-view-intent-mvi-fd142b12fc81) - Introduction into Model-View-Intent architecture
- [SwiftUI - MVI Architecture](https://betterprogramming.pub/mvi-architecture-for-swiftui-apps-cff44428394) - Example of using MVI with SwiftUI
- [fantastic ios architecture](https://github.com/onmyway133/fantastic-ios-architecture) - Exhaustive list of all iOS app architecture related materials

## Dependency Injection
- :star: [Resolver for iOS Dependency Injection](https://www.raywenderlich.com/22203552-resolver-for-ios-dependency-injection-getting-started) - Explanation of Dependency Injection and its example using Resolver
- [Avoiding singletons in Swift](https://www.swiftbysundell.com/articles/avoiding-singletons-in-swift/) - Why singletons are bad and how to avoid them
- [Using protocol composition for dependency injection](http://merowing.info/2017/04/using-protocol-compositon-for-dependency-injection/) - Simple dependency injection with Dependencies typealias

## Modularisation
- :star: [Modular Architecture in iOS](https://tech.olx.com/modular-architecture-in-ios-c1a1e3bff8e9) - Introduction into principles of modularisation
- [The structure of a Swift Package](https://tiagolopes.blog/2022/01/16/the-structure-of-a-swift-package) - How to create Swift Packages
- [PresentationDomainDataLayering](https://martinfowler.com/bliki/PresentationDomainDataLayering.html) - Different approaches to modularisation in Clean Architecture

## Flow controllers
- :star: [Improve your iOS Architecture with FlowControllers](http://merowing.info/2016/01/improve-your-ios-architecture-with-flowcontrollers/) - Introduction into the flow controllers concept
- [Flow Coordinators in iOS](https://medium.com/@dkw5877/flow-coordinators-333ed64f3dd) - More in-depth article about the flow controllers
- [Back Buttons and Coordinators](http://khanlou.com/2017/05/back-buttons-and-coordinators/) - How to handle back buttons in flow controllers

## SwiftUI
- :star: [Introducing SwiftUI](https://developer.apple.com/tutorials/swiftui) - Official SwiftUI tutorial from Apple
- :star: [SwiftUI State Management Fundamentals](https://mykola-harmash.medium.com/swiftui-state-management-fundamentals-5b28d2522e4d) - A beginner’s guide to @State, @StateObject and @ObservedObject
- :star: [Encapsulating SwiftUI view styles](https://www.swiftbysundell.com/articles/encapsulating-swiftui-view-styles/) - Introduction into SwiftUI encapsulation and modifiers
- [Redacted View Modifier](https://www.avanderlee.com/swiftui/redacted-view-modifier/) - How to use the Redacted View Modifier in SwiftUI to create skeletons
- [Fucking SwiftUI](https://fuckingswiftui.com) - Cheatsheet of UIKit equivalents in SwiftUI
- [SwiftUI by Example](https://www.hackingwithswift.com/quick-start/swiftui/) - Biggest collection of SwiftUI tutorials and examples
- [SwiftUI Architectures: Model-View, Redux & MVVM](https://quickbirdstudios.com/blog/swiftui-architecture-redux-mvvm/) - Overview of using common app architectures with SwiftUI

## UIKit
- :star: [Solving duplicated / repeating cells in Table view](https://fluffy.es/solve-duplicated-cells/) - How cell reusing in UITableView works
- :star: [Scroll View Layouts With Interface Builder](https://useyourloaf.com/blog/scroll-view-layouts-with-interface-builder/) - Proper way to setup UIScrollView
- :star: [Container View Controllers](https://useyourloaf.com/blog/container-view-controllers/) - How to split massive view controller into multiple view controllers
- [Self-sizing Child Views](https://useyourloaf.com/blog/self-sizing-child-views/) - Automatic height adjustment when composing views
- [Auto layout magic: Content sizing priorities](https://krakendev.io/blog/autolayout-magic-like-harry-potter-but-real) - Content hugging vs content compression resistance
- [How To Adopt Dark Mode In Your iOS App](https://www.fivestars.blog/code/ios-dark-mode-how-to.html) - Everything you need to know about the dark-mode

## Database
- :star: [Realm property cheatsheet](https://www.mongodb.com/docs/realm/sdk/swift/model-data/define-model/supported-types/#property-cheat-sheet) - How to define different properties in Realm models
- [Examples of NSPredicate usage](https://nspredicate.xyz/) - When you need to adjust your database query
- [NSPredicate Cheatsheet](https://academy.realm.io/posts/nspredicate-cheatsheet/) - List of all operators usable in database queries

## Debugging
- :star: [Intermediate Debugging with Xcode 8](https://www.raywenderlich.com/721-intermediate-debugging-with-xcode-8) - Introduction to Xcode Debugger
- :star: [Breakpoints in Proxyman](https://proxyman.io/posts/2019-09-15-Use-Breakpoint-to-intercept-and-edit-request-response-on-iOS-app) - How to intercept and edit HTTP request/response
- [Locating the source of a memory leak](https://medium.com/@xcadaverx/locating-the-source-of-a-memory-leak-712667bf8cd5) - How to find memory leaks in Xcode Debugger
- [LifetimeTracker](https://github.com/krzysztofzablocki/LifetimeTracker) - Simple library for finding memory leaks and retain cycles

## Testing
- :star: [Testing iOS Apps](http://merowing.info/2017/01/testing-ios-apps/) - Basic overview of testing iOS apps
- [Test Driven Development Tutorial for iOS](https://www.raywenderlich.com/5522-test-driven-development-tutorial-for-ios-getting-started) - How to start with TDD
- [Language without Mocking Frameworks](https://blog.pragmaticengineer.com/swift-the-only-modern-language-with-no-mocking-framework/) - Why we don't have a mocking framework
- [Code Generating Swift Mocks with Sourcery](https://www.vadimbulavin.com/mocking-in-swift-using-sourcery/) - How to generate mocks

## Continuous Integration
- :star: [Git process that works](https://reallifeprogramming.com/git-process-that-works-say-no-to-gitflow-50bf2038ccf7) - Simplified GitFlow that we are using on most of our projects
- [Testing & CI on iOS](https://slideslive.com/38897365/testing-ci-on-ios-cz) - Nice introduction into the fastlane (13:20 - 28:45)
- [fastlane - match](https://docs.fastlane.tools/actions/match/) - fastlane essentials 1/3 - sign your app
- [fastlane - gym](https://docs.fastlane.tools/actions/gym/) - fastlane essentials 2/3 - build your app
- [fastlane - pilot](https://docs.fastlane.tools/actions/pilot/) - fastlane essentials 3/3 - distribute your app
- [GitHub Actions Documentation](https://help.github.com/en/actions) - Everything you need to know about GitHub Actions

## Other materials
- [iOS-factor](https://ios-factor.com/) - Set of best practices for writing iOS apps
- [Awesome iOS](https://github.com/vsouza/awesome-ios) - Probably the biggest up-to-date list of all available iOS libraries and frameworks
- [The Ultimate Guide To iPhone Resolutions](https://www.paintcodeapp.com/news/ultimate-guide-to-iphone-resolutions) - Useful when you need to check iPhone resolution etc.

## RxSwift (deprecated)
- :warning: We are replacing RxSwift with async / await and Combine
- :star: [Thinking in RxSwift](http://adamborek.com/thinking-rxswift/) - Cool introduction into RxSwift
- :star: [Memory management in RxSwift – DisposeBag](http://adamborek.com/memory-managment-rxswift/) - How disposing in RxSwift works
- :star: [Better Error Handling With CompactMap](https://medium.com/@michaellong/rxswift-better-error-handling-with-compactmap-48a5d314d0f1) - How to handle errors easily in RxSwift
- :star: [RxSwift + MVVM: how to feed ViewModels](https://medium.com/blablacar-tech/rxswift-mvvm-66827b8b3f10) - How to design RxSwift based ViewModels with inputs and outputs
- [Surviving RxSwift](https://medium.com/better-programming/surviving-rxswift-d6bfe562fb22) - Best practices to not get overwhelmed by RxSwift
- [RxSwift Made Easy: Working with Subjects](https://medium.com/swift2go/rxswift-part-2-working-with-subjects-34e35a058a2c) - Everything you need to know about RxSwift subjects
- [Top mistakes in RxSwift you want to avoid](http://adamborek.com/top-7-rxswift-mistakes/) - Just don't do this!
- [RxTest & MVVM](https://benoitpasquier.com/how-to-use-rxtests-to-test-mvvm/) - How to test ViewModels with RxTests
- [Testing Your RxSwift Code](https://www.raywenderlich.com/7408-testing-your-rxswift-code) - More complex RxSwift testing tutorial
