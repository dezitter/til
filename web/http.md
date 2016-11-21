# What is the maximum number of connections a browser can make ?

Theoretically, a limit of two connections per hostname is suggested by **HTTP/1.1**.

See [HTTP/1.1 - RFC 2616](https://www.ietf.org/rfc/rfc2616.txt), section 8.1.4
"Connections - Practical consideration"

> A single-user client SHOULD NOT maintain more than 2 connections with any server or proxy.

Generally speaking, browsers open between 6 and 8 connections per server.

For example:

* IE8 uses 6 connections
* Firefox 3 uses 6 connections

It is also possible to reconfigure the browser to use different limits.

See also [browserscope](http://www.browserscope.org/?category=network) or
Steve Souders' [Roundup on Parallel Connections](http://www.stevesouders.com/blog/2008/03/20/roundup-on-parallel-connections/).

# What is HTTP Basic Authentication

A method for a user agent to provide a login/password.
Uses the `Authorization` field in the HTTP *header* in each requests.

Does not require cookies, sessions or login.
Typically the browser caches the credentials to avoid asking them to the user
on each requests.

The credentials "login:password" are encoded in Base64.

See [wikipedia](https://en.wikipedia.org/wiki/Basic_access_authentication)
