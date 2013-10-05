## update sources
sudo apt-get update

## install sqlite3 and libproj
sudo apt-get install libsqlite3-dev
sudo apt-get install libproj-dev


## Install GeoS
Go to http://trac.osgeo.org/geos/
Download geos-3.4.2.tar.bz2

```
tar jxf geos-3.4.2.tar.bz2
cd geos-3.4.2
./configure
make
sudo make install
```



## Install freexl
Go to https://www.gaia-gis.it/fossil/freexl/index
Download, extract and install

```
tar -xvzf freexl-xxxxxxx.tar.gz
cd freexl-1.0.0e/
./configure 
make -j8
sudo make install-strip
```


## Install the library
Go to http://www.gaia-gis.it/gaia-sins/
Download, extract and install

```
tar -xvzf libspatialite-4.x.x.tar.gz
cd libspatialite-4.x.x
./configure 
make -j8
sudo make install-strip
```


## Register Binaries

```
Edit
sudo nano /etc/ld.so.conf

Add
/usr/local/lib

Refresh
sudo ldconfig
```

