# Logger

A simple swift-wrapper around [c-logger](https://github.com/yksz/c-logger). This is useful if you need a logging library, that works across C, Objectice-C and Swift. C-logger does implement the logging with macros, which is [not supported](https://developer.apple.com/documentation/swift/imported_c_and_objective-c_apis/using_imported_c_macros_in_swift) in Swift. Therefore helper functions around these macros are provided for Swift, such as `logInfo` or `logError`.

**Step 1: Initialize the logger:**

``` Swift
// Flush every 5 seconds
logger_autoFlush(5000) 
// Init the console logger
logger_initConsoleLogger(nil)
// Init the file logger with a 5MB limit per file
logger_initFileLogger("Some/Path/To/A/LogFile, 1024*1024*5, 5)
// You can use the rest of the C-API as well
```

**Step 2: Usage in Swift:**

``` Swift
// Since swift does not support C Macros, use the helper functions
let myValue = 3
logInfo("Some string with value: \(myValue)")
```

**Step 3: Usage in C or Objective-C**
```C
int myValue = 3; 
LOG_INFO("Some string with value: %d", myValue);
