# Tween.js

A versatile and performant **Tween API**

![Tween.js](/tween.png)

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
.start();

// instantiate Tween
const tween = Tween(object, fps);

// methods
// tween a property of object (chainable method)
tween.animate(property, keyframes, duration, delay, easing, options);
// keyframes is an object that has keyframe numbers or ranges as keys and paths as values
// Ex1:
// {'from':a, 'to':b}
// same as: {'0%':a, '100%':b}
// same as: {'0%-100%':Tween.Path.line(a, b)}
// same as: Tween.Path.line(a, b)

// Ex2:
// {'0%':0, '50%':0.3, '100%':1}

// Ex3:
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

// Tween.Easing implements various easing methods (similar to css easings)

// Tween.Path implements various curves that a tween property can be animated upon:
// Line: Tween.Path.line(a, b), line between a, b values
// PolyLine: Tween.Path.polyline(a, b, c, d, ..), polyline between a, b, c, d, .. values
// Bezier: Tween.Path.bezier(a, b, c [, d]), quadratic or cubic bezier by a, b, c [, d] control values
// Arc: arc=Tween.Path.arc(x1, y1, x2, y2, rx, ry, phi, fa, fs)
// use arc.x or arc.y
// elliptic arc curve from (x1,y1) to (x2,y2) with given radii and rotation phi and large arc fa and sweep fs flags
```