pygc
====

Great Circle calculations in Python using Vincenty's formulae


### Great Circle
```python
from pygc import great_circle
```

##### New point from initial point, distance, and azimuth
```python
great_circle(distance=111000, azimuth=65, latitude=30, longitude=-74)
{'latitude': 30.41900364921926,
'longitude': -72.952930949727573,
'reverse_azimuth': 245.52686122611451}
```

##### Three new points in three different angles from an initial point
```python
great_circle(distance=[100000, 200000, 300000], azimuth=[90, 180, -90], latitude=30, longitude=-74)
{'latitude': array([29.99592067, 28.1955554, 29.96329797]),
'longitude': array([-72.96361148, -74., -77.10848799]),
'reverse_azimuth': array([270.51817296, 360., 88.44633085])}
```

##### Three point south of three initial points (longitude shouldn't change much)
```python
great_circle(distance=[100000, 200000, 300000], azimuth=180, latitude=30, longitude=[-74, -75, -76])
{'latitude': array([29.09783841, 28.1955554, 27.29315337]),
'longitude': array([-74., -75., -76.]),
'reverse_azimuth': array([360., 360., 360.])}
```

##### Three point west of three initial points (latitude shouldn't change much)
```python
great_circle(distance=[100000, 200000, 300000], azimuth=270, latitude=[30, 31, 32], longitude=-74)
{'latitude': array([ 29.99592067, 30.98302388, 31.96029484]),
 'longitude': array([-75.03638852, -76.09390011, -77.17392199]),
 'reverse_azimuth': array([ 89.48182704, 88.92173899, 88.31869938])}
```


##### Starburst pattern around a point
```python
great_circle(distance=100000, azimuth=[0, 60, 120, 180, 240, 300], latitude=30, longitude=-74)
{'latitude': array([ 30.90203788, 30.44794729, 29.54590235, 29.09783841, 29.54590235, 30.44794729]),
 'longitude': array([-74., -73.09835956, -73.10647702, -74., -74.89352298, -74.90164044]),
 'reverse_azimuth': array([ 180., 240.45387965, 300.44370186, 360., 59.55629814, 119.54612035])}
```


### Great Distance
```python
from pygc import great_distance
```

##### Distance and angle between two points
```python
great_distance(start_latitude=30, start_longitude=-74, end_latitude=40, end_longitude=-74)
{'azimuth': 0.0, 'distance': 63564833.462465033, 'reverse_azimuth': 180.0}
```

##### Distance and angle between two sets of points
```python
great_distance(start_latitude=[30, 35], start_longitude=[-74, -79], end_latitude=[40, 45], end_longitude=[-74, -79])
{'azimuth': array([0., 0.]),
 'distance': array([63564833.46246503, 63618453.36677702]),
 'reverse_azimuth': array([180., 180.])}
```

##### Distance and angle between initial point and three end points
```python
great_distance(start_latitude=30, start_longitude=-74, end_latitude=[40, 45, 50], end_longitude=[-74, -74, -74])
{'azimuth': array([0., 0., 0.]),
 'distance': array([6.35648335e+07, 9.53877888e+07, 1.27238665e+08]),
 'reverse_azimuth': array([180., 180., 180.])}
```
