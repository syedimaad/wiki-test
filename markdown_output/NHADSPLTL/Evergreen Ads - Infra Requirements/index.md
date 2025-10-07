# Overview

The purpose of this document is to collate all the Infrastructure
requirements for the Evergreen Ads flow.

# Workflow

1.  On the notification delivery, the DH App will make an API call to
    fetch Evergreen Ads.

2.  The Evergreen Ads are cached beforehand and are common for all the
    users and are eligible to be rendered in the appropriate zones
    across the App.

3.  We have 2 options for the cache -

    1.  Akamai CDN:

        1.  Use Akamai Edge Workers to do minor processing.

        2.  Use Akamai Storage to cache the static Evergreen Ad
            response.

        3.  Use Akamai CDN to cache the response.

    2.  GCP:

        1.  Use Google Cloud Function to do minor processing.

        2.  Use Google Object Storage to cache the static Evergreen Ad
            response.

        3.  Use Akamai CDN to cache the response.

4.  Every `x` minutes once, we will have an offline job that refreshes
    the cached response, if needed, and also calls Akamai API to
    invalidate the cache.

# Why move the whole domain to Akamai?
