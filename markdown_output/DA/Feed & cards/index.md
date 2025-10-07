# KT videos 

1.  2022 cards fields and filtering
    [https://drive.google.com/file/d/1KvtaDG8Y2yY-OWPmYjoCh4bF3XFNc3U5/view](https://drive.google.com/file/d/1KvtaDG8Y2yY-OWPmYjoCh4bF3XFNc3U5/view){card-appearance="inline"}
     

# Showing timeStamp

For feed-card, upgrade/config returns `oldestListDisplayTimeGap `(it is
in sec); if recommendationTime(or publishTime as fallback) is older than
this gap, timeStamp will not be shown in the card.

For details, publishTime is used. If not null, it is shown. No
additional condition.

Ref:
com.newshunt.appview.common.ui.helper.CardsBindUtils.Companion#getDisplayTimeTextAsStoryCard(com.newshunt.dataentity.common.asset.CommonAsset)

# Places where filtering happens

1.  CardDeserializer .transf (FilteroutUnknownCards)

2.  FetchCardListFromUrlUsecase

3.  itemsMatching 

4.  ReadCardsUsecase

    \- If deserialization fails, typeConverter with set it to invalid-ID
    and that card will be ignored by this Usecase

5.  FetchCacheUsecase

6.  CardsAdapter

7.  FetchDao.fillLocalColdStartChildrenAndFilterBlocks

# Present in BE response but not showing 

1.  null or unknown format/subformat/uitype

2.  is an empty collection

3.  is from a blocked source 

4.  is disliked 

5.  is deduped (already present in the same feed, could be nested in a
    collection; `DedupUtil` )

6.  unsupported format for xpresso

7.  unsupported player type for xpresso

8.  deserializing from DB failed

9.  url of the feedpageview of CF2 is not matching the url of fetch_data
    row

10. location in fetch_info is different from CF2 (or any other param
    which will make it not find the correct fetch_id)
