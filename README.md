# Polymer Server

[![CircleCI](https://circleci.com/gh/firstor/polymer-server.svg?style=svg)](https://circleci.com/gh/firstor/polymer-server)

This is the fundamental project, to serve, experience, and test Polymer components
in both development and production environment.

## Setup

#### Prerequisites

First, install [node.js](https://nodejs.org) and [npm](https://www.npmjs.com).

Second, install [Bower](https://bower.io/) globally using [npm](https://www.npmjs.com)

    npm install -g bower

#### Install components locally

    npm install
    bower install

## Start the development server

This command serves the app at `http://localhost:3030` and provides basic URL
routing for the app:

    npm run start

## Production Build

The `polymer build` command builds your Polymer application for production, using build configuration options provided by the command line or in your project's `polymer.json` file.

You can configure your `polymer.json` file to create multiple builds. This is necessary if you will be serving different builds optimized for different browsers. You can define your own named builds, or use presets. See the documentation on [building your project for production](https://www.polymer-project.org/2.0/toolbox/build-for-production) for more information.

Builds will be output to a subdirectory under the `build/` directory as follows:

```
build/
  es5/
  bundled/
  unbundled/
```

* `es5` is a bundled, minified build with a service worker. ES6 code is compiled to ES5 for compatibility with older browsers.
* `bundled` is a bundled, minified build with a service worker. ES6 code is served as-is. This build is for browsers that can handle ES6 code - see [building your project for production](https://www.polymer-project.org/2.0/toolbox/build-for-production#compiling) for a list.
* `unbundled` is an unbundled, minified build with a service worker. ES6 code is served as-is. This build is for browsers that support HTTP/2 push.


## Preview the build

This command serves your app.

    npm run start:es5
    npm run start:bundled
    npm run start:unbundled

## Run tests

This command will run [Web Component Tester](https://github.com/Polymer/web-component-tester)
against the browsers currently installed on your machine:

    polymer test

If running Windows you will need to set the following environment variables:

- LAUNCHPAD_BROWSERS
- LAUNCHPAD_CHROME

Read More here [daffl/launchpad](https://github.com/daffl/launchpad#environment-variables-impacting-local-browsers-detection)

## Adding a new view

You can extend the app by adding more views that will be demand-loaded
e.g. based on the route, or to progressively render non-critical sections of the
application. Each new demand-loaded fragment should be added to the list of
`fragments` in the included `polymer.json` file. This will ensure those
components and their dependencies are added to the list of pre-cached components
and will be included in the build.
