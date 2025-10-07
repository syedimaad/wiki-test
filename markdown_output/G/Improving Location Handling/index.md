  ----------------------- ----------------------------------------------
  **Document Status**     NOT STARTED / IN-PROGRESSYellow / READYGreen
  **Product Owners**      @ product owners
  **Product Designers**   @ product designers
  ----------------------- ----------------------------------------------

##  Executive Summary

Location is currently resolved in 4 ways depending on the availability
of data. Problems have been observed in accuracy due to location
availability in various systems. Additionally, the confidence in
location is not relayed to the systems using the location service.

This document outlines initiatives to improve the accuracy and
operational maintainability of the location service while providing
confidence indication.

17true

##  Objective

Towards the overall goal of reducing user/advertiser reports on
mismatched locations.

+----------------------------------+----------------------------------+
| **Goal**                         | **Action**                       |
+----------------------------------+----------------------------------+
| Improve transparency of location | - All responses relay the        |
| confidence                       |   expected accuracy and          |
|                                  |   resolution method              |
+----------------------------------+----------------------------------+
| Match all users to a location    | - Ensure location ID in every    |
| entity                           |   response                       |
+----------------------------------+----------------------------------+
| Increase the share of high       | - Implemented coarse location    |
| confidence matches               |   stage                          |
|                                  |                                  |
|                                  | - Implemented trained IP stage   |
+----------------------------------+----------------------------------+
| Improve maintainability of the   | - Standardized stable IDs for    |
| location service and data        |   location entities              |
| updates                          |                                  |
|                                  | - Low effort data updates        |
|                                  |                                  |
|                                  | - Service for current location   |
|                                  |   hierarchy discovery            |
+----------------------------------+----------------------------------+

##  Context

Location resolution summary

  ------------------------ --------------------------------------------------------------------------- ------------------------- -------------------------------------------------------------
  **Technique**            **User Data**                                                               **Reference Data**        **Process**
  Fine GPS                 Fine permission from user and GPS on.                                       Geocoder                  (longitude, latitude) → reverse geocoding → location entity
  Cell ID                  Fine location permission from user and GPS off.                             Trained data + Geocoder   Cellid → (longitude, latitude) → \<Same as gps\>
  DFP                      No fine location permission from the user. Have shown DFP/Adx ads before.   DFP                       ClientId → location entity
  IP                       None of the above                                                           Maxmind + Geocoder        IP → MaxMind → (longitude, latitude) → \<Same as GPS\>
  Proposed: Coarse GPS??   Coarse location permission from the user. GPS can be off.                   Geocoder                  \<Same as GPS\>
  Proposed: Trained IP     No                                                                          Trained data + Geocoder   IP → trained data → location id
  ------------------------ --------------------------------------------------------------------------- ------------------------- -------------------------------------------------------------

##  Functional Specifications

### Transparent Accuracy

The system will report the accuracy based on

1.  Method of location resolution

2.  Time elapsed since the determination of the location

3.  The granularity of the resolved entity (in sq KM)

4.  Parent entities of the resolved location entity

#### Method of location resolution and accuracy score

The following accuracy scores will be used for the method of location
resolution:

1.  Fine device location - 0.9

2.  \<New\> Coarse device location - 0.8

3.  Cell tower location - 0.7

4.  \<New\> Trained high confidence IP location - 0.6

5.  Ad network location - 0.5

6.  IP db location - 0.4

7.  \<New\> CDN location - 0.3

8.  \<New\> State / region from network/sim - 0.2

9.  \<New\> Country from network - 0.1

#### Time elapsed since determination

We should preserve and return the resolution time and resolved location
(if different) of 1-5. We should also report the timestamp of the
reference data refresh for each of the methods above.

#### The granularity of resolved entity

The size of the resolved entity in Sq KM can be attempted if available.
To start with the type of resolved entity should be returned (locality,
postcode, city, county, state, region, country, etc.)

### Entities in Response

#### Entity IDs

Return the id of the matched location

#### Parent entities

For cases where the resolution is more granular than needed by the
calling service, return all the parent entities of the resolved location
entity in an array.

#### Request for expanding

Return the identifiers for all location entities, with an optional
parameter to return the expanded data about self and parent entities.

1.  Expand levels request parameter

    1.  null =\> self

    2.  0 → none

    3.  1 → self

    4.  n \> 1 → self + n-1 containing entities in hierarchy

### New location resolution types

Introduce new location resolutions where they can reduce the unresolved
or low-accuracy resolved user locations.

The following accuracy values will be used for the method of location
resolution:

1.  Fine device location - 0.9

2.  \<New\> Coarse device location - 0.8

3.  Cell tower location - 0.7

4.  \<New\> Trained high confidence IP location - 0.6

5.  Ad network location - 0.5

6.  IP db location - 0.4

7.  \<New\> CDN location - 0.3

8.  \<New\> State / region from network/sim - 0.2

9.  \<New\> Country from network - 0.1

Even though some of these don't exist yet, this lists the initial values
we can use to make decisions about which location resolution is
superior.

#### Coarse location-based

If we are able to get more device locations due to coarse locations, we
should introduce that level.

#### Trained IP

Lookup the location based on high confidence training for IP-location
mapping

#### CDN POP based location

This will require another path that goes via the CDN for location
resolution. Determine the priority after seeing what all

#### Network / SIM-based location

Lookup the location based on the network / SIM in the device

### Stable location identities

The identities of the location should stay stable across data updates.
Two potential stable identities can be explored to reduce the
maintenance overheads. WOF and Genomes. Maxmind returns geonames and is
our final fallback database. Pelias uses WOF and is our reverse
geocoding software. Need to explore operationally which will be the
least effort.

### Updating the reference data

#### Geocoding

1.  Run the Pelias updaters every night

2.  Subselect the datasets that are sufficient for us

3.  Remove disputed entities using LOC and LAC as borders in the data or
    in the service

4.  Keep the reference hierarchy service in sync with Pelias updaters

#### Cell ID

1.  Move to a dynamic data pipeline that keeps updating throughout the
    day

2.  Go directly from cellid to location id

Trained IP location

1.  Dynamic runtime/pipeline updation of IP database

2.  Sorted KV store? Rocks DB?

#### IP-location

1.  Move to a dynamic data pipeline that keeps updating throughout the
    day

2.  Go directly from IP to location id

#### Maxmind

1.  Use the updation scripts for their DB from the Maxmind GitHub

2.  Consider using the MaxMind library instead of importing it into our
    database. Alternatively, see if a structure similar to that used for
    the trained location can be better.

3.  Keep an iprange → entity id (WOF ID) mapping instead of matching the
    lat/long and looking up

## Error Handling

TODO: Spec the errors reported by the service here.

##  Open Questions

  ----------------------------------------------------------- ----------------------------------------------------------------------- -----------------------
  **Question**                                                **Answer**                                                              **Date Answered**
  e.g., How might we make users more aware of this feature?   e.g., We\'ll announce the feature with a blog post and a presentation   Type // to add a date
  ----------------------------------------------------------- ----------------------------------------------------------------------- -----------------------

##  Out of Scope

List the features discussed which are out of scope or might be revisited
in a later release.

## Reference Materials

Add links to research and other key documents here.

## Additional Notes

Add additional notes or comments, if any.

##  Figma

Type /image to add mockups, diagrams, and screenshots related to the
requirements.

## Instrumentation
