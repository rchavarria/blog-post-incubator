# learning-ionic-2

A small project for learning the Ionic 2 framework (Angular 2, TypeScript, Cordova, Android)

## Introduction

- What is it Ionic?
- Ionic 2?
- I discovered it during Angular Connect conference, and I was looking forward to test it since then

## Requirements

a. Install/Update latest version of Android SDK (Android SDK tools v24.x)

`<android sdk>/tools/android sdk`

b. Install a recent version of NodeJS? (v5.0.0)

c. Update to a newer version of Cordova (v5.3.3)

`npm install -g cordova@5.x.x`

## Create the first project

1. Install ionic alpha version. It can manage Ionic 2 projects and Ionic 1.x projects

`npm install -g ionic@alpha`

2. Start a new project, using the [tutorial](https://github.com/driftyco/ionic2-starter-tutorial) starter template. Other templates are available.

`ionic start MyFirstIonic2Project tutorial --v2`

It downloads the template, install NodeJS dependencies, and make the project ready to run.

3. `cd MyFirstIonic2Project`
4. Serve the application to run it in a browser: `ionic serve`

## Project structure

Almost all application files are placed under `www` directory, just as a Cordova project.

The main entry point for the application is `www/index.html`. It sets up CSS, includes JavaScript files and bootstrap the application. Ionic looks for an `ion-app` tag inside this first HTML page.

The code inside `www/app` is transpiled into the right version of JavaScript the browser supports. So, we could find TypeScript or ES2015 code in that folder. `www/app/app.js` creates the entry point of the application. It creates a component with the `@App` decorator. Every Ionic application needs that component.

``` javascript
@App({
  templateUrl: 'app/app.html'
})
class App {
//...
}
```

It configures `app/app.html` as the template for the application:

``` html
<ion-menu [content]="content">

  <ion-content>
    <ion-list>
      <button ion-item *ng-for="#p of pages" (click)="openPage(p)">
      </button>
    </ion-list>
  </ion-content>

</ion-menu>

<ion-nav id="nav" [root]="rootPage" #content swipe-back-enabled="false"></ion-nav>
```

In this template, we can see a menu (defined under `ion-menu`) and a navigation bar (`ion-nav`). The `ion-menu` takes a property of `content`, and we can pass the local variable of `#content` from our `ion-nav`.

The `ion-nav` tag defines a binding to the `root` property of the component. When the navigation controller loads, the component referenced by `rootPage` will be the root page.

In `app/app.js`, the root component `MyApp` specifies two properties: `pages` and `rootPage`.

``` javacript
import {App, IonicApp, IonicPlatform} from 'ionic/ionic';
import {HelloIonicPage} from './hello-ionic/hello-ionic';
import {ListPage} from './list/list';

class MyApp {
  constructor(app: IonicApp, platform: IonicPlatform) {
    // set up our app
    // ...

    // set our app's pages
    this.pages = [
      { title: 'Hello Ionic', component: HelloIonicPage },
      { title: 'My First List', component: ListPage }
    ];

    // make HelloIonicPage the root page
    this.rootPage = HelloIonicPage;
  }
  // ...
}
```

## Creating a page

The `HelloIonicPage` is defined in `app/hello-ionic/hello-ionic.js` file. It has a `@Page` decorator (provided by Ionic). It creates an Ionic Page (Angular component and view).

``` javascript
import {Page, NavController} from 'ionic/ionic';

@Page({
  templateUrl: 'app/hello-ionic/hello-ionic.html'
})
export class HelloIonicPage {
  constructor(nav: NavController) {
    this.nav = nav;
  }
}
```

Every page have both a `class` and a template. Let's see the template:

``` html
<ion-navbar *navbar>
  <a menu-toggle><icon menu /></a>
  <ion-title>Hello Ionic</ion-title>
</ion-navbar>

<ion-content>
  <h3>Welcome to your first Ionic app!</h3>
  <p>
    ...
  </p>
</ion-content>
```

The `<ion-navbar *navbar>` works as configuration for the navigation bar. It includes buttons to be shown and a title.

## Navigation between pages

The other page, `ListPage`, contains a list of items the user can tap (or click) to navigate to. That page is defined in `app/list/list.js`:

``` javascript
import {IonicApp, Page, NavController, NavParams} from 'ionic/ionic';

@Page({
  templateUrl: 'app/list/list.html'
})
export class ListPage {
  constructor(app: IonicApp, nav: NavController, navParams: NavParams) {
    this.nav = nav;
    // ...
   }
   // ...
   itemTapped(event, item) {
     // ...
   }
}
```

And the template includes a list of items. `*ng-for` is the `ng-repeat` in Angular 2. The click event handler is defined in `(click)=itemTapped()` part, so that everytime the user taps/clicks, `itemTapped` method is called.

``` html
<ion-item *ng-for="#item of items" (click)="itemTapped($event, item)">
```

To navigate to a new page, we can use the `NavController` component provided by Ionic. We saved it in the `nav` property of `ListPage`. Navigation in Ionic 2 works as a stack, you can `push` and `pop` pages from the stack.

``` javascript
itemTapped(event, item) {
  this.nav.push(ItemDetailsPage, {
    item: item
  });
}
```

We are pushing to a new page, `ItemDetailsPage`. It is a component provided in the tutorial starter, and we need to import it to use it:

``` javascript
import {ItemDetailsPage} from '../item-details/item-details';
```

## Next steps

There are lots of resources in the [Ionic 2] page:

- [Documentation about components]: http://ionicframework.com/docs/v2/components
- [Documentation about devices API]: http://ionicframework.com/docs/v2/platform
- [More resources]: http://ionicframework.com/docs/v2/resources/
- **NEXT WEEK: TESTING THE APP WITH JASMINE (WELL, FIRST STEPS TO TEST THE APP)** -> https://angular.io/docs/ts/latest/testing/






