# Universal Music Server

Universal Music Server (UMUS) plans to be a fork of [Universal Media Server](https://www.universalmediaserver.com/) that is geared toward audio only use. 

Currently it is just standard [UMS](https://github.com/UniversalMediaServer/UniversalMediaServer/) with additional audio transcoding support. I have not started removing video support.

## Build & Use Instructions

Build as you would normal UMS. Add the following to your renderer config:

`TranscodeAudio = OPUS`

This will set the transcode format to the default of Opus @ 128kbps. To use a different bitrate, specify it in the renderer config:

`CustomFFmpegAudioOptions = -b:a 96k`

substituing 96 for the approximate bitrate you want. I'm digging through ffmpeg/libopus docs to see if we can pass q values.

## The Big Picture

I'm basically on this roll of "nothing works how I want so I'm going to build something that does". I sat down trying to piece together how I'd give another crack at being my own music streaming service; and I didn't like what was out there. It felt like they were telling me how to handle my music, or refusing to let me do things ways they didn't understand. 

The biggest thing UMS didn't do out of the box was transcode to Opus. This turned out to be stupidly simple to add. It was mostly just modifying the ffmpeg parser and the renderer config parsing. Even if I don't get the video ripped out of it successfully; maybe they'll merge the audio codec changes. I mean I'm going to submit them anyway. That's just something the program should have.

There's a client side to this I need to work on. Right now it's looking like modifying YAACC or maybe starting from scratch with something.

## Changes
```
13-SEP-2025: Initial fork and commit. Add Opus as audio transcode format.
```
