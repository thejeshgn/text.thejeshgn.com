Create a table
```
CREATE TABLE experiment ( 
  p_id INTEGER PRIMARY KEY,
  p_name VARCHAR
);
```

Add gis column
```
SELECT AddGeometryColumn('experiment','gis_center_point','4326','POINT',2);
```

insert some values

```
INSERT INTO experiment(p_id, p_name, gis_center_point)
VALUES(1, 'Random point', ST_GeomFromText('POINT(-71.060316 48.432044)', 4326));

INSERT INTO experiment(p_id, p_name, gis_center_point)
VALUES(2, 'my home', ST_GeomFromText('POINT(12.978596 77.591668)', 4326));
```

select values

```
select * from experiment;
```

select as geojson

```
my_gis_database=# select * from experiment;
 p_id |    p_name    |                  gis_center_point                  
------+--------------+----------------------------------------------------
    1 | Random point | 0101000020E61000003CDBA337DCC351C06D37C1374D374840
    2 | my home      | 0101000020E61000002AFEEF880AF52940BE8575E3DD655340
(2 rows)

my_gis_database=# SELECT ST_AsGeoJSON(gis_center_point) from experiment;
                     st_asgeojson                      
-------------------------------------------------------
 {"type":"Point","coordinates":[-71.060316,48.432044]}
 {"type":"Point","coordinates":[12.978596,77.591668]}
(2 rows)

my_gis_database=# SELECT p_id,p_name,  ST_AsGeoJSON(gis_center_point) from experiment;
 p_id |    p_name    |                     st_asgeojson                      
------+--------------+-------------------------------------------------------
    1 | Random point | {"type":"Point","coordinates":[-71.060316,48.432044]}
    2 | my home      | {"type":"Point","coordinates":[12.978596,77.591668]}
(2 rows)
					   

```