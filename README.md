### ATTENTION. Bolstr: This has the GDAL stuff removed, as we didn't need it and it was taking up too much room in our Heroku Slug (pushing us over 300mb limit).
###  We forked this from https://github.com/cyberdelia/heroku-geo-buildpack but still ran into problems, so we took the same approach that https://github.com/MattFenelon/heroku-buildpack-ruby-poppler does and build from source/cache for future builds via the buildpack process.

Heroku buildpack: geo
=====================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpacks) that
vendors main geo/gis libraries like geos, proj and gdal.

You will use this buildpack with other major buildpack such as Ruby buildpack.

Usage
-----

Example usage:

```
$ heroku buildpacks:set https://github.com/bolstr/heroku-geo-buildpack.git
$ heroku buildpacks:add heroku/ruby
```

Run `heroku buildpacks` to make sure that `heroku-geo-buildpack` is added before
the language buildpacks.

```
$ heroku buildpacks
=== sushi Buildpack URLs
1. https://github.com/bolstr/heroku-geo-buildpack.git
2. heroku/ruby
```

Testing
-------

For rgeo:

```ruby
>>> require 'rgeo'
>>> RGeo::CoordSys::Proj4.supported?
=> true
>>> RGeo::Geos.supported?
=> true
```
