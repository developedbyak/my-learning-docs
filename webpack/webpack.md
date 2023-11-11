# webpack

<P>A bundler for javascript and friends.</P>

> Click :star:if you like the project and follow [@developedbyak](https://twitter.com/developedbyak) for more updates.

### Table of Contents

| No. | Topics                                                            |
| --- | ----------------------------------------------------------------- |
| 1   | [Introduction](#1-introduction-🐱‍🏍)                              |
| 2   | [Installing & Running Webpack](#2-installing--running-webpack-😎) |
| 3   | [Imports, Exports, & Modules](#3-imports-exports--modules)        |

## 1. Introduction 🐱‍🏍

A bundler for javascript and friends. Packs many modules into a few bundled assets. Code Splitting allows for loading parts of the application on demand. Through "loaders", modules can be CommonJs, AMD, ES6 modules, CSS, Images, JSON, Coffeescript, LESS, ... and your custom stuff.

**The 2 Main Things Webpack Does**

-   It bundles our code/assets together
-   It also manages dependencies
    <br>
    <br>

## 2. Installing & Running Webpack 😎

<br>

**So first we arrange our assets or js files in a good way**:
<br>
<br>

**What does that mean ?**
<br>

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
│   └── index.js
├── index.html
└── webpack.config.js

```

> We will learn `webpack.config.js` later ignore for now

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
    <br>
    <br>

## 3. Imports, Exports, & Modules

<br>

-   Now earlier we only write a single line of code into `index.js`.

-   Its time to import all our codes inside the `index.js`.
<br>
<br>
<h1>😀1st method: (Note this method is for vanilla js projects)</h1>
<br>

**Structure for vanilla-js project**

```
                project/
      --------->|-- dist/main.js ------------->
      |         |-- src/                      |
      |         │   |-- fonts/                |
      |         │   |-- images/               |
      |         │   |-- styles/               |
      <---------|---|--index.js               |
                ├── index.html <---------------
```

It is used for a simple and small projects where all the codes are present in one script file.

-   Now add all the javascript code to your `index.js` and run `npm start`.
-   You will see all the Javascript code is minified and added to the `main.js` which is link to our `index.html`;
-   Note your `index.html` should only have the `main.js` link

```js
// index.html
<script src="./dist/main.js"></script>
```

<br>
<br>
<h1>😀2nd method: React</h1>
<br>

-   In `javascript` we only have a `js` file which will get minified and added to the `index.html`.
-   But in react we will have a lot's of `components`, `utils`, `custom functions` etc.
-   So we have to export them and add the entry point to the `index.js` which will later get minified and used by the application.

-   Don't worry for now we will learn more when we use `webpack.config.js`.

<br>
<br>

## 4. Configuring Webpack 🛰

<br>

-   So let's go through what we just learn , right now the webpack is looking for the default location `src/index.js` to bundle the file.
-   Now create a `webpack.config.js` on root of your project.

-   And This is how the syntax will look like .

```js
// webpack.config.js

const path = require("path");

module.exports = {
    entry: "./src/index.js",
    output: {
        filename: "main.js",
        path: path.resolve(__dirname, "dist"),
    },
};
```

-   So we said `module.exports` and then it is a object where it has an `entry` point and an `output` path.

-   Inside `output` it's another object first `filename` will be the name of the file that will generate and `path` will determine where to save it .

-   We are using `path` which is a inbuilt node_module.

-   Before we run our command add this to your `package.json`

```js
  "scripts": {
    "start": "webpack --config webpack.config.js"
  },
```

-   Now if you run `npm start` you will see main.js got all the minified codes!!. But wait isn't 😒 that's the same as we run by-default?

-   Well no now we can add a lot's of different options like

```js
const path = require("path");

module.exports = {
    mode: "development", // added this line
    entry: "./src/index.js",
    output: {
        filename: "main.js",
        path: path.resolve(__dirname, "dist"),
    },
};
```

-   That line of code will stop the webpack to minified our code as we are still in development mode.

-   You might got a notice like

```js
 * ATTENTION: The "eval" devtool has been used (maybe by default in mode: "development").
 * This devtool is neither made for production nor for readable output files.
 * It uses "eval()" calls to create a separate source file in the browser devtools.
```

-   To fix this

```js
module.exports = {
    mode: "development",
    entry: "./src/index.js",
    output: {
        filename: "main.js",
        path: path.resolve(__dirname, "dist"),
    },
    devtool: false, // add this line
};
```

-   Now you can see all your js codes inside `dist/main.js`.
-   Next we will learn how to handle different types of files and not only javascript.
