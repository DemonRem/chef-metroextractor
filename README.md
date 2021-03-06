Metroextractor Chef
===================
[![CircleCI Build Status](https://circleci.com/gh/mapzen/chef-metroextractor.svg?style=svg)](https://circleci.com/gh/mapzen/chef-metroextractor)

Attribution
-----------
Heavily influenced by Mike Migurski's [Extractotron](https://github.com/migurski/Extractotron/)

What does it do?
----------------
Downloads the latest planet in pbf format.
Produces, via osmconvert or vex, a number of metro extracts in both pbf and bz2 formats.
Produces shape files in both imposm and osm2pgsql formats.

Projections
-----------
GeoJSON is generated via ogr2ogr and output in CRS:84 (e.g. EPSG:4326) projection.

Imposm shapfiles are generated in EPSG:4326.

What hardware do I need?
------------------------
This depends on a few factors:
  - what backend processing system for extracts do you want to use? We support vex and osmconvert.
  - if you're using vex, do you have enough memory to store the planet in RAM?
  - if osmconvert, how many cores do you have and how fast are they?

The short version is that this could take anywhere from a few hours to days depending on setup and hardware .

If you'd rather not go that route, you're in luck. We'll be producing extracts weekly, and you can find
them here: [Mapzen Metro Extracts](https://mapzen.com/metro-extracts/)

Contributing
------------
Extract creation is driven off the cities.json file found here: [metroextractor-cities](https://mapzen.com/data/metro-extracts/cities-extractor.json)

The extract list is more or less frozen at the ~200 found there. If you need a custom extract, please check out our [On Demand Extracts](TODO) system!

If you'd like to update any other code, please fork, update, write specs for your changes and submit a pull.

Usage
-----
    include_recipe 'metroextractor'

Supported Platforms
-------------------
Tested and supported on the following platforms:

* Ubuntu 14.04LTS

Requirements
------------
* Chef >= 11.4

Attributes
----------
* see [attributes/default.rb](https://github.com/mapzen/chef-metroextractor/blob/master/attributes/default.rb)

Dependencies
-----------
apt, ark, osm2pgsql, postgresql, python, user

License and Authors
-------------------
License: GPL
Authors: grant@mapzen.com
