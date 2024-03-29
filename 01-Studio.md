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

- [Healthcare Facilities](https://github.com/mjdanielson/WFP/blob/master/Data/Healthcare_Facilities.geojson)
- [Kindergarten school locations](https://github.com/mjdanielson/WFP/blob/master/Data/Kindergarten.geojson)
- [Healthcare Facility Icon](https://github.com/mjdanielson/WFP/blob/master/image/Hospital-2.svg)


----------

**Resources to further your knowledge:**

🔗 [Glossary](https://docs.mapbox.com/help/glossary/) 

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

----------

### Uploading data to Studio

To add the data to a style in Mapbox Studio, you need to upload it to your account. Go to your [**Tilesets**](https://www.mapbox.com/studio/tilesets) [page](https://www.mapbox.com/studio/tilesets) in Mapbox Studio to upload your data.

On your Tilesets page, click the **New tileset** button. Select the geojson file containing your kindergarten data and upload it to your account. 

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/tilesets.png">
  </p>

Try uploading the **healthcare facilities** dataset. 

----------

### Inspect your tileset 

When the upload is complete, click on the arrow next to the filename to open its information page.

When you upload vector data to your Mapbox account, our servers convert it to a vector tileset so it can be rendered quickly and efficiently in the Mapbox Studio style editor and with Mapbox GL JS. The tileset information page shows some useful information about the tileset that was created from your uploaded data.

<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/tilesets.png">
  </p>
  
 
----------

### Create a new style

After you've uploaded your data, it's time to create a new style so you can put it on the map! Go to your [Styles page](https://www.mapbox.com/studio/). Click the **New style** button. Find the *Basic Template* style and click **Create**.

Excellent! Welcome to the Mapbox Studio style editor. This is where you will create your map style.

<p align="center">
  <img src="/image/Studio.png>
  </p>

Rename the style so that you can find it later. Click into the title field in the upper left side of the screen to change the title from Basic Template to ‘Mapbox Workshop’.


*You can always refer to the* [*Mapbox Studio Manual*](https://www.mapbox.com/studio-manual/reference/styles/) *for more information on getting started.*

----------

### Add a new layer

To add and style your data, you will need to add a **new layer** to the map. At the top of the layer panel, click **+ Add layer** and select your **kindergarten** layer that you just uploaded as a tileset. 


<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/add-layer.png">
  </p>


The editor is now showing your map in “x-ray mode.” X-ray mode shows all the data in the sources added to the style, regardless of whether there is a layer to style it.

In the *New layer* panel, look in the list of *Data sources* for the Kindergarten source. Click the tileset and then select the source layer as the source for this new style layer.

The default Basic map view is not centered on the Nicaragua. Mapbox Studio recognizes that the data you have uploaded is focused on a different location, so it displays the message *"This tileset isn't available from your map view."* Click **Go to data**, and the map view will refocus on Nicaragua or type Nicaragua into the search bar.



<p align="center">
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/xray1.png">
  </p>



Your new layer will be highlighted on the x-ray map.


<p align="center">
  <img src="/image/Search.gif">
  </p>



Click the **Style** tab and the map will switch back to style mode displaying your new layer. You will see the data on the map with a default style (black with 100% opacity).


You can rename a layer by clicking on the name of the layer at the top of the panel. Rename your new layer **kindergarten**.


----------

### Style the layer

Each layer in Studio can be styled individually by clicking on the name of the layer in the Layer list. There are several layer types to choose from. Each layer type has a unique set of layer properties that can be specified. There are a few options for specifying property values. You can pick values individually, based on a data attribute, based on the zoom level, or the value of another property. For more information on layer types and their styling rules check out this [reference guide](https://docs.mapbox.com/studio-manual/reference/styles/).


----------

### Data driven styling 

In the Mapbox Studio style editor, you create graduate symbols based on numeric attributes. Click the Style link in the kindergarten layer. Next, click **Radius** and then **Style across data range**.

Under *Choose a numeric data field to interpolate over a range*, select amount_child_f (number of female children) to style the layer by the number of females students at each school. 


<p align="center">
  <img src="/image/Screen%20Shot%202019-12-04%20at%205.23.20%20PM.png">
  </p>

Before moving on to the next step, make the **kindergarten** layer invisible. 

<p align="center">
  <img src="/image/invisible.gif">
  </p>

----------

### Add a layer as a symbol

There are many different ways to style point data in Mapbox Studio, Mapbox GL JS, and the Mapbox iOS and Android SDKs. In this tutorial, we’ll walk you through how to visualize your point data with custom icons and markers. 

First add a **new layer** to the map. At the top of the layer panel, click **+ Add layer** and select your **healthcare facilities** data layer that you just uploaded as a tileset. 

Make sure to change the 'type' to **symbol** before selecting the data from the layer menu. 

<p align="center">
  <img src="/image/healthcare.png">
  </p>

Select the **Icon** tab and click on **Manage icons** in your spritesheet. This opens the Images option in the top toolbar. Select cutsom image and upload this image to your sprite sheet [hosptial_image](https://github.com/mjdanielson/WFP/blob/master/image/Hospital-2.svg)

<p align="center">
  <img src="/image/icon.png">
  </p>
  
Click the Style link in the hospital layer. Next, click **icon** and then select the hospital-2 icon that you just uploaded to your sprite sheet. 

<p align="center">
  <img src="/image/hospital-sprite.png">
  </p>

----------
  
 ### Style across a zoom range 

In the Mapbox Studio style editor, you can style symbols across zoom levels. Click the Style link in the hospital layer. Next, click on the icon and select  and then **Style across a zoom range**.

<p align="center">
  <img src="/image/zoom.png">
  </p>


Before publishing your map, make your **kindergarten** layer visible again.  

----------

### Publish the style


Now that you've got your map looking good, it's time to publish! Click the **Publish style** button at the top of the toolbar on the right side of the screen, then click **Publish** again on the next prompt.

<p align='center'>
  <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/publish_styel.png">
</p>

Hooray! Your style is now published! If you go back to your Styles page, you will see your new style at the top of the list.
You can use your ‘Share URL’ to open your style in a new browser tab and share it with collaborators for review.
