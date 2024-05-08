# AltAzRange - Calculate altitude, azimuth, distance from gps cords
[![MIT License](https://img.shields.io/apm/l/atomic-design-ui.svg?)](https://github.com/tterb/atomic-design-ui/blob/master/LICENSEs)
[![Version](https://badge.fury.io/gh/tterb%2FHyde.svg)](https://badge.fury.io/gh/tterb%2FHyde)
[![Hits](https://hits.seeyoufarm.com/api/count/incr/badge.svg?url=https%3A%2F%2Fgithub.com%2Fsq3tle%2Faltazrange&count_bg=%2379C83D&title_bg=%23555555&icon=&icon_color=%23E7E7E7&title=hits&edge_flat=false)](https://hits.seeyoufarm.com)

Simple tool to calculate altitude (elevation), azimuth and range between observer and object or pair of coordinates.

This version of the code has been modified to accept numpy arrays as input. 
This allows for the calculation of multiple targets in one sweep using vector calucations.
    
Note that inputs and outputs are in degrees.
 
**Useful for eg. finding where to aim your antenna - no matter if it's drone, satellite, high altitude balloon.**

## Basic Usage

```python
from AltAzRange import AltAzimuthRange

observer = np.array([51.773931, 18.061959, 50])
target = np.array([[51.681562, 17.778988, 430000],
                  [52.30, 21.37, 190000]])
    
 calculator = AltAzimuthRange(observer, target)

 result = calculator.calculate()

[[2.45487200e+02 8.68612000e+01 4.30555143e+05]
 [7.41011000e+01 3.75527000e+01 3.04391381e+05]]
```
###  Old version
This is how you would call the tool in the original version
```python
from AltAzRange import AltAzimuthRange
AltAzimuthRange.default_observer(51.773931, 18.061959, 50)
satellite_1 = AltAzimuthRange()
high_alt_balloon = AltAzimuthRange()
satellite_1.target(51.681562, 17.778988, 43152)
high_alt_balloon.target(52.30, 21.37, 190000)

satellite_1.calculate()
{'azimuth': 245.49, 'elevation': 86.86, 'distance': 430555.14}

high_alt_balloon.calculate()
{'azimuth': 74.1, 'elevation': 37.55, 'distance': 304391.38}

```

