# Political Map Simulator
Copyright (C) 2021  Ponderix

A website engine which aims to create a more transparent and dynamic way of making interactive political map websites. Initially intended for the [GovMap](https://github.com/haroldTheDeveloper/GovMap) project.

## Naming Conventions
Maps in [assets/maps](assets/maps) should be named `[Country]_[type-(YEAR)]_(HYP)`. E.g `Germany_Wahlkreise-2021` for a real life map or `Adoria_NationalAssembly_HYP` for a hypothetical map, all fictional countries count as hypothetical. The `[type]` must be written as one word, even if the proper name is two seperate words e.g `RegionalParliament`.

Function arguments are kept short as one or two letter words, here is a list of a few and their corresping meaning. The arguments aren't always used appropriate to their precise technical definition, rather they are used as a way to make code more organised and intuitive.

* e => element
* n => given number or string
* m => map
* d => data
* i => index
* p => path
* fc => feature collection
* wd, ht, ln => width, height, length


## Other Notes
All maps in [assets/maps/geojson](assets/maps/geojson) must be topojson GeoJSON files. Use [mapshaper](https://mapshaper.org/) to convert to topojson.


The feature collection of all topojson files must be named `boundaries` so it can be parsed by the fetching functions.
```js
//this function parses a topojson file and transforms it into a vector graphic
let map = e.selectAll("path")
    .data(topojson.feature(data, data.objects.boundaries).features) //here is the important part, look at keyword ".boundaries"
    .enter().append("path")
        .attr("d", path);
```


An extensive guide to GIS and vector graphics as well as the use of bounding boxes and coordinate systems cis provided in [documentation](DOCUMENTATION.md).

