What.CD
=======

Simple, idiomatic access to the API features of [What.CD](https://what.cd/).

Overview
--------

What.CD provides a JSON API to registered users. This library aims to maintain
coverage of all features within a reasonable timeframe and provide an easy to
use and obvious surface.

This should also work on other Gazelle-based websites, but will be tested with
what.cd only.

Installation
------------

    npm install whatcd

OR

    git clone git://github.com/deoxxa/whatcd.git

Example
-------

```javascript
var WhatCD = require("whatcd");

var client = new WhatCD("https://what.cd", "username", "password");

client.index(function(err, data) {
  if (err) {
    return console.log(err);
  }

  console.log(data);
});
```

Usage
-----

```javascript
client.METHOD([PARAMETERS,] function(err, data) {
  ...
});
```

**METHOD** is one of the methods below and **PARAMETERS** is an object that maps
directly to URL parameters in the request to the website. For more information,
see [this article](https://what.cd/wiki.php?action=article&name=api). You will
need to be logged in to view it.

There's also an `api_request` method that automatically handles login and such,
and is in fact what all the rest of these methods are built upon. You can use it
to make arbitrary requests to the website while ensuring that the correct steps
have been taken to ensure that you're authenticated.

```javascript
client.api_request(PARAMETERS, function(err, data) {
  ...
});
```

**PARAMETERS** is the same as before, where each property maps to a query string
parameter. To request the index, for example, you would do this:

```javascript
client.api_request({action: "index"}, function(err, data) {
  ...
});
```

This is exactly how all the methods listed below operate under the hood.

Available Methods
-----------------

* artist
* bookmarks
* browse
* forum_main
* forum_viewforum
* forum_viewthread
* inbox
* inbox_conversation
* index
* notifications
* request
* requestsearch
* rippy
* subscriptions
* top10
* top10_tags
* top10_torrents
* top10_users
* torrentgroup
* user
* usersearch

License
-------

3-clause BSD. A copy is included with the source.

Contact
-------

* GitHub ([deoxxa](http://github.com/deoxxa))
* Twitter ([@deoxxa](http://twitter.com/deoxxa))
* Email ([deoxxa@fknsrs.biz](mailto:deoxxa@fknsrs.biz))
