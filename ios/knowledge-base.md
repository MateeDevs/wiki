# Matee Wiki - iOS - Knowledge base

## Introduction
- This a curated list of links to articles, blogposts and examples related to the [Matee iOS DevStack](https://github.com/MateeDevs/devstack-ios-app).
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

## RxSwift
- :star: [Thinking in RxSwift](http://adamborek.com/thinking-rxswift/) - Cool introduction into RxSwift
- :star: [Memory management in RxSwift – DisposeBag](http://adamborek.com/memory-managment-rxswift/) - How disposing in RxSwift works
- :star: [Better Error Handling With CompactMap](https://medium.com/@michaellong/rxswift-better-error-handling-with-compactmap-48a5d314d0f1) - How to handle errors easily in RxSwift
- [Surviving RxSwift](https://medium.com/better-programming/surviving-rxswift-d6bfe562fb22) - Best practices to not get overwhelmed by RxSwift
- [RxSwift Made Easy: Working with Subjects](https://medium.com/swift2go/rxswift-part-2-working-with-subjects-34e35a058a2c) - Everything you need to know about RxSwift subjects
- [Top mistakes in RxSwift you want to avoid](http://adamborek.com/top-7-rxswift-mistakes/) - Just don't do this!

## App architecture
- :star: [Good iOS Application Architecture](https://slideslive.com/38897361/good-ios-application-architecture-en) - Overview of commonly used app architectures ([updated version from 2018](https://youtu.be/PdkWjdKOqfo))
- :star: [Clean Architecture and MVVM on iOS](https://tech.olx.com/clean-architecture-and-mvvm-on-ios-c9d167d9f5b3) - Introduction into Clean Architecture principles
- :star: [RxSwift + MVVM: how to feed ViewModels](https://medium.com/blablacar-tech/rxswift-mvvm-66827b8b3f10) - How to design ViewModels with inputs and outputs
- :star: [Using protocol compositon for dependency injection](http://merowing.info/2017/04/using-protocol-compositon-for-dependency-injection/) - Simple dependency injection with Dependencies typealias
- :star: [The structure of a Swift Package](https://tiagolopes.blog/2022/01/16/the-structure-of-a-swift-package) - How to create Swift Packages
- [Avoiding singletons in Swift](https://www.swiftbysundell.com/articles/avoiding-singletons-in-swift/) - Why singletons are bad and how to avoid them
- [fantastic ios architecture](https://github.com/onmyway133/fantastic-ios-architecture) - Exhaustive list of all iOS app architecture related materials

## Flow controllers
- :star: [Improve your iOS Architecture with FlowControllers](http://merowing.info/2016/01/improve-your-ios-architecture-with-flowcontrollers/) - Introduction into the flow controllers concept
- [Flow Coordinators in iOS](https://medium.com/@dkw5877/flow-coordinators-333ed64f3dd) - More in-depth article about the flow controllers
- [Back Buttons and Coordinators](http://khanlou.com/2017/05/back-buttons-and-coordinators/) - How to handle back buttons in flow controllers

## Database
- :star: [Realm property cheatsheet](https://realm.io/docs/swift/latest/#property-cheatsheet) - How to define different properties in Realm models
- [Examples of NSPredicate usage](https://nspredicate.xyz/) - When you need to adjust your database query
- [NSPredicate Cheatsheet](https://academy.realm.io/posts/nspredicate-cheatsheet/) - List of all operators usable in database queries

## SwiftUI
- :star: [Introducing SwiftUI](https://developer.apple.com/tutorials/swiftui) - Official SwiftUI tutorial from Apple
- [SwiftUI by Example](https://www.hackingwithswift.com/quick-start/swiftui/) - Biggest collection of SwiftUI tutorials and examples
- [SwiftUI Architectures: Model-View, Redux & MVVM](https://quickbirdstudios.com/blog/swiftui-architecture-redux-mvvm/) - Overview of using common app architectures with SwiftUI
- [MovieSwiftUI](https://github.com/Dimillian/MovieSwiftUI) - Example app using SwiftUI and Combine

## UIKit
- :star: [Solving duplicated / repeating cells in Table view](https://fluffy.es/solve-duplicated-cells/) - How cell reusing in UITableView works
- :star: [Scroll View Layouts With Interface Builder](https://useyourloaf.com/blog/scroll-view-layouts-with-interface-builder/) - Proper way to setup UIScrollView
- :star: [Container View Controllers](https://useyourloaf.com/blog/container-view-controllers/) - How to split massive view controller into multiple view controllers
- [Self-sizing Child Views](https://useyourloaf.com/blog/self-sizing-child-views/) - Automatic height adjustment when composing views
- [Auto layout magic: Content sizing priorities](https://krakendev.io/blog/autolayout-magic-like-harry-potter-but-real) - Content hugging vs content compression resistance
- [How To Adopt Dark Mode In Your iOS App](https://www.fivestars.blog/code/ios-dark-mode-how-to.html) - Everything you need to know about the dark-mode
- [Backwards compatibility for iOS 13 system colors](https://noahgilmore.com/blog/dark-mode-uicolor-compatibility/) - How to use new dark-mode colors on older versions of iOS
- [Easy Skeezy Date Formatting for Swift and Objective-C](https://nsdateformatter.com/) - Helper for checking your date formatting

## Debugging
- :star: [Intermediate Debugging with Xcode 8](https://www.raywenderlich.com/721-intermediate-debugging-with-xcode-8) - Introduction to Xcode Debugger
- :star: [Breakpoints in Proxyman](https://proxyman.io/blog/2019/08/Use-Breakpoint-to-intercept-and-edit-request-response-on-iOS-app.html) - How to intercept and edit HTTP request/response
- [Locating the source of a memory leak](https://medium.com/@xcadaverx/locating-the-source-of-a-memory-leak-712667bf8cd5) - How to find memory leaks in Xcode Debugger
- [LifetimeTracker](https://github.com/krzysztofzablocki/LifetimeTracker) - Simple library for finding memory leaks and retain cycles

## Testing
- :star: [Testing iOS Apps](http://merowing.info/2017/01/testing-ios-apps/) - Basic overview of testing iOS apps
- :star: [RxTest & MVVM](https://benoitpasquier.com/how-to-use-rxtests-to-test-mvvm/) - How to test ViewModels with RxTests
- [Testing Your RxSwift Code](https://www.raywenderlich.com/7408-testing-your-rxswift-code) - More complex RxSwift testing tutorial
- [Test Driven Development Tutorial for iOS](https://www.raywenderlich.com/5522-test-driven-development-tutorial-for-ios-getting-started) - How to start with TDD
- [Language without Mocking Frameworks](https://blog.pragmaticengineer.com/swift-the-only-modern-language-with-no-mocking-framework/) - Why we don't have a mocking framework

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
- [WWDC 2020 Viewing Guide](https://useyourloaf.com/blog/wwdc-2020-viewing-guide/) - Best sessions from WWDC 2020
