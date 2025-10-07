# Live TV Timestamp

- Timestamp should not be shown on Live TV detail page

- Need to validate if not sending timestamp from BE solves for old and
  new clients

# Loading screen for standalone Xpresso videos 

**Current Confugiration :**

1.  A blank black screen is shown while the video is loading

2.  The Title and Video come up parallelly.

3.  In cases where there is buffering the video stays on the last shown
    frame without the loading icon

**Why the change is required:**

1.  The proposed change will the bring Video Experience of Xpresso
    similar to that what is currently on LR.

2.  The Xperience will be in line with apps that have similar content
    feed like Instagram.

3.  Many users also feel the current black loading screen time is on the
    higher side.

**Proposed Changes :**

During the loading of a video, we have the below 3 items to be shown to
the user

- Video title

- Video thumbnail image

- Video

The ideal sequence based on the availability of the above should be

1.  The Title of the video loads ~~first on the black shimmering
    screen~~ loads with the thumbnail or the video

2.  Once the video thumbnail is available, we show the video title,
    thumbnail, and loader icon with progress bar and mute icon hidden.

3.  In video load error case - Show thumbnail and remove the loader

4.  Once the video is available, then we replace the thumbnail with the
    video and continue showing the video

5.  In case there is buffering in the middle of the video play, we show
    the loading icon.

# Video details full screen icon change

## Android

Changes are already done

## iOS

Full screen icon link:

https://www.figma.com/file/xrea3pXhacYYCaKpF1XRom/Dev-Design?node-id=3%3A8&t=jZhGvLNhmZC12zg6-4

Icon to shrink the screen back:

https://www.figma.com/file/xrea3pXhacYYCaKpF1XRom/Dev-Design?node-id=3%3A8&t=jZhGvLNhmZC12zg6-4
