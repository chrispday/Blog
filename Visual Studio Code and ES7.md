Getting Visual Studio Code
==========================
Don't search for "vs code" on google, all you'll get a Victoria's Secrets Coupons
* Download from [https://code.visualstudio.com/](https://code.visualstudio.com/)

Getting Intellisense for JS
===========================
VS Code provides intellisense via the [Defintely Typed](https://github.com/borisyankov/DefinitelyTyped) project.
This project provides [Typescript](http://www.typescriptlang.org/) definition files for lots of popular javascript libraries.
First, in the very unlikely chance you don't have it, you should install node.js which comes with NPM. 
* Download from [https://nodejs.org/download/](https://nodejs.org/download/)

To add the definition files for the libraries you are using we need [tsd](https://www.npmjs.com/package/tsd)
	npm install tsd -g

There are a few subtle trick to using tsd which will make it easier get intellisense with VS Code.
When the type definitions are downloaded they should go in the `typings` folder.
The key thing in this folder is that if there is a file present called `tsd.d.ts` this can contain all the references to any other `.d.ts` files and VS Code will automatically use them to provide intellisense in any javascript file.
To get intellisense for `express` run
	tsd query express install -ios
This will download and install the `express.td.s` and add `/// <reference path="express/express.d.ts" />` to the `tsd.d.ts` file.

