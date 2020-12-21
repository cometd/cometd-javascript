## The CometD Project

Welcome to the [CometD](https://cometd.org) Project, a scalable comet 
(server push) and websocket messaging library for the web.

This repository mirrors the JavaScript sources hosted at the [main
CometD repository](https://github.com/cometd/cometd).
Those JavaScript sources are not suitable to be consumed with NPM,
and are therefore re-arranged in this repository for to make it simpler
to use CometD with NPM.

### Versions

`5.0.x` &#8658; based on CometD 5.0.x - minimal ECMAScript 5 (`var` everywhere)  
`6.0.x` &#8658; N/A  
`7.0.x` &#8658; based on CometD 7.0.x - minimal ECMAScript 6 (`let`, `const` and arrow functions)

Version `6.0.x` is not released to NPM since it's identical to `7.0.x`.  
The `6.0.x` numbering exists only because the main CometD project, on the server side, is different from `7.0.x`, but on the client side there is no difference.

### License

The CometD source code is released under the Apache 2.0 License.

### NPM Installation

```
npm install cometd
```

### CommonJS Usage

```javascript
// Obtain the CometD APIs.
var lib = require('cometd');

// Create the CometD object.
var cometd = new lib.CometD();

// Optionally, obtain an extension and register it.
var TimeStampExtension = require('cometd/TimeStampExtension');
cometd.registerExtension('timestamp', new TimeStampExtension());

// Configure the CometD object.
cometd.configure({
    url: 'http://host/cometd'
});

// Handshake with the server.
cometd.handshake(function(h) {
    if (h.successful) {
        // Subscribe to receive messages from the server.
        cometd.subscribe('/topic', function(m) {
            var dataFromServer = m.data;
            // Use dataFromServer.
        });
    }
});
```

### Bower installation

```javascript
bower install cometd
```

### AMD Usage

```javascript
require({
    paths: {
      'cometd': 'bower_components/cometd'
    }
}, ['cometd/cometd', 'cometd/TimeStampExtension'], function(lib, TimeStampExtension) {
    var cometd = new lib.CometD();
  
    // Optionally, install an extension.
    cometd.registerExtension('timestamp', new TimeStampExtension());
    
    // Configure the CometD object.
    cometd.configure({
        url: 'http://host/cometd'
    });
    
    // Handshake with the server.
    cometd.handshake(function(h) {
        if (h.successful) {
            // Subscribe to receive messages from the server.
            cometd.subscribe('/topic', function(m) {
                var dataFromServer = m.data;
                // Use dataFromServer.
            });
        }
    });
});
```
