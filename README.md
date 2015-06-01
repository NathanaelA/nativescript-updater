# NativeScript Realtime Updater

A NativeScript module providing real time development for Android and (hopefully soon) iOS applications.


## Realtime Editing Demo
[![Video Showing off Realtime Development Ability](http://img.youtube.com/vi/cCiyJZexSOQ/0.jpg)](http://www.youtube.com/watch?v=cCiyJZexSOQ)


## Installation

Run `npm install jshint -g`
Run `npm install nativescript-updater --save` from inside your project's `app` directory:

```
.
├── app <------------------------------ run npm install from inside here
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


## Usage

To use the updater module you must first `require()` it from your project's `node_modules` directory:

```js
var updater = require( "./node_modules/nativescript-updater/updater" );
```

If you put this in your **app.js** like so:
```js
var application = require("application");
application.mainModule = "main-page";
// ----- MODIFY THIS LINE -----
application.cssFile = "app.css"; // this was "./app.css"
// ----------------------------

// ---- ADD THIS LINE ----
require('./node_modules/nativescript-updater/updater');
// -----------------------

application.start();
```

Then this will activate at the start of the application and work for the entire time, also notice the removal of the "./" in the cssFile.  

You will also want to copy the "support" folder files to your main folder as it will contain a jslintrc file, and the nifty watcher.js file that you run at the start of your development.
