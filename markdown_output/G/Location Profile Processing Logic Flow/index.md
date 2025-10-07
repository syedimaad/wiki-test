1.  Fetch an entry from Kafka

2.  if client id is empty

- increment client id empty counter

- return

3.  fetch entry from scyllaDB for that client id

4.  if `locUpdate`=1

- send entry to analytics Kafka and for scyllaDB batch write

- return

5.  if first event of the day

- send entry to analytics kafka and update for scyllaDB write

- return

6.  fetch mobile,GPS and IP params as well as hostAppId

7.  if all three are invalid

- increment counter for invalid params

- return

8.  if params have not changed for the user

- increment counter for already in cache

- return

9.  else

- add to cache for every param (key: `client_id`+`mcc`/`gps/ip`, value:
  params)

10. create json entry from scyllaDB entry to compare with location
    service entry

11. if scyllaDB empty

- increment entry scyllaDB counter

12. create location service URL param based on params from kafka entry
    (rounded off lat/long to 3 decimals)

13. cache the location service call based on URL

14. process the response and convert into JSON response to compare with
    kafka entry location JSON

15. fetch \`top_cities\` and add to entry to push into scyllaDB and
    analytics kafka //comment will address below this was some addition
    due to redis U key not having but UUP key having it

16. if check eligibility to be replaced

- set `to_be_replaced` to True and the new source

17. create a dictionary called processed entry and fill details

18. increment counter based on the source

19. if source is dfp

- clear dictionary and fill that user's `dfp_location`from scyllaDB

- use a cache to store dfp_location based on cityid,stateid and
  countryid

20. if source is IP and city in `hingoli`

- increment skipped centroid counter

- return

21. check if city and state has changed between kafka entry and old
    scyllaDB entry

- create entry for analytics location and push that to analytics kafka

22. pop out `previous_location` and add the old scyllaDB one //this key
    is not in scyllaDB

23. update last_updated timestamp with current time

24. add to batch for scyllaDB update

## Check Eligiblity to be replaced logic

new_entry: Entry from location service available_entry: Location entry
available in ScyllaDB scylla_entry: Complete entry available in
ScyllaDB 1. fetch new source and scyllaDB source 2. if precedence of new
source is higher than scyllaDB source 3. replace with dfp location if
new source is IP or LOCATION_IP_MODEL 4. else 5. check last updated of
scyllaDB with current and check config for
LOWER_PRECEDENCE_LOCATION_OVERRIDE_DAYS, 6. if the last updated is
higher than that make it eligible for replacement and do the same check
for dfp
