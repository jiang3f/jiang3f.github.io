A collection of common technical interview questions, in my own words.

### Table of Contents

[What's the differences between Dash manifest and HLS manifest?](#sid_1)

[How to create encrypted HLS contents](#sid_2)

[Compare TCP, UDP and SRT](#sid_3)

[Explains fragmented MP4 format](#sid_4)

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

*Extended:* CBC, AES-128, # key tag, Cenc in DASH manifest.

<a id="sid_3"></a>
### 3. Compare TCP, UDP and SRT

Keyword for TCP: reliable, connection-orient, it has handshake. It garantees not packets loss, duplicate or out of order. Unicast. Used for FTP, etc. High lantency.
Keyword for UDP: no connection, no handshake, uses checksum to check error, drop packet once it occurs. It supports unicast, multicast, broadcast. Used for broadcast, streaming. now lantency
Keyword for SRT: based on UPD, connection-orient. It is designed for live streaming. It handles packets lots, packet delay variation and fluctation bandwith. relative low lantency than TCP and more reliable than UDP.

*Extended:* Jitter. Other network protocol used by live stream.

<a id="sid_4"></a>
### 4. Explains fragmented MP4 format

MP4 files is designed as nest MP4 boxes. Fragmented mp4 files includes initialization segment file and media segment files.

Extended: moov, moof, avcc, avcconfiguration boxes. PPS and SPS.

<a id="sid_5"></a>
### 4. How to unwrap the element stream from MPEG2 TS?

1. Scan for PAT table and locate the pid for PMT.
2. Parse PMT table to obtain pids for video, audo and all other element streams.
3. Assemble the payloads from the packets with the same pid to create video, audio and other es.

*Extended:* PES header, Parse PMT table, Adaptaton, PTS, DTS, PCR.


