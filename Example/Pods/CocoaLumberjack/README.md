<p align="center" >
  <img src="https://raw.githubusercontent.com/CocoaLumberjack/CocoaLumberjack/master/LumberjackLogo.png" title="Lumberjack logo" float=left>
</p>

CocoaLumberjack
===============
![Unit Tests](https://github.com/CocoaLumberjack/CocoaLumberjack/workflows/Unit%20Tests/badge.svg)
[![Pod Version](http://img.shields.io/cocoapods/v/CocoaLumberjack.svg?style=flat)](http://cocoadocs.org/docsets/CocoaLumberjack/)
[![Carthage compatible](https://img.shields.io/badge/Carthage-compatible-4BC51D.svg?style=flat)](https://github.com/Carthage/Carthage)
[![Pod Platform](http://img.shields.io/cocoapods/p/CocoaLumberjack.svg?style=flat)](http://cocoadocs.org/docsets/CocoaLumberjack/)
[![Pod License](http://img.shields.io/cocoapods/l/CocoaLumberjack.svg?style=flat)](http://opensource.org/licenses/BSD-3-Clause)
[![codecov](https://codecov.io/gh/CocoaLumberjack/CocoaLumberjack/branch/master/graph/badge.svg)](https://codecov.io/gh/CocoaLumberjack/CocoaLumberjack)
[![codebeat badge](https://codebeat.co/badges/840b714a-c8f3-4936-ada4-363473cd4e6b)](https://codebeat.co/projects/github-com-cocoalumberjack-cocoalumberjack-master)


**CocoaLumberjack** is a fast & simple, yet powerful & flexible logging framework for Mac and iOS.

### How to get started

First, install CocoaLumberjack via [CocoaPods](http://cocoapods.org), [Carthage](https://github.com/Carthage/Carthage), [Swift Package Manager](https://swift.org/package-manager/) or manually.
Then use `DDOSLogger` for iOS 10 and later, or `DDTTYLogger` and `DDASLLogger` for earlier versions to begin logging messages.

#### CocoaPods

```ruby
platform :ios, '8.0'

target 'SampleTarget' do
  use_frameworks!
  pod 'CocoaLumberjack/Swift'
end
```
Note: `Swift` is a subspec which will include all the Obj-C code plus the Swift one, so this is sufficient.
For more details about how to use Swift with Lumberjack, see [this conversation](https://github.com/CocoaLumberjack/CocoaLumberjack/issues/405).

For Objective-C use the following:
```ruby
platform :ios, '8.0'

target 'SampleTarget' do
    pod 'CocoaLumberjack'
end
```

#### Carthage

Carthage is a lightweight dependency manager for Swift and Objective-C. It leverages CocoaTouch modules and is less invasive than CocoaPods.

To install with Carthage, follow the instruction on [Carthage](https://github.com/Carthage/Carthage)

Cartfile
```
github "CocoaLumberjack/CocoaLumberjack"
```


#### Swift Package Manager

As of CocoaLumberjack 3.6.0, you can use the Swift Package Manager as integration method.
If you want to use the Swift Package Manager as integration method, either use Xcode to add the package dependency or add the following dependency to your Package.swift:

```swift
.package(url: "https://github.com/CocoaLumberjack/CocoaLumberjack.git", from: "3.6.0"),
```

#### Install manually

If you want to install CocoaLumberjack manually, read the [manual installation](https://raw.githubusercontent.com/CocoaLumberjack/CocoaLumberjack/master/Documentation/GettingStarted.md#manual-installation) guide for more information.

#### Swift Usage

Usually, you can simply `import CocoaLumberjackSwift`. If you installed CocoaLumberjack using CocoaPods, you need to use `import CocoaLumberjack` instead.

```swift
DDLog.add(DDOSLogger.sharedInstance) // Uses os_log

let fileLogger: DDFileLogger = DDFileLogger() // File Logger
fileLogger.rollingFrequency = 60 * 60 * 24 // 24 hours
fileLogger.logFileManager.maximumNumberOfLogFiles = 7
DDLog.add(fileLogger)

...

DDLogVerbose("Verbose")
DDLogDebug("Debug")
DDLogInfo("Info")
DDLogWarn("Warn")
DDLogError("Error")
```

#### Obj-C usage

If you're using Lumberjack as a framework, you can `@import CocoaLumberjack;`.
Otherwise, `#import <CocoaLumberjack/CocoaLumberjack.h>`

```objc
[DDLog addLogger:[DDOSLogger sharedInstance]]; // Uses os_log

DDFileLogger *fileLogger = [[DDFileLogger alloc] init]; // File Logger
fileLogger.rollingFrequency = 60 * 60 * 24; // 24 hour rolling
fileLogger.logFileManager.maximumNumberOfLogFiles = 7;
[DDLog addLogger:fileLogger];

...

DDLogVerbose(@"Verbose");
DDLogDebug(@"Debug");
DDLogInfo(@"Info");
DDLogWarn(@"Warn");
DDLogError(@"Error");
```

#### More information

- read the [Getting started](https://raw.githubusercontent.com/CocoaLumberjack/CocoaLumberjack/master/Documentation/GettingStarted.md) guide, check out the [FAQ](https://raw.githubusercontent.com/CocoaLumberjack/CocoaLumberjack/master/Documentation/FAQ.md) section or the other [docs](Documentation/)
- if you find issues or want to suggest improvements, create an issue or a pull request
- for all kinds of questions involving CocoaLumberjack, use the [Google group](http://groups.google.com/group/cocoalumberjack) or StackOverflow (use [#lumberjack](http://stackoverflow.com/questions/tagged/lumberjack)).


### CocoaLumberjack 3

#### Migrating to 3.x

* To be determined

### Features

#### Lumberjack is Fast & Simple, yet Powerful & Flexible.

It is similar in concept to other popular logging frameworks such as log4j, yet is designed specifically for Objective-C, and takes advantage of features such as multi-threading, grand central dispatch (if available), lockless atomic operations, and the dynamic nature of the Objective-C runtime.

#### Lumberjack is Fast

In most cases it is an order of magnitude faster than NSLog.

#### Lumberjack is Simple

It takes as little as a single line of code to configure lumberjack when your application launches. Then simply replace your NSLog statements with DDLog statements and that's about it. (And the DDLog macros have the exact same format and syntax as NSLog, so it's super easy.)

#### Lumberjack is Powerful:

One log statement can be sent to multiple loggers, meaning you can log to a file and the console simultaneously. Want more? Create your own loggers (it's easy) and send your log statements over the network. Or to a database or distributed file system. The sky is the limit.

#### Lumberjack is Flexible:

Configure your logging however you want. Change log levels per file (perfect for debugging). Change log levels per logger (verbose console, but concise log file). Change log levels per xcode configuration (verbose debug, but concise release). Have your log statements compiled out of the release build. Customize the number of log levels for your application. Add your own fine-grained logging. Dynamically change log levels during runtime. Choose how & when you want your log files to be rolled. Upload your log files to a central server. Compress archived log files to save disk space...

### This framework is for you if:

-   You're looking for a way to track down that impossible-to-reproduce bug that keeps popping up in the field.
-   You're frustrated with the super short console log on the iPhone.
-   You're looking to take your application to the next level in terms of support and stability.
-   You're looking for an enterprise level logging solution for your application (Mac or iPhone).

### Documentation

- **[Get started using Lumberjack](https://github.com/CocoaLumberjack/CocoaLumberjack/blob/master/Documentation/GettingStarted.md)**<br/>
- [Different log levels for Debug and Release builds](https://github.com/CocoaLumberjack/CocoaLumberjack/blob/master/Documentation/XcodeTricks.md)<br/>
- [Different log levels for each logger](https://github.com/CocoaLumberjack/CocoaLumberjack/blob/master/Documentation/PerLoggerLogLevels.md)<br/>
- [Use colors in the Xcode debugging console](https://github.com/CocoaLumberjack/CocoaLumberjack/blob/master/Documentation/XcodeColors.md)<br/>
- [Write your own custom formatters](https://github.com/CocoaLumberjack/CocoaLumberjack/blob/master/Documentation/CustomFormatters.md)<br/>
- [FAQ](https://github.com/CocoaLumberjack/CocoaLumberjack/blob/master/Documentation/FAQ.md)<br/>
- [Analysis of performance with benchmarks](https://github.com/CocoaLumberjack/CocoaLumberjack/blob/master/Documentation/Performance.md)<br/>
- [Common issues you may encounter and their solutions](https://github.com/CocoaLumberjack/CocoaLumberjack/blob/master/Documentation/ProblemSolution.md)<br/>
- [AppCode support](https://github.com/CocoaLumberjack/CocoaLumberjack/blob/master/Documentation/AppCode-support.md)
- **[Full Lumberjack documentation](Documentation/)**<br/>

### Requirements
The current version of Lumberjack requires:
- Xcode 11 or later
- Swift 5.0 or later
- iOS 8 or later
- macOS 10.10 or later
- watchOS 3 or later
- tvOS 9 or later

#### Backwards compatibility
- for Xcode 10 and Swift 4.2, use the 3.5.2 version
- for iOS 6, iOS 7, OS X 10.8, OS X 10.9 and Xcode 9, use the 3.4.2 version
- for iOS 5 and OS X 10.7, use the 3.3 version
- for Xcode 8 and Swift 3, use the 3.2 version
- for Xcode 7.3 and Swift 2.3, use the 2.4.0 version
- for Xcode 7.3 and Swift 2.2, use the 2.3.0 version
- for Xcode 7.2 and 7.1, use the 2.2.0 version
- for Xcode 7.0 or earlier, use the 2.1.0 version
- for Xcode 6 or earlier, use the 2.0.x version
- for OS X < 10.7 support, use the 1.6.0 version

### Communication

- If you **need help**, use [Stack Overflow](http://stackoverflow.com/questions/tagged/lumberjack). (Tag 'lumberjack')
- If you'd like to **ask a general question**, use [Stack Overflow](http://stackoverflow.com/questions/tagged/lumberjack).
- If you **found a bug**, open an issue.
- If you **have a feature request**, open an issue.
- If you **want to contribute**, submit a pull request.

### Author
- [Robbie Hanson](https://github.com/robbiehanson)
- Love the project? Wanna buy me a coffee? (or a beer :D) [![donation](http://www.paypal.com/en_US/i/btn/btn_donate_SM.gif)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=UZRA26JPJB3DA)

### Collaborators
- [Ernesto Rivera](https://github.com/rivera-ernesto)
- [Dmitry Vorobyov](https://github.com/dvor)
- [Bogdan Poplauschi](https://github.com/bpoplauschi)
- [C.W. Betts](https://github.com/MaddTheSane)
- [Koichi Yokota (sushichop)](https://github.com/sushichop)
- [Nick Brook](https://github.com/nrbrook)
- [Florian Friedrich](https://github.com/ffried)
- [Stephan Diederich](https://github.com/diederich)
- [Kent Sutherland](https://github.com/ksuther)
- [Dmitry Lobanov](https://github.com/lolgear)
- [Hakon Hanesand](https://github.com/hhanesand)

### License
- CocoaLumberjack is available under the BSD 3 license. See the [LICENSE file](https://github.com/CocoaLumberjack/CocoaLumberjack/blob/master/LICENSE).

### Extensions
- [LogIO-CocoaLumberjack](https://github.com/s4nchez/LogIO-CocoaLumberjack) A log.io logger for CocoaLumberjack
- [XCDLumberjackNSLogger](https://github.com/0xced/XCDLumberjackNSLogger) CocoaLumberjack logger which sends logs to NSLogger

### Architecture

<p align="center" >
    <img src="https://raw.githubusercontent.com/CocoaLumberjack/CocoaLumberjack/master/Documentation/CocoaLumberjackClassDiagram.png" title="CocoaLumberjack class diagram">
</p>
