## Requirement

Personalization of the Camera Assets served to the Users. Camera Assets
/ Asset in this doc refers to EFFECT / FILTER / STICKER / MASK / GAME in
the camera open / content create flow

## Current Available data

- The videos created using the Camera Asses are updated with the Asset
  id in the content meta.

- Video count and other stats info for the respective Assets

## Possible Scenarios

- **User Data Basis** - By using the data of assets already used by a
  user

  - Engage users to use the same and create more videos.

  - Provide a similar set of Assets to promote users to use them as
    well.

- **Viral / Trending Basis**

  - Figuring out Most Popular / Trending Assets based on some available
    stats with the respective Asset (video_count)

  - Consider the last month's Trending Assets or in the interval of the
    last n days.

- **Time-Slot-Based Assets**

  - Giving prior orders to assets for a day. For example, showing Good
    morning and Good night Stickers during morning and night
    respectively

- **Event Basis**

  - Based on the event hashtag attached to an Asset, promote the same
    during the day of the event on the Top of the assets list served to
    the users (by considering the location of the user as well).

- **Following/Contact Basis**

  - Suggesting user with the list of assets used by his following users
    set

  - Suggesting user with the list of assets used by his Contact users

## Data to be Captured

- Capture the Asset (both asset id and the combination id) used by a
  User.

- Attach an Event hashtag/event_id with the Asset, to serve the
  respective asset during the event duration.

- User assets usage history data

  - If the user is not using the asset for some last N days what we
    provided as part of personalization, changing the order, OR
    suggesting some other assets.

## Required Client Changes

- The client needs to pass the Combination Id that is used for creating
  the video

## Timelines

**Phase1 -** The Event, Time based assets, and Viral ones

**Phase2 -** User Basis + Following/Contact Basis

## Technical / BE Implementation Details

### API Changes

- New **Feature Tab** addition with the current assets tabs (controlled
  in the Static config from Gateway) OR In the respective Asset tab
  serve based on the scenarios defined.

- **Event Basis**

  - Fetch the Current running event from available josh-events data.

  - Fetch the assets mapped to the currently running event

- **Time basis serving**

  - Include feed serving time with the asset metadata, which will be
    given priority over the event time

- **Viral/Trending**

  - Consider those assets which have more video_count, other, etc
