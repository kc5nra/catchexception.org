---
layout: downloads
title: Video Source Plugin
permalink: /downloads/video-source-plugin/
---

The latest version of the Video Source Plugin is *1.0-17*.

There are several flavors so be sure to select the correct download for the version of OBS that you are using.

## Prerequisites

If you do not understand which version of the plugin to install and where to put it please refer to this [plugin installation documentation](../../docs/installation).

## Download

[VSP 1.0-17 32bit](http://catchexception.org/plugins/vsp/VSP-1.0-17-g6cd7d7f-VLC20-x86.7z)

[VSP 1.0-17 64bit](http://catchexception.org/plugins/vsp/VSP-1.0-17-g6cd7d7f-VLC20-x64.7z)

[Source Code](https://github.com/kc5nra/VideoSourcePlugin)

<div class="note info">
  <h5>Confirm your platform!</h5>
  <p>
	Make *sure* that you download the correct platform and put it in the correct plugin directory.
	If you are at all unsure check the <a href="../../docs/installation">plugin installation documentation</a> again.
  </p>
</div>

## Changelog

### 1.0-17 `Current Version`

- Changes
	
	+ Updated to 2.0.7 and 2.2 nightly
	+ Downmix number of channels before sending to OBS audio (fix >2ch)
	+ Down/Up sample to 44100 before sending to OBS audio 
		(fix crackling at >441k)

- Bugs
	
	+ Fixed a bug in dragging (r1ch)
	+ Fix delay problems when outputting audio to stream
	+ Fix problems in device resolution in 2.2 (still too unstable)

### Previous versions

#### 1.0-14:

- Bugs
	
	+ Fixed a bug where there was a small delay when transitioning to the next video in the playlist

#### 1.0-13:

- Bugs
	
	+ Fixed bug when adding empty lines to playlist
	+ Fixed a bug when loading bad video plugin configs in a scene
	+ Fixed a bug where the wrong pitch was set for non-aligned videos

#### 1.0-12:

- Changes
	
	+ Videos now disappear when they finish playing
	+ File/Urls are now trimmed of leading spaces

- Bugs
	
	+ Fixed memory leak in configuration window
	+ Fixed bug where you could add empty url/streams

#### 1.0-10:

- Additions

	+ Added playlist

#### 1.0-6:

- Additions
	
	+ Added audio output device selection

#### 1.0-4:

- Additions
	
	+ Output sound directly to stream
	+ Aspect ratio and stretching
