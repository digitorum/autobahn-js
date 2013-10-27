# AutobahnJS

AutobahnJS is a JavaScript client library that implements **[The WebSocket Application Messaging Protocol](http://wamp.ws/)**:

 * implements WAMP v1, works with any WAMP server
 * provides **asynchronous RPC** and **PubSub messaging patterns**
 * easy to use Promise-based API
 * pluggable promises/deferreds: use [when.js](https://github.com/cujojs/when) (bundled), jQuery, Dojo or others
 * flexible, automatic reconnect
 * session authentication (WAMP-CRA)
 * no dependencies
 * works with AMD/CommonJS module loaders
 * tiny size (111kB source, 30kB minified, 10kB compressed)
 * open-source (MIT License)


## Get it

You can get the latest prebuilt AutobahnJS release from here:

  1. [Production (minimized and gzipped)](http://autobahn.s3.amazonaws.com/js/autobahn.min.jgz)
  2. [Production (only minimized)](http://autobahn.s3.amazonaws.com/js/autobahn.min.js)
  3. [Development](http://autobahn.s3.amazonaws.com/js/autobahn.js)

> Note: You can use those via direct linking for *development purposes*, but please do not hotlink for production. It won't work anyway, since we restrictions on HTTP referer.

## What is that?

[WebSocket](http://tools.ietf.org/html/rfc6455) is already built into
modern browsers and provides bidirectional low-latency messaging.

However, as such, it is quite low-level. Web apps often have a need for
higher level messaging patterns:

  * Publish & Subscribe
  * Remote Procedure Calls

This is where [WAMP](http://wamp.ws/) enters. WAMP runs on top of raw WebSocket and provides *asynchronous RPC and PubSub*.

Technically, WAMP is a proper WebSocket *subprotocol* that uses JSON as
message serialization format. WAMP was designed to be easy to use and
simple to implement.

AutobahnJS implements WAMP in JavaScript to be used in browser based applications.


## Where to go

For more information, including getting started, tutorials and reference documentation, please visit the project's [homepage](http://autobahn.ws/js).


## Get in touch

Get in touch on IRC `#autobahn` on `chat.freenode.net` or the [mailing list](http://groups.google.com/group/autobahnws).


## Acknowledgements

AutobahnJS includes code from the following open-source projects

  * [when.js](https://github.com/cujojs/when)
  * [CryptoJS](http://code.google.com/p/crypto-js/)

Special thanks to the [Coders with an Unhealthy Javascript Obsession](http://cujojs.com/) for creating *when.js - A lightweight Promise and when() implementation, plus other async goodies.*


# Building

To build, you will need

  * [SCons](http://www.scons.org/)
  * [Google Closure Compiler](http://closure-compiler.googlecode.com/files/compiler-latest.zip)
  * [Taschenmesser](https://github.com/oberstet/taschenmesser)

SCons is a Python based build tool, so you will need [Python](http://python.org/) as well. Taschenmesser is an SCons toolbelt also written in Python.

Set environment variables:

  1. JAVA_HOME pointing to your Java run-time, e.g.
   
  		C:\Program Files\Java\jre7

  2. adding Python & Python scripts to PATH, e.g.  		
		
 		C:\Python27;C:\Python27\Scripts;

  3. JS_COMPILER pointing to the Google Closure compiler.jar
  
		C:\Program Files\Google Closure\compiler.jar

Now clone the repo:

	git clone git://github.com/tavendo/AutobahnJS.git
	cd AutobahnJS

You need to get any Git submodules:

	git submodule init
	git submodule update 

Updating CryptoJS needs to be done manually, since they are not on Git.

For  a release version, set the appropriate AutobahnJS version in `version.txt`.

Then start the build:

	scons

This will produce 3 files inside the `build` directory:

    build/autobahn.js
    build/autobahn.min.js
    build/autobahn.min.jgz

To clean up your build:

	scons -uc
