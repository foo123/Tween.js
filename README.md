# Tween.js

A versatile and performant **Tween API**

**version: 1.0.0 in progress**


**Demo Example**

* [Rubik3](http://foo123.github.io/examples/rubik3/)


**API**

```js
// animate an HTML element
const el = document.getElementById('animated');

Tween({alpha:0, x:0, y:0}, 60/*fps*/)
.animate('alpha', {from:0, to:1}, 400/*duration*/, 0/*delay*/)
.animate('x', Tween.Path.bezier(0, 30, 10), 600/*duration*/, 0/*delay*/, 'ease-out'/*easing*/)
.animate('y', Tween.Path.bezier(0, 30, 10), 600/*duration*/, 0/*delay*/, 'ease-out'/*easing*/, {
    // callbacks
    onStart: function(obj, tween) { },
    onProgress: function(obj, tween) {
        el.style.left = obj.x.toFixed(2) + 'px';
        el.style.top = obj.y.toFixed(2) + 'px';
        el.style.opacity = obj.alpha.toFixed(2);
    },
    onEnd: function(obj, tween) { }
})
.initialize()
.start();

// instantiate Tween
const tween = Tween(object, fps);

// methods
// tween a property of object (chainable method)
tween.animate(property, keyframes, duration, delay, easing, options);
// keyframes are objects that have keyframe numbers or ranges as keys and paths as values
// eg:
// {'from':0, 'to':1} same as {'0%':0, '100%':1} same as {'0%-100%':Tween.Path.line(0, 1)}
// {'0%':0, '50%':0.3, '100%':1}
// {'0%-50%':Tween.Path.line(0, 0.3), '50%-100%':Tween.Path.bezier(0.3, 0.5, 0.6, 1)}
// etc..

// reverse tween (chainable method)
tween.reverse();

// initialize tween, set object properties to initial values (depending on direction of tween) (chainable method)
tween.initialize();

// finalize tween, set object properties to final values (depending on direction of tween) (chainable method)
tween.finalize();

// stop tween (chainable method)
tween.stop();

// resume tween (chainable method)
tween.resume();

// rewind tween, so it can replay (chainable method)
tween.rewind();

// update tween manually (only if start() method is not used) (chainable method)
tween.update();

// start tween, immediately if immediately = "immediately", updates tween automatically (chainable method)
tween.start(immediately);

// whether tween has finished (true/false)
tween.finished();

// the fps of the tween (integer)
tween.fps();

// dispose tween
tween.dispose();

// Tween.Easing implements various easing methods
// Tween.Path implements various curves that a tween property can be animated upon (except the trivial "line" curve)
```