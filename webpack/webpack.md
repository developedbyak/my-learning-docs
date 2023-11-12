# webpack

<P>A bundler for javascript and friends.</P>

> Click :star:if you like the project and follow [@developedbyak](https://twitter.com/developedbyak) for more updates.

### Table of Contents

| No. | Topics                                                         |
| --- | -------------------------------------------------------------- |
| 1   | [Introduction](#1-introduction)                                |
| 2   | [Installing & Running Webpack](#2-installing--running-webpack) |
| 3   | [Imports, Exports, & Modules](#3-imports-exports--modules)     |
| 4   | [Configuring Webpack](#4-configuring-webpack)                  |
| 5   | [Webpack Loaders, CSS & SASS 🔃](#5-webpack-loaders-css--sass) |
| 6   | [Cache Busting & Plugins](#6-cache-busting--plugins)           |

## 1. Introduction

A bundler for javascript and friends. Packs many modules into a few bundled assets. Code Splitting allows for loading parts of the application on demand. Through "loaders", modules can be CommonJs, AMD, ES6 modules, CSS, Images, JSON, Coffeescript, LESS, ... and your custom stuff.

**The 2 Main Things Webpack Does**

-   It bundles our code/assets together
-   It also manages dependencies
    <br>
    <br>

## 2. Installing & Running Webpack

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

**[⬆ Back to Top](#table-of-contents)**

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

**[⬆ Back to Top](#table-of-contents)**

## 4. Configuring Webpack

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
    <br>
    <br>

**[⬆ Back to Top](#table-of-contents)**

## 5. Webpack Loaders, CSS & SASS

<br>

<h2>Loaders</h2>

Docs: https://webpack.js.org/loaders/
<br>
<br>
Loaders are transformations that are applied to the source code of a module. They allow you to pre-process files as you import or “load” them. Thus, loaders are kind of like “tasks” in other build tools and provide a powerful way to handle front-end build steps. Loaders can transform files from a different language (like TypeScript) to JavaScript or load inline images as data URLs. Loaders even allow you to do things like import CSS files directly from your JavaScript modules!

<br>

**We will start from adding css to out webpack:**

-   Create a `main.css` file inside `src` folder.

```js
src / main.css;
```

-   Now we have to add loaders
-   First we will setup `css-loader`

```js
npm install --save-dev style-loader css-loader
```

-   Now update config file like this :

```js
module.exports = {
    mode: "development",
    entry: "./src/index.js",
    output: {
        filename: "main.js",
        path: path.resolve(__dirname, "dist"),
    },
    devtool: false,
    module: {
        rules: [
            {
                test: /\.css$/i,
                use: ["style-loader", "css-loader"],
            },
        ],
    },
};
```

<h2>Note: </h2>

```js
use: ["style-loader", "css-loader"];

// the order will be like this first "style-loader" then "css-loader"
```

<h2>Things to know:</h2>

```js
test: /\.css$/i, (Case-Insensitive)

The /i at the end makes the regular expression case-insensitive. This means it will match .css, .CSS, .CsS, etc.
```

```js
test: /\.css$/, (Case-Sensitive)

Without the /i, the regular expression is case-sensitive. It will only match files with the exact extension .css in the specified case.
```

-   Now add some css to `main.css`

```css
body {
    background-color: purple;
}
```

-   Run

```js
npm start
```

-   `css-loader` convert css to javascript and `style-loader` takes that javascript which is actually css and inject into DOM.

<h2>If you want to add bootstrap to loader</h2>

**steps to follow**

```js
// step: 1
npm install --save-dev bootstrap

// step: 2
// Remove the bootstrap link from index.html

// step: 3
// main.css or main.scss
@import "~bootstrap/scss/bootstrap"; or
@import url("../node_modules/bootstrap/scss/bootstrap");

// If you using scss follow this
https://webpack.js.org/loaders/sass-loader

// step: 4
npm install sass-loader sass webpack --save-dev

// step: 5
    module: {
        rules: [
            {
                test: /\.css$/,
                use: [
                    "style-loader", // Inject styles into DOM
                    "css-loader", // Turns css into commonJS
                    "sass-loader" // Turns sass into css
                  ],
            },
        ],
    },
```

<br>
<br>

**[⬆ Back to Top](#table-of-contents)**

## 6. Cache Busting & Plugins

<br>
Update your code like this -

```js
// webpack.config.js

    output: {
        filename: "main.[contenthash].js",
        path: path.resolve(__dirname, "dist"),
    },

// output
dist/main.03b93fab3298fdd4420c.js

```

What does `main.[contenthash].js` do is everytime we build our bundle files it will generate a new hash for the bundle so the cache data that the broswer saved it got refresh with new.
<br>
If we don't change the name like this then even if we chnage the bundle the browser will use the old cache files that he saved.

<h2>But now how we gonna add that dynamic main.js??</h2>

```js
// This is how it looks right now
<script src="./dist/main.js"></script>
```

And the answer is we don't do that , we will not use this script anymore and the thing that will help us do is called `plugins`.

<h1>Plugins</h1>
<br>

website : https://webpack.js.org/concepts/#plugins
<br>
list of plugins : https://webpack.js.org/plugins/

**How to use**<br>
Let's see the example with : **HtmlWebpackPlugin**<br>

```js
npm install --save-dev html-webpack-plugin
```

**Add the plugin to your webpack configuration as follows:**

```js
const HtmlWebpackPlugin = require("html-webpack-plugin");
const path = require("path");

module.exports = {
    mode: "development",
    entry: "./src/index.js",
    output: {
        filename: "main.[contenthash].js",
        path: path.resolve(__dirname, "dist"),
    },
    devtool: false,
    plugins: [new HtmlWebpackPlugin()], // newly added
    module: {
        rules: [
            {
                test: /\.css$/,
                use: ["style-loader", "css-loader"],
            },
        ],
    },
};
```

-   now run

```
npm start
```

You will notice there's a new `index.html` file inside dist folder. But there is no content.
<br>
Let's fix it .

-   Create a `template.html` inside `src` directory.

-   Copy the entire content of `index.html` to `template.html`.

Now change this -

```js
    plugins: [
        new HtmlWebpackPlugin({
            template: "./src/template.html",
            title: "Animated website",
            scriptLoading: "blocking", // put the script inside body, if you not give this option it will put the script to head.
        }),
    ],
```

**[⬆ Back to Top](#table-of-contents)**

<br>
<br>

## 7. Splitting Dev & Production

<br>

-   So we will have 3 different config files and each file will serve different purpose .

```js
// create all 3 config files -

webpack.common.js; // renamed from webpack.config.js
webpack.dev.js;
webpack.prod.js;
```

-   And this is how it will be now :
    <br>

**webpack.common.js**<br>

```js
const HtmlWebpackPlugin = require("html-webpack-plugin");
const path = require("path");

module.exports = {
    entry: "./src/index.js",
    devtool: false,
    plugins: [
        new HtmlWebpackPlugin({
            template: "./src/template.html",
            title: "Animated website",
            scriptLoading: "blocking",
        }),
    ],
    module: {
        rules: [
            {
                test: /\.css$/,
                use: ["style-loader", "css-loader"],
            },
        ],
    },
};
```

<br>

**webpack.dev.js**

```js
const HtmlWebpackPlugin = require("html-webpack-plugin");
const path = require("path");

module.exports = {
    mode: "development",
    output: {
        filename: "main.js",
        path: path.resolve(__dirname, "dist"),
    },
    devtool: false,
};
```

<br>

**webpack.prod.js**

```js
const HtmlWebpackPlugin = require("html-webpack-plugin");
const path = require("path");

module.exports = {
    mode: "production",
    output: {
        filename: "main.[contenthash].js",
        path: path.resolve(__dirname, "dist"),
    },
    devtool: false,
};
```

-   Now

```js
npm install --save-dev webpack-merge
```

-   Merge the `webpack.common.js` with `webpack.dev.js`

```js
const path = require("path");
const common = require("./webpack.common");
const { merge } = require("webpack-merge");

module.exports = merge(common, {
    mode: "development",
    output: {
        filename: "main.js",
        path: path.resolve(__dirname, "dist"),
    },
    devtool: false,
});
```

-   Do the same for production config

```js
const path = require("path");
const common = require("./webpack.common");
const { merge } = require("webpack-merge");

module.exports = merge(common, {
    mode: "production",
    output: {
        filename: "main.[contenthash].js",
        path: path.resolve(__dirname, "dist"),
    },
    devtool: false,
});
```

-   Now the `common config` is merged with `dev` and `prod` which will give different output for development and production build.

<h2>Let's setup the dev server</h2>
why we need this ?<br>
So everytime we made some changes we don't have to build everytime and test while on development mode .

<br>

```js
npm install --save-dev webpack-dev-server
```

```js
// package.json

  "scripts": {
    "start": "webpack-dev-server --config webpack.dev.js --open",
    "build": "webpack --config webpack.prod.js"
  },
```

```js
// it will open a dev server on browser now
npm start
```
