# Server-side DOM implementation based on Mozilla's dom.js


## Simplicity over Isolation

In contrast to the original [dom.js](https://github.com/andreasgal/dom.js) project, domino was not designed to run untrusted code. Hence it doesn't have to hide its internals behind a proxy facade which makes the code not only simpler, but eventually also more performant.

## Speed over Compliance

Domino is intended for _building_ pages rather than scraping them. Hence Domino doesn't execute scripts nor does it download external resources.

Also Domino doesn't implement any properties which have been deprecated in HTML5.

Domino sticks to the [DOM level 4](http://dvcs.w3.org/hg/domcore/raw-file/tip/Overview.html#interface-attr) working draft, which means that Attributes do not inherit the Node interface. Also [Element.attributes](http://dvcs.w3.org/hg/domcore/raw-file/tip/Overview.html#dom-element-attributes) returns a read-only array instead of a NamedNodeMap.

## Designed for Node

As the name might suggest, domino's goal is to provide a <b>DOM in No</b>de. The library is organized in CommonJS modules and doesn't require any additional build steps. Domino currently doesn't use any harmony features like proxies or WeakMaps and will also run in older Node versions.

## CSS Selector Support

Domino provides support for `querySelector()` and `querySelectorAll()` backed by the [Sizzle](http://sizzlejs.com/) selector engine.

## Usage

    var domino = require('domino');

    var window = domino.createWindow('<h1>Hello world</h1>');
    var document = window.document;

    var h1 = document.querySelector('h1');
    console.log(h1.innerHTML);

## Tests

Domino includes test from the [W3C DOM Conformance Suites](http://www.w3.org/DOM/Test/)
as well as tests from [HTML Working Group](http://www.w3.org/html/wg/wiki/Testing).

The tests can be run via `npm test` or directly though the [Mocha](http://visionmedia.github.com/mocha/) command line:

![Screenshot](http://fgnass.github.com/images/domino.png)

## License and Credits

The majority of the code was written by [Andreas Gal](https://github.com/andreasgal/) and [David Flanagan](https://github.com/davidflanagan) as part of Mozilla's dom.js project. Please refer to the included LICENSE file for the original copyright notice and disclaimer.
