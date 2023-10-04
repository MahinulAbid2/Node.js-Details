### List of content
1. HTTP MODULE
![MongoDB-chart1](https://github.com/MahinulAbid2/Node.js-Details/assets/70069009/3ac0f6b9-4697-408b-b43f-278a9c0b3db3)


<br>
<br>
<br>


## NODE.js intro
=================================
* Node.js is not a framework or programming language.
* Its a `runtime environment`. So I have to install in my computer inorder to work with node.js
* `https://nodejs.org/en/download/` - here is the Node.js environment which I have to install on my pc.
* If I already have node.js, there is no need to download additional file in order to make the code work below.
* How to check If I have node.js installed on my pc? Run this command on terminal.
```javascript
node -v
// result will be something like v16.17.1 if I already have node.js installed on my pc.
// otherwise there will be different result.
```

<br>
<br>

## Node.js modules
=======================================================

Node.js includes three types of modules.
* Core Modules
* Local Modules
* Third Party Modules

<br>

## Core Modules(Intoduction)
=========================================================
* The core modules include bare minimum functionalities of Node.js.
* These core modules are compiled into its binary distribution and load automatically when Node.js process starts.
* However, you need to import the core module first in order to use it in your application.

<br>
<br>

## Local Modules
============================================================
* Local modules are modules created locally in your Node.js application
* These modules include different functionalities of your application in separate files and folders
* You can also package it and distribute it via NPM, so that Node.js community can use it.
* For example, if you need to connect to MongoDB and fetch data then you can create a module for it, which can be reused in your application.


<br>
<br>

## Core Modules(Details)
=========================================================

The following table lists some of the important core modules in Node.js.

![coreModules](/Docs/coreModules.png)



<br>
<br>


## HTTP Module
================================================
* HTTP module allows Node.js to transfer data over the Hyper Text Transfer Protocol (HTTP).
* To include the HTTP module, use the `require()` method at the top of javascript of typescript file.
```javascript
const http = require('http');
```
* The HTTP module can create an HTTP server that listens to server ports and gives a response back to the client.
* `createServer()` method allows node.js to create an `HTTP server` <br>
    ✔️ That server listens to request and <br>
    ✔️ Give feedback according to the request.

<br>
<br>

### Create Web Server Using HTTP module
* Two method will be used in this web server creation. <br>
    ✔️ .createServer(a function will be here) <br>
    ✔️ .listen(a port number will be here) <br>
    
those two function will be combined inorder to create a web server that will listen to the HTTP request.
```javascript
var http = require('http');

//create a server object:
http.createServer(function (req, res) {
//here will be some operation related to the request and response according to the request.
}).listen(8080); //the server object listens on port 8080
```

* Will be executed when someone tries to access the computer on port 8080 via browser.
* I call it - `send request via HTTP` <br>
* <ins> When a user sends request, it must needs to be end by sending a `response` </ins>
* A request without ending, will keep the request running, A VERY BAD THING.
* `res.end();` ends the response, close the whole server process.
```javascript
var http = require('http');

//create a server object:
http.createServer(function (req, res) {
res.write("Hello world") // this is just a response text which will show a bare text for now.
res.end(); //ends the response, close the whole server process.
}).listen(8080); //the server object listens on port 8080
```
> res.write(), I won't write `res` for now. Just know that res.write(), write some text in the webpage as raw text.

<br>
<br>

### Send the request in browser
* I wrote the code for create a Server and let user send request.
* How to initialize node.js server?
* How to send that specific request?

<br>

#### How to initialize the server?
* In VS code Editor, go to terminal.
* Make sure I'm in the project directory.
* Type the command in the console.
* The Node server will start.
* Remember, it doesn't keep looking for the code changes.
* So when I make some changes, it doesn't automacally updated. I have to restart the node server to see the changes.
* There are some library for node.js server to keep watching our changes. One of the library name is `NODEMON`.

```console
node index.js
```
> This `index.js` can be any file name. This is where I've put the node.js code.

<br>
<br>

#### How to send that specific request?
* After initializing the node.js server, go to a browser.
* Visit 

```javascript
http://localhost:8080
//8080 is the port number which I've put it in .listen() method.
```

<br>
<br>
<br>




## URL Module(Basic)
======================================================================
```javascript
var url = require('url');
```

<br>

* Parse an address with the `url.parse()` method, and it will return a `URL object` with each part of the address as properties.
>Parsing means analyzing and converting a program into an internal format that a runtime environment can actually run, for example the JavaScript engine inside browsers. The browser parses HTML into a DOM tree. HTML parsing involves tokenization and tree construction

<br>


```javascript
var url = require('url');

//I WILL LEARN TO FETCH URL FROM BROWSER LATER
// LETS WORK WITH PREDEFINED URL NOW
var adr = 'http://localhost:8080/default.htm?year=2017&month=february';

//i'll research later what the true means in the url.parse function.
var q = url.parse(adr, true);

console.log(q.host); //returns 'localhost:8080'
console.log(q.pathname); //returns '/default.htm'
console.log(q.search); //returns '?year=2017&month=february'

var qdata = q.query; //returns an object: { year: 2017, month: 'february' }
console.log(qdata.month);
```
<br>

**Structure of URL** <br>
![url](/Docs/urlStructure.png)



### URL API
------------

There are two types of API to parse an URL. Up above, that is `LEGACY API`. These two types of API are:
* Legacy API
* WHATWG API

<br>
<br>

**LEGACY API**
> The legacy URL API is a part of the Web API and has been around since the early days of the web. It provides a simple interface to parse and manipulate URLs, but it has several limitations, such as lack of support for non-ASCII characters and internationalized domain names (IDNs).

<br>
<br>

**WHATWG API**
> On the other hand, the WHATWG URL API is a newer API designed to address the limitations of the legacy URL API. It provides a more powerful and flexible interface for working with URLs, including support for IDNs and non-ASCII characters. It also includes several new features, such as the ability to parse and serialize URL fragments and query strings.

<br>
<br>

**When to use LEGACY or WHATWG API?**
>In general, if you are working with simple URLs that do not require support for non-ASCII characters or IDNs, then the legacy URL API may be sufficient. However, if you need to work with more complex URLs or want to ensure compatibility with modern web standards, then the WHATWG URL API may be the better choice.

Ultimately, the choice between the two APIs will depend on the specific requirements of your project and the level of support you need for various URL features.









<br>
<br>
<br>

## HTTP Header
=========================================================
* The header tells the server details about the request such as what type of data the client, user, or request wants in the response. 
* Type can be html , text , JSON , cookies or others.
* When a user send request, some additional information about the request which a user can't see bare eyes are sent in the browsers.
* In order to see the `HTTP Header`, user need to inspect browser.
* Then go to `network` or `performence` tab. It's where you'll find HTTP header.
* This `header` is important when building an `API - Application Programming Interface`.

<br>

![Image](/Docs/writehead.png)
![code how to writehead](/Docs/writeheadCode.png)

<br>
<br>

This is what `header` looks like.

<br>

### How to write HTTP header?
```javascript
const http = require("http");

http.createServer((req, res) => {
    res.writeHead(200, {
        'Text-header-wrote-by-me': "The text value we want to deliver"
    });
    res.end(); // ending the request with a response is necessary
}).listen(8000);
```

<br>

Seperate CODE:
```javascript
res.writeHead(200, {
        'Text-header-wrote-by-me': "The text value we want to deliver"
});
```

<br>
<br>

### What is that `200` in the res.writeHead()?
Answer: `200` is a status code which means the files are okay. <br> There are many status code which bears different meaning. here are some of them.
I'll write about this later.

<br>
<br>
<br>


## Server Response
```javascript
http.createServer((req, res) => {

}).listen(8000);
```
* Here, createServer() has an anonymous function.
* The `createServer()` has <ins>One function</ins> and that function has <ins>Two Arguments</ins>.
* `(req, res)` - the first argument is `request` and the second argument is `response`. 
> Remember that first argument can not be `response` and the second argument cannot be `request`. It has a sequence.

#### Note: Both `request` & `response` has many methods. I have to note them down later.

<br>
<br>
<br>

## NODE.JS File System
=============================================================

<br>

* With the help of NODE.JS FILE SYSTEM, I can --
<br>
✔️Write anything inside of a file. That can be a HTML, CSS, JavaScript, TXT nything. <br>
✔️ Rename files. <br>
✔️ Create Files <br>
✔️ Read Files. <br>
✔️ Update Files. <br>
✔️ Delete Files. <br>



### Module
___________________________________________

```javascript
var fs = require('fs');
```

<br>

**Asyncronous File Reading**
```javascript
//syntax structure
fs.readFile(fileName [,options], callback)


//Practical Use of fs
fs.readFile('TestFile.txt', function (err, data) {
// do something with this file
});
```

> Remember that Asyncronous code blocks the procedure. While Syncronoys Code doesn't block processing.

<br>

**Asyncronous File Reading**
```javascript
var fs = require('fs');

var data = fs.readFileSync('dummyfile.txt', 'utf8');
console.log(data);
});
```

<br>

**Difference**
```javascript
//Asyncronous
fs.readFile('TestFile.txt', function (err, data) {
console.log(data)
});


//Syncronous
var data = fs.readFileSync('dummyfile.txt', 'utf8');
//Do some other stuff

console.log(data);
```



