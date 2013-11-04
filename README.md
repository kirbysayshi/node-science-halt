
science-halt
============

usage
-----

````js
var scihalt = require('science-halt');

scihalt(function(){
  // do something when ESC is pressed
})
````

rationale
---------

This is a stupid module. Everytime I make a game loop, I do something like this:

````js
var last = Date.now()
  , running = true;

(function anim() {
  if (running) requestAnimationFrame(anim);
  var now = Date.now();
  doUpdate(now - last);
  last = now;
}());

document.addEventListener('keydown', function(e) {
  if (e.which == 27) {
    running = false;
    console.log('HALT IN THE NAME OF SCIENCE!');
  }
})
````

This module takes care of the keybinding for halting... because apparently I find `27` a really hard number to remember. The above example becomes:

````js
var scihalt = require('science-halt');

var last = Date.now()
  , running = true;

(function anim() {
  if (running) requestAnimationFrame(anim);
  var now = Date.now();
  doUpdate(now - last);
  last = now;
}());

scihalt(function() { running = false; })
````
