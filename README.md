# heroku-buildpack-nodejs-npm-task

Run an arbitrary npm task on deploy to Heroku. 

This buildpack is intended for use after the regular [nodejs-buildpack]. 

_It will probably work with any other buildpack that installs nodejs + npm too_

# Usage

Assuming you are already using the default (or another nodejs installing) buildpack, append the heroku-buildpack-nodejs-npm-task to your buildpack list:

```
heroku buildpacks:add https://github.com/sandfox/heroku-buildpack-nodejs-npm-task
```

configure `HEROKU_NPM_DEPLOY_TASK` environment variable with the task you want to run:

```
heroku config:set HEROKU_NPM_DEPLOY_TASK='build-assets'
```

this would result with the command `npm run build-assets` being executed

# License

MIT, see the LICENSE file.

[nodejs-buildpack]:https://github.com/heroku/heroku-buildpack-nodejs