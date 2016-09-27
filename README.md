# SMOS ISEA 4H9 Discrete Global Grid over Land
ESA's ***Soil Moisture Ocean Salinity (SMOS)*** Earth Explorer mission's data (multi-angular brightness temperature and soil moisture) are processed onto ISEA 4H9 Discrete Global Grid [[1]](https://earth.esa.int/web/guest/missions/esa-operational-eo-missions/smos)[[2]](https://smos-ds-02.eo.esa.int/oads/access/).

The `isea4h9_smos_dgg_id.shp` file contains "cells over land" of ***ISEA 4H9 Discrete Global Grid (DGG)***. DGG grid was created using ***DGGRID Version 6.2b*** [[3]](http://www.discreteglobalgrids.org/software/). Then DGG cells over land were filtered and id of cells was changed to those that correspond to smos_id [[4]](http://www.cesbio.ups-tlse.fr/SMOS_blog/?tag=isea-grid).

If you want to get cells just for particular area (or you SMOS IDs you need) you can simply use QGIS, gdalwarp, PostGIS...

The `yamal_isea4h9_land.shp` file contains area of Yamal peninsula.
