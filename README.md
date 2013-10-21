# Disclaimer
I'm developing Slideways using [Readme Driven Development](http://tom.preston-werner.com/2010/08/23/readme-driven-development.html), so this README is (more or less) a huge lie. I'll remove this disclaimer whenever the library actually matches its specification.

# Slideways
Slideways is a library for full page transitions, with mobile performance in mind. It provides a common interface to various transition providers (e.g. handwritten CSS, [animate.css](https://github.com/daneden/animate.css), jQuery.animate, etc.) and adds helpful features for things like Backbone.View or Marionette.View.

# Overview

To transition to a new page, Slideways follows the following steps, most of which are optional:

1) Position the new page outside of the viewport.
2) Force a reflow.
3) Transition the page to its ending position.
4) Remove the old page from the DOM.
5) Clean up after view object (i.e. kill all zombies).

# Installation

Just include it:

`<script src="slideways.js"></script>`

Or use [bower](http://bower.io):

`$ bower install slideways`
`<script src="/bower_components/slideways/index.js"></script>`

Use it with AMD:

```javascript
define(['slideways'], function(Slideways) {
  return function() {};
});
```

or CommonJS:

```javascript
var Slideways = require('slideways');
module.exports = function() {};
```

or throw caution to the wind!:

```javascript
!!window.Slideways; //true
```

# Usage

<pre>
************************************
* Viewport                         *
************************************
* +--------------------------------*--------------------------------+
* | #page-container                *                                |
* |--------------------------------*--------------------------------|
* |                                *                                |
* | +----------------------------+ * +----------------------------+ |
* | | .stage-center              | * | .stage-right               | |
* | |----------------------------| * |----------------------------| |
* | |                            | * |                            | |
* | |                            | * |                            | |
* | |                            | * |                            | |
* | |                            | * |                            | |
* | |                            | * |                            | |
* | |                            | * |                            | |
* | |                            | * |                            | |
* | |                            | * |                            | |
* | |                            | * |                            | |
* | |                            | * |                            | |
* | |                            | * |                            | |
* | |                            | * |                            | |
* | |                            | * |                            | |
* | |                            | * |                            | |
* | |                            | * |                            | |
* | +----------------------------+ * +----------------------------+ |
* |                                *                                |
* +--------------------------------*--------------------------------+
************************************
</pre>

# Gotchas

- `#page-container` should be `position: static`, otherwise when the pages are `position: absolute`d, they would positioned as children of `#page-container` instead of `body`, causing the reflow to reflow the contents of `#page-container` instead of just the new page. (This may or may not be an actual thing, requires more research to verify)

# Writing a transition provider

# TODO
- Support for subviews
- Extensive configuration options
- Automatically determine the sliding direction based on the page history.
- Provide a hook (using the webkitTransitionEnd event) for adding some logic when the transition completes.

# License
Slip n Slide is licensed under the [MIT License](http://opensource.org/licenses/MIT).
