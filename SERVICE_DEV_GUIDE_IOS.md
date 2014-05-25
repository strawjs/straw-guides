# Plugin Development Guide for Straw iOS

## Concept

Straw iOS Service consists of two parts; Native part and JS part.

Native part is a native implementation of service. And it includes actual service procedures.

JS part is the interface of the native implementation of the service in the WebView.


## Prerequisite

- :potable_water: xcode 5.1 or higher
- :red_circle: ruby 1.9.3 or higher
- :green_apple: node.js 0.8 or higher
- :o2: cocoapods
```
gem install cocoapods
```
- :custard: xctool 0.1.5 or higher (optional)
- :tropical_drink: gulp or :boar: grunt (optional)

## Steps

### Build Native part

**1. Create `Cocoa Touch Static Library` project with Xcode.**

**1.2. Change the scheme shared (for ci).**

**2. Add Straw pod.**

```ruby
pod 'Straw', :git => 'https://github.com/strawjs/straw-ios.git', :tag => 'v0.3.5'
```

**3. Implement Service class which confirms to `STWService`.**

```objective-c
#include <Straw/Straw.h>

@interface MYServiceFooBar : NSObject <STWService>
...
@end
```

```objective-c
@implementation MYServiceFooBar

- (NSString *)name {...}
- (BOOL)isBackgroundJob:(NSString *)method {...}

// Service Method
- (void)foo:(NSDictionary *)params withContext:(id<STWServiceCallContext>)context {...}
- (void)bar:(NSDictionary *)params withContext:(id<STWServiceCallContext>)context {...}

@end
```

**4. Add tests.**

**5. Add .podspec.**

### Build JS part
