# Today I Learned ES

## ES6 and strict mode

ES6 modules are implicitly in strict mode.

See the [spec](http://www.ecma-international.org/ecma-262/6.0/#sec-strict-mode-code)

    10.2.1 Strict Mode Code

        * Module code is always strict mode code.

## Promises can "swallow" errors

If an error is thrown during the promise constructor or in one of the `.then`
callbacks *(onFulfilled/onRejected)*, the error is automatically caught and the
promise rejected.

This is a good thing, however it can be perturbing when debugging. If no *onRejected*
callback is attached the error will be "swallowed" and the failure silent.

For example:

    const promise = new Promise(function() {
        throw new Error('boom');
    });

    // 'promise' is rejected, no 'onRejected' callback is attached so the failure is silent

Similarly:

    const promise = new Promise(function(resolve, reject) {
        resolve(42);
    });

    const promise2 = promise.then(function(value) {
        throw new Error('boom');
    });

    // 'promise2' is now rejected, no onRejected callback so the failure is silent

The [RSVP](https://github.com/tildeio/rsvp.js) library helps solving this problem
by proposing an [error handler](https://github.com/tildeio/rsvp.js#error-handling)

    RSVP.on('error', function(error) { // ... });

See [JavaScript Promises - html5rocks](www.html5rocks.com/en/tutorials/es6/promises/)

> Rejections happen [...] implicitly if an error is thrown in the constructor callback.

> [...] errors are automatically caught and become rejections.

> The same goes for errors thrown in "then" callbacks.

See [section 7. ii - Promises/A+ spec](https://github.com/promises-aplus/promises-spec)

> If either onFulfilled or onRejected throws an exception e, promise2 must be rejected
  with e as the reason.

See also an interesting discussion on the [v8 repository](https://code.google.com/p/v8/issues/detail?id=3093) about this issue.
