# Today I Learned Bundler

## Bundler.require

Putting the following snippet in your app:

    require 'rubygems'
    require 'bundler/setup'
    Bundler.require

will properly setup the $LOAD_PATH and require all gems from your Gemfile.
It is equivalent to manually loading them:

    require 'sinatra'
    require 'nokogiri'
    # ...

See [bundler.io](http://bundler.io/v1.10/bundler_setup.html)

## In your Gemfile, the order might matter

The [mustache-sinatra](https://github.com/mustache/mustache-sinatra) gem depends
on [sinatra](http://www.sinatrarb.com/), **but does not require it**.

When using `Bundler.require` (see above), if the Gemfile specifies:

    gem 'mustache-sinatra'
    gem 'sinatra'

Bundler will load `mustache-sinatra` **before** `sinatra` and fail with error:

    Uninitialized constant Sinatra

See [Ruby Require Order Problems by yehudakatz](http://yehudakatz.com/2010/04/17/ruby-require-order-problems/)

See also [bundler "Order" spec suite](https://github.com/bundler/bundler/blob/v1.10.6/spec/runtime/require_spec.rb#L230):

The suite makes use of two gems:

* `one.rb` uses **but not require** the gem `two.rb`
* `two.rb` which is standalone

    # Gemfile
    gem 'one'
    gem 'two'

works, see [l.255](https://github.com/bundler/bundler/blob/v1.10.6/spec/runtime/require_spec.rb#L255)

    # Gemfile
    gem 'two'
    gem 'one'

fails, see [l.295](https://github.com/bundler/bundler/blob/v1.10.6/spec/runtime/require_spec.rb#L295)
