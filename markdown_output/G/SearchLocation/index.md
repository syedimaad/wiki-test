This controller is mapped for three API:

1.  `GET /global/v1/location/search`

2.  `GET /v2/location`

3.  `GET /v1/location`

Expected Query Params & related services:

> **lat/long =\> GetGPSResponse**
>
> By Using Lat, Long try to find the location first check inmem, if not
> then ask pelias for same. Further Translate the location from pelias
> to DH vocabulary and then store same in mem before responding.

> **Cellid =\> GetCellId Response**
>
> By Using cellid get the location detail already stored in memory from
> learned\* data(sql) of cell tower.

> **IP =\> GetIpResponse**
>
> First check the IP in redis (TRAINED_IP_MODEL) and then in mmdb. Also
> fetch the isp details from mmdb for given IP.

FLOW DIAGRAM:
<https://drive.google.com/file/d/1I_jOKT4aZgF7N42CqmOLO12adGFljvrD/view?usp=sharing>
