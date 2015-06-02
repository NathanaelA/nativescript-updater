# NativeScript Updater

**PLEASE NOTE** if you are looking for the Real Time Live Syncing for Development, I have changed that project name to LiveSync, and this project will become my original idea for a simple downloadable update system.
The LiveSync repo is at [http://www.github.com/NathanaelA/NativeScript-LiveSync](http://www.github.com/NathanaelA/NativeScript-LiveSync)

 A NativeScript module providing easy to deploy updates from your own web server(s).    


## License

All this code is (c)2015, Master Technology.   This is released under the MIT License, meaning you are free to include this in any type of program -- However for entities that need a support and/or a commercial license please contact me (nathan@master-technology.com).

I do contract work; so if you have a module you want built for NativeScript (or pretty much any other language) feel free to contact me.




## Installation

Run `npm install nativescript-updater --save` from inside your project's `app` directory:


```
├── app <------------------------------ run npm install from inside the app folder, here
│   ├── app.css
│   ├── app.js
│   ├── main-page.js
│   ├── main-page.xml
│   ├── node_modules
│   │   └── nativescript-updater <-- The install will place the module's code here
│   │       └── ...
│   ├── package.json <----------------- The install will register “nativescript-updater” as a dependency here
│   ├── App_Resources  
│   └── tns_modules
│       └── ...
├── lib
└── platforms
    ├── android
    └── ios
```

As is, using npm within NativeScript is still experimental, so it's possible that you'll run into some issues. A more complete solution is in the works, and you can check out [this issue](https://github.com/NativeScript/nativescript-cli/issues/362) for an update on its progress and to offer feedback.

If npm doesn't end up working for you, you can just copy and paste this repo's updater.android.js, and updater.ios.js files into your app and reference them directly.


## Usage & Running

To use the updater module you must first `require()` it from your project's `node_modules` directory:

```js
var updater = require( "./node_modules/nativescript-updater/updater" );
```

You should as a minimum put this in your **app.js** like so:
```js
var application = require("application");
application.mainModule = "main-page";
application.cssFile = "./app.css"; 

// ---- ADD THIS LINE ----
require('./node_modules/nativescript-updater/updater');
// -----------------------

application.start();
```

Then this will activate at the start of the application and process any updates that it has already downloaded.  


## Get the LiveSync object
```var updater = require('./node_modules/nativescript-updater/updater');```

### Methods

#### checkForUpdate(webPage)
##### Parameters
* webPage - web site to download changed from

#### enabled(value) 
##### Parameters
* (no parameter) will return if it is enabled
* (value) - set it to be enabled (true) or disabled (false)

#### debugMode(value)
##### Parameters 
* (no Parameter) will return if it is running in debugMode 
* (value) - set it to be forced into or out of debugMode, rather than letting it use the detection method.

#### getAppName()
This will return the package name in the from the AndroidManifest

#### getAppVersion()
This will return the VersionName from inside the AndroidManifest

#### restart()
This will fully restart the application 

#### checkForEmulator()
This will check to see if the app is running on a emulator

#### checkForDebugMode()
This will check to see if the app was signed with a debug key (i.e. debug mode)

#### isSuspended()
This will tell you if the application is suspended.  (i.e. some other app has focus)

#### currentAppPath()
This will return the current application path.
