# Searchable Map Template - Heroku Ready

This is a basic site template that I use to kick off a lot of my map projects. Uses Fusion Tables, Ruby, Sinatra, Haml and Twitter Bootstrap with tie-ins to Heroku for hosting and Google Analytics.

For help setting up your Fusion Table for use with this template, see the [original Searchable Map Template Readme](https://github.com/derekeder/FusionTable-Map-Template/blob/master/README.md)

### [See the working demo](http://searchable-map-template.herokuapp.com) 

## Installation

```bash
  git clone git@github.com:derekeder/site-template.git
  cd site_template
  gem install bundler
  bundle
  unicorn
  navigate to http://localhost:8080/
```

## Deploy to Heroku
  
Heroku is a cloud hosting platform that can host small Ruby apps (among others) for free. Deploying is built on top of git, so it helps to be familiar with those commands. More info: https://devcenter.heroku.com/articles/git

```bash
  heroku create name-of-your-app
  # make sure all of your changes are committed
  git push heroku master
```

## Setup for fusion_tables gem

To access Fusion Tables in more advanced ways, you will need to setup the fusion_tables gem connection by providing a Google account and password.

```bash
  cp config/config.yml.example config/config.yml
  # set the Google account and password you want to use to access your Fusion Table
  unicorn
  # navigate to http://localhost:8080/location_list to see a demonstration
```

When you want to deploy to Heroku, you will need to set your account, password and [api key](https://code.google.com/apis/console/) as Heroku config variables. For more info, see https://devcenter.heroku.com/articles/config-vars

```bash
  heroku config:add google_account=youraccount
  heroku config:add google_password=yourpassword
  heroku config:add google_api_key=yourapikey
```

## Caching

This template comes with hooks in to Heroku's memcache plugin for caching pages. To set up memcache on heroku:

```bash
  heroku addons:add memcache
```

Then uncomment these lines in application.rb

```bash
  cache_control :public, max_age: 1800  # 30 min
```

### Flushing the cache

To clear the cache manually, just load `http://[your app]/flush_cache` in your browser. 

If you want to get fancy, you can also set up a Heroku HTTP deploy hook to clear the cache every time you push to Heroku. In the command line:

```bash
  heroku addons:add deployhooks:http --url=http://[your app]/flush_cache
```

## Dependencies

* [Fusion Tables](http://www.google.com/fusiontables/Home/)
* [fusion_tables gem](https://github.com/tokumine/fusion_tables)
* [Ruby 1.9.3](http://www.ruby-lang.org/en/downloads)
* [Sinatra](http://www.sinatrarb.com)
* [Haml](http://haml.info)
* [Heroku](http://www.heroku.com)
* [Twitter Bootstrap](http://twitter.github.com/bootstrap)
* [Google Analytics](http://www.google.com/analytics)


## Errors / Bugs

If something is not behaving intuitively, it is a bug, and should be reported.
Report it here: https://github.com/derekeder/FusionTable-Map-Template-Heroku/issues


## Note on Patches/Pull Requests
 
* Fork the project.
* Make your feature addition or bug fix.
* Commit and send me a pull request. Bonus points for topic branches.

## Copyright

Copyright (c) 2013 Derek Eder. Released under the MIT License.

See LICENSE for details https://github.com/derekeder/FusionTable-Map-Template-Heroku/wiki/License
