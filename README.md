# Geovisto Choropleth Layer Tool
Extension of the [Geovisto core library](https://github.com/geovisto/geovisto) which provides the tile layer.

This repository is a snapshot of Geoviosto ``tools/layers/choropleth`` derived from the development repository: [geovisto/geovisto-map](https://github.com/geovisto/geovisto-map).

![sample](https://user-images.githubusercontent.com/1479229/131523051-b2723b80-84eb-496c-8b96-5e615a9e4944.png)

## Usage

```js
import { GeovistoChoroplethLayerTool } from 'geovisto-layer-choropleth';
import 'geovisto-layer-choropleth/dist/index.css';

// create instance of map with given props
const map = Geovisto.createMap({
  // ...
  tools?: Geovisto.createMapToolsManager([
    // instances of Geovisto tools (extensions) which will be directly used in the map
    // ...
    GeovistoChoroplethLayerTool.createTool({
      id: "geovisto-tool-layer-choropleth"
      dimensions?: ...; // provide instance of IChoroplethLayerToolDimensions to override dimensions
      geoData?: ...; // provide instance of IGeoDataManager to override geographical data manager
    }),
  ])
});

// rendering of the map
map.draw(Geovisto.getMapConfigManagerFactory().default({
  // initial settings of the map can be overriden by the map config - JSON structure providing user settings 
  // ...
  tools?: [
    // config of Geovisto tools (extensions) used in the map
    {
      "type": "geovisto-tool-layer-choropleth",
      "id": "geovisto-tool-layer-choropleth",
      "enabled": true,
      "name": "Choropleth layer",
      // mapping of data domains to data dimensions
      "data": {
        "country": "country", // domain name
        "value": "value", // domain name
        "aggregation": "sum", // [ "sum", "count" ]
        "scaling": "median", // [ "median", "relative [0-max]", "relative [min-max]", "decimal [0-max]" ]
        "range": 7, // 1..7
        "customColor": true,
        "color": "#e32400"
      }
    },
  ]
}));
```

## Installation

```
npm install --save geovisto-layer-choropleth
```

Peer dependencies:
```
npm install --save geovisto leaflet
```

This package serves as an extension of Geovisto core using the API for Geovisto tools (extensions). Follow Geovisto core on [Github](https://github.com/geovisto/geovisto).

## License

[MIT](https://github.com/geovisto/geovisto-themes/blob/master/LICENSE)

