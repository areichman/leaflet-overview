# L.Control.Overview
Provides an overview map that responds to base layer changes.

## Setup
The same layer instance cannot be used in the main map and the overview at the same
time, so separate layers must be created. Because there are multiple layers of the same 
type involved, each layer must contain a 'name' attribute so the control can keep the
two maps in sync with each during base layer changes.

First, define two base layers and initialize the main map with the default base layer:

```javscript
var osm = L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
  name: 'osm',
  attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
});
          
var mqo = L.tileLayer('http://otile{s}.mqcdn.com/tiles/1.0.0/osm/{z}/{x}/{y}.png', {
  name: 'mapquest',
  attribution: 'Tiles courtesy of <a href="http://www.mapquest.com/">MapQuest</a>',
  subdomains: '1234'
});
          
var map = L.map('map', {
  layers: osm,
  center: [43.12, -77.67],
  zoom:   10
});
```

Next, add the layer switcher control to the map:

```javascript
L.control.layers({
  'OpenStreetMap': osm, 
  'MapQuest Open': mqo
}).addTo(map);
```

Last, define two more versions of our base layers that will be used by the overview control:

```javascript
var osm2 = L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
  name: 'osm',
  attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
});
            
var mqo2 = L.tileLayer('http://otile{s}.mqcdn.com/tiles/1.0.0/osm/{z}/{x}/{y}.png', {
  name: 'mapquest',
  attribution: 'Tiles courtesy of <a href="http://www.mapquest.com/">MapQuest</a>',
  subdomains: '1234'
});
            
L.control.overview([osm2, mqo2]).addTo(map);
```

You can see the above code in action in the [example](http://areichman.github.io/leaflet-overview/example/).

## License
L.Control.Overview is free software, and may be redistributed under the MIT-LICENSE.
