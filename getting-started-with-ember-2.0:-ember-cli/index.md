---
title: "Getting Started with Ember 2.0: Ember-cli"
description: "Node.js is a platform built on Chrome’s JavaScript runtime for easily building fast, scalable network applications. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and…"
date: "2015-06-11T02:58:29.626Z"
categories: 
  - JavaScript
  - Ember
  - Getting Started

published: true
canonicalLink: https://medium.com/@jamesfuthey/getting-started-with-ember-cli-3dd0a4022415
---

### **Node.js**

Node.js is a platform built on [**Chrome’s JavaScript runtime**](http://code.google.com/p/v8/) for easily building fast, scalable network applications. Node.js uses an event-driven, non-blocking I/O model that makes it lightweight and efficient, perfect for data-intensive real-time applications that run across distributed devices.

Node comes with **_NPM_**,  the _Node Package Manager_. This can be used to install & manage dependencies within your application. It is particularly useful when distributing applications. When a _package.json_ file is present, you can run the command \`npm install\` to install the correct version of all dependencies in your project quickly and easily.

You need to install \`node.js\` in order to run \`ember-cli\` . If you haven’t installed it already, head on over to [http://nodejs.org/](http://nodejs.org/).

### **Ember-cli**

_Ember CLI_ is an [Ember.js](http://emberjs.com/) command line utility which provides a fast asset pipeline powered by [Broccoli](https://github.com/joliss/broccoli) and strong conventional project structure.

_Ember-cli_ is the command-line interface for building Ember applications. It is built and maintained by _Stefan Penner (_[_iamstef.net_](https://iamstef.net/)_), and i_t helps structure, scaffold, and deploy your projects, so you can spend more time building your applications, instead of the tooling to support your applications.

It includes several tools, such as ECMAScript 6 transpiler ([_Babel_](https://babeljs.io/)), an asset-pipeline ([_Broccoli_](http://broccolijs.com/)), and a testing framework ([_Qunit_](https://qunitjs.com/) _&_ [_Testem_](https://github.com/airportyh/testem)). It also includes several _blueprints_ for scaffolding & maintaining your app. These blueprints help scaffold Routes, Models, Controllers, Components, Adapters, Initializers, and Views. It’s not important for you to understand how this works when using Ember-cli, but it can be quite useful if you decide you want to contribute.

Once you’ve installed **Node.js**, you can install ember-cli from the command-line.

To install Ember CLI, run the following in your console:

```
npm install -g ember-cli
```

### **Bower**

_Bower_ is another popular command-line dependency manager for front-end development. Not only will you need it for developing ember-cli applications, but it is very likely you will be using projects or code which include bower dependencies. Bower keeps track of these packages in a manifest file, \`bower.json\`.

Bower uses a flat dependency tree, requiring only one version for each package, reducing page load to a minimum. The Bower CLI follows a similar syntax to NPM, with a few interesting features. For example, Bower can also install static files or a Github repository as dependencies.

To install bower, run the following command in your console:

```
npm install -g bower
```

### **Ember Inspector**

_Ember Inspector_ is a Chrome & Firefox extension written by Teddy Zeenny. It adds an Ember tab to Chrome or Firefox Developer Tools that allows you to inspect Ember objects in your application.

![](./asset-1.)

While it’s not impossible to develop an Ember app without the Ember Inspector, I highly advise against attempting to do so, especially if you’re new to the framework. It makes debugging your ember application effortless and easy.

After installing this extension, you’ll be able to:

-   View all of the routes defined in your application.
-   Reference Ember’s naming conventions for your URLs, including what to name your controllers, templates, routes and more.
-   Overlay your application with information about what templates, controllers, and models are currently being rendered.
-   Inspect the objects in your application, such as models and controllers, with UI that fully supports Ember features such as bindings and computed properties.
-   Make your application’s objects available in the console as the $E variable.
-   If you’re using Ember Data, see all of the records that have been loaded.

#### **Chrome**

Chrome: [https://chrome.google.com/webstore/detail/ember-inspector/bmdblncegkenkacieihfhpjfppoconhi?hl=en](https://chrome.google.com/webstore/detail/ember-inspector/bmdblncegkenkacieihfhpjfppoconhi?hl=en)

#### **Firefox**

Firefox: [https://addons.mozilla.org/en-US/firefox/addon/ember-inspector/](https://addons.mozilla.org/en-US/firefox/addon/ember-inspector/)

#### **Bookmarklet (for other browsers)**

[https://github.com/emberjs/ember-inspector#bookmarklet-all-browsers](https://github.com/emberjs/ember-inspector#bookmarklet-all-browsers)

### **An Interesting Fact**

_The_ _Ember Inspector itself is an ember application._ If you want to go meta on the Ember Inspector, you can use the Ember inspector to inspect the Ember Inspector itself!

![](./asset-2.)

Once you’re finished, you can [**head here**](https://medium.com/@jamesfuthey/8ef1f378ee4) to get started on our next project, [**_Building a simple blog with Ember 2.0_**](https://medium.com/@jamesfuthey/8ef1f378ee4).

---

If you have any suggestions, please feel free to let me know in the comments. Thanks!