# Colorado 14ers I have climbed

Contains tracks from 2013 and 2014.

# How to convert GPX tracks from Garmin Connect to geojson
## Export gpx file from Garmin Connect
1. Pull up the activity page for the activity you are interested in.  For example:

        https://connect.garmin.com/modern/activity/123456789

2. Find the gear icon in the upper right.  Then, select "Export to GPX".

## Install togeojson
1. Install **[togeojson](https://github.com/tmcw/togeojson)** node module:

        npm install -g togeojson

2. Go to directory of GPX file and run the following command line:

        togeojson file.gpx > file.geojson

*Note:*  I noticed that there seemed to be quite a few points in the .gpx files with a latitude and longitude of 0,0.  This puts you in the Atlantic Ocean off the coast of Africa!  (Wonder if this is a bug in the Garmin firmware?  Time and elevation looked correct.)

I just stripped these out with one line of perl.  For example:

        cat Mount_Sherman.gpx | perl -ne 'print unless /\<trkpt lat=\"0\" lon=\"0\"\>/ .. /\<\/trkpt\>/' > Mount_Sherman.gpx.tmp

# GitHub reference
Mapping geoJSON files on GitHub:

        https://help.github.com/articles/mapping-geojson-files-on-github/
