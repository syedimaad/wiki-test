## Video Transcoding

Current Process

- H265 Encoded video of format M3U8 containing ts files

- H264 Encoded video of format M3U8 containing ts files

- H264 Encoded video of format MP4

Changes Made

- New Fragmented MP4 video generated having H265 Encoding (New addition)

- H265 Encoded video of format M3U8 containing ts files where these ts
  files are generated using the Fragmented MP4

## API Changes

### Feed

- Old Clients

  - Android - Serve [ucq_url]{.underline} with H265 M3U8

  - IOS - Serve [ucq_url]{.underline} with H264 M3U8 ( ? Do we need to
    serve M3U8 with FMP4 ?)

- New Clients

  - Android - New field [fmp4_url]{.underline} having FMP4 with H265
    Encoded video.

  - IOS - New field [fmp4_url]{.underline} having FMP4 with H265 Encoded
    video.

### API (Share Path)

- Old Clients

  - Android - Serve [ucq_url]{.underline} with H265 M3U8

  - IOS - Serve [ucq_url]{.underline} with H264 M3U8 ( ? Do we need to
    serve M3U8 with FMP4 ?)

- New Clients

  - Android - New field [fmp4_url]{.underline} having FMP4 with H265
    Encoded video.

  - IOS - New field [fmp4_url]{.underline} having FMP4 with H265 Encoded
    video.

### H265 Supported Header(API + Feed)

- Supported / Request Header Not present: Serve fmp4_url

- Not Supported: Don't send fmp4_url in response, change ucq_url to
  serve H264 M3U8 video

### Download Url

No Change in Download Url (wmj) we will be retaining the same H264 MP4
video.

## Android / IOS client Changes

- Use fmp4_url for playing the video

- Fallback to ucq_url if fmp4_url is not present

- Sending [h265_supported]{.underline} request header in all the API
  calls with true / false as value.

- For MP4 format videos prefetch is supported
