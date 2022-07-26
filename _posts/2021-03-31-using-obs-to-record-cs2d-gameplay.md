---
title: Using OBS to Record CS2D. Setup, Specs, Tips, and Troubleshooting
author:
  name: Denis Kryukov
  link: https://devishnya.github.io
date: 2021-03-31 18:32:00 -0500
categories: [Blogging, Tutorial]
tags: [google analytics, pageviews]
---

Hello, world!

CS2D doesn’t have a shortage of tournaments: With a number of competitive communities ([cs2d.eu](cs2d.eu) and [RU2D](cs-2d.ru)), 2020 has seen numerous events, including classic 1v1, classic 2v2, shotgun, laser, and so on. Too many tournaments, however, have been held with little to no coverage (i.e. match videos) — their only remnant is a [tournament bracket on Challonge](https://challonge.com/979j1hzb) (sad emoji.)

I love watching tournament matches; every now and then, I also re-watch old videos. To facilitate more CS2D content on YouTube, we're writing this guide to help you get started with recording CS2D matches. 

The goal of this guide is to facilitate a **media team**, making it possible to **record every tournament match**. Here’s what we’ve captured so far:

* [Single Seasons Cup 2020: Autumn](https://www.youtube.com/playlist?list=PLEVlJXfo90ZzhN4y6_byhOv-caZu-U768)
* [Duo Shotgun Cup 2020](https://www.youtube.com/watch?v=sPIVHPVJn2k&list=PLEVlJXfo90ZwZcikDFbMETqvbyLhzPvWu)
* [Classic Duo Championship 2020](https://www.youtube.com/playlist?list=PLEVlJXfo90ZyK05rPg8QatNERVYU3soGj)
* [RU2D LaserCup 2020](https://www.youtube.com/playlist?list=PLEVlJXfo90ZzJUsMkx_u841QyThlj5NPo)
* [CS2D.EU Laser Cup 2020](https://www.youtube.com/playlist?list=PLEVlJXfo90Zx_zQV_lNGFsIkdiZ7wVt7K)

## Why record at all?

The entire process (keeping track of the match’s date and time, recording, troubleshooting, uploading, formatting results, and posting to Discord) does take some effort, but it’s well worth it in the end: 

* **Interesting content**: Watching players in a match with real stakes is fascinating.
* **Preserving our memories**: Rewatching that match a few years later is equally fun.
* **Promoting the game among inactive players**: Tournament videos may very well convince old players to return for a tournament or two.
* **Promoting the game among new players**: Yeah, CS2D will probably never become YouTube’s second Fortnite, but there are players unfamiliar with the competitive scene — and our videos will serve as a great introduction to it.

## Recording software and its settings

There’s a plethora of video recording software you can choose from. This guide covers [OBS](https://obsproject.com/) because:

* it’s **free** and
* it’s **highly customizable**.

### Recording setup

Download OBS, install, and run it. You’ll be greeted with the main menu:

![OBS main menu](https://i.imgur.com/l5xfyQc.png)

Launch CS2D. To record it, we need to add it to as a **source** — you can see the Sources menu at the bottom. Click the plus sign and select *Window Capture*, click OK, then choose `[CS2D.exe]: Unreal Software’s CS2D`. Upon clicking OK, the black area in the center will now show CS2D:

![OBS with CS2D as a Source](https://i.imgur.com/oZNK4V6.png)

*(Even though Game capture provides better performance, we need to use Window capture for the streaming overlay to work.)*

We also need an audio source to capture CS2D's sounds — in the *Sources* menu, click the plus sign, select `Audio Output Capture`, and choose your audio device (the `Default` option will probably work OK.) In the *Audio Mixer* menu (right to *Sources*), move the volume slider of *Desktop Audio* to the `-20` mark — this will ensure CS2D isn't overly loud. Also, if you're not planning to use your microphone (yet), mute *Mic/Aux*:

![Desktop audio settings](https://i.imgur.com/wOdjJSh.png)

### Recording option 1: 1080p @60 fps

Recording in FullHD is preferred because it provides the best viewing experience. Go to *Settings → Video → Base (Canvas) Resolution* and *Output (Scaled) Resolution* and set it to `1920x1080`. 

**System requirements for recording 1080p @60 fps**: My half-decent laptop (i7-8550U, 16GB RAM, 2GB VRAM) handles this pretty well, with occasional frame drops to approx. 55 fps. If you have similar computer specifications, you should try this option first.

### Testing our first recording

In the bottom right corner, press *Start Recording* and take a test drive — start a new game and spend some time running around the map or spectating bots. It's helpful to turn the fps counter on: *Options → More → Debugging → debug `1` (Debug Info & FPS)*: In the top left corner, you'll now see the game's fps count.

![image](https://i.imgur.com/ei9PB4z.png)

Pay close attention to it while recording: Is the game running smoothly (60 fps) or is it struggling to maintain consistent fps? In my experience, occasional fps drops from 60 to 50 isn't a huge problem because the viewer doesn't really notice it.

Click *Stop recording* and watch the footage — you can find the output folder in *Settings → Output → Recording  → Recording Path*.

### Recording option 2: Lower resolution / lower fps

Recording at a high resolution is a CPU-intensive task, so some computers will have problems with the first option. In this case, you can try toning your recording settings down:

* Resolution: `720p` (or even `480p`) instead of `1080p`. Go to *Settings → Video → Output (Scaled) Resolution* and change the parameter.
* Fps: `50` (or even `30`) instead of `60`. Go to *Settings → Video → Common FPS Values* and change the parameter.
* Capture method: Using *Game capture* instead of *Window capture* in OBS will yield more fps while recording (but you won't be able to use the streaming overlay.)

Furthermore, you can play around with recording quality settings: [This page](https://obsproject.com/wiki/General-Performance-And-Encoding-Issues) provides a detailed overview of various settings you can tweak. In my case, switching from `x264` to `QuickSync H.264` in *Settings → Output → Streaming → Encoder* removed almost all fps drops.

### Streaming overlay

Pawelek has created an [overlay](https://github.com/xAranaktu/CS2D-Overlay) that enhances your spectating capabilities. Here’s what it can do (taken from the project’s GitHub page):

* Free look
* No Flash
* No Fow
* X-ray
* Automatically updating match score
* Showing damage dealt by each player

You can find the installation instructions and download link [here](https://github.com/xAranaktu/CS2D-Overlay). However, the overlay has a few bugs:

* Updating score manually doesn’t work, and
* CS2D is forced to run in DirectX, which prevents the game from being recorded in OBS’ *Game capture* source (we’ll have to use *Window capture* instead.)

### CS2D graphics settings

As pro players, we’re used to toning any graphical enhancement down. This makes CS2D’s graphics too minimalistic for its own good: We don’t notice it while playing an important match, but *watching* an important match with these settings doesn’t make for a pleasing viewing experience. 

Let’s compare the following screenshots — which footage would you rather spend 10 minutes watching?

![Low graphics settings](https://i.imgur.com/qFfumdP.jpg)
![high graphics settings](https://i.imgur.com/3moGLI1.jpg)

CS2D videos should be presentable. Here are some useful settings we can use:

* *Options → Game → Advanced minimap* `on`: Unlike the regular minimap, it shows positions of all players. It can also zoom out and highlight players’ movement throughout the round — might be useful at the start of each 5v5 round? 

![Advanced minimap](https://i.imgur.com/1EQ0qT6.png)

* *Options → Game → Scale HUD automatically* `on`: Bigger HUD elements (kill feed, player names, chat, etc.) for better accessibility.
* *Options → Graphics →* Maximum values for all graphics settings. 

![My graphics settings](https://i.imgur.com/tU4VbRb.png)

## Troubleshooting

The instructions above look pretty simple, but you still might run into some unexpected bugs. We want this guide to be a living document — as we find solutions to common recording-related problems, we'll post them here.

### Poor performance (low fps, stutters, etc.)
As mentioned earlier, try playing around with these settings:
* Switch from `x264` to `QuickSync H.264` in *Settings → Output → Streaming → Encoder*.
* [Try these steps](https://obsproject.com/wiki/General-Performance-And-Encoding-Issues).

### OBS records in 20-30 fps, even though CS2D's fps counter shows 60
Open Windows 10's *Settings → System → Display → Graphics Settings*. In the *Choose an app to set preference* bar, select `Classic app`, click *Browse*, and locate the OBS executable file (mine is in `C:\Program Files\obs-studio\bin\64bit`.) 

Click on the *OBS Studio* tile, select *Options*, and try choosing between `System default`, `Power saving`, and `High performance`. Interestingly enough, the `High performance` option was the culprit of this problem in my case — switching to `Power saving` fixed it.

![Windows system graphics settings](https://i.imgur.com/fCWqbT3.png)

### CS2D doesn’t let you alt-tab
* Switch to `OpenGL` in *Options → Graphics → Graphics driver* or
* Check *Disable fullscreen optimization* in CS2D.exe's settings. Shout-out to [S!im](https://cs2d.eu/forum/viewtopic.php?f=20&t=177) for finding this fix.

![Disabling fullscreen optimization](https://i.imgur.com/qEfxyEh.png)

### Problems with Pawelek's overlay 

The overlay injects a .dll into CS2D, so your antivirus might think it's malware (mine was always deleting the .dll file.) Try adding the overlay's entire folder to your antivirus' white list (or exceptions.)

## Future updates to this guide
* **Uploading to YouTube**: tags, playlists, thumbnails templates.
* **TBD**.



