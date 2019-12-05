<img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/logo.png">

<h2 align="center"> Part II: Adding interactivity to web maps with GL JS </h3>


### In this tutorial you will:


- Publish a map style without adding layers
- Learn about GL JS and adding interactivity
- Call on map layers using GL JS
- Learn additional tools and tricks for creating compelling maps

A few additional resources for Mapbox GL JS:

- [https://www.mapbox.com/mapbox-gl-js/api/](https://www.mapbox.com/mapbox-gl-js/api/)
- [https://www.mapbox.com/mapbox-gl-js/examples](https://www.mapbox.com/mapbox-gl-js/examples) 
- Example finished maps that use Mapbox GL JS for more design control and interactivity: [https://native-land.ca/](https://native-land.ca/) or [https://www.mapbox.com/amnesty/](https://www.mapbox.com/amnesty/) or [https://www.nytimes.com/interactive/2018/upshot/election-2016-voting-precinct-maps.html](https://www.nytimes.com/interactive/2018/upshot/election-2016-voting-precinct-maps.html) 

----------

### Get started

To create a web map, you'll need to have some familiarity with HTML, CSS, and JavaScript. If you are new to web maps, explore our [tutorials](https://docs.mapbox.com/help/tutorials/) and [documentation](https://docs.mapbox.com/help/how-mapbox-works/web-apps/) to help you get started.
Here’s what you’ll need to get started:

- [Github account](https://github.com/join)
- [JSFiddle Text Editor](https://jsfiddle.net/)

*This is a very beginner intro by a non-developer - there’s a lot more to learn about developing more complex web apps and sites, but we’re focusing just on a simple web map. For more complex projects and teams, you’ll want to learn more about version control and using Github properly, with pull requests etc.*

----------


### Orientation to your tools


For this lesson, we will be using a program called JSFiddle. You can sign up for a free acount at: [https://jsfiddle.net/](https://jsfiddle.net/)
JSFiddle is a simple tool for building and testing code for web development. We recommend using JSFiddle in a Chrome browser
For simplicity, we recommend that you change the editor layout settings in JSFiddle to display by ‘tabs’


<p align="center">
<img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/jsfiddle-tabs.gif">
</p>


----------


### Writing your first code


To begin, we will be using a sample code created by the documentation team at Mapbox to initialize a simple web map in JSFiddle. 

```html
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8' />
    <title>Display a map</title>
    <meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
    <script src='https://api.tiles.mapbox.com/mapbox-gl-js/v1.4.0/mapbox-gl.js'></script>
    <link href='https://api.tiles.mapbox.com/mapbox-gl-js/v1.4.0/mapbox-gl.css' rel='stylesheet' />
    <style>
        body { margin:0; padding:0; }
        #map { position:absolute; top:0; bottom:0; width:100%; }
    </style>
</head>
<body>

<div id='map'></div>
<script>
mapboxgl.accessToken = 'pk.eyJ1IjoibWpkYW5pZWxzb24iLCJhIjoiY2p2bzFlbnZ5MW5pbTN5cGJ2YWp2MW9vaiJ9.kAaZq3iyJwvrMLK7XDs_qw';
var map = new mapboxgl.Map({
    container: 'map', // container id
    style: 'mapbox://styles/mapbox/streets-v11', // stylesheet location
    center: [-74.50, 40], // starting position [lng, lat]
    zoom: 9 // zoom level
});
</script>

</body>
</html>
```


1. Copy [this sample code](https://www.mapbox.com/mapbox-gl-js/example/simple-map/) and paste it into the **HTML section** of your JSFiddle.
2. Edit the code to add your Mapbox [access token](https://www.mapbox.com/help/define-access-token/) (get your access token from your Mapbox [‘Account’ page](https://account.mapbox.com/)).
3. Click ‘Run’ in the upper left


<p align="center">
<img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/changes_map1.png">
</p>


4. Add a title and description and hit save!

5. See your map in fullscreen: Grab your JSFiddle unique ID (url), paste it into a new tab and add `/show` to the end. For example: ‘https://jsfiddle.net/4up1vwsm/show’


 **You’ve just made a web map! Not too shabby!**

<p align="center">
<img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/fistbump.png">
</p>


----------

### Editing your code

Now that we’ve initialized the webmap, let’s try to make some changes to our code. Currently, your map is centered on New Jersey, USA when it loads. We need to change the location and the zoom level so that the map is centered on Nicaragua. 

1. Locate the line of code that is telling the map where to center the view.
2. Try changing the center location to the center of the US by picking a new coordinate using [http://geojson.io/](http://geojson.io/#map=2/20.0/0.0) (or looking at the bottom of the right-hand panel in the Mapbox Studio style editor).
3. Change the coordinates in your code and run your changes.
4. Change the zoom level to 6. 
5. Click ‘Run’ to see the changes to your map. 


<p align="center">
    <img src="/image/Nicaragua.png">
    </p>

----------

### Adding your custom style

**Style**: The map loads a style via the URL mapbox://styles/mapbox/streets-v11. This is a URL to a remote file that the map will download to determine the [tilesets](https://docs.mapbox.com/help/glossary/tileset/) it includes and how they are styled for the end-user. Mapbox GL JS permits URLs instead of literal data in several places, including data sources. To load the style that you created in the previous assignment, you need to go to go your Mapbox Studio account and find your Style URL ([how to find your Style URL](https://docs.mapbox.com/help/glossary/style-url/)):


<p align="center">
    <img src="https://github.com/mjdanielson/University-of-Oregon/blob/master/Labs/Opioid-Tutorial/Images/mapstyle.png">
    </p>
<br></br>
<h3 align ="center"> OR </h3>
<br></br>
<p align="center">
    <img src="/image/publihs-style.gif">
    </p>


- Edit the row with the style URL it in your code and run your changes. *(Which row to edit? Look for a row with something that looks similar to your style URL)*

<p align="center">
    <img src="/image/Jsfiddle_style.png">
    </p>

----------

## Add navigation controls

Let’s try modifying the code to add a new element to the map. Currently, you can zoom in and out using your mouse, but we want to add navigation controls (zoom in, zoom out, and north arrow) to make the zooming functions more obvious to our end users.

To get started, check out this code: [https://www.mapbox.com/mapbox-gl-js/example/navigation/](https://www.mapbox.com/mapbox-gl-js/example/navigation/)

What part of the example is missing for your current code? Copy and paste the navigation control function into your code after your `var = map` element but before the ```</script>``` and click ‘Run’ when you have finished.  

```javascript

mapboxgl.accessToken = 'pk.eyJ1IjoibWpkYW5pZWxzb24iLCJhIjoiY2p2bzFlbnZ5MW5pbTN5cGJ2YWp2MW9vaiJ9.kAaZq3iyJwvrMLK7XDs_qw';
var map = new mapboxgl.Map({
    container: 'map', // container id
    style: 'mapbox://styles/mjdanielson/ck3s0iii80io11co4w5duvd86', // stylesheet location
    center: [ -85.045166015625,
          12.704650508287893], // starting position [lng, lat]
    zoom: 6 // starting zoom
});

// Add zoom and rotation controls to the map.
map.addControl(new mapboxgl.NavigationControl());


</script>

</body>
</html>
```

----------

### Adding [toggling interactions](https://docs.mapbox.com/mapbox-gl-js/example/toggle-interaction-handlers/)

Adding toggling interactions allows user to Enable or disable layers on the map.

Copy and paste the following just after the opening ``<body>`` tag in your code: 

```css
<style>
#menu {
background: #fff;
position: absolute;
z-index: 1;
top: 10px;
right: 10px;
border-radius: 3px;
width: 120px;
border: 1px solid rgba(0,0,0,0.4);
font-family: 'Open Sans', sans-serif;
}

#menu a {
font-size: 13px;
color: #404040;
display: block;
margin: 0;
padding: 0;
padding: 10px;
text-decoration: none;
border-bottom: 1px solid rgba(0,0,0,0.25);
text-align: center;
}

#menu a:last-child {
border: none;
}

#menu a:hover {
background-color: #f8f8f8;
color: #404040;
}

#menu a.active {
background-color: #3887be;
color: #ffffff;
}

#menu a.active:hover {
background: #3074a4;
}
</style>

```

Next, add the following code below your map variable: 

```javascript
var toggleableLayerIds = [ 'Healthcare Facilities', 'Kindergarten' ];

for (var i = 0; i < toggleableLayerIds.length; i++) {
var id = toggleableLayerIds[i];

var link = document.createElement('a');
link.href = '#';
link.className = 'active';
link.textContent = id;

link.onclick = function (e) {
var clickedLayer = this.textContent;
e.preventDefault();
e.stopPropagation();

var visibility = map.getLayoutProperty(clickedLayer, 'visibility');

if (visibility === 'visible' || visibility === undefined) {
map.setLayoutProperty(clickedLayer, 'visibility', 'none');
this.className = '';
} else {
this.className = 'active';
map.setLayoutProperty(clickedLayer, 'visibility', 'visible');
}
};

var layers = document.getElementById('menu');
layers.appendChild(link);
}

```

 
 Hit run to see your changes!
 
 <p align="center">
    <img src="/image/finished%20map.png">
    </p>

----------

### Create your webpage


*You’ve made a web map! But this is just serving the map directly from the code within JSFiddle, it isn’t a webpage yet… to do that we need some way to host a webpage. Today, let’s use Github Pages.*
**Orientation to Github Pages** 

1. (Create a Github account if you don’t have one)
2. Set up a Github [repository](https://help.github.com/articles/create-a-repo/)
    - Name it whatever you want
    - Make it Public
    - Click the box to ‘Initialize this repository with a README’
![](https://lh3.googleusercontent.com/asCZvCmvq6bxNthgMEgDhmq1uQ1IwHqdLYOkGAKpoQT2yEhf_7e8Rsu5doIZ--mvDJ3Ru6h7Qf_rO95LEn9s7spGUnx2xLI7MleSAML0ra6fR1A6jpbx26qfKL9ksWsi74q1P9uC)

3. **Create a new file** called index.html
4. In the blank index.html file, paste in the entire code we built in JSFiddle

```html
<!DOCTYPE html>
<html>
<head>
<meta charset='utf-8' />
<title>Display a map</title>
<meta name='viewport' content='initial-scale=1,maximum-scale=1,user-scalable=no' />
<script src='https://api.tiles.mapbox.com/mapbox-gl-js/v1.5.1/mapbox-gl.js'></script>
<link href='https://api.tiles.mapbox.com/mapbox-gl-js/v1.5.1/mapbox-gl.css' rel='stylesheet' />
<style>
body { margin:0; padding:0; }
#map { position:absolute; top:0; bottom:0; width:100%; }
</style>
</head>
<body>

<style>
#menu {
background: #fff;
position: absolute;
z-index: 1;
top: 10px;
right: 10px;
border-radius: 3px;
width: 120px;
border: 1px solid rgba(0,0,0,0.4);
font-family: 'Open Sans', sans-serif;
}

#menu a {
font-size: 13px;
color: #404040;
display: block;
margin: 0;
padding: 0;
padding: 10px;
text-decoration: none;
border-bottom: 1px solid rgba(0,0,0,0.25);
text-align: center;
}

#menu a:last-child {
border: none;
}

#menu a:hover {
background-color: #f8f8f8;
color: #404040;
}

#menu a.active {
background-color: #3887be;
color: #ffffff;
}

#menu a.active:hover {
background: #3074a4;
}
</style>

<nav id="menu"></nav>
<div id="map"></div>

<script>
mapboxgl.accessToken = 'pk.eyJ1IjoibWpkYW5pZWxzb24iLCJhIjoiY2p2bzFlbnZ5MW5pbTN5cGJ2YWp2MW9vaiJ9.kAaZq3iyJwvrMLK7XDs_qw';
var map = new mapboxgl.Map({
    container: 'map', // container id
    style: 'mapbox://styles/mjdanielson/ck3s0iii80io11co4w5duvd86', // stylesheet location
    center: [ -85.045166015625, 12.704650508287893], // starting position [lng, lat]
    zoom: 6 // starting zoom
});

var toggleableLayerIds = [ 'Healthcare Facilities', 'Kindergarten' ];

for (var i = 0; i < toggleableLayerIds.length; i++) {
var id = toggleableLayerIds[i];

var link = document.createElement('a');
link.href = '#';
link.className = 'active';
link.textContent = id;

link.onclick = function (e) {
var clickedLayer = this.textContent;
e.preventDefault();
e.stopPropagation();

var visibility = map.getLayoutProperty(clickedLayer, 'visibility');

if (visibility === 'visible' || visibility === undefined) {
map.setLayoutProperty(clickedLayer, 'visibility', 'none');
this.className = '';
} else {
this.className = 'active';
map.setLayoutProperty(clickedLayer, 'visibility', 'visible');
}
};

var layers = document.getElementById('menu');
layers.appendChild(link);
}

</script>

</body>
</html>

```

5. [Enable Github Pages](https://pages.github.com/) (in repo Settings - the gear symbol in the upper right):
6. Then wait a minute, then go to your Github page address (https://[YOUR GITHUB NAME].github.io/[YOUR REPO NAME]/) - you can find this by scrolling back to the Github Pages settings.
7. (You might need to wait another minute if it doesn’t work right away)

***Voila! Now you have a live website with a Mapbox map!*** 

<p align="center">
    <img src="https://media.giphy.com/media/Bj2UZgqqzUxwc/giphy.gif">
    </p>

**Polishing steps:**

- Currently, the tab for your webpage in your browser says ‘Display a map’ - let’s give it a better title - can you see where in the code to change that?

- Change it in your code, commit your changes in your Github index.html file, give it a minute, and check your webpage.



