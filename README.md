# SMOS ISEA 4H9 Discrete Global Grid over Land
ESA's ***Soil Moisture Ocean Salinity (SMOS)*** Earth Explorer mission's data (multi-angular brightness temperature and soil moisture) are processed onto ISEA 4H9 Discrete Global Grid [[1]](https://earth.esa.int/web/guest/missions/esa-operational-eo-missions/smos)[[2]](https://smos-ds-02.eo.esa.int/oads/access/).

The `isea4h9_smos_dgg_id.shp` file contains "cells over land" of ***ISEA 4H9 Discrete Global Grid (DGG)***. DGG grid was created using ***DGGRID Version 6.2b*** [[3]](http://www.discreteglobalgrids.org/software/). Then DGG cells over land were filtered and id of cells was changed to those that correspond to smos_id [[4]](http://www.cesbio.ups-tlse.fr/SMOS_blog/?tag=isea-grid).

If you want to get cells just for particular area (or you SMOS IDs you need) you can simply use QGIS, gdalwarp, PostGIS...

The `yamal_isea4h9_land.shp` file contains area of Yamal peninsula.

## How to get coordinates of needed hexagon?

For my purpose(s), I keep SMOS pixels in the database (PostgreSQL with PostGIS extension), and then a can simply use some command in PostGIS to get coordinates of a hexagon that I need.

__Or you can use ogr2ogr to extract area you need:__
ogr2ogr -t_srs EPSG:4326 -spat -26 -39 60 39 my_area_isea4h9_land.shp isea4h9_smos_dgg_id.shp

Note, that after that you will probably need to delete the "parallel lines". These lines are hexagons that go through the 180/-180 longitude line (180th meridian) and usually, they are visualized in that strange way. You can delete them for example in QGIS.

__Or you can use ogr2ogr to extract pixels you need:__
ogr2ogr -t_srs EPSG:4326 -where "smos_id in (2033600, 2034113, 2034114)" my_pixels_isea4h9_land.json isea4h9_smos_dgg_id.shp

If you will use for example json format, you can open the file in some text editor and you will see the coordinates of each pixel. 

Or you can use some other GIS tool. For visualization I use QGIS. With QGIS you can also extract pixels. And do a lot of GIS.
