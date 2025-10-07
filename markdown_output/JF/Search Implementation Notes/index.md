- Probable fields to match search query :
  content_title,prepared_content_title, tags,conttent_category,
  category_search,genre.values\[\].
  audio_search_meta{artist\[\],user_name, name,
  label},user_profile{curated_tg, username,curated_genre\[\],
  curated_gender,}.

- for All existing data in content es, **We need to backpopulate the
  edgengram/ngram/refined_soundex/{Some other search type} for search**
  on required fields.

- The search results of Video will be included in All search result.

- The search query is unique on based on indexname, type and algo
  defined in **search_config.json**

  - There can be different type of video search like : Trending video
    search. All video search , or Something else. The ordering will be
    done post fetching the results of all search query defined for video
    and then sort on score(**Query and order should be configurable via
    search_config**).

- A new Search for video Search will be created which will extend
  in.dailyhunt.personalisation.josh.feedengine.search.entity.EntitySearchService

- There are three type of search is supported in current system

  - All content when query is empty. : `MathAllQueryTypeFunctionImpl`

  - when Query is present : `QueryFunctionTypeImpl`

  - Recommended : `RecommendationQueryFunctionTypeImpl`

  - Do we need any other type for Video ? or these three is enough ?

- Must filter must be applied over search result like : duplicate,
  legal_issue,active, `mustFilters` in Foryou tab can be good starting
  implementation.

- Boosting → ex: boost verified content and no boosting for Non
  verified.

[**Performance Optimization consideration:**]{.underline}

- All search is Sequential in terms of elastic queries. This need to be
  concurrent.

- Do we need to cache the results for some time ? In current Search
  Architecture, the results are cached for MatchAll only ? Video search
  can be slow, depend on \# of fields used in search query. Do we need
  the caching layer in btw. Because the results will change for query
  over time ? Does caching make sense for this a functional question.

- Some refactoring is also required in Search code for better
  maintenance.
