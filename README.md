# leaflet.resetview
[Trafford Data Lab](https://www.trafforddatalab.io) plugin for the [Leaflet](https://leafletjs.com) JavaScript library to [re]set the map view to particular coordinates and zoom level. Although there are many similar plugins available, what makes this one different is that you can attach it to other plugin containers, e.g. the built-in zoom control, or display it within its own. Most similar plugins re-create the zoom control functionality to achieve this. Also you can specify the coordinates and zoom values if you wish, allowing multiple instances of the control to be added to your map to provide a method of jumping between specific places etc. [Check out the demo](https://www.trafforddatalab.io/leaflet.resetview/leaflet.resetview_example.html) to get an idea of the various possibilities.

## Documentation
After including the JS in your page (NOTE - you can also use the minified version leaflet.resetview.min.js if you prefer):...
```HTML
<script src="https://cdn.jsdelivr.net/gh/trafforddatalab/leaflet.resetview@v1.0.0/leaflet.resetview.js"></script>
```

...you can then initialise the plugin in the standard Leaflet way adding it to a map instance:

```javascript
<body>
    <div id="map"></div>

    <script>
        // Create the Leaflet map object
        var map = L.map('map', { center: [53.4189, -2.33], zoom: 12 });

        // Create a Leaflet tile layer object
        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
        }).addTo(map);

        // Initialise the plugin
        L.control.resetView({
            // add settings/options here
        }).addTo(map);
    </script>
</body>
```

This is the minimum code required and will use all the default settings, e.g. left arrow symbol to represent the control, current coordinates and zoom value of the map at the time the control is added to the map. To customise the plugin for your requirements you will need to change the default options.

### Options

These are the options available for the control:

| Option      | Type        | Default                                          | Description |
| ----------- | ----------- | ------------------------------------------------ | ----------- |
| `center`    | array       | Current map centre coordinates on initialisation | Array specifying the latitude and longitude coordinates in the form `[Lat, Lng]` |
| `container` | HTMLElement | Creates its own internally                       | The HTML container for the control. Can be an existing control's container obtained via the Leaflet function `getContainer()`. |
| `content`   | string      | HTML left-arrow entity `&larr;`                  | The content you want displaying within the control. If you want to use an icon font simply pass an empty string for this and use the `cssClass` option to specify the icon. |
| `cssClass`  | string      | Empty string                                     | CSS class name(s) to style the control. Can also be used to specify icon fonts to display in place of `content`. |
| `position`  | string      | `'topleft'`                                      | One of the map corners where you want the control to appear. Can be `'topleft'`, `'topright'`, `'bottomleft'`, `'bottomright'`. |
| `title`     | string      | `'Reset map view'`                               | Tooltip to appear when the user hovers over the control. |
| `zoom`      | number      | Current map zoom on initialisation               | The zoom level that the map should be displayed at when the control is activated. |

The [example code in the demo](https://github.com/traffordDataLab/leaflet.resetview/blob/master/leaflet.resetview_example.js) shows how to use the options above.

## Licence
This software is provided under the terms of the [MIT License](https://www.trafforddatalab.io/leaflet.resetview/LICENSE.txt).
