# MX Player Video Start

## Export Info:
**Tasker Version:** `5.9.1`  
**Timestamp:** `2020-01-15 02.38.36`  



## Profile Names:
**Count:** `0`




## Scene Names:
**Count:** `0`




## Task Names:
**Count:** `1`

- *`MX Player Video Start`*



## Profiles Info:



## Tasks Info:

**#:** `1`  
**Name:** `MX Player Video Start`  
**ID:** `489`  
**Collision Handling:** `Run Both Together`  
**Keep Device Awake:** `false`  
**Help:**
```
A task that sends an intent to MX Player to start a video with optional subtitles.

MX Player app version to use will automatically be decided if the app is installed. Priority will be given to Pro version if both Pro and Ads are installed.

The video file must exist at video_path passed. It must be an absolute unix file path.

The subtitle file must exist at subtitle_path if passed. It must be an absolute unix file path.

If the subtitle_path is not passed, then MX Player will automatically detect if a subtitle file exists in the video directory with same filename or if subtitles are embedded in the video itself. Passing subtitle_path is likely only to be necessary if the subtitle file has a different filename than the video or if it's in a different directory than the video.

Check "https://sites.google.com/site/mxvpen/api" for more information on how to send an intent to MX Player.


Input %par1:
"
video_path
"

Input %par2:
"
subtitle_path #optional
"

Returns:
"
result_code
"

If the intent is sent successfully, then result_code will contain "0".
Otherwise it will contain an appropriate exit code or will not be set if there are exceptions.
```
##

