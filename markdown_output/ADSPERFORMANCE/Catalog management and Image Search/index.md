# Aim

The document aims to capture the universal schema for Shoppable, which
is agnostic to sellers.

Requests you to please add schema for the catalog that we will be
manage/curate

Flow of the catalog ingestion

1.  Vendor specific format ingestion

2.  Mapping & Conversion to Dailyhunt specific accepted format

3.  Saved the converted format

4.  Code diagram:
    <https://app.diagrams.net/#G1yPFR5ovKJG3jozUPaFtu6UM8CcooYCzu>

:warning:atlassian-warning#F4F5F7

Depending on vendor we need to decide on full dump or delta change
(applicable for Feed API)

Accepted values for a catalog{ \"id\":
\"4e79c3a9-8750-4191-abc3-1ce9e8ce3613\", \"creator_id\": \"\",
\"content_url\": \"\", \"active\": \<bool\>, \"created_on\": \"\",
\"catalog_products\": { \"dh_product_id_1165051\": { \"timestamps\": \[
3, 16, 18, 22, 26, 30 \], \"match_score\": 0.3321 } }
\"match_updated_on\": \"\" }Accepted values for a productjson{ \"id\":
\"\", // sku_id preferrable (general should contain value which uniquely
identifieds the item) \"title\":\"Blue Cotton T-Shirt\", // name of the
product \"description\":\"\", // description of the product
\"avalability\":\"\", // in stock, out of stock, available for order
\"condition\": \"\", // new, refurbished, used etc \"price\": 9.99, //
value (Note) \"product_link\": \"\", // url to the product on the vendor
website \"image_link\": \"\", // url to the product image \"brand\":
\"\", // brand of the product like Nike etc \"size\": \"\", // depending
of product type (example apparel will have different size abbreviation
than shoes) \"product_type\":\"\", //
https://www.google.com/basepages/producttype/taxonomy-with-ids.en-US.txt
\"currency_code\": \"\", // INR/USD \"sale_price\": 1.00, // sale price
for the product
\"sale_price_effective_date\":\"YYYY-MM-DDT23:59+00:00/YYYY-MM-DDT23:59+00:00\",
// span for which the product needs to be sold \"item_group_id\":\"\",
// to support variant based logic \"status\":\"\", // active or archived
in terms of visibility to client \"color\":\"\", // name of the color
\"gender\":\"\", // male, female, unisex \"age_group\":\"\", // adult,
all ages, teen, kids, toddler, infant, newborn \"material\":\"\", //
material of the product \"pattern\":\"\", // Flannel, Gingham, Polka
dots, stripes \"video\":{ \"url\":\"\", \"tags\":\[\"\"\] },
\"mobile_link\":\"\", // mobile url webpage, \"applink\":{}, // app
links \"origin_country\":\"\", \"category\": \"\", \"sub_category\":
\"\", \"sub_sub_category\": \"\", \"vendor\": \"\", \"created_on\":
ISODate(\"2022-06-15T13:25:01.058Z\"), \"updated_on\":
ISODate(\"2022-06-15T13:25:01.058Z\") }Database specifications

1.  Collections (products)

2.  Indexes(id and vendor, created_on, updated_on)

Token generation steps for using with Postman

1.  bashappName=\"verse-inc-dev\" userName=\"verse-inc-dev\"
    timestamp=\`date +%s\` secret=\"\<\<secret key\>\>\" // secret key
    given by amazon team token=\`echo -n
    \"\${secret}\${userName}\${appName}\${timestamp}\" \| openssl dgst
    -sha512 -binary \| xxd -p -c 256\`
    URL=\"application=\${appName}&username=\${userName}&ts=\${timestamp}&authtoken=\${token}\"
    echo \"\${URL}\"

    Add this script to a shell file and run it to generate token string.
    This will come in handy when using postman.

2.  Import the postman collection and make the changes as below.

    1.  In API 1, query params (excluding numObjects and videoFormat)
        replace others with the string received in Step 1. If
        successful, capture **url** (s3 signed url of bucket) and
        **content** (identifier for file to be used for checking file
        upload status).

    2.  In API 2, The url received above is the request URL to be used
        for uploading content video file. It will take sometime to
        upload.

    3.  In API 3, under param section replace the videoId with content
        from step 1, ts as received in Step 1 result and auth token. The
        processing taken sometime on amazon front to process and
        recommend.

    4.  In API 4, replace params as similar to Step 3 and provide asin
        number received in Step 3 to get the meta details of the
        product.

Phase 2.1

- Update flow NHADSPLTL-4960e55da6ef-1840-3475-9293-310ba48d502dSystem
  JIRA

- Deletion flow NHADSPLTL-4961e55da6ef-1840-3475-9293-310ba48d502dSystem
  JIRA

- Source file name as field to state the source of entry
  NHADSPLTL-4962e55da6ef-1840-3475-9293-310ba48d502dSystem JIRA

- Monitoring NHADSPLTL-4704e55da6ef-1840-3475-9293-310ba48d502dSystem
  JIRA

Error reporting specification \[Pending\]

Possible error reporting format: \[To be discussed for future proof\]

json{ \"file_error\": \"any one of file name issue, unsupported file
type, file parsing issue\", \"data_errors\": \[{ \"err_msg\":\"any one
of incorrect data format/unknown discussed enums\", \"err_code\": \"add
error code for easy checking\", \"data\": {} } \] }
