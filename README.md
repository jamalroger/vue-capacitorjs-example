# How to transform any SPA/PWA web application into mobile app with CapacitorJs ??

Hi all,web development become more powerful, web now is more easy we can build complex application with technology like Angular, VueJs and react those technology can build ``SPA/PWA``.

What is ``SPA/PWA/Capacitorjs??`` ``SPA`` is short of "single page application"  is web application that can run in one page in the browser , the app don't need refresh to post or fetch data, we ajax nested of refreshing.

``PWA`` is a ``SPA`` with capacity of work offline with "service worker" that cache asset file(js,css) in the browser means no need to download asset file from http server in the second request.

``CapacitorJs`` is a cross-platform native runtime for web apps, means can transform web application into mobile app and run it in ``os``, it take SPA/PWA and run it on a ``WebView`` in native application this native application can run anywhere in any os mobile like android and ios.

let take a example  with a ``VueJs`` app
we suppose that you have already had a ``Vuejs`` app
if you don't now how to create a vue app please read this article [Get started with Vuejs](https://dev.to/josesrodriguez610/vuejs-starting-a-new-project-ke1)

#The structure of Vue projet is like  this
![Alt Text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/bku4lc4zzvx9rp673mzo.png)

when you build your vuejs app you will find dist that contains  of entrypoint of your ``SPA``
![Alt Text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/879yod14nvi5m5e5469g.png)
if you open index.html in the browser  will run your app,
``note`` "verify the the path of assets in index.html"

Now let add ``CapacitorJs`` to our vue app.

#Installing capacitorjs
```shell
npm install @capacitor/core @capacitor/cli
```

#Init app for CapacitorJs
```shell
npx cap init 
```
this command should ask about your name  of your app,ID,...
and will generate capacitor.config.json for Capacitorjs config  should be like that
```json
{
  "appId": "com.app.app",
  "appName": "app",
  "bundledWebRuntime": false,
  "npmClient": "npm",
  "webDir": "www",
  "plugins": {
    "SplashScreen": {
      "launchShowDuration": 0
    }
  },
  "cordova": {}
}
```
we will edit the value of attribute ``webDir``  from ``www`` into ``dist`` because Vuejs  build your app into dist folder 

now should will be like that 

```json
{
  "appId": "com.app.app",
  "appName": "app",
  "bundledWebRuntime": false,
  "npmClient": "npm",
  "webDir": "dist",
  "plugins": {
    "SplashScreen": {
      "launchShowDuration": 0
    }
  },
  "cordova": {}
}
```

Now will should add platform can be android,ios or electron.
#Let start with android


```shell
npx cap add android
```

That should create android folder in your root folder
![Alt Text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/88et2mh188usc945po5g.png)

Now let sync our web app with the android app

```
npx cap sync
```
by run this command will copy the dist folder to android app

![Alt Text](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/prjx0up32fe0ud48rxki.png)

Now our app is ready to run in android by open ``android`` folder in ``android studio`` and build our apk.

you can find the source code here [vue-capacitorjs-example](https://github.com/jamalroger/vue-capacitorjs-example)
 
Sorry for my bad English, Thanks you for reading.










   
