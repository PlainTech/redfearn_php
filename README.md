# redfearn_php
**Redfearn's Formula** allows conversions between latitude & longitude coordinates and Australian grid coordinate systems
such as GDA94 and AGD84. The calculations performed in this module are based on the
[Geocentric Datum of Australia - Technical Manual Version 2.3 Amendment 1](www.icsm.gov.au/gda/gdatm/gdav2.3.pdf).

A web based application of this tool is available at [plaintech.net.au](https://plaintech.net.au/redfearn).

A python version of this code is available on [pypi](https://pypi.python.org/pypi/redfearn) with source code available on [here](https://bitbucket.org/plaintech/redfearn/overview).

Tested in Python 2.7+ and Python 3.3+

Example Usage:

```php

  $latitude_dms = DecimalDegreestoDMS(-37.652821141666664)
  // result: ("Degrees" => -37, "Minutes" => 39, "Seconds" => 10.15611)

  $longitude_dms = DecimalDegreestoDMS(143.9264955361111)
  // result: ("Degrees" => 143, "Minutes" => 55, "Seconds" => 35.38393)

  $latitude_dd = DMStoDecimalDegrees($latitude_dms["Degrees"], $latitude_dms["Minutes"], $latitude_dms["Seconds"])
  # result: -37.652821141666664

  $longitude_dd = DMStoDecimalDegrees($longitude_dd["Degrees"], $longitude_dd["Minutes"], $longitude_dd["Seconds"])
  # result: 143.9264955361111

  $grid_coordinates = redfearnLLtoGrid($latitude_dd, $longitude_dd, "GDA-MGA")
  // result:   (
  //                "Easting" = > 758173.798005752,
  //                "Northing" = > 5828674.339728091,
  //                "Zone" = > 54,
  //                "GridConvergence" = > 1.7887112307424733,
  //                "PointScale" = > 1.0004210730644858
  //            )

  $easting = 758173.798
  $northing = 5828674.340
  $zone = 54

  $lat_long = redfearnGridtoLL($easting, $northing, $zone, "GDA-MGA")
    // result:   )
    //                "Latitude" = > -37.65282114013244,
    //                "Longitude" = > 143.92649553599782,
    //                "PointScale" = > 1.0004210730517988,
    //                "GridConvergence" = > 1.7887112306027275
    //            )
