# Today I Learned - NodeJS

## npm run && PATH

When you execute a script declared in your *package.json*:

    {
        "scripts": {
            "build": "gulp compile"
        }
    }

    $ npm run build

npm will set the './node_modules/.bin' directory into your PATH.
In this particular example there would be no need to install *gulp* globally.

See [docs.npmjs.com/misc/scripts#path](https://docs.npmjs.com/misc/scripts#path)

## Testing POST requests using expressjs body-parser

The `content-type` parsed by the json [expressjs/body-parser](https://github.com/expressjs/body-parser)
defaults to *application/json*.

If you test using the **cURL** tool:

    curl -X POST --data "{...}" localhost:8000/post

you'll need the set the proper `content-type` header to let expressjs's body-parser.json()
properly intercept the payload.

    curl -X POST -H "Content-Type: application/json" --data "{...}" localhost:8000/post

See *type* option in [bodyParse.json() doc](https://github.com/expressjs/body-parser/#bodyparserjsonoptions)

    > Defaults to application/json.

See [cURL POST tutorial](http://curl.haxx.se/docs/httpscripting.html#POST)

    > This kind of POST will use the Content-Type application/x-www-form-urlencoded
      and is the most widely used POST kind.

## Browserify and shimmed modules

Since purpose of Browserify is to provide a bundle for a browser, some Node's specifics modules are replaced by
a shimmed version of them to provide more compatibility between client & server code (case of an Isomorphic
application).

More details at [Browserify compatibility documentation](https://github.com/substack/node-browserify#compatibility).
