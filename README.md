# GIS-Web-Map
The web map was created using leaflet to host both vector and raster data. It also allows geoprocessing such as measure, buffer creation for layers and intersections. The application was created using JavaScript.

Dataset used to create the application
1. PTA Shapefiles:
The vector data for Pretoria was downloaded from Openstreet maps as an osm file .
The osm file was converted to shapefiles using   QGIS.
The shapefiles extracted from the osm file were points, polygons, lines and multilines.
2. PTA Geotiff Images:
The Geotiff images were downloaded from the link given and georeferenced using Global Mapper. 
The Geotiff files were converted to jpg, extracted the bounds and added to the map.
3. Openstreet basemap:
The basemap was added using the link "http://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
4. ArcGIS Imagery basemap

Set up for running the application on a local disk

1. The application was created using Geoserver, PostGIS, Postegresql, PgAdmin 4 and QGIS.
> Postgresql 10.5 was downloaded from the postgresql website. PgAdmin 4 and PostGIS with the PostGIS shapefile loader were installed on postgresql. 
> A database for the application was created on PgAdmin 4 using postgresql server to load the shapefiles. PostGIS extensions were added to the database. 
> PTA shapefiles were then loaded to the database using PostGIS shapefile loader. Geoserver was used to create the tile map layer and publish the layers from PostGIS. The layers were then displayed on QGIS by connecting to PostGIS and loaded the shapefiles. Qgis2web plugin from QGIS was used to import the layers from QGIS to display them on the web using leaflet.
2. The application contains css files and js files which connect to the index html file. The index html file recquires all the css files, javascripts file and access to the internet to run on a local disc. The index file should be downloaded with all the fies and be packed together into a folder. Then open the index file to run the application.


