# gdal_cheatsheet

Frequently used GDAL (ogr2ogr) commands from spatial data processing.

## ogr2ogr

### Convert CSV to GeoJSON

```
$ ogr2ogr -f geojson 190313_bomen.geojson -oo X_POSSIBLE_NAMES=longitude -oo Y_POSSIBLE_NAMES=latitude -oo KEEP_GEOM_COLUMNS=NO bomen_gisib_utrecht.csv
```

## Convert WFS to GeoJSON

```
$ ogr2ogr -f GeoJSON footprints.geojson WFS:"http://geodata.nationaalgeoregister.nl/bag/wfs" bag:pand
```

## Convert shape to GeoJSON

```
$ ogr2ogr -f GeoJSON output.geojsoninput.shp
```

## Load GeoJSON to PostGIS

```
$ ogr2ogr -f "PostgreSQL" PG:"dbname=postgres user=postgres password=postgres" "./sample_Data/buildings_utrecht.geojson" -nln buildings_utrecht
```

## Reproject from EPSG:4326 to EPSG:28992

```
$ ogr2ogr -f geojson reproj.geojson -t_srs EPSG:28992 190313_bomen.geojson
```

## Spatial query

```
$ ogr2ogr -f geojson reproj1.geojson -spat 136356.6585 455832.7428 136922.3581 456107.1495 reproj.geojson
```
