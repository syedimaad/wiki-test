### Content System Tasks

1.  Creative Ingestion

    1.  Meta

    2.  Creative

    3.  Product

2.  Upsert handling on Crawling

### Decisions

1.  Store Image and Image collections creatives in Image ES with ce_type
    as shoppable

2.  Store video creatives in Content/Image ES with ce_type as shoppable

3.  Chose the vendor_id as the user uuid

    1.  **How to get the vendor meta?**

    2.  **What is the user type to be set ?**

4.  Add the below schema to such content/images

    1.  product_meta : Nested Object

        1.  category

        2.  **price**

        3.  **deal**

        4.  **availability**

        5.  misc

    2.  product_cta : Format to be decided

    3.  product_tracker

    4.  Use existing control_config for social interactions

        1.  comment

        2.  share

        3.  download

        4.  like

### Integration Flow

1.  Ads BE to crawl the catalogs periodically

2.  Push the product details to a SQS queue

3.  Lambda to consume messages from queue

4.  Write to cassandra table → product

5.  Lambda to check the parameters and evaluate for each vendor + "\_" +
    id. Possible outcomes

    1.  New

        1.  Insert into Product table with primary key as vendor +
            "\_" + id.

        2.  Call creative service to generate the creative with callback
            url

        3.  Update the product table status → CREATIVE_REQUESTED

        4.  Creative Service to Call the Josh BE API once creative
            generation is successful

        5.  Create the content/image based on the callback

        6.  Send the creative for transcoding

        7.  Update the meta on Josh BE once success

    2.  Meta Update

        1.  Update the product table

        2.  Update the respective meta on content/image ES

    3.  Creative and Meta Update

        1.  Call creative service to Generate new creative with callback
            url

        2.  Creative service to generate new creative and call the
            callback API

        3.  Josh BE to send the new creative for transcoding

        4.  Update the respective meta on content/image ES

    4.  No Change

### API

1.  Product Sync SQS payload

Payload : ArrayList\<ProductList\> (max 1GB) SQS Queue ARN

2\. Creative Creation Callback API

Path : /apij/creative/callback Method : POST Content-Type:
multipart/form-data Payload : details : { product_primary_id: \'\',
content_type: \'IMAGE/VIDEO\', }, file : \<CreativeFile\>

### Product POJO

product_primary_id -\> vendor + \"\_\" + id -\> composite id -\> Josh BE
to store at processing id -\> vendor gernerated id vendor -\> text
age_group app_link availability brand category color condition
created_on currency_code description gender image_link item_group_id
material mobile_link origin_country pattern price product_id -\> ads
system generated uuid product_link product_type sale_price
sale_price_effective_date size status sub_category sub_sub_category
title updated_on
