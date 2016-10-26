## The CometD Project

Welcome to the [CometD](https://cometd.org) Project, a scalable comet 
(server push) and websocket messaging library for the web.

This repository mirrors the JavaScript sources hosted at the [main
CometD repository](https://github.com/cometd/cometd).
Those JavaScript sources are not suitable to be consumed with NPM,
and are therefore re-arranged in this repository for to make it simpler
to use CometD with NPM.

### License

The CometD source code is released under the Apache 2.0 License.

### Installation

```
npm install cometd
```

### Usage

```javascript
var lib = require('cometd');
var cometd = new lib.CometD();
cometd.configure({
    url: 'http://host/cometd'
});

// Handshake with the server.
cometd.handshake(function(h) {
    if (h.successful) {
        // Subscribe to receive messages from the server.
        cometd.subscribe('/topic', function(m) {
            var dataFromServer = message.data;
            // Use dataFromServer.
        });
    }
});
```
