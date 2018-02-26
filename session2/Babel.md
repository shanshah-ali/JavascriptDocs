## Babel

> Babel is a JavaScript transpiler that converts edge JavaScript into plain old ES5 JavaScript that can run in any browser (even the old ones). 

> It makes available all the syntactical sugar that was added to JavaScript with the new ES6 specification, including classes, fat arrows and multiline strings.


```
Installation -
	npm install –save-dev 'babel-cli'
	
An ES6 class looks like this:
1.	class Person {}
	var dave = new Person
	
If we run it through Babel we simply get a constructor function, 
plus a little decoration:

"use strict";
function _classCallCheck(instance, Constructor) {
  if (!(instance instanceof Constructor)) {
    throw new TypeError("Cannot call a class as a function");
  }
}
var Person = function Person() {
  _classCallCheck(this, Person);
};
var dave = new Person();

2. Fat Arrow Functions
	(x, y) => {return x + y};
	
	In Babel:-
		(function (x, y) {
		  return x + y;
		});

```

## [NPM](https://www.npmjs.com)

npm is a package manager for Node.js with hundreds of thousands of packages. Although it does create some of your directory structure/organization, this is not the main purpose.

To install npm -> **npm install npm@latest -g**

NPM Registry of Evive - **http://mac-build-server.dev.evivehealth.com:4000/**

To change your registry use - npm config set registry (url to point)






