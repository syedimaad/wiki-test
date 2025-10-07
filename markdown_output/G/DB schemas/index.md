+---------------------+----------------+-------------------------------+
| **col_name**        | **value type** | **details**                   |
+---------------------+----------------+-------------------------------+
| dh_id               | int            | countrycode\_                 |
|                     |                |                               |
|                     |                | for state:                    |
|                     |                | countrycode_locationID.       |
|                     |                | `"AE_1376826403",`            |
|                     |                |                               |
|                     |                | for city:                     |
|                     |                | countrycode_locationID        |
|                     |                | "`AE_1234546`"                |
+---------------------+----------------+-------------------------------+
| full_name           | string         |                               |
+---------------------+----------------+-------------------------------+
| location_type       | string         | country, region, county,      |
|                     |                | locality, post office,        |
|                     |                | neighbourhood                 |
+---------------------+----------------+-------------------------------+
| country_code        |                |                               |
+---------------------+----------------+-------------------------------+
| other_language_name | json string    |                               |
+---------------------+----------------+-------------------------------+
| source_name         | string         | bhuvan, whosonfirst           |
+---------------------+----------------+-------------------------------+
| source_id           | string         |                               |
+---------------------+----------------+-------------------------------+
| created_at          | timestamp      |                               |
+---------------------+----------------+-------------------------------+
| last_updated_at     | timestamp      |                               |
+---------------------+----------------+-------------------------------+
|                     |                |                               |
+---------------------+----------------+-------------------------------+

dh_id **will have many** geo_key

Table: mappings

for a given DH ID, it will map all its parent location entities

  -------------- -- --
                    
  dh_id             
  path_to_root      
                    
  -------------- -- --

**table 1 : location_geojson**

  -------------- ---------------- -----------------
  **col_name**   **value type**   **details**
  geo_key                         gps_lat_long
  lat                             
  long                            
  dh_id                           `AE_1376826403`
  updated_at                      
  -------------- ---------------- -----------------

# Approach 2:

**Country**

  ------------ ----------- ------------
  **column**   **type**    
  id           string      
  name         string      
  created_at   timestamp   (optional)
  updated_at   timestamp   (optional)
  ------------ ----------- ------------

**Region**

  ------------ ----------- ------------
  **column**   **type**    
  id           string      
  name         string      
  created_at   timestamp   (optional)
  updated_at   timestamp   (optional)
  ------------ ----------- ------------

**County**

  ------------ ----------- ------------
  **column**   **type**    
  id           string      
  name         string      
  created_at   timestamp   (optional)
  updated_at   timestamp   (optional)
  ------------ ----------- ------------

**Locality**

  --------------------- ------------ ------------
  **column**            **type**     
  id                    string       
  name                  string       
  pincode/postal code   string       
  created_at            timestamp    (optional)
  updated_at            created_at   (optional)
  --------------------- ------------ ------------

**gps_mapping**

  -------------- ----------- --
  **column**     **type**    
  gps_lat_long   string      
  country_id     string      
  region_id      string      
  county_id      string      
  locality_id    string      
  created_at     timestamp   
  updated_at     timestamp   
  -------------- ----------- --

**cellid_mapping**

  ---------------- ----------- --------------------
  **column**       **type**    
  id               string      C_1234_123_123_123
  gps_mapping_id   string      gps_12.34_12.34
  created_at       timestamp   
  updated_at       timestamp   
  ---------------- ----------- --------------------
