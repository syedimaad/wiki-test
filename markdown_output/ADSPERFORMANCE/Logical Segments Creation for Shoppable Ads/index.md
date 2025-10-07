**Current Production Algorithm**

nonesegments = {} for segment in \[uniform-length segments starting from
timestamp 0\]: products = {set of all products that have at least one
timestamp in this segment} products = filter(products) \# Filters
applied: \# 1. merchant filters \# 2. categories filters \# 3.
in_stock=True \# 4. match_score \> threshold \# Pick top K products
sort(products) by match_score in descending order products =
products\[:k\] \# Keep only the fields to be returned products =
\[transform(product) for product in products\] segments\[segment\] =
products return segments

**Flaws with the current logic**

1.  Duplication: If a product has timestamps spanning multiple segments
    and it has a high match_score, then the same product will be
    selected for all these segments.

2.  Segments are fixed, that is, it does not allow any flexibility in
    selecting the \[start, end\] of the segments.

**Initial Planning for a better solution**

SEGMENT_LENGTH = 3 secs while True: if no product left or video covered
(all secs have a segment and all segments have 5 products) : break pick
top product from remaining products by match score, while not flag from
product_timestamps pick a window SEGMENT_LENGTH secs - at lowest
product_timestamp (first appearance) - central to the overall products.
(mid) OR - higherst timestamp (last appearance) - Allow for
discontinuity in window ? - Ask accio if they can share the
best_match_score timestamp. if valid(window): if window overlap with
existing segment i.e start+SEGMENT_LENGTH: if existing segment not full:
append product to existing segment flag = True else:
segments.append(window_start, \[product\]) flag = True slide this window
to next_timestamp. remove this product from list.

**Using a python script for experimenting with variations of the above
algorithm**

The script is located at the following location on learning-n3:

`/mnt/vol1/dh-ads/meet/shoppable_ads/segment_products.py`

Variations in script from the above algorithm:

1.  Always pick first / last non-overlapping window (with/without 100%
    coverage), and fallback to an overlapping window only if there is
    none available.

2.  Window-score based algorithms that sort all possible windows by the
    following metrics:

    1.  Coverage score (fraction of timestamps of the segment that the
        product appears in)

    2.  Continuity score (higher if there are less gaps in product
        timestamps within the segment)

    3.  Centrality score (inversely proportional to the distance between
        window and the centre of product timestamps)

    4.  Priority score (prefers picking a segment that has less number
        of products, so this product appears earlier in the list of
        alternatives)

Five videos with significant number of products were picked and used as
data for the variants. The results of the above script are added to the
following sheet:

[https://docs.google.com/spreadsheets/d/1NfopY7S8n8JzCAFNJAcaE2xV0MW7U4bKK4kO5-32c4Q/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1NfopY7S8n8JzCAFNJAcaE2xV0MW7U4bKK4kO5-32c4Q/edit?usp=sharing){card-appearance="block"}

It also contains a summary of the observations made from the result.
