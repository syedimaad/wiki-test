**Background**

A new ad type is being introduced for JOSH videos, where ad consumers
will be offered with an option to purchase products similar to ones
being showcased in the video content. 

\

A list of products (related to a particular video) shall be procured
using an external service provider, and the Content ops team may
regulate the output using dashboard developed on Daedalus.

## New terminologies:

1.  Shoppable post

A shoppable post can be described as a post/content/video which has been
processed by content Ops team and is ready to be made live. Processing
shall typically involve defining segments, time offset for videos and
shortlisting products to be shown at a particular
offset.Publish/unpublish controls shall exist to save in-progress work
as draft

1.  Product Banner

A product banner will serve as a **group of shoppable posts**, and
allows for metadata specifications, which will apply on all posts linked
to it. Configurability includes:

- Custom color scheme 

- Custom trackers

\

It can also be used to pre-define certain filters which will
automatically apply to linked posts that shall be configured
**thereafter** (Ex: merchants such as amazon), hence restricting the
product list that needs to be checked for each shoppable post. *These
filters can be relaxed by content ops from the dashboard during the
configuration.*

\

A shoppable post can be a part of multiple product banners, and linkage
with at least one product banner will be required on creating a post.
Similarly, the product banner can be linked across multiple campaigns,
allowing it to be used as a context.

\

Conclusively, It can be used to create a basket of products which can
cater to specific business requirements, examples can be (but not
limited to). All amazon/flipkart products, all electronics by Amazon
etc. 

\

1.  Shoppable creative

From a campaign targeting perspective, a new creative type (Shoppable
creative) has been provisioned that can be mapped to a product banner,
allowing usage of all campaign level targeting features. The
configuration of product banners shall remain dynamic, i.e. any changes
to product banner metadata or linked posts will apply to all linked
creatives.

# Dashboard Screens

### Step 1: Shoppable Product banner

\

+---------------+--------------------+
| 1.  List view | 1.  Create options |
+---------------+--------------------+
|               |                    |
+---------------+--------------------+

\

### Step 2: Shoppable post creation

\

  ------------- ---------------------------- ----------------------------------
  1.List View   2.Create view: Define meta   3.Create View: Product selection
                                             
  ------------- ---------------------------- ----------------------------------

\

Other options under product selection view

\

  ----------------- --------------------
  Output Preview    Product Properties
                    
  ----------------- --------------------
