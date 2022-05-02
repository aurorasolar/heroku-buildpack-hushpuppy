# Heroku buildpack: hushpuppy

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) that allows one to install 
[hushpuppy](https://www.notion.so/aurorasolar/HushPuppy-912cbebe65bc485ba019305cff012b41) in a dyno alongside application code.  It is meant to be 
[used in conjunction with other buildpacks](https://devcenter.heroku.com/articles/using-multiple-buildpacks-for-an-app).

Documentation on how to [build a custom buildpack](https://devcenter.heroku.com/articles/buildpack-api)

# Description

This script download the HushPuppy's install into the vendor directory, then execute the script to install `hp` under 
`/bin` for the application to use.

## Usage

Adding the buildpack:

    heroku buildpacks:add --index 3 https://github.com/aurorasolar/heroku-buildpack-hushpuppy.git -a aurorasolar-ENV
    Buildpack added. Next release on aurorasolar-ENV will use:
      1. heroku-community/apt
      2. https://github.com/DataDog/heroku-buildpack-datadog.git#1.20
      3. https://github.com/aurorasolar/heroku-buildpack-hushpuppy.git
      4. heroku/metrics
      5. heroku/ruby
    Run `git push heroku main` to create a new release using these buildpacks.    

Installation output:
    
    $ git push heroku main
    ...
    remote: -----> Building on the Heroku-XX stack
    remote: -----> Using buildpacks:
    remote:        1. https://github.com/aurorasolar/heroku-buildpack-hushpuppy.git
    remote:        2. heroku/ruby
    remote: -----> hushpuppy app detected
    remote: Downloading https://github.com/aurorasolar/hushpuppy/releases/download/0.5.0/hp-0.5.0.linux-amd64.tar.gz
    remote: https://github.com/aurorasolar/hushpuppy/releases/download/0.5.0/hp-0.5.0.linux-arm64.tar.gz...
    remote: HushPuppy CLI v0.5.0 installed as /tmp/build_fa2fe968/bin/hp
    remote: -----> hushpuppy-buildpack: done
    remote: -----> Ruby app detected
    ...
