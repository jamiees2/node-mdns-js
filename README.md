mDNS-js
==========

Pure JavaScript/NodeJS mDNS discovery implementation.

A lot of the functionality is copied from 
https://github.com/GoogleChrome/chrome-app-samples/tree/master/mdns-browser
but adapted for node.

Install by

    npm install mdns-js


Future
------
It would be great to have a full implementation of mDSN + DNS-SD in pure JS but
progress will be slow unless someone is willing to pitch in with
pull requests, specifications for wanted functions etc.



example
-------

```javascript
var Mdns = require('mdns-js');

var mdns = new Mdns();

mdns.on('ready', function () {
    mdns.discover(); 
});

mdns.on('update', function () {
    console.log('ips with _workstation._tcp service', mdns.ips('_workstation._tcp')); 
    console.log('services on host 10.100.0.61', mdns.services('10.100.0.61'));
});
```



Debugging
---------
This library is using the [debug](https://github.com/visionmedia/debug) module from TJ Holowaychuk and can be used like this.

```bash
DEBUG=mdns* node examples/simple.js
```

This will spit out a lot of information that might be useful.



License
=======
Apache 2.0. See LICENSE file.



References
==========

* https://github.com/GoogleChrome/chrome-app-samples/tree/master/mdns-browser
* http://en.wikipedia.org/wiki/Multicast_DNS
* http://en.wikipedia.org/wiki/Zero_configuration_networking#Service_discovery
* RFC 6762 - mDNS - http://tools.ietf.org/html/rfc6762
* RFC 6763 - DNS Based Service Discovery - http://tools.ietf.org/html/rfc6763
