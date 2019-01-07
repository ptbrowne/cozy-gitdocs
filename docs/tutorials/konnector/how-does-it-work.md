## How does it work?

A connector is a NodeJS script.
The target node version used to run your connector is the [current LTS version](https://github.com/nodejs/Release#release-schedule) (8 at the time this doc was written).

Like client side apps, connectors communicate with the [Cozy Stack] using its HTTP API, and get a unique auth token every time they start.
They need to register with a manifest, and ask the user for permissions.

To facilitate connector development, a npm package, [cozy-konnector-libs], provides some shared libraries that are adapted to be used for a connector:

 - [cheerio](https://cheerio.js.org) to easily query a HTML page
 - [request-promise](https://github.com/request/request-promise): [request](https://github.com/request/request) with Promise support
 - [request-debug](https://github.com/request/request-debug) that displays all the requests and responses in the standard output.
   Toggle _debug_ option in [requestFactory options](https://github.com/konnectors/libs/blob/master/packages/cozy-konnector-libs/docs/api.md#module_requestFactory)

Besides, you'll probably need some other npm packages to help you run your connector:

 - [momentjs](http://momentjs.com/docs/) or [date-fns](https://date-fns.org) to manage dates
 - [bluebird](http://bluebirdjs.com) to get enhanced promises

When the connector is started, it also receives some data via environment variables:

 - `COZY_CREDENTIALS`: an auth token used by [cozy-client-js] to communicate with the server
 - `COZY_URL`: the Cozy Stack API entry point
 - `COZY_FIELDS`: settings coming from [Cozy Collect] and filled by the user (login, password, directory path).

These variables are used by the connector and the cozy-client to configure the connection to the [Cozy Stack] with the right permissions as defined in the connector manifest.
They are simulated in standalone mode so that you do not need a real Cozy Stack to develop a connector.
[[More about BaseKonnector](https://github.com/cozy/cozy-konnector-libs/blob/master/packages/cozy-konnector-libs/docs/api.md#basekonnector)]

From the server point of view, each connector is a `job` which is executed periodically via a `trigger`.
[[More about Cozy Stack jobs](https://cozy.github.io/cozy-stack/jobs.html)]
