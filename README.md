<img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/logo.png">

<h2> Part 1: Adding data to Studio </h2>

----------

### In this tutorial you will:

- [Create a style](https://www.mapbox.com/help/how-map-design-works/#how-map-styles-work) for a basemap for a dynamic, [interactive web map or app](https://www.mapbox.com/help/how-web-apps-work/)
- [Manage and edit layers](https://www.mapbox.com/studio-manual/reference/styles/#style-editor) in your style
- [Add data](https://www.mapbox.com/help/uploads/) to a style
- Make [beautiful custom styles](https://www.mapbox.com/designer-maps/)

----------

### Data

Note: The data was prepared for you to use. This lesson doesn’t go into data clean-up and geo-processing.


----------

**Resources to further your knowledge:**

🔗 [Our awesome glossary](https://docs.mapbox.com/help/glossary/) from our Doc Queens 👑

🔗 [Our Election Guide](https://blog.mapbox.com/visualizing-election-data-a-guide-to-mapbox-gl-expressions-92cc469b8dfd) covers a bunch of our core elements, like expressions and feature-state

🔗 [The Guide To Map Design](https://www.mapbox.com/map-design/) by [Amy Lee Walton](https://twitter.com/amyleew)

🔗 Convert GeoJSON to MBTiles using [tippecanoe](https://github.com/mapbox/tippecanoe)

----------

### Introduction to geodata 

Tilesets: 

A [tileset](https://www.mapbox.com/help/define-tileset) is a collection of raster or vector data broken up into a uniform grid of square tiles at up to 22 preset zoom levels. Tilesets are used in Mapbox libraries and SDKs as a core piece of making maps visible on mobile or in the browser; they are also the main mechanism we use for determining [map views](https://www.mapbox.com/help/define-map-view/).

Tilesets are made up of vector tiles and are developed for caching, scaling and serving map imagery rapidly.

Mapbox web and mobile-ready vector tiles are 75% smaller than a raster tilesets. This results in fast, smooth zooming from the worldview of a map down to street-level detail. Tilesets are highly cacheable and load quickly. Vector tiles are developed for caching, scaling and serving map imagery rapidly – to vector data.

As the name suggests, vector tiles contain vector data instead of the rendered image. They contain geometries and metadata – like road names, place names, house numbers – in a compact, structured format. Vector tiles are rendered only when requested by a client, like a web browser or a mobile app. Rendering happens either in the client.

----------

### Mapbox File types:

**CSV**


![](https://paper-attachments.dropbox.com/s_50EEDCA7947791B75F33CD388F18E96B2D817BF4D6A654F9CA53F7D29F431CBD_1552101439099_Cdb2Yk26asXjvd1a5qozUyhXW78FyAqh7LgwASVZljjIBhk-V9XgsFE2O1PXoQWVYMRXlq6ZT28IEjpk_nps97VUbcoUE8jOI9zJcwHQ_1WFgwVPWh7ZZyArl4yQbKSPoNZuCJ21MUw.png)


The **CSV** (comma-separated values) format is common for table data, like the kind you may use in Excel or other spreadsheets. CSV files aren’t necessarily mappable unless they contain geographic information (like latitude and longitude).

When uploading CSV files, keep the following in mind:


- Check out the [Mapbox Uploads API documentation](https://docs.mapbox.com/api/) for the current size limit for CSV files.
- CSV files must be in UTF-8 encoding.
- CSV files must contain coordinates (latitude and longitude) when uploading in Mapbox Studio or Mapbox Studio Classic.
- CSV files are for point data only.

----------

**GeoJSON**


![](https://paper-attachments.dropbox.com/s_50EEDCA7947791B75F33CD388F18E96B2D817BF4D6A654F9CA53F7D29F431CBD_1552101520402_0SVEgCPUYw-Iq-mhsUDcvmStyYOz4kTFVUYgAVMQ7T16k7IALQlrxYSBHsdSeJRVWsQEFTxxQusW5RGZGUvuVVdTgQcO6Go-2AAzWi94cE5b-aoCAXXjSQd9qggbjrsJgIIBg2QV_N4.gif)


[**GeoJSON**](http://geojson.org/) is a file format for map data served by Mapbox [web services and APIs.](https://docs.mapbox.com/api/) As a subset of the [JSON](https://www.json.org/) format, it can be parsed in modern software and native to the JavaScript language.
There are several open source tools for converting other geospatial data formats to GeoJSON. A few faves:


- [togeojson](https://www.npmjs.org/package/togeojson), a node package for converting KML and GPX (XML formats).
- [ogr2ogr](http://www.gdal.org/ogr2ogr.html), the ultimate 40-in-1 vector data conversion tool.
- [geojson.io](http://geojson.io) for creating, converting, and editing GeoJSON.

----------

**MBTiles**

![](https://paper-attachments.dropbox.com/s_50EEDCA7947791B75F33CD388F18E96B2D817BF4D6A654F9CA53F7D29F431CBD_1552101614814_uKV9VZgC77uTUC697Aek2rOP_BkWUxB9hDFQbS-jizVvqxX0GFpUsUH_5Es0J2eOf-PpgZ9xTccEctDOFw1PWmB-7tKsRBlRvSwa_6r6Idd_YQRn172uxRP2_FedOHFPReyAOXBuhqM.png)


**MBTiles** is a file format for storing [tilesets](https://www.mapbox.com/help/define-tileset). It’s designed so that you can package the potentially thousands of files that make up a tileset and move them around, eventually uploading to Mapbox or using in a web or mobile application. [MBTiles is an open specification](https://github.com/mapbox/mbtiles-spec) and is based on the [SQLite](https://sqlite.org/) database. MBTiles can contain raster or vector tilesets.

----------

**KML**

![](https://paper-attachments.dropbox.com/s_50EEDCA7947791B75F33CD388F18E96B2D817BF4D6A654F9CA53F7D29F431CBD_1552101717660_JHkQUFnA_E4SoLBPpRmx6EXrdnvoGxi9cL4ggnV60HT38fvqTZ6MaCrz6XREULxPv5H6X_au2uGUjnCnR8iz38olTJmKjBmDQ5RQgSGisZm0lG5xjfzZfVau4wxsr42kLVRkxepf37o.png)

[**KML**](https://developers.google.com/kml/documentation/kmlreference) is a file format that is like [GeoJSON](https://www.mapbox.com/help/define-geojson/), but used more commonly in Google products. Like GeoJSON, it can store points, lines, polygons, and other vector data. Unlike GeoJSON, it’s based on [XML](https://en.wikipedia.org/wiki/XML), rather than [JSON](http://www.json.org/). When uploading KML, please note that Mapbox does not support any KML extensions.

----------

**GPX**


![](https://paper-attachments.dropbox.com/s_50EEDCA7947791B75F33CD388F18E96B2D817BF4D6A654F9CA53F7D29F431CBD_1552101729059_sYeff4-sRnxPY6oiQu5RWpKqOktIVkab-gZlqcdtQQr1p1jIfA8o0nt3syQtU4blRZwM3Q1X8tbBfd90-XLfGwsNlvjXwEgKQ_MkT9tpKUzwz0XoaiKNhbWd5INmcqelMh0ODO4_h6E.png)


[**GPX**](http://en.wikipedia.org/wiki/GPS_eXchange_Format), or GPS eXchange format, is a data format commonly created from GPS receivers.
You can upload GPX files to your Mapbox account to use in a custom map style. Please note that Mapbox does not support values along lines (for example, elevation and time at various points along a jogging route). A GPX file with values along a line can be uploaded, but Mapbox will ignore any data along the line.

----------

**Shapefile**

![](https://paper-attachments.dropbox.com/s_50EEDCA7947791B75F33CD388F18E96B2D817BF4D6A654F9CA53F7D29F431CBD_1552101803249_Screen+Shot+2019-03-08+at+7.23.13+PM.png)


A **shapefile**, also known as an [ESRI shapefile](https://en.wikipedia.org/wiki/Shapefile), is a file format for storing geographic vector data.
When uploading shapefiles, keep the following in mind:


- Check out the Mapbox Uploads API documentation for the current size limit for shapefiles. Note that this limit applies to the shapefile’s uncompressed size, not the size of the compressed zip.
- Shapefiles are composed of several individual files, which should be combined into a single zip file before uploading. Of these files, Mapbox can read shp, shx, dbf, prj, and index files. Any other files you upload with your zip file will be ignored.

----------

**TIFF**

![](https://paper-attachments.dropbox.com/s_50EEDCA7947791B75F33CD388F18E96B2D817BF4D6A654F9CA53F7D29F431CBD_1552101864821_download.png)


A **TIFF**, or sometimes TIF, is a file format for saving raster images. With Mapbox, a TIFF is often a GeoTIFF, meaning the file is embedded with georeferencing information.

You can upload TIFF files as [tilesets](https://www.mapbox.com/help/define-tileset) in Mapbox Studio and use them in the Mapbox Studio style editor. When uploading a TIFF file, keep in mind the [current size limit for TIFF files](https://www.mapbox.com/help/upload-troubleshooting).

----------


### 🔺 Geometry types
- Points
- Line strings
- Polygons/multi-polygons
- Multi-part collections

----------

### The Mapbox Ecosystem

**Dataset**: Edit your data 📝

**Tileset**: Bake your data into Vector tiles or upload rasters 🗾

**Styles**: Customize your style in the Studio interface — You can also style your data here 🎨

**Libraries**: Add your style to applications using one of our Mapbox libraries — You can also style your data here *👩‍💻*  (GL JS, IOS SDK…)


