## GIS-Web-Map
The web map was created using leaflet and javascript to host both vector and raster data. It also allows geoprocessing such as measure, buffer creation for layers and intersections.

### Dataset used to create the application
1. PTA Shapefiles:
The vector data for Pretoria was downloaded from Openstreet maps as an osm file .
The osm file was converted to shapefiles using QGIS.
The shapefiles extracted from the osm file were points (nodes), polygons (buildings), lines (roads) and multilines (roads, pathways and railway lines).
2. PTA Geotiff Images:
The Geotiff images were downloaded from the link given and georeferenced using Global Mapper. 
The Geotiff files were converted to png, extracted the bounds and added to the map.
3. Openstreet basemap:
The basemap was added using the link "http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
4. ArcGIS Imagery basemap

### Softwares used to create the application
* The application was created using Geoserver, PostGIS, Postegresql, PgAdmin 4 and QGIS.
* Postgresql 10.5 was downloaded from the postgresql website which automatically installs PgAdmin 4 and PostGIS 2.5 with the PostGIS shapefile loader were installed on postgresql server using the application stack builder. 
* A database for the application was created on PgAdmin 4 using postgresql server to load the shapefiles. PostGIS extensions were added to the database. 
* PTA shapefiles were then loaded to the database using PostGIS shapefile loader. Geoserver was used to create the tile map layer and publish the layers from PostGIS. The layers were then displayed on QGIS by connecting to PostGIS and loaded the shapefiles.
* Qgis2web plugin from QGIS was used to import the layers from QGIS to display them on the web using leaflet.

### Running the application on a local disk
* The application contains css files and js files which were created with the index html file and are recquired to run the application on any local disk. 
* The files can be downloaded as a zip file from the repository
* Create a folder and extract all the files to the folder.
* Then open the index file on a web browser.
* The application needs internet connection to run.

### How to use the application
* To open the application, open the index.html file with chrome or firefox browser, in internet explorer some of the features are not supported.
* The layers (Pretoria shapefiles and Geotiff images) are visible on the initial view of the map.
* The layers can be switched off using the layers icon on the right.
* The map has two basemaps Openstreet and ArcGIS Imagery and can be switched.
* Map has a zoom function including the home zoom.
* The scale which is at the bottom of the map changes as you zoom in or out
* The geolocator tool on the left shows the location of the user when clicked on it.
* The sidebar on the left has the functionality to upload shapefiles. The functinality uploads shapefiles that are zipped., 
* To show legend, click on the show legend button.
* To close the sidebar, click on the tab button twice.

### Geoprocessing
* The map has a measure tool on the top right corner which measures distances areas for polygons. The distance is measures in meters and also converted to kilometers, the area is measured in square kilometers and hectares.
* A buffer can be created for the shapefiles. The buffer has been created for points and lines on the map. 
* The blue circles on the map show the 50 m buffer for the layer points.
* The yellow lines represent the 50 m buffer for the layer lines. 
* Creating a buffer for other layers:
* Install visual studio code, open it after installation and install javascript tool support.
* Open the index.html file using visual studio code and copy the code below and paste it at the bottom of the file before </script> 
*        // layer: is the layer to be buffered
*        // 0.05 size of the buffer in kilometers
*        var json_layer_buffer = turf.buffer(layer.toGeoJSON(), 0.05, {units: 'kilometers'}); 
*        // creating buffer, choosing style, color and add to map
*        var layer_buffer = L.geoJson(json_layer_buffer, {style:{color: 'yellow',
*        dashArray: '5,5', fillOpacity: 0}}).addTo(map);
* Buffers created for points and lines are visible on initial view of the map and can be switched off from the layers list.
* Intersecting lines and multilines: 
* Add the below code to index.html in visual studio code
*        var intersection = turf.lineIntersect(layer_lines_3.toGeoJSON(), layer_multilines_2.toGeoJSON());.addTo(map);
* For intersecting polygons: 
* The web map has a single shapefile for polygons therefore an intersecting polygons is not possible for my dataset.
*        var intersection = turf.polygonIntersect(layer1.toGeoJSON(), layer2.toGeoJSON()).addTo(map);

### Limitations and Areas for improvement
* The application does not add Geotiff files directly, they should be converted to png or jpg images and specify the bounds when adding.
* Implementing the functionality to export shapefiles
* Add other geoprocessing tools such as union to the map.
* Geotiff images were converted to png format and added to the map, but they could not be uploaded on github together with other files because their size exceeds 25 mb. Github does not take images with a size that exceeds 25 mb.

### Libraries used
* Turf.js
Turf is a JavaScript library for spatial analysis.  Turf is an open source project maintained by Mapbox that allows for performing spatial operations in the browser. Turf helps to analyze, aggregate, and transform data in order to visualize it in new ways and answer advanced questions. There are many functions that can be done using turf and this project turf was used to create a buffer and do an intersection. Turf can be added to the webpage by defining it using the url "<script src='https://npmcdn.com/@turf/turf/turf.min.js'></script>" in the head of the html document.

### License information
* MIT License - Open source license

### References
* Leaflet plugins and tutorials - https://leafletjs.com/



