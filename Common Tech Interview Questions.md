A collection of common technical interview questions, in my own words.

### Table of Contents

[What's the differences between Dash manifest and HLS manifest?](#sid_1)

[How to create encrypted HLS contents](#sid_2)

<a id="sid_1"></a>
### 1. What's the differences between Dash manifest and HLS manifest?

The Dash manifest is a single file. Everything from adaptation groups to each segment is defined in this file. The file has hierachical structure. The file is defined in XML format.
The HLS uses plain text format. It contains two types of lines:
* line starts with '#'. i.e. #EXT-X-MEDIA, it defines a media stream with specific attributes.
* Some tags followed by URI line to tell the location.

HLS uses main playlist if there are multiple variants/representations, 

<a id="sid_2"></a>
### 2. How to create encrypted HLS contents

Encrypting HLS is defined in Apple Fairplay spec. There are three steps to create encrypted HLS contents:
1. Encrypted the media samples. There are some specific way to encrypt the video and audio sample. i.e. only the 10% of video NALs should be encrypted.
2. Modify the media file header to indicate the content is protected. i.e. Different media types for encrypted the video and audio streams are defined in MPEG2-TS PMT. In fMP4 file, additional mp4 boxes are added such as PSSH.
3. A HLS key tag is added in the playlist to indicate the following contents are protected.

