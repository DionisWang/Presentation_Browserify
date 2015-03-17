# Presentation_Browserify
Browserify is a package installed using Node.js’s npm. The focus of Browserify is to neatly and efficiently bundle all of the necessary libraries in a webpage. This is done via the require(‘this.js’) function. Using required you can write a main.js that requires all of the functions for many different libraries including npm libraries and you own libraries. A sample code would look like this.

```javascript
//main.js
require(‘cradle’) //will look for the cradle in node_modules and check package.json to require main javascript file. 
require(‘./sample.js’) //will look for sample.js in the same directory
require(‘node_modules/cradle/something.js’) // to require specific part of a library
```
terminal:
$ browserify main.js > bundle.js
index.html
```html
<html>
<head>
<script src=”bundle.js”></script>
</head>
</html>
```
browserify recursively analyzes all the require() calls in your app and builds bundle.js with all the dependencies.Browserify becomes more useful with websites that use many libraries because instead of a hundred script tags in the html they could bundle all the libraries up and use the one script tag.
## Exporting
Not only can you export a library or its parts but even a function or just a variable.

```javascript
module.exports = function (n) {
    return n * 111
};

var foo = require('./foo.js');
console.log(foo(5));

//gets 555
//and using 
module.exports = 555

var foo = require('./foo.js');
console.log(foo);
//gets you 555
for multiple values to export you can do
module.exports.one = 555

module.exports.two = 1


var foo = require('./foo.js');
console.log(foo.one);

var two = foo.two;
console.log(two);

console.log(foo.one+two);
//gets
//555
//1
//556
```
## Other from http://coenraets.org/blog/2014/01/browserify-sample-application-with-backbone-jquery-handlebars-and-cordova/ :
*	You can “require” core node modules (crypto, querystring, url, etc.), community modules published on npm, and your own application modules.
*	Browserify requires you to build your application (using the “browserify” command line tool) before you can run/test it. But watchify or beefy can make that build process transparent during development by watching for source file changes, and building your application behind the scenes.
*	Browserify supports source maps to let you debug your application using individual JavaScript files.
*	Browserify provides an extensibility mechanism through “transforms”. A browserify transform lets you transform the source code of modules at build time before it’s injected in the bundle. For example, in the Employee Directory app, I use the hbsfytransform to transform Handlebars HTML templates into precompiled template functions.

For more info there are great tutorials online and and browserify handbook.
