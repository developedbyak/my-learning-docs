# webpack

<P>A bundler for javascript and friends.</P>

> Click :star:if you like the project and follow [@developedbyak](https://twitter.com/developedbyak) for more updates.

### Table of Contents

| No. | Topics                                                         |
| --- | -------------------------------------------------------------- |
| 1   | [Installation](#1-installation)                                |
| 2   | [Installing & Running Webpack](#2-installing--running-webpack) |
| 3   | [Imports, Exports, & Modules](#3-imports-exports--modules)     |

## 1. Installation

A bundler for javascript and friends. Packs many modules into a few bundled assets. Code Splitting allows for loading parts of the application on demand. Through "loaders", modules can be CommonJs, AMD, ES6 modules, CSS, Images, JSON, Coffeescript, LESS, ... and your custom stuff.

**The 2 Main Things Webpack Does**

-   It bundles our code/assets together
-   It also manages dependencies

## 2. Installing & Running Webpack

**So first we bundle our assets or js files**:<br><br>
**What does that mean ?**<br>

-   So basically make folders for each files and arrange them in a good and clean way so we can bundle them together. <br>
-   Remember we can bundle a single file also.

**Here's some example how to make the structure**

```
project/
├── src/
│   ├── index.html
│   ├── style.css
│   └── index.js
├── dist/
└── webpack.config.js
```

```
project/
├── assets/
│   ├── fonts/
│   ├── images/
│   ├── styles/
│   └── js/
├── index.html
└── webpack.config.js
```

<h2 style="color:red">But wait this is just break codes into separate files, no webpack we used yet!!</h2>

**So to install webpack first thing we need to do**:<br>

-   setup package.json

```js
npm init -y
```

-   Then install webpack

```
npm install webpack webpack-cli --save-dev
```

-   Now the package.json might look like this

```js
{
  "name": "website-2",
  "version": "1.0.0",
  "private": true,
  "description": "",
  "main": "index.js",
  "scripts": {},
  "keywords": [],
  "author": "",
  "license": "ISC",
  "devDependencies": {
    "webpack": "^5.89.0",
    "webpack-cli": "^5.1.4"
  }
}
```

-   I added `private:true` optional.
-   Now lets config the scripts

```js
  "scripts": {
    "start": "webpack"
  },
```

**Now try to run npm start**
you will see this error :

```
Module not found: Error: Can't resolve './src'
```

-   Now inside src folder create `index.js` and write a simple alert says `Hello World!` and run the command again `npm start`.
-   Now you will see a `dist` folder has been created.
-   Inside that dist folder you will have a `main.js` file which will have all the webpack magic code .
-   Now link that `main.js` file to `index.html`, And if you refresh your website you will see the alert message.

## 3. Imports, Exports, & Modules

-   Now earlier we only write a single line of code into `index.js`.

-   Its time to import all our codes inside the `index.js` and we will do that using `ES6 import` methode.
