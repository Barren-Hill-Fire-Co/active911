Active911 for Node.js
=====================

[![Build Status](https://travis-ci.org/benburwell/active911.svg)](https://travis-ci.org/benburwell/active911)
[![npm version](https://badge.fury.io/js/active911.svg)](https://badge.fury.io/js/active911)

by Ben Burwell <ben@benburwell.com>

Installation
------------

Installation is simple: `npm install --save @barrenhill/active911`.

Basic Usage
-----------

```javascript
var Active911 = require('active911');
var client = new Active911.RefreshClient('YOUR REFRESH TOKEN');

client.getAgency().then(function(agency) {
  console.log(agency.name);
}).catch(function(err) {
  console.log('Problem getting Agency details:', err);
});
```

API Methods
-----------

The following public API methods are available:

* `getAgency()`
* `getDevice(device_id)`
* `getAlerts({ alert_days: 1, alert_minutes: 30 })`, where the object parameter
  is optional. You should not use both keys; if `alert_minutes` is provided, it
  will override `alert_days` as documented [on the wiki](http://wiki.active911.com/wiki/index.php/Accessing_the_API#Alerts).
* `getDeviceAlerts(device_id)`
* `getAlert(alert_id)`
* `getLocations()`
* `getLocation(location_id)`
* `getResource(resource_id)`

Each method returns a promise for a result, which will resolve as either an
object or an array, depending on the cardinality (e.g. `getAlerts` resolves as
an array, while `getAlert` resolves as an object).

For details on the format of the result, please see the [Active911 API
wiki](https://active911.atlassian.net/wiki/spaces/AED/pages/1866825767/Accessing+the+API).

Contributing
------------

Contributions are encouraged. For a list of open issues, see
<https://github.com/Barren-Hill-Fire-Co/active911/issues>.

More Information
----------------

More information about the API is available on [the Active911
wiki](https://active911.atlassian.net/wiki/spaces/AED/pages/240123959/Advanced+Features#Active911-Developer-API).

