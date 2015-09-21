# superhero.js

---

# Node.js, Master of Universe?

---

> Trust me, Node is more than awesome.

---

# A *Javascript* Web Server?

> Qu'est ce que tu me racontes là ?

---

# Yes. A Web Server!

### Something a little bit obscur as Apache and IIS

---

# Numbers don't lie

---

## 2/3 of americans connect to the Internet via a Mobile device.

## 34 of the world's Top 100 websites are using HTML5

---

# HTML 5 + mobile

---

# The Web is Real-Time

---

# Real-Time stack technology

---

# Node.js in 3 tweets

---

# Event driven
# non-blocking I/O
## model

---

# Build on JavaScript

> unify client-side and server-side architectures.

---

# High

### performance
### scalable
### distributed

---

# 2nd most popular projects on GitHub

> In 2013, 4 years after its debut

---

# Give me notable users

---

# Linkedin

> On the server side, mobile software stack is completely build in Node.js

---

### from 15 servers with 15 instances
## to just 4 instances
# 2x the traffic

---

# Walmart

> $486 USD billions of revenue in	January 2015

---

## JavaScript processing to the server

> rich and dynamic experience for customers

---

# Today

---

- | -
---- | ---
Ebay | NPR
CBS Interactive | Zappos.com
General Motors | Yahoo!
Condé Nast | Adobe
DowJones | Uber
Dell | Mozilla

---

# etc, etc, etc...

---

## Networked multiplayer games
## Interactive websites
## Chat system...

---

# Why you can't say no?

---

## It's JavaScript
## Code reuse at every level

> Yes! Browser and server

---

## Strong community
## Performance and scalability

---

# A Web Server in Javascript? WTF

---

# V8

---

# Chrome, Super P(Br)ow(s)ers!

---

# V8, the JavaScript engine written in C++

> In 2008, Google open-sourced

---

# Increase the performance
## of the JavaScript execution
###  inside web browsers

---

# How?

---

# Translate JavaScript code

> into more efficient machine code instead of using an interpreter

---

> It’s not just about making your current application run faster, it’s about enabling things that you have never been able to do in the past.

Daniel Clifford (tech lead and manager of the V8 team)

---

# Node.js

> Node.js was released in 2009 as an open source project

---

##  designed to help you to write JavaScript programs

---

# talk to

## networks
## file systems
## other I/O sources

---

# That's it!

---

## Just simple and stable I/O platform

---

# I/O?

---

