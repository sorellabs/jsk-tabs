Tabs
====

JumperSkirt's **Tab** component implementation.



### Usage

Tabs can be either anchors with a ``jsk-anchor`` class and a ``href`` attribute
pointing over to the element's ID, or ``data-jsk-target`` attribute pointing to
the target's ID.

```html
<style>
  .tabs > div { display: none }
  .tabs > div.active { display: block }
</style>

<ul class="tab-list">
  <li><a href="#tab1" class="jsk-anchor">Tab 1</a></li>
  <li><a href="#tab2" class="jsk-anchor">Tab 2</a></li>
  <li class="last" data-jsk-target="tab3">Tab 3</li>
</ul>

<div class="tabs">
  <div id="tab1" class="active">First tab</div>
  <div id="tab2">Second tab</div>
  <div id="tab3">Third tab</div>
</div>
```

To initialise the tabs, just instantiate the ``jsk-tabs`` module (you can pass
a selector engine and an event manager if you're supporting older browsers),
and pass a selector for an element containing the tab anchors.

```js
var tabify = require('jsk-tabs')(Sizzle, require('moros/lib/bridge/bean'))
tabify('.tab-list:not(.jskp-tabgroup)')
// adding the `:not(.jskp-tabgroup)` constraint ensures elements are
// processed for tabifying just once.
```

A group is created for each matching element for the given selector, groups
ensure that only one tab in that group is active at any given time. The
initialisation code doesn't mark any tab as active — you can do that yourself
in the HTML, since an active tab is just an element with class ``active``.

Take a look at the ``docs/examples/`` folder for more usage examples.


### Requirements and supported platforms

This library makes use of a safely shim-able subset of ECMAScript 5
features. If you need to support older browsers, you'll have to include
the [es5-shim][] library.



### Installation

If you're using [Browserify][] — you really should! — to manage your
dependencies, just grab it from [NPM][]:

```bash
$ npm install -d jsk-tabs
```

Otherwise, [download the latest release][] and include both the
Browserify prelude and the Tabs library in your page:

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>Ur Awesome Stuff</title>
  </head>
  <body>
    {{ Lots of stuff might go here }}
    <script src="/path/to/browserify.js"></script>
    <script src="/path/to/jsk-tabs.js"></script>
  </body>
</html>
```

In any of the cases above, Tabs will be a `require`-able module in your
platform, so you can just use `require("jsk-tabs")` to instantiate it.



### Building

If you want to build stuff from the source, you'll need
[LiveScript][]. Once you've got that installed and `Slake` on your path,
just run:

```bash
$ git clone git:/github.com/killdream/jsk-tabs.git   # Download the project
$ cd jsk-tabs                                        # Move to the project folder
$ npm install -d                                     # Initialise the dependencies
$ slake build:all                                    # Runs the build tasks
```


### Tests

For building the test files, you can use `slake test`. For building them
continuously, use `slake test:continuous`.



### Licence

Tabs is licensed under the delicious and permissive [MIT][] licence. You
can happily copy, share, modify, sell or whatever — refer to the actual
licence text for `less` information:

```bash
$ less LICENCE.txt
```

[download the latest release]: https://github.com/downloads/killdream/jsk-tabs/jsk-tabs-0.1.0.tar.gz

[es5-shim]: https://github.com/kriskowal/es5-shim
[Browserify]: https://github.com/substack/node-browserify
[NPM]: http://npmjs.org/
[LiveScript]: https://gkz.github.com/LiveScript
[MIT]: https://raw.github.com/killdream/jsk-tabs/master/LICENCE.txt
