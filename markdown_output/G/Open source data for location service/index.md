We have different source for location informations.

1.  From the
    [http://data.gov](http://data.gov){card-appearance="inline"} we have
    a list of post offices along with their pincode but missing
    lat-long.

    1.  ***link*** **:**
        [https://docs.google.com/spreadsheets/d/1qU1zPQaINBs2Rse401BlIL9aFa67Ykwj4X1qSSGWSC8/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1qU1zPQaINBs2Rse401BlIL9aFa67Ykwj4X1qSSGWSC8/edit?usp=sharing){card-appearance="inline"}

2.  from bhuvan (ISRO) we have scrapped lat-long for post offices.

    1.  ***link***
        [https://docs.google.com/spreadsheets/d/1OQKwBB0MHp-eBiNyE5wfcTS4QwFXzxE6qJKQ7EIycIk/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1OQKwBB0MHp-eBiNyE5wfcTS4QwFXzxE6qJKQ7EIycIk/edit?usp=sharing){card-appearance="inline"}

3.  From DH- location service we have verified the data collected.

4.  From
    [https://www.latlong.net/Show-Latitude-Longitude.html](https://www.latlong.net/Show-Latitude-Longitude.html){card-appearance="inline"}
    and google map we have cross verified the mismatch data fromm
    ISRO-bhuvan and our location service

**Some conclusive data:**

[https://docs.google.com/spreadsheets/d/1nvbcIpHd47ZgqFwzIEZHy4Ml-XQyNynsW4fuCxPE3b0/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1nvbcIpHd47ZgqFwzIEZHy4Ml-XQyNynsW4fuCxPE3b0/edit?usp=sharing){card-appearance="inline"}

contains most of the concluded data

**Some Explored data points:**

  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------ --------------------------------------------------------
  **Link**                                                                                                                                                                                                                                 **Details**                                                                          **comments**
                                                                                                                                                                                                                                                                                                                                
  <https://data.gov.in/sites/default/files/all_india_PO_list_without_APS_offices_ver2_lat_long.csv>                                                                                                                                        154797 post offices with pincode but without lat long                                
  [https://bhuvan-app1.nrsc.gov.in/postal/#](https://bhuvan-app1.nrsc.gov.in/postal/#){card-appearance="inline"}                                                                                                                           135513 post offices with accurate lat long                                           This should be mapmyindia data. Validate terms of use.
  [https://docs.google.com/spreadsheets/d/1nvbcIpHd47ZgqFwzIEZHy4Ml-XQyNynsW4fuCxPE3b0/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1nvbcIpHd47ZgqFwzIEZHy4Ml-XQyNynsW4fuCxPE3b0/edit?usp=sharing){card-appearance="inline"}   compared data from existing location service, collected data from different source   
                                                                                                                                                                                                                                           5961 Post office (872 pincode)data whose lat long can not be collected from bhuvan   
                                                                                                                                                                                                                                                                                                                                
  [https://data.gov.in/catalog/locality-based-pincode#](https://data.gov.in/catalog/locality-based-pincode#){card-appearance="inline"}                                                                                                     906268 row for locality along with pincode                                           can be used later
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- ------------------------------------------------------------------------------------ --------------------------------------------------------

monofalserightVerticalfalsefalse154796CenterPie#8eb021,#d04437,#3572b0,#f6c3421649882728587_526falseLabelfalse3Percentagefalsetotal
POPoint (.)falsefalsetruevalidated po (bhuvan)‚mismatch of
PINCODE‚mismatch of city‚mismatch of statedd M yy365\|5\|8\|y w d h m\|y
w d h m

+----------------------------------------------------+-----------+
| **Header**                                         | **count** |
+----------------------------------------------------+-----------+
| total PO (data.gov)                                | 154796    |
+----------------------------------------------------+-----------+
| validated post office with lat long (bhuvan)       | 135513    |
+----------------------------------------------------+-----------+
| **mismatch of Pincode for postoffice(lat long )**  | 44167     |
|                                                    |           |
| 1.  for each PO bhuvan has a lat long              |           |
|                                                    |           |
| 2\. that latlong has a pincode in DH               |           |
|                                                    |           |
| compared PO                                        |           |
|                                                    |           |
| (bhuvan lat-long (n:1 pincode), lat-long DH (n:1)) |           |
+----------------------------------------------------+-----------+
| null in DH (pincode)                               | 2313      |
+----------------------------------------------------+-----------+
| **mismatch of city**                               | 15930     |
+----------------------------------------------------+-----------+
| **mismatch of state**                              | 1456      |
+----------------------------------------------------+-----------+

out of 1456, 836 rows are boundary of UP where dh location service
resolve area of UP and pincode of neighbour state.

Total DH pincode : 18469

total bhuvan pinocde : 18228

total [http://data.gov](http://data.gov){card-appearance="inline"}
pincode : 19100
