# Tippecanoe

Tippecanoe is developed by Mapbox. It builds vector tilesets from collections of GeoJSON features. For original source and commands see: https://github.com/mapbox/tippecanoe.

## Features 

* Convert GeoJSON to mbtiles
* Merge geo-data into mbtiles vector tile database

## Environment

Docker image on DockerHub for Mapbox's Tippecanoe, based on Ubuntu.

This [Dockerfile](Dockerfile) installs TippeCanoe in a docker container with entrypoint tippecanoe so you can use docker to run the TippeCanoe command.

### Build

```shell
docker build -t eslider1/docker-tippecanoe .
```

### Usage

Run docker-tippecanoe with docker run, mounting a local directory or use Docker volumes as needed with `-v`. 

See example:

```shell
docker run --rm -u $(id -u ${USER}):$(id -g ${USER}) -v$PWD:/data_tiles eslider1/docker-tippecanoe  -o data_tiles/output.mbtiles /data_tiles/example.geojson 
```

If no files are specified, it reads GeoJSON from the standard input. If multiple files are specified, each is placed in its own layer.


#### Help

To run the tippecanoe help:

```shell
docker run --rm eslider1/docker-tippecanoe --help
```

For more information, please read the Tippecanoe documentation: https://github.com/mapbox/tippecanoe.

#### Making your own vector tiles with TippeCanoe

output.mbtiles- Docker
- Geodata as GeoJSONs

1. Export your geodata to GeoJSON. For example with ogr2ogr or export from QGIS or any other GIS tool you use. You can also simply edit geojson map data here: http://geojson.io.
2. Get Tippecanoe. Get the code from: https://github.com/mapbox/tippecanoe . Here you can also find their documentation. Tippecaoe has already been dockerized and put on the Docker Hub. So you can also immediately pull it from there.

```
docker pull eslider1/docker-tippecanoe
```

To run Tippecanoe, for the first time just run:

```
docker run eslider1/docker-tippecanoe
```

For more information, please read the Tippecanoe documentation: https://github.com/mapbox/tippecanoe.

## Get tiles from OSM

Another way of getting vector tiles, without having your own data is from OpenMapTiles.

Have a look at: https://openmaptiles.org/ (Former project name: <a href="https://openmaptiles.org/osm2vectortiles/">OSM2VectorTiles</a>). OpenMapTiles.org is an open-source project from <a href="https://www.klokantech.com/">Klokan Technologies GmbH</a>  and <a href="https://github.com/openmaptiles">OSM community</a>. The project turns the publicly available OpenStreetMap data into ready-to-use packages containing vector tiles for the whole planet, individual countries and major cities.
