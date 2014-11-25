sails-resource
==============

[Sails.js](http://sailsjs.org) is a realtime MVC framework for NodeJS. This module was inspired by
[Angular ngResource](https://github.com/angular/angular.js/blob/master/src/ngResource/resource.js),
[AngularSails](https://github.com/balderdashy/angularSails)
and little bit by [angular-resource-sails](https://github.com/angular-resource-sails/angular-resource-sails)


Install
==============

Add 'angularSails', 'EventEmitter' and 'sails-resource' to your bower.json file. The include them to your pages. E.g

```
<script src="/bower_components/eventEmitter/EventEmitter.js"></script>
<script src="/bower_components/sails.io.js/dist/sails.io.js"></script>
<script src="/bower_components/angularSails/dist/ngsails.io.js"></script>
<script src="/bower_components/sails-resource/src/sailsResource.js"></script>
```

Then include 'sailsResource' to your application:

```
angular.module('myApp', ['sailsResource']);
```

Usage
==============

```
angular.module('myApp').factory('User', function($sailsResource) {
  // First argument is model name used for socket events
  // Next arguments are similar to the ngResource
  return $sailsResource('user', "/api/v1/users/:id", { id: '@id' })
})
```

Why is EventEmitter included?
==============

All resources can listen for ```updated``` and ```reloaded``` events.

```
var user = User.findOne(id);
user.$on('updated', function() {
    // User was updated by socket
    // so we can e.g. notify user
})
```
