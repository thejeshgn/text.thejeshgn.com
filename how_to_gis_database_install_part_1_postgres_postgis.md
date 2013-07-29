###STEP0: Ubuntu
Ubuntu 12.04 LTS

###STEP1: Install postgresSQL 9.1

```
apt-get install postgresql-9.1
```


###STEP2: Prerequisites


```
sudo apt-get install build-essential postgresql-9.1 postgresql-server-dev-9.1 libxml2-dev libproj-dev libjson0-dev xsltproc docbook-xsl docbook-mathml

sudo apt-get install libgdal1-dev
```

###STEP3: Build and install GEOS 3.3.x

PostGIS 2.0 requires GEOS >= 3.3.2 for topology support

```
wget http://download.osgeo.org/geos/geos-3.3.8.tar.bz2
tar xvfj geos-3.3.8.tar.bz2
cd geos-3.3.8
./configure
make
sudo make install
cd ..
```

###STEP4: PostGIS

```
wget http://download.osgeo.org/postgis/source/postgis-2.0.3.tar.gz
tar xfvz postgis-2.0.3.tar.gz
cd postgis-2.0.3
./configure
make
sudo make install
sudo ldconfig
sudo make comments-install
```

simlink so you can run directly.

```
sudo ln -sf /usr/share/postgresql-common/pg_wrapper /usr/local/bin/shp2pgsql
sudo ln -sf /usr/share/postgresql-common/pg_wrapper /usr/local/bin/pgsql2shp
sudo ln -sf /usr/share/postgresql-common/pg_wrapper /usr/local/bin/raster2pgsql
```

###STEP5: CREATE A DB

First create a ubuntu user with the same name. Then create a postgres user with the same name. Then su to it

```
useradd gisuser
sudo -u postgres createuser gisuser
su gisuser
```

Create a database

```
sudo -u postgres createdb --encoding=UTF8 --owner=gisuser my_gis_database
psql -d my_gis_database
```

###STEP6: ENABLE GIS for DB

Login to db and enable extensions


```
psql -d my_gis_database
CREATE EXTENSION postgis;
CREATE EXTENSION postgis_topology;
```


###STEP7: CHECK GIS  DB

```
psql -d my_gis_database 
```

Run comman "\d" It should return

```
my_gis_database=# \d
                 List of relations
  Schema  |       Name        |   Type   |  Owner   
----------+-------------------+----------+----------
 public   | geography_columns | view     | postgres
 public   | geometry_columns  | view     | postgres
 public   | raster_columns    | view     | postgres
 public   | raster_overviews  | view     | postgres
 public   | spatial_ref_sys   | table    | postgres
 topology | layer             | table    | postgres
 topology | topology          | table    | postgres
 topology | topology_id_seq   | sequence | postgres
(8 rows)
```

Check if the GIS extensions are installed

```
SELECT name, default_version,installed_version 
FROM pg_available_extensions WHERE name LIKE 'postgis%' ;
```

it should return


```
       name       | default_version | installed_version 
------------------+-----------------+-------------------
 postgis_topology | 2.0.3           | 2.0.3
 postgis          | 2.0.3           | 2.0.3
(2 rows)
```