![IO](https://raw.githubusercontent.com/maxogden/art-of-node/master/server-diagram.png)

---

# 2 choices
## to build a fast and robust web server

---

## Write from scratch
# C

---

## difficult to code but super fast results

---

# Take existing one

---

## Easy to code but forget to request 5Gb data

---

# balance

> to be relatively easy to understand and use and fast enough for most use cases.

---

# No no and no

---

## Node.js is not a web framework

---

## Node.js is not a programming language

---

# So, what?

---

## Higher level

---

# Fast I/O and/or handle lots of connections

---

## lower level

---

# Programs using the protocols of the web

---

# Programs reading and writing data to the filesystem or local processes/memory

---

# No-blocking

---

# asynchronous

>  handle lots of different things simultaneously.

---

# Burger King

---

# Installation

Go to [https://nodejs.org](https://nodejs.org)

---

## The famous
# "Hello World"

```js
console.log("Hello World");
```

---

```sh
❯ node index.js                                                                                                                                                                                    Hello World
```

---

# 0,30% of Node

---

# Let's go!

---

# Core modules

---

# Small core group of modules


> Node core: minimalist public API

---

## fs
## dns
## url
## path
## ...

---

```js
var fs = require('fs');

fs.readFile(...){
  ...
}
```

---

# Modularity

> AMD? CMD?

---

# CommonJS Modules/1.1

> keep files self-contained

---

```js
// lib/rental.js

var api = {
  'price': function(distance){
    return distance * 0.30;
  }
};

module.exports = api;
```

---

## require

```js
var rental = require('./lib/rental.js');
var price = rental.price(100);

console.log('The rental price is '+  price + ' euros');
```

---

## physical path
## package name
## local vs global

---

#  Callbacks

---

# everything in node uses callbacks

> Thanks JavaScript

---

## executed asynchronously
## or at a later time

---

## top to bottom
# VS
## different times

---

# Synchronous example

```js
var nbDrivers = 1;

function addDriver() {
  nbDrivers++;
}

addDriver();

console.log(nbDrivers) // logs out 2
```

---

## without waiting for anything
## sequentially runs top to bottom

---

# Asynchronous example

---

```js
var license = require('license');
var nbDrivers = 1;

function addDriver(driver, callback) {
  license.check(driver, function(err, done){
    if (err){
      throw new Error('Suspended licence');
    }

    nbDrivers++;
    callback();
  })
}
```

```js
function printDrivers (){
  console.log(nbDrivers) // logs out 2
}

addDriver({'name':'yassine', 'license':'3467772ZfFR4'},
 printDrivers);
```

---

## 1. functions are immediately defined
## 2. they don't all execute immediately

> fundamental

---

## Callbacks === executed later

---

## Question:

# When this operation will complete ?

> I don't know

---

# Use callback

---

# Events

---

## when X do Y
# do X then Y

---

Many objects in Node emit events: a `net.Server` emits an event each time a peer connects to it, a `fs.readStream` emits an event when the file is opened.

All objects which emit events are instances of `events.EventEmitter`.

You can access this module by doing: `require('events')`;

---

# Listeners

> Functions to be executed when an event is emitted

---

```js
var settings = require('widget-settings');
...
settings.emit('change', {'data': 'percentage;'})
```

```js
var widget = require('widget');
...
widget._settings.on('change', function(){
  // do some actions when settings changed
});
```

---

# NPM

---

# 180.000

---

## The simplest module

---

package.json

```js
{
  "name": "my-first-module",
  "version": "1.0.0"
}
```

---

index.js

```js
module.exports = ...
```

```js
var myFirstModule = require('my-first-module');
```

---

## install a module

> npm install module-name

---

## add a dependencies

> npm install --save deps-name

---

## Kickstarter
# HTTP server in node

---

```js
var http = require('http');

http.createServer(function(req, res) {
  res.end('Hello Node', 200);
}).listen(8000);

// http://localhost:8000
```

---

# Rocket Launcher: Express!

```js
//app.js
var express = require('express');
var app = express();

app.get('/', function (req, res) {
  res.send('Life better with Express!!');
});

app.listen(3000);
```

---

```js
app.get('/home', function (req, res) {
  res.send('Home page');
});

app.get('/about-me', function (req, res) {
  res.send('About me');
});
```

---

# Templating

---

# NEXT TIME

https://github.com/workshopper/learnyounode

---

# CROSS BROWSER

---

# render all elements more consistently

---

# JavaScript actions

---

# normalize.css

> researching the differences between default browser styles in order to precisely target only the styles that need or benefit from normalizing

---

## Preserve useful browser defaults rather than erasing them

---

## Normalize styles for a wide range of HTML elements

---

## Correct bugs and common browser inconsistencies

---

## Improve usability with subtle improvements

---

## Explain the code using comments and detailed documentation

---

# caniuse.com

---

##  provides up-to-date browser support tables for support of front-end web technologies on desktop and mobile web browsers

---

# http://caniuse.com

---

# Polyfills

> Functionalities in browsers that don't natively support them.

---

## Example with [classList](https://github.com/Polyfiller/polyfiller)

---

# Modernizr

> Modernizr tells you what HTML, CSS and JavaScript features the user’s browser has to offer.

---

## Fast detection

```js
Modernizr.on('flash', function( result ) {
  if (result) {
   // the browser has flash
  } else {
    // the browser does not have flash
  }
});
```

---

```js
function get_location() {
  if (Modernizr.geolocation) {
    navigator.geolocation.getCurrentPosition(show_map);
  } else {
    // no native support; maybe try a fallback?
  }
}
```

---

# Cross Device

---

# A challenge?

> Building A Responsive Web Application

---

# Responsive or Adaptive

---

# Designing for browser sizes?

> Responsive Web Design

---

## Fluid grids

## flexible images

## Media queries

---

## [Bootstrap](http://expo.getbootstrap.com/)
## [Foundation](http://foundation.zurb.com/)
## [Pure](http://purecss.io/)

---

# Designing for browser capabilities?

> Adaptive Web Design

---

# What web app features will Chrome/Firefox/IE support?

---

# Example

---

![template](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2013/05/flexbox_mini1.jpg)

---

![columns](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2013/05/responsicecolumns_mini1.jpg)

---

![date](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2013/05/datepicker-jquery_mini2.jpg)

---

![date](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2013/05/mobile-input-type-date_mini1.jpg)

---

![table](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2013/05/responsivedatable01_mini1.jpg)

---

![nav](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2013/05/navigations-mobile_mini1.jpg)

---

![table](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2013/05/responsivetable03_mini1.jpg)

---

![click](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2013/05/touchaccess_mini.jpg)

---

![icon](http://media.mediatemple.netdna-cdn.com/wp-content/uploads/2013/05/navigationicons_mini.jpg)

---

# Material Design Lite

> Library of components & templates in vanilla CSS, HTML and JS

---

# Good design and beautiful UI across all device

> Material Design by Google in 2014

---

# MDL for websites

---

### lite for
## Few dependencies
## Easy to install
## Easy to use
## Framework agnostic
## ~27KB gzipped

---

# Templates

---

![blog](http://www.getmdl.io/assets/templates/blog.jpg)

---

![dashboard](https://cdn-images-2.medium.com/max/800/1*foCgfXyJv5FjACTnEXpc0A.png)

---

![heavy](http://www.getmdl.io/assets/templates/text-only.jpg)


---

![post](http://www.getmdl.io/assets/templates/article.jpg)

---

# [components](http://www.getmdl.io/components/index.html)

---

## buttons
## text fields
## tooltips
## spinners
## responsive grids...

---

# GIT

---

# decentralised

---

# new repository

> git init


---

# checkout a repository

> git clone /path/to/repository

---

# TREES

---

## Working direcrtory
## Index
## HEAD

---

![trees](http://rogerdudler.github.io/git-guide/img/trees.png)

---

# ADD & COMMIT

---

> git add filename

> git add *

> git commit -m "Inital commit message"

---

# Push

> git push origin master

> git push origin branchename

---

# remote

> git remote add origin /path/to/repo

> git remote add upstream /path/to/repo

> git push upstream branchename

---

# branching

---

![branch](http://rogerdudler.github.io/git-guide/img/branches.png)

---

> git checkout -b feature-2637

> git checkout master

> git branch -d feature-2637

---

# Update

> git pull

# Merge

> git merge

---

# Diff

> git diff

---

#[.gitconfig](https://github.com/92bondstreet/dotfiles/blob/master/.gitconfig)

---

[# Front-end Tooling Workflows](https://speakerdeck.com/addyosmani/front-end-tooling-workflows)

> by Addy Osmani

---

# Thank You
