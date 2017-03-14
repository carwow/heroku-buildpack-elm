# Heroku buildpack for Elm apps

This is a fork of srid/heroku-buildpack-elm which doesn't try to build your Elm app, just downloads
and installs the Elm Platform.

- Add the elm buildpack: `heroku buildpacks:add https://github.com/carwow/heroku-buildpack-elm`
- Deploy!
  - e.g. `git commit -am "empty" && git push heroku master && heroku ps:scale web=1`

## HACKING

### Generating and uploading binaries

Binaries are generated using docker, and uploaded to s3.

```
# To generate docker image containing the binaries
make binaries

# To upload to s3
aws configure  # creates ~/.aws/...
make upload
```

### Upgrading to newer Elm version

* Modify the `ELM_VERSION` env var in Dockerfile
* `make binaries upload`
* Modify the `ELM_VERSION` env var in `bin/compile`
* Update CHANGELOG.md
* git push

## Questions?

Feel free to ask in Github Issues.
