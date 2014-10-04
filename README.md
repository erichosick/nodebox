# Ultimate Node.js Full Stack Cheat Sheet

## Introduction

For OSX, JavaScript Node, Express, Postgress Sql, Grunt, Mocha and Chai

### Core Environment

* git
* github
* node
* [gulp](http://gulpjs.com/) ([gulp and grunt](http://jaysoo.ca/2014/01/27/gruntjs-vs-gulpjs/))
* PostgressSql

### Development, Testing and CI

* mocha
* chai
* coffeescript
* haml
* [Browserify](http://browserify.org/)
* [teacup](https://github.com/goodeggs/teacup)

### Front End

* [Angular](https://angularjs.org/) [Angular-vs-Backbone](http://www.infoq.com/articles/backbone-vs-angular)
* [rivets](http://rivetsjs.com/)
* [bootstrap](http://getbootstrap.com/)

## Setup OS X Development Machine

### Git

Install Git - [Download OSX](http://git-scm.com/download/mac).

    $ git --version // check current version

READ ME! APPEND AT END OF PATH TO OVERRIDE APPLE GIT

    $ echo 'export PATH=/usr/local/git/bin:$PATH' >> ~/.bash_profile

[Git Config](http://git-scm.com/book/en/Customizing-Git-Git-Configuration)

    $ git config --global user.name "DEVELOPER_NAME"
    $ git config --global user.email DEVELOPER_EMAIL
    $ git config --global core.editor mate // or your own

### Node Version Manager ([NVM](https://github.com/creationix/nvm))

Work on this later

### Node and NPM

Install [Node.js](http://nodejs.org/).

Setup Npm Global Install [Without Sudo](https://stackoverflow.com/questions/19352976/npm-modules-wont-install-globally-without-sudo).

    $ npm update -g npm
    $ npm config set prefix ~/npm
    $ echo 'export PATH="$PATH:$HOME/npm/bin"' >> ~/.bashrc

    $ source ~/.bashrc

    $ npm set init.author.name "YOUR_NAME"
    $ npm set init.author.email "YOUR_EMAIL"
    $ npm set init.author.url "http://YOUR_SITE"

Publishing a node module? Need a user

    $ npm adduser // creates ~/.npmrc

### Gulp

Install [Gulp globally](https://github.com/gulpjs/gulp/blob/master/docs/getting-started.md).

    $ npm install -g gulp // may need sudo

### Express ([Expressjs](http://expressjs.com/))

    $ npm install -g express

### Mocha Testing ([Mocha](https://visionmedia.github.io/mocha/))

    $ npm update -g npm
    $ npm install -g mocha

### [Browserify](http://browserify.org/)

    $ npm install -g browserify // may need sudo

## NEW Full-Stack Project

Development (You Are Ready To Go)

    $ cd ~/Projects/PROJ
    $ mate . // or use whatever editor you use
    $ gulp

Run tests individually

    $ mocha "tests/**/*.js" -w -u bdd -c

Or using npm

    $ npm test
  

Code away!

## Creating a New Project ([Creating a Node Project](http://quickleft.com/blog/creating-and-publishing-a-node-js-module), [Node From Scratch](https://www.codefellows.org/blog/create-a-node-js-project-from-scratch-with-node-sass))

Goto [github](https://www.github.com) signup and [create a project](https://github.com/new).

* Choose node.js for default project (for the .gitignore)
* Choose a license (MIT for example)
* Check a readme

Goto your development directory (~/Projects for example).

    $ cd ~/Projects/
    $ mkdir PROJ
    $ cd PROJ
    $ git init

    $ git remote add origin git@github.com:ORGANIZATION/PROJ.git
    $ git pull origin master

    npm init
    
[Package Documentation](https://www.npmjs.org/doc/files/package.json.html)) for options.

* name : check first to [see if it exists](https://www.npmjs.org/).
* main: MAIN_FILE
* test command: mocha 'tests/**/*.js' -w -u bdd -c
* version: VERSION see [SemVer](http://semver.org/)

Create core js file:

    $ mkdir src
    $ mkdir dist
    $ touch src/MAIN_FILE.js

For user issues:

    $ mkdir issues

### Continuous Development ([Gulp](https://github.com/gulpjs/gulp/blob/master/docs/getting-started.md))

    $ npm install --save-dev gulp
    $ touch gulpfile.js
    $ mate gulpfile.js

Add the following

    var gulp = require('gulp');
    var gutil = require('gulp-util');

    gulp.task('default', function() {
      // place code for your default task here
      // ALWAYS do return gulp.task(...); or synchronous tasks will not work
    });
    
Great reads:

* [Building With Gulp](http://www.smashingmagazine.com/2014/06/11/building-with-gulp/)
* [Running Tasks in Series](https://github.com/gulpjs/gulp/blob/master/docs/recipes/running-tasks-in-series.md)

### Testing Mocha and Chai

[Add a test, always add test](https://www.youtube.com/watch?v=7BpwdhAhep0&t=07)!

    $ npm install mocha --save-dev
    $ npm install chai --save-dev // may need sudo
    $ npm install --save-dev gulp-mocha
    $ npm install --save-dev gulp-util
    
Add to gulpfile.js    
See [reporters](https://visionmedia.github.io/mocha/#reporters) for different reporters (we are using spec here).

    var mocha = require('gulp-mocha');

    gulp.task('mocha', function() {
      return gulp.src(['tests/*.js'], { read: false })
        .pipe(mocha({ reporter: 'spec' }))
        .on('error', gutil.log);
    });

    gulp.task('watch-mocha', function() {
      return gulp.watch(['src/**', 'tests/**'], ['mocha']);
    });    

Setup initial test file
    
    $ mkdir tests
    $ touch tests/MAIN_FILE.js

Using Chai and expect and Javascript

    $ echo 'var chai = require("chai");' >> tests/MAIN_FILE.js
    $ echo 'var expect = chai.expect;' >> tests/MAIN_FILE.js
    $ echo 'var LIBRARY_NAME = require("../src/MAIN_FILE.js");' >> tests/MAIN_FILE.js

### [CoffeeScript Gulp](https://www.npmjs.org/package/gulp-coffee)

    $ npm install --save-dev gulp-coffee // may need sudo?

Add the following to the existing gulpfile.js. Check the "source" and "destination" directory.

    var coffee = require('gulp-coffee');

    gulp.task('coffee', function() {
      return gulp.src('./src/*.coffee')
        .pipe(coffee({bare: true}).on('error', gutil.log))
        .pipe(gulp.dest('./public/'))
    });

### [Uglify Gulp](https://www.npmjs.org/package/gulp-uglify)

Make things smaller.

    $ npm install --save-dev gulp-uglify // may need to sudo

Add the following to an existing gulpfile.js. Check the "source" and "destination" directory.

    var uglify = require('gulp-uglify');

    gulp.task('compress', function() {
      return gulp.src('lib/*.js')
        .pipe(uglify())
        .pipe(gulp.dest('dist'))
    });
    
    
### Rename Streams

Rename a stream so you can do like file.js and then file-min.js

    $ npm install --save-dev gulp-rename // may need to sudo

Add the following to an existing gulpfile.js.

    var rename = require('gulp-rename');
    
example:

    .pipe($.rename('app.min.js'))

### Browserfy ([Handbook](https://github.com/substack/browserify-handbook), [Gulp Browserify](http://viget.com/extend/gulp-browserify-starter-faq), [Bulp Browserify and Watchify](https://github.com/gulpjs/gulp/blob/master/docs/recipes/fast-browserify-builds-with-watchify.md))

Turn your core javascript file into a single browsable .js.

    $ npm install --save-dev vinyl-source-stream // may need sudo?
    $ npm install --save-dev browserify // may need sudo?
    $ npm install --save-dev watchify // may need sudo?
    
Add the following to the existing gulpfile.js.

    var source = require('vinyl-source-stream');
    var watchify = require('watchify');
    var browserify = require('browserify');

    gulp.task('watch', function() {
      var bundler = watchify(browserify('src/MAIN_FILE.js', watchify.args));

      // Optionally, you can apply transforms
      // and other configuration options on the
      // bundler just as you would with browserify
      bundler.transform('brfs');

      bundler.on('update', rebundle);

      function rebundle() {
        return bundler.bundle()
          // log errors if they happen
          .on('error', gutil.log.bind(gutil, 'Browserify Error'))
          .pipe(source('bundle.js'))
          .pipe(gulp.dest('./dist'));
      }

      return rebundle();
    });

### First Push

    $ git add .
    $ git add -A
    $ git commit -m “Initial version”
    $ git push origin master
    $ git tag 1.0.0 // VERSION during npm init
    $ git push origin master —tag


===========

## Older Configs

### Grunt ([Getting Started](http://gruntjs.com/getting-started), [Grunt-Contrib](https://github.com/gruntjs/grunt-contrib))

    npm update -g npm
    npm install -g grunt-cli

### Continuous Development (Grunt, [Grunt-simple-mocha](http://fairwaytech.com/2014/01/understanding-grunt-part-2-automated-testing-with-mocha/))

        $ npm install grunt --save-dev // may need sudo
        $ npm install grunt-simple-mocha --save-dev
        $ touch gruntfile.js




