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
