# gdal_cheatsheet

Frequently used GDAL (ogr2ogr) commands for spatial data processing.

Run on Docker on Windows:

```
$ docker run -v d:\test:/data  geodata/gdal ogr2ogr
```

Run on Docker on Mac/Linux:

```
$ docker run -v $(pwd):/data  geodata/gdal ogr2ogr
```


## OGR2OGR

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

## Sql query on csv file

```
$ ogrinfo -q data.csv -dialect sqlite -sql "SELECT distinct field_2, field_3 FROM data"
```

## Spatial query

```
$ ogr2ogr -f geojson reproj1.geojson -spat 136356.6585 455832.7428 136922.3581 456107.1495 reproj.geojson
```

## GDAL

### GdalInfo on tif file

```
$ gdalinfo /data/i09bz13857.tif
```

### GdalWarp on tif file

```
$ gdalwarp -t_srs EPSG:3857 /data/i09bz1.tif
```
