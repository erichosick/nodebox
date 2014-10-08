# Ultimate Node.js Full Stack Cheat Sheet

# <a name="toc"></a>TOC

* [TOC](#toc)
* [Introduction](#introduction)
* [Setup Your Development Machine](#osx)
* [Creating a New Project](#new-project)
* [Developing in Your Project](#developing-project)

---

# <a name="introduction"></a>Introduction

This document will, hopefully, get you up and running developing web based applications with node on the back end.

For a lot of tools, there are multiple choices (browsersync or CodeKit). The ones chosen were based on a gut feel.

Text in ALL-CAPS is something you need to enter a value for.

## <a name="global-env"></a>Global Environment Tools

[osx-link]: https://www.apple.com/osx/ "OS X operating system"
[brew-link]: http://brew.sh/ "Package manager for OS X"
[brew-link-install]: http://brew.sh/#install "Install brew"
[git-link]: http://git-scm.com/ "Version control system"
[github-link]: https://github.com/ "Place to share and store git repositories"
[nvm-link]: https://github.com/creationix/nvm "Manage different node versions"
[node-link]: http://nodejs.org/ "Run javascript outside of a browser"
[npm-link]: https://www.npmjs.org/ "Find and manage node packages"
[gulp-link]: http://gulpjs.com/ "A system to setup automated builds"
[postgres-link]: http://www.postgresql.org/ "Sql database systems"

* [OS X][osx-link] ([setup](#osx)) - OS X operating system.
* [brew][brew-link] ([setup](#brew)) - Package manager for OS X.
* [git][git-link] ([setup](#git)) - Version control system.
* [github][github-link] ([setup](#github), [project](#github-project)) - Place to share and store git repositories.
* [nvm][nvm-link] ([setup](#nvm)) - Manage different node versions.
* [node][node-link] ([setup](#node)) - Run javascript outside of a browser.
* [npm][npm-link] ([setup](#npm)) - Find and manage node packages.
* [gulp][gulp-link] ([setup](#gulp), [project](#gulp-project)) - A system to setup automated builds.
* TODO: [postgres][postgres-link] - a sql database system.

## <a name="global-resources"></a>Resources

[npmjs-link]: https://www.npmjs.org/ "find node packages"
[cdnjs-link]: http://www.cdnjs.com/ "cdn for javascript"
[jsperf-link]: http://jsperf.com/ "performance testing for java script"
[github-ignore-link]: https://github.com/github/gitignore "List of github ignore files"
[yeoman-link]: http://yeoman.io/ "Package generator to get projects started"

* [npmjs][npmjs-link] - find node packages.
* [cdnjs][cdnjs-link] - cdn for javascript.
* [jsperf][jsperf-link] - performance testing for java script.
  * example [mixin-fun](http://jsperf.com/mixin-fun/2)
  * mechanism example [mechanisms](http://jsperf.com/mechanism03/2)
* [github ignore][github-ignore-link] - List of github ignore files
* [yeoman.io][yeoman-link] - Package generator


## <a name="global-dev-support"></a>Project Development Support

## Project Environment Testing Tools

### Testing Backend

[mocha-link]: https://visionmedia.github.io/mocha/ "Testing engine running on node"
[chai-link]: http://chaijs.com/ "Assertion library with should, expect and assert"
[cucumber-link]: https://github.com/cucumber/cucumber-js "BDD using gherkin"

* [mocha][mocha-link] ([project](#mocha-project)) - Testing engine running on node.
* [chai][chai-link] ([project](#chai-project))- Assertion library (should, expect, assert)
* TODO: [cucumber][cucumber-link] - BDD using gherkin which is AWESOME.

### Testing Frontend

[browserSync-link]: http://www.browsersync.io/ "Live reloading in a browser"
[chai-webdriver-link]: https://github.com/goodeggs/chai-webdriver "Continuous integration"

* TODO: [browserSync][browserSync-link] ([project](#browserSync-project)) - Live reloading in a browser
* TODO: [chai-webdriver][chai-webdriver-link] - Continuous integration.

## Project Environment Development Tools

### Backend

[teacup-link]: https://github.com/goodeggs/teacup "Node template engine with Coffeescript type syntax"
[haml-link]: http://haml.info "Rails template engine"
[jade-link]: http://jade-lang.com/ "Node template engine"
[handlebars-link]: http://handlebarsjs.com/ "Template engine with {{ }} syntax"
[mustache-link]: https://mustache.github.io/ "Template engine with {{ }} syntax"
[express-link]: http://expressjs.com/ "A web application framework for node"

* [coffeescript](http://coffeescript.org/) optional
* [browserify](http://browserify.org/) optional
* TODO: [haml][haml-link] - Rails Template engine
* TODO: [jade][jade-link] - Node template engine
* TODO: [handlebars][handlebars-link] - Template engine with {{ }} syntax.
* TODO: [mustache][mustache-link] - Template engine with {{ }} syntax.
* TODO: [teacup][teacup-link]([project](#teacup-project)) - Template engine with Coffeescript type syntax.

* [express](http://expressjs.com/) ([project](#express-project)) - A web application framework for node.

### Front End

* TODO: [angular](https://angularjs.org/) 
* TODO: [rivets](http://rivetsjs.com/)
* TODO: [bootstrap](http://getbootstrap.com/)


---

# <a name="osx"></a>Setup Your Development Machine

Let's install everything you need to get going. Later, we will talk about how to use them.

## <a name="brew"></a>Home Brew

### Installation

From [Brew][brew-link-install] website:

    $ ruby -e "$(curl -fsSL https://raw.github.com/Homebrew/homebrew/go/install)"
    
Add path to your bash_profie (if it isn't there already):
    
    $ echo 'export PATH=/usr/local/bin:$PATH' >> ~/.bash_profile
    
Reload your terminal session:

    $ source ~/.bash_profile

Update brew to the latest version:

    $ brew doctor

## <a name="git"></a>Git

### Install

[Download OSX](http://git-scm.com/download/mac) and following instructions.

> READ ME! We can append the git path to the beginning of PATH to override apples git.

Append path, reload path and verify version:

    $ echo 'export PATH=/usr/local/git/bin:$PATH' >> ~/.bash_profile
    
Reload your terminal session:    
    
    $ source ~/.bash_profile
    
Verify the version:

    $ git --version

### Configure

[Git Config](http://git-scm.com/book/en/Customizing-Git-Git-Configuration)

    $ git config --global user.name "DEVELOPER-NAME"
    $ git config --global user.email DEVELOPER-EMAIL
    $ git config --global core.editor vi // This is for vi.

## <a name="github"></a> Github

### Setup

You will need to go to [github][git-link] and setup a user account if you haven't done so already.

We suggest using your DEVELOPER-NAME and DEVELOPER-EMAIL set in git.

## <a name="nvm"></a> Node Virtual Manager

### Install [NVM](https://github.com/creationix/nvm)

With [Brew](http://brewformulas.org/Nvm).

    $ brew install nvm
    $ echo 'export NVM-DIR=~/.nvm' >> ~/.bashrc
    $ echo 'source $(brew --prefix nvm)/nvm.sh' >> ~/.bashrc
    $ source ~/.bashrc

### <a name="node"></a> Install Node Using NVM

Setup node (latest version was 0.10 at the time of this writing)

    $ nvm install 0.10
    $ echo 'export PATH="$PATH:$HOME/npm/bin"' >> ~/.bashrc
    $ nvm alias default 0.10
    
List version installed

    $ nvm ls

### <a name="npm"></a> Setup NPM

Setup npm defaults.

    $ npm set init.author.name "YOUR-NAME"
    $ npm set init.author.email "YOUR-EMAIL"
    $ npm set init.author.url "http://YOUR-SITE"

Publishing a node module? Then you need to create a user.

    // creates ~/.npmrc
    $ npm adduser 

### Local, Global and Both NPM

See [Npm-folders](https://www.npmjs.org/doc/files/npm-folders.html)

Running a module on command line: it needs to be global.

Running a module using requires modules to be placed in PROJECT/node_modules

Using a module in both: npm link


## <a name="gulp"></a> Gulp Global

### Install

Gulp [installation](https://github.com/gulpjs/gulp/blob/master/docs/getting-started.md) help.

We are running Gulp from the command line so:

    $ npm install -g gulp

### Similar tools

* [gulp and grunt](http://jaysoo.ca/2014/01/27/gruntjs-vs-gulpjs/)
    
## Mocha Testing Global ([Mocha](https://visionmedia.github.io/mocha/))

### Install

If you want to run mocha globally:

    $ npm install -g mocha

---

# <a name="new-project"></a>Creating a New Project

## Resouces

* [Creating a Node Project](http://quickleft.com/blog/creating-and-publishing-a-node-js-module)
* [Node From Scratch](https://www.codefellows.org/blog/create-a-node-js-project-from-scratch-with-node-sass)

## <a name="github-project"></a>Step 1 - Github Project

[Create a project](https://github.com/new) chosing the correct default project, readme and license (see below).

### A Node Project?

* Choose node.js for default project (for the .gitignore)
* Choose a license (MIT for example)
* Check a readme

## Setup 2 - Create a Project Directory

### Create Project

Goto your development directory (~/Projects for example).

    $ cd ~/YOUR-DEV-DIRECTORY/
    $ mkdir PROJ
    $ cd PROJ
    $ git init

    $ git remote add origin git@github.com:ORGANIZATION/PROJ.git
    $ git pull origin master

    npm init
    
### User Issues

[Github][github-link] has a built in issue support system for your project. Let's create a directory for issues.

    $ mkdir issues

### Node Package?
    
Setup node package information. See [package documentation](https://www.npmjs.org/doc/files/package.json.html)) for options.

* name : check first to [see if it exists](https://www.npmjs.org/).
* main: MAIN-FILE
* test command: mocha 'tests/**/*.js' -w -u bdd -c
* version: VERSION see [SemVer](http://semver.org/)

## <a name="gulp-project"></a>Step 3 - Gulp Continuous Development

### Introduction

Continuous development allows you to make changes and have actions occur for you automatically based on those changes. Examples are converting coffeescript to javascript and running regression tests.

[Gulp][gulp-link] helps you with continuous development. Gulp is **huge** and we can't cover everything in this document.

### Resources

* [Building With Gulp](http://www.smashingmagazine.com/2014/06/11/building-with-gulp/)
* [Running Tasks in Series](https://github.com/gulpjs/gulp/blob/master/docs/recipes/running-tasks-in-series.md)

### Installation

Setup gulp locally

    $ npm install --save-dev gulp

Create a gulp configuration file:
    
    $ touch gulpfile.js
    
Open it in your favorite editor (this is textmate):
    
    $ mate gulpfile.js

Add the following:

```javascript
var gulp = require('gulp');
var gutil = require('gulp-util');

gulp.task('default', [], function() {
});
```

## <a name="mocha-project"></a>Step 4 - Mocha Chai Testing Backend

### Introduction

Remember to [add a test, always add test](https://www.youtube.com/watch?v=7BpwdhAhep0&t=07)!

Mocha and chai can be used to test your backend. Let's setup automatic testing for backend code. Note that browser testing and headless front end testing are provided below.

TODO: Add links to browser testing

### Installation

From your project directory:

    $ npm install --save-dev mocha
    $ npm install --save-dev chai
    $ npm install --save-dev gulp-mocha
    $ npm install --save-dev gulp-util


Your gulpfile.js:

```javascript
var gulp = require('gulp');
var gutil = require('gulp-util');
var mocha = require('gulp-mocha');

gulp.task('default', ['mocha','watch-mocha'], function() {});

gulp.task('mocha', function() {
    return gulp.src(['tests/*test.js'], { read: false })
        .pipe(mocha({ reporter: 'spec' }))
        .on('error', gutil.log);
});

gulp.task('watch-mocha', function() {
    return gulp.watch(['src/**', 'tests/**'], ['mocha']);
});
```

#### HAVE RETURNS IN YOUR TASKS!!!

It is very important to have a 'return' for your gulp task. This allows other tasks to wait on your task before the start execution (see the default task for an example).

As an example, if you forget a return, gulp may run a test before it's finished generating javascript from coffeescript. This leads to strange behavior where you need to save twice to get your changes recognized by your tests.

#### Gulp Default Task

The default task is ran when you type the following in your project directory:

    $ gulp // don't do it yet
    
In our example, we will run all of our tests first, then watch for any changes in our source and test directories.

```javascript
// Task is named 'default'
// The task named 'mocha' will run and then 'watch-mocha' will run
// When those are done, the 'default' task runs (which is empty)
gulp.task('default', ['mocha','watch-mocha'], function() {});
```

#### Gulp Mocha Task

In our example, we have placed all of our tests in a directory called tests.

```javascript
// ...
return gulp.src(['tests/*test.js'], { read: false })
// ...
```

We can display the results of our test using different [reporters](https://visionmedia.github.io/mocha/#reporters). We are using 'spec' for our tests.

```javascript
// ...
.pipe(mocha({ reporter: 'spec' }))
// ...
```

#### Gulp Watch Task

Gulp can watch changes to any directory and then run a gulp task when a change occurs in that task (see TODO: Watchifiy to speedup development).

In this case, we are watching all files in the src directory (src/**) and all files in the tests directory (tests/**). We then run the 'mocha' task if any files change in either of these directories.

```javascript
// ...
return gulp.watch(['src/**', 'tests/**'], ['mocha']);
// ...
```

## <a name="chai-project"></a>Step 5 - Your First Test

### Introduction

We will be using mocha and expect as the assertion library. Chai 

### Setup Your Test Files

We are putting tests in the directory tests but you can use another directory. We are placing our source files in the src directory but you can use another one. For every file in src you should create a test in the tests directory
    
    $ mkdir tests
    $ touch tests/MAIN-FILE.js

Open your MAIN-FILE.js and add the following

```javascript
var chai = require("chai");
var expect = chai.expect;
var LIBRARY-NAME = require("../src/MAIN-FILE.js");

describe("your first test", function() {
  it ("should pass one test", function() {
    expect("it works!").to.equal("it works!");
  });
});
```
    
Save the file and run gulp to start testing:

    $ gulp
    
You should see one test pass. Woo hoo!!!

## Step 6 Coffeescript

[Coffeescript][coffeescript-link]


### [CoffeeScript Gulp](https://www.npmjs.org/package/gulp-coffee)

    $ npm install --save-dev gulp-coffee // may need sudo?

Add the following to the existing gulpfile.js. Check the "source" and "destination" directory.

```javascript
var coffee = require('gulp-coffee');

gulp.task('coffee', function() {
  return gulp.src('./src/*.coffee')
    .pipe(coffee({bare: true}).on('error', gutil.log))
    .pipe(gulp.dest('./public/'))
});
```


## Step 7 [Uglify Gulp](https://www.npmjs.org/package/gulp-uglify)

Make things smaller.

    $ npm install --save-dev gulp-uglify // may need to sudo

Add the following to an existing gulpfile.js. Check the "source" and "destination" directory.

```javascript
var uglify = require('gulp-uglify');

gulp.task('compress', function() {
  return gulp.src('lib/*.js')
    .pipe(uglify())
    .pipe(gulp.dest('dist'))
});
```
    
### Rename Streams

Rename a stream so you can do like file.js and then file-min.js

    $ npm install --save-dev gulp-rename // may need to sudo

Add the following to an existing gulpfile.js.

    var rename = require('gulp-rename');
    
example:

    .pipe($.rename('app.min.js'))


## Browser Development

If you will be developing programs that run in the browser.

## Step 8 Browserify

### Introduction

Browserify let's you use "require" in a web page. It takes a node module at makes it work on the web. You can also merge together multiple node packages into a single javascript file that you include in your web page.

Remember, you need to require and export node modules you want to require('') in your webpage. See our post on getting browserify working [here](https://github.com/erichosick/nodeboxrequire/) for more information.

### Resources

* ([Handbook](https://github.com/substack/browserify-handbook)
* [Gulp Browserify](http://viget.com/extend/gulp-browserify-starter-faq)
* [Gulp Browserify and Watchify](https://github.com/gulpjs/gulp/blob/master/docs/recipes/fast-browserify-builds-with-watchify.md))

TODO: Show how browserify integrates with watchify.

## <a name="express-project"></a>Step 9 Express

### Introduction

Let's setup an [Express][express-link] project to serve web-pages. We will need to do this so we have a system to generate dynamic-web page content that BrowserSync can run against.

### Installation

Follow the instructions at [express guide](http://expressjs.com/guide.html).

Things to consider when using Express

* Add a .gitignore file. An example is the [node gitignore](https://github.com/github/gitignore/blob/master/Node.gitignore) file.
* Choose a template engine [Node Templates](https://paularmstrong.github.io/node-templates/).
  * See [Teacup](#teacup-project) below for the one we are using.



## <a name="teacup-project"></a> Teacup Template Engine

### Introduction

[Teacup][teacup-link] is a node template engine.

### Setup

See [Teacup][teacup-link] for more information.

Add Teacup to your project (can't it just be for development?):

    $ npm install --save teacup





## <a name="browserSync-project"></a>Step 10 BrowserSync

### Introduction

Every time you make a change to your project, you may want to see what it looks like. This would usually mean that you need to go refresh the web page. Let's setup [browserSync][browserSync-link] so you can watch all of your changes live.

We an sync both static and dynamic web pages. For dynamic web pages, we are using [Express][express-link].

### Installation Command Line

If you want to run [browserSync][browserSync-link] from the command line then run:

    $ npm install -g browser-sync

### browserSync Gulp Tasks

Let's setup some browserSync tasks in Gulp.





https://github.com/shakyShane/browser-sync
https://github.com/quagliero/generator-gulp-webapp
http://addyosmani.com/blog/browser-sync/
http://www.browsersync.io/
https://www.npmjs.org/package/browser-sync





TODO: Show how it integrates with watchify.

### Similar Tools

See [slant](http://www.slant.co/topics/1479/compare/~browsersync_vs_livereload_vs_codekit) for more info.

* [Livereload](http://livereload.com/) (don't need to purchase)
* [Codekit](https://incident57.com/codekit/) - Looks really cool but need to purchase.



## First Push

    $ git add .
    $ git add -A
    $ git commit -m “Initial version”
    $ git push origin master
    $ git tag 0.1.1 // VERSION during npm init
    $ git push origin master -—tag

## OTHER










### Uninstall Everything

#### When Installed from package file downloaded from node.

To restart from scratch see [Uninstall Node](https://stackoverflow.com/questions/11177954/how-do-i-completely-uninstall-node-js-and-reinstall-from-beginning-mac-os-x).

BE CAREFUL

    $ sudo rm -rf /usr/local/lib/node_modules
    $ sudo rm /usr/local/lib/node
    $ sudo rm /usr/local/bin/npm
    $ sudo rm -rf /usr/local/include/node
    $ sudo rm -rf /usr/local/include/node_modules
    $ rm -rf ~/.npm
    $ sudo rm -rf /usr/local/share/man/man1/node.1
    $ rm /usr/local/lib/dtrace/node.d

---

# <a name="developing-project"></a>Developing in Your Project

Follow steps in "Create a New Project".

### Development

Go to directory of project, edit and start continuous development environment

    $ cd ~/Projects/PROJ
    $ npm install
    $ mate . // or use whatever editor you use

Run tests

    $ gulp watch-mocha

Or running directly with mocha

    $ mocha "tests/**/*test.js" -w -u bdd -c

Code away!

### Publishing a Module

    $ git add .
    $ git add -A
    $ git commit -m “Some message”
    $ git push origin master
    $ git tag 0.1.1 // VERSION in package.json
    $ git push origin master -—tag
    $ npm publish

