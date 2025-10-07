There are certain business requirements that require detecting the
location of the users and the accuracy of the location detection can
have a direct huge impact on the end-user experience. For Example, at
Verse, we have a division called Dailyhunt which is India's largest news
aggregator platform. One of the primary features of the app is to serve
news related to the nearby location or news from the city of the users.
Many users want to consume news from around the world but they also
don't want to miss out on news from nearby areas. In order to cater to
this requirement of the users knowing the location of the user is
extremely important.

**Getting the location from the user directly**

GPS is one of the most accurate ways to get the location of the users.
We at Dailyhunt have the functionality to ask users to share their
location so that we could serve them relevant news. Thereby improving
the stickiness of the users on the app. However, most of the users don't
end up sharing the location. After looking at the data we found out that
almost 25% of the overall request had GPS information and for the rest
of the requests we don't have any direct information about the user\'s
location. Knowing the location of the user is really important for the
app keeping stickiness of the users in mind. In order to know the
location of the remaining 75% of the requests only information that we
have is IP. We were using [Maxmind](https://www.maxmind.com/en/home)
which is a market leader in detecting location based on IP.

Maxmind, publically claims to have an accuracy of 56% for Cellular and
Broadband IPs within a range of 50 Km. Maxmind Accuracy
[https://www.maxmind.com/en/geoip2-city-accuracy-comparison](https://www.maxmind.com/en/geoip2-city-accuracy-comparison){card-appearance="inline"}

This low accuracy of Maxmind is not acceptable for the quality of the
experience we want to provide to our users. This problem was surfaced by
our users as well multiple times.

**How do we address the problem of low accuracy in our Location
Service?**

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

# Solution
