# heroku-buildpack-nodejs-npm-task

Run an arbitrary npm task on deploy to Heroku. 

This buildpack is intended for use after the regular [nodejs-buildpack], because composition is great and building one off "batteries-included" buildpacks that are forks of the offical nodejs buildpack is bad for many many reasons. 

_It will probably also work with any other buildpack that installs nodejs + npm too_

## Usage

Assuming you are already using the default (or another nodejs installing) buildpack, append the heroku-buildpack-nodejs-npm-task to your buildpack list:

```
heroku buildpacks:add https://github.com/sandfox/heroku-buildpack-nodejs-npm-task
```

configure `HEROKU_NPM_DEPLOY_TASK` environment variable with the task you want to run:

```
heroku config:set HEROKU_NPM_DEPLOY_TASK='build-assets'
```

this would result with the command `npm run build-assets` being executed

## Questions etc

> Why would I use it?

It's great for running build tasks and asset compilation that needs doing before running in production. Think architecture/platform specific stuff and images/css/blah

> Why not just do that as part of npm install

It's not the worst solution, but it's clunky and you probably don't want to tie dependency installation to asset compilation/etc.

> Why not just add those assets to git / source control

While tracking build artifacts with version control software is great, it's best if that is tracked in another repo to the original source code. _[insert list of millions reason why here one day]_, my simplest answer is keeping your repository noise free and small.

# License

MIT, see the LICENSE file.

[nodejs-buildpack]:https://github.com/heroku/heroku-buildpack-nodejs