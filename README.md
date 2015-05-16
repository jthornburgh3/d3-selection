# d3-selection

This EXPERIMENTAL module implements the core concept of D3: manipulating the DOM by selecting elements and joining to data.

API changes from D3 3.x:

* The Selection class now extends Object, not Array, obviating the need for [prototype injection](http://perfectionkills.com/how-ecmascript-5-still-does-not-allow-to-subclass-an-array/#wrappers_prototype_chain_injection) (and [direct property injection](http://perfectionkills.com/how-ecmascript-5-still-does-not-allow-to-subclass-an-array/#wrappers_direct_property_injection) on runtimes that do not support `__proto__`). See [#2191](https://github.com/mbostock/d3/issues/2191).

* The selection.data method, when called with arguments, now modifies the current selection to be the update selection. Previously, selection.data returned a new selection. See [#2402](https://github.com/mbostock/d3/issues/2402).

* The selection.enter and selection.exit selections are now simply fields (defined by selection.data), not methods. See [#2402](https://github.com/mbostock/d3/issues/2402).

* The selection.data method, when called *without* arguments, now returns an array of data for all elements in the selection, not just the first group.

* Similarly, a new selection selection.nodes method returns an array of all elements in the selection, flattening the underlying groups.

* The implementation is now organized into CommonJS modules, rather than the ad hoc [SMASH](https://github.com/mbostock/smash) concatenation process used previously. A standalone build is provided for your convenience using [Browserify](http://browserify.org/), but you are free to define your own build process (e.g., [Webpack](https://webpack.github.io/)). See [#2220](https://github.com/mbostock/d3/issues/2220).

* The selection.classed method has been renamed selection.class. (Note: `class` is a reserved word in ES6, but ES5 and later allow reserved words as identifier names.)

* The selection.on method has been renamed selection.event.

* A new selection.dispatch method dispatches a [custom event](https://dom.spec.whatwg.org/#interface-customevent) of the specified type to all selected elements.

* The d3.ns.prefix namespace map is now exposed as d3.namespace.

* [Multi-value map](http://bl.ocks.org/mbostock/3305515) variants of selection.attr, selection.style, selection.property, selection.class and selection.on are now implemented as distinct methods in the [d3-selection-multi plugin](https://github.com/d3/d3-selection-multi), rather than overloading the arguments. See [#2109](https://github.com/mbostock/d3/issues/2109).

* Removed support for Sizzle. It’s time.
