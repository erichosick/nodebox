Just snippits - Please Ignore



===========

### Express ([Expressjs](http://expressjs.com/))

    $ npm install -g express

### [Browserify](http://browserify.org/)

    $ npm install -g browserify // may need sudo

## Old Stuff - Ignore

    $ echo $PATH | tr : "\n" | grep "/usr/local/bin"


Setup Npm Global Install [Without running as root](https://stackoverflow.com/questions/19352976/npm-modules-wont-install-globally-without-sudo).

    $ sudo npm update -g npm
    $ npm config set prefix ~/npm

    $ source ~/.bashrc


## Web Testing Using Mocha and Chai

### Setup

Don't run if you already have a public directory.

Create the templates

    $ mocha init public
    
Test it out by right mouse clicking on index.html.

Add chai.js to your setup (located in node_modules/chai/chai.js):





### Setup Automated Testing

If you want your tests to automatically reload:


https://github.com/ludovicofischer/mocha-chai-browser-demo



### Browserfy


    $ npm install browserify --save-dev


    https://www.npmjs.org/package/gulp-browserify


         $ npm install gulp-gzip --save-dev

https://stackoverflow.com/questions/15456426/global-require-with-browserify-v2




### Browserify Try 34


https://github.com/substack/browserify-handbook/blob/master/readme.markdown#introduction

http://viget.com/extend/gulp-browserify-starter-faq
https://github.com/gulpjs/gulp/blob/master/docs/recipes/fast-browserify-builds-with-watchify.md





## Older Configs

### Chrome Driver selenium stuff.


## Chrome Driver

### Install

    $ brew install chromedriver

Required paths should be setup by brew.


* [chromeDriver](http://chromedriver.storage.googleapis.com/index.html)


### Browser Testing

Setup chai-webdriver:

    $ npm install chai-webdriver --save-dev
    $ npm install selenium-webdriver --save-dev

// Regression testing web

var sw = require('selenium-webdriver');
var chai = require('chai');
var chaiWebdriver = require('chai-webdriver');

function seleniumSetup() {
   var driver = new sw.Builder()
     .withCapabilities(sw.Capabilities.chrome())
     .build()
   chai.use(chaiWebdriver(driver));
   driver.get('http://github.com');
   chai.expect('#site-container h1.heading').dom.to.contain.text("I'm a kitty!");
}

gulp.task('web-test', function() {
   seleniumSetup();
});


### [Browser Sync](http://www.browsersync.io/) Global

If you want to run browser-sync globally

    $ npm install -g browser-sync
   
To run globally (example has static files contained in a 'public' folder)

    $ browser-sync start --server "./public/" --files "./public/*.html"

[Angular-vs-Backbone](http://www.infoq.com/articles/backbone-vs-angular)

### [Livereload](https://www.npmjs.org/package/gulp-livereload)

    // $ npm install --save-dev gulp-livereload
    // $ npm install --save-dev connect

[Livereload Magic](http://rhumaric.com/2014/01/livereload-magic-gulp-style/)

    $ npm install tiny-lr --save-dev
    $ npm install connect-livereload --save-dev




http://blog.overzealous.com/post/74121048393/why-you-shouldnt-create-a-gulp-plugin-or-how-to-stop

    $ npm install gulp-livereload --save-dev 
    $ npm install connect --save-dev
    $ npm install connect-livereload --save-dev
    
    
https://www.youtube.com/watch?v=KURMrW-HsY4

### Grunt ([Getting Started](http://gruntjs.com/getting-started), [Grunt-Contrib](https://github.com/gruntjs/grunt-contrib))

    npm update -g npm
    npm install -g grunt-cli

### Continuous Development (Grunt, [Grunt-simple-mocha](http://fairwaytech.com/2014/01/understanding-grunt-part-2-automated-testing-with-mocha/))

        $ npm install grunt --save-dev // may need sudo
        $ npm install grunt-simple-mocha --save-dev
        $ touch gruntfile.js


        ### [Browsersync](http://www.browsersync.io/docs/gulp/)

        Place browser-sync in package.json.

          $ npm install browser-sync --save-dev

        [Options](http://www.browsersync.io/docs/options/) for setting up browser-sync.

        Basic static auto reload:

            var browserSync = require('browser-sync');

            ...
            
            // Static server
            gulp.task('browser-sync', function() {
              var config = {
                server: {
                  baseDir: "./public"
                },
                browser: ["google chrome", "firefox"]
              } 
              browserSync(config);
            });

            gulp.task('watch-browser', ['mocha','browser-sync'], function() {
                gulp.watch(['src/**', 'tests/**'], ['mocha']);
                gulp.watch(['public/**'], [reload]);
            });
