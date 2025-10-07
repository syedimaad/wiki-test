1.  take input params for locations.

2.  params list: ip, lat,long,mcc,mnc,lac,app_name

    1.  precedence

        1.  lat/long

        2.  mcc/mnc/lac

        3.  ip

    2.  for lat long direct resolution from cache

    3.  for mcc/mnc from cell centric data

    4.  for ip

        1.  mmdb

        2.  then lat long

Other points:

- How to take confidence on ip resolution?

- to chose from

  - 1st empty and then subsequent location response

  - high wait time for 1st call
