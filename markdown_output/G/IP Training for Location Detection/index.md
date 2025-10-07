17

# Aim

The document aim at capturing ways to improve the accuracy of IP-based
location detection by applying heuristics if possible

# Problem

Location service has the following hierarchy in detecting location GPS,
Mobile Tower ids, and IP-based resolution in respective order. Coverage
of each source varies

  ------------ -------------- --------------------
  **Source**   **Coverage**   **Accuracy**
  GPS          \~13%          \>95%
  CellId       \~20%          85-90%
  IP           \~67%          42% (10 km radius)
  ------------ -------------- --------------------

As seen in the above table coverage of IP is highest with the lowest
accuracy. Hence, improving IP-based location resolution accuracy can
help improve the overall accuracy of the Location Service.

# Why low accuracy via IP-based location resolution?

We are using MaxMind for IP-based location detection and as per official
public documents of Maxmind, it claims to have an accuracy of 42% for
India under a 10 km radius
[https://www.maxmind.com/en/geoip2-city-accuracy-comparison?country=&resolution=10&cellular=all](https://www.maxmind.com/en/geoip2-city-accuracy-comparison?country=&resolution=10&cellular=all){card-appearance="inline"}

# Impact due to low accuracy in Location Service

Location service is being used at multiple places like Ads, MDM, Rico,
DH publish, and detecting the wrong location leads to a bad user
experience having multiple side effects. Location targetting is one of
the most important targetting for Ads and brands aggressively monitor
it.

# How to overcome the low accuracy of MaxMind?

As we know that we get GPS information for about 13% of the requests and
GPS-based resolution has high accuracy in detecting location. We can
utilize this information to train IPs based on location detection via
GPS and Cell Tower Ids.

**Note**: We are aiming to improve IP-based location resolution based
training on IP information that we get from GPS requests since GPS-based
resolution is of high accuracy. Hence, it acts as our training dataset

## Public/External IPs

There can be many users behind a specific public/external IPs and if few
of them have GPS enabled then we might be able to confidently
predict/estimate the location of the other users under the same public
IP.

**Gotchas**:

This looks logically correct to be able to predict the location of users
with the same IP that we have got in the past along with GPS
Information. However, IP changes pretty frequently. **For Example**:

  --------------- --------------------------------------- --------------------- ------------
  **IP**          **Client ID**                           **Hour of the Day**   **City**
  152.57.64.10    1080353410                              22                    yavatmal
  152.57.64.10    1339211333                              22                    Wardha
  152.57.64.10    1450495316                              13                    thane
  152.57.64.10    dh.TkN1OW9AUR21qKzYrOGZiZ2VvWUl0QT09A   14                    Raigad
  152.57.64.100   964997208                               10                    Latur
  152.57.64.100   dh.K1hXWHUvb3kySXF1WlJiMS9AzbHlQQT09A   23                    Chandrapur
  --------------- --------------------------------------- --------------------- ------------

**Note**: Above data is extracted for **7-June-2022**, if you try to
check the location for the above IPs it might change as IP gets
allocated dynamically by ISPs

As we can learn from the above examples that the request from the same
IP can come from a different location even within the same day. This
raises the below questions:

1.  How frequently the IP changes?

2.  Can we even rely on IPs if they change so frequently?

## IP Ranges

Ip Range is a bundle of consecutive **public** IP addresses. The size of
the IP range is determined by the subnet mask, which limits the sizes
to:

- 4 Public IP Addresses (subnet /30)

- 8 Public IP Addresses (subnet /29)

- 16 Public IP Addresses (subnet /28)

- 32 Public IP Addresses (subnet /27)

- 64 Public IP Addresses (subnet /26)

For detailed information, one can refer to
[https://en.wikipedia.org/wiki/Subnetwork](https://en.wikipedia.org/wiki/Subnetwork){card-appearance="inline"}

# Data Analysis

As we know from above that there can be multiple users behind the same
IP thereby most probably having the same location and also ISPs allocate
bundles of the consecutive public IP address. Lets us utilize this
information to know how this fits with our data.

**What do we want to check?**

1.  We want to check if the city remains the same within the same IP
    range?

2.  Since IP range can vary from place to place. For example, in a big
    city where there are many internet users ISPs usually open up
    bundles with a higher range, and say for a village where there would
    be fewer users bundles that are allocated can be of lower size. We
    want to come up with an optimal IP range within which city is the
    same.

3.  Since IP changes pretty frequently and also changing IP with every
    request would also be very costly for ISPs, we would want to know
    the optimal time till with IP remains static and represents a
    user/city.

**Summary**: We can want to know the optimal IP range, the optimal time
range after which IP changes, and validate that within an IP-range city
remains the same.

**Query1**:

Below query returns avg `distinct_city_count` for a provided IP-Range
and time window.

with table_1 as (SELECT properties_ip, client_id, properties_latitude,
properties_longitude, properties_et_hour,
concat(split_part(properties_ip, \'.\', 1) , \"-\" ,
split_part(properties_ip, \'.\', 2) , \"-\" , split_part(properties_ip,
\'.\', 3)) as ip_range, cast(split_part(properties_ip, \'.\', 4) as int)
as level4, properties_city, cast(properties_epoch_time_millis /
cast(\'\${window}\' as int) as int) as time,
cast(cast(split_part(properties_ip, \'.\', 4) as int) /
cast(\'\${bit_range}\' as int) as int) as tmp from nrt_ads_events_data
WHERE properties_et_year = 2022 and properties_et_month = 06 and
properties_et_day in (7) and properties_has_request \> 0 and
properties_city is not null and properties_latitude != \'NA\' and
properties_longitude != \'NA\'), table_2 as (select ip_range, time, tmp,
count(\*) as total, count(distinct(properties_city)) as
distinct_city_count, count(distinct(client_id)) as num_users from
table_1 group by ip_range, time, tmp having
count(distinct(properties_city)) \> 0 order by ip_range, time, tmp)
select avg(distinct_city_count), max(distinct_city_count),
min(distinct_city_count), stddev(distinct_city_count), count(\*) from
table_2;

**Query2**:

Below query returns number of distinct cities with a given IP range and
given timeframe. This will help us gauge accuracy of the IP training.

with table_1 as (SELECT properties_ip, client_id, properties_latitude,
properties_longitude, properties_et_hour,
concat(split_part(properties_ip, \'.\', 1) , \"-\" ,
split_part(properties_ip, \'.\', 2) , \"-\" , split_part(properties_ip,
\'.\', 3)) as ip_range, cast(split_part(properties_ip, \'.\', 4) as int)
as level4, properties_city, \--properties_epoch_time_millis,
cast(properties_epoch_time_millis / cast(\'\${window}\' as int) as int)
as time, cast(cast(split_part(properties_ip, \'.\', 4) as int) /
cast(\'\${bit_range}\' as int) as int) as tmp from nrt_ads_events_data
WHERE properties_et_year = 2022 and properties_et_month = 06 and
properties_et_day in (7) and properties_has_request \> 0 and
properties_city is not null and properties_latitude != \'NA\' and
properties_longitude != \'NA\'), table_2 as (select ip_range,
\--properties_et_hour, time, tmp, count(\*) as total,
count(distinct(properties_city)) as distinct_city_count,
count(distinct(client_id)) as num_users from table_1 group by ip_range,
time, tmp having count(distinct(properties_city)) \> 0 order by
ip_range, time, tmp) select distinct_city_count,
avg(distinct_city_count), max(distinct_city_count),
min(distinct_city_count), stddev(distinct_city_count), count(\*) from
table_2 group by distinct_city_count order by distinct_city_count;

  ---------------- --------------- ----------------------- ------------------------------------------------
  **Time Range**   **Bit Range**   **Avg Distinct City**   **% with the same city in the provided range**
  5mins            4               1.090                   91.99%
  5mins            8               1.135                   88.59%
  **10mins**       **4**           **1.128**               **89.01%**
  10mins           8               1.194                   84.55%
  15mins           1               1.085                   92.21%
  15mins           2               1.110                   90.22%
  15mins           4               1.158                   86.80%
  15mins           8               1.243                   81.58%
  15mins           16              1.388                   74.70%
  15mins           32              1.620                   66.98%
  30 mins          1               1.114                   89.87%
  30 mins          2               1.155                   86.84%
  30 mins          4               1.231                   82.04%
  30 mins          8               1.362                   75.50%
  30 mins          16              1.575                   67.89%
  30 mins          32              1.899                   60.32%
  ---------------- --------------- ----------------------- ------------------------------------------------

More details of the iterations are captured here →
[https://docs.google.com/spreadsheets/d/1sibqnBu5LzYHMYVhN62u9DdB9SmzYHD08eTIEkN7S3o/edit#gid=0](https://docs.google.com/spreadsheets/d/1sibqnBu5LzYHMYVhN62u9DdB9SmzYHD08eTIEkN7S3o/edit#gid=0){card-appearance="inline"}

# Conclusion

From the above analysis, we can conclude that in order to train the
location based on IPs we will need to have a window of **10mins** and an
**IP range of 4 bit** to achieve an accuracy of \~90%.

Having an IP range of 4 bits means that if we get a GPS request with
single IP in the IP range we are 90% confident that other IPs in the IP
range have the same IP. **We expect to increase the accuracy to around
96% by applying heuristics for IP ranges within 2 cities. We have found
that when the IP range has 2 cities, out of the 2 cities one city is
almost always prominent.**
