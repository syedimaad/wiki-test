The model is currently running on blip real time service, where it takes
10 equidistant frames from the video and video length as input. The
output of the model consists of embedding_features, raw_features and
enriched_features, where enriched features are a subset of raw_features.

### INPUT

- video_url (mp4)

  - 10 equidistant frames are extracted from the video

- video_length

### OUTPUT

- `embedding_features`

  - video2text_feat (256 dimensions)

  - content_metrics_feat (256 dimensions)

  - creator_id_feat (256 dimensions)

- `raw_features`

  - watch_hist

  - glamorlevel

  - taxonomy_elements_people_in_video

  - taxonomy_genre_target_type

  - taxonomy_genre_target_sub_type

  - taxonomy_genre_target_theme

  - taxonomy_video_quality_video_glamour_grade

  - taxonomy_video_quality_video_glamour_region

  - taxonomy_video_quality_video_glamour_sub_type

  - competitor_logo_name

  - skip_reason

  - taxonomy_video_quality_look_feel

  - moderation_levelp2

  - share_rate

  - download_rate

  - like_rate

- `enriched_features`

  - glamorlevel

  - taxonomy_video_quality_look_feel

  - taxonomy_video_quality_video_glamour_grade

  - share_rate

  - download_rate

  - like_rate

  - watch_hist

### GIT REPO LINK

- <https://gitlab.dailyhunt.in/josh-ai-labs/blip-azure-service/-/tree/prod/api/v2v>
