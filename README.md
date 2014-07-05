Straw, a JS/Native bridge :tropical_drink: :tropical_drink:

----

> The guide to build application with Straw Framework.

# iOS

**Note**: This is one of the recommended ways. Using cocoapods and bower is optional. And you can replace `middleman` with any of your favorite static generators ( http://www.staticgen.com/ ).

## Prerequisites

- :potable_water: xcode 5.1 or higher
- :o2: cocoapods (ruby gem)
```
gem install cocoapods
```
- :man: middleman (ruby gem)
```
gem install middleman
```
- :baby_chick: bower (node module)
```
npm install bower -g
```

## Create Straw App

**1. Create iOS app with xcode wizard**

**2. Install straw-ios and straw-ios-services which you need as Pod dependency.**

Write in Podfile:
```ruby
platform :ios, "6.0"

pod 'Straw', :git => 'https://github.com/strawjs/straw-ios.git', :tag => 'v0.3.5'
```

**3. Init middleman in repository**

```sh
cd [App dir]
middleman init .
```

Set source dir and build dir.

Write in config.rb (middleman):
```
set :source, 'www-source'
set :build_dir, 'AppName/www'
```

**4. Install js-interfaces of straw-ios and straw-ios-services which you need as bower dependency.**

In command line:
```sh
bower init # create bower.json

bower install --save straw-ios=https://github.com/strawjs/straw-ios.js.git
bower install --save straw-ios-service-http=https://github.com/strawjs/straw-ios-service-http.js.git
```

**5. Load bower dependencies through asset pipe line in middleman.**

Write in config.rb (middleman):
```ruby
ready do
    sprockets.append_path File.join root, 'bower_components'
end
```

Write in all.js (in middleman source):
```js
//= require straw-ios
//= require straw-ios-service-http
```

Check with following steps:
- hit the command `middleman server` on the top of the repository.
- open http://localhost:4567/javascript/all.js
- check if straw-ios and services are loaded.

**6. Load `STWViewController` and `STWService`s in AppDelegate.**

Check with following steps:
- Run the app.
- Check if the middleman welcome page is loaded.
- Open OSX's safari.
- Attach to app's UIWebView ( like https://coderwall.com/p/fsywdg )
- Hit `straw` on console. If it's an object then it's ok, but if it's undefined then something is wrong.
- Hit `straw.service.http.get('http://www.example.com/').done(function (data) { console.log(data); });`
- If the html of www.exmple.com is shown then everything's ok otherwise something is wrong.

# Android

**Note**: This is one of the recommended ways. Using gradle and bower is optional. And you can replace `middleman` with any of your favorite static generators ( http://www.staticgen.com/ ).

## prerequisites

- :cactus: Android SDK
- :deciduous_tree: gradle
- :man: middleman (ruby gem)
```
gem install middleman
```
- :baby_chick: bower (node module)
```
npm install -g bower
```
