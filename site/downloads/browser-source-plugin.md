---
layout: downloads
title: Browser Source Plugin
permalink: /downloads/browser-source-plugin/
---

The latest version of the Browser Source Plugin is *1.0-24*.

There are several flavors so be sure to select the correct download for the version of OBS that you are using.

## Prerequisites

If you do not understand which version of the plugin to install and where to put it please refer to this [plugin installation documentation](../../docs/installation).

## Download

[BSP 1.0-24 32bit](http://catchexception.org/plugins/bsp/BSP-1.0-24-g30ce603-x86.zip)

[Source Code](https://github.com/kc5nra/BrowserSourcePlugin)

<div class="note info">
  <h5>Confirm your platform!</h5>
  <p>
	Make *sure* that you download the correct platform and put it in the correct plugin directory.
	If you are at all unsure check the <a href="../../docs/installation">plugin installation documentation</a> again.
  </p>
</div>

## Changelog

### 1.0-24 `Current Version`

- Bugs

	+ Fixed a bug when custom css or asset templates were empty

### Previous versions

#### 1.0-23

- Changes

	+ Updated to Awesomium 1.7.1
	+ Internal preparation for 64bit client
	+ Added Javascript Extension framework
	+ Added Twitch IRC JS extension

- Bugs

	+ Fixed bug in isConnected for irc
	+ Fixed bug where threads weren't cleaning up properly
	+ Fixed bug where webviews when deleted/updated could cause a crash

#### 1.0-11

- Changes
	
	+ Added all common mimetypes when resolving files with asset loader
	+ First support of javascript API binding but disabled at the moment

- Bugs

	+ There was a major flaw in how I handled deconstruction of the BrowserSource.
	+ Fixed a double delete of memory.
	+ Fixed a major bug in the BrowserManager where it would try to deference event object after it had been deleted

- Misc

	+ Switched to spaces only in the source.

#### 1.0-9

- Changes

	+ Added a CSS editor (similar to the html one0
	+ Added a new blank asset for loading only from asset wrapper
	+ Added a KeyboardManager for future capabilities
	+ Default editor for wrap templates is now scintilla

- Bugs

	+ Fixed a small bug where the custom css wasn't being saved
	+ Some bugs in mime types were fixed as well as several added
	+ Moved the datasources into their own file

- Misc

	+ Cleaned up Swf style, cosmetic changes and memleak

#### 1.0-6

- Changes

	+ Asset wrapping now allows you to load types like swf and wrap them in a html template.
	+ Added a Swf parser to determine native size of swf assets. (Useful in the future maybe?)

- Bugs

	+ Fix bug in flash where it crashed if it wasn't 'navigated off' before destroying
	+ Fixes a small memory leak when creating view

#### 1.0-4

- Changes
	
	+ Events can now notify on completion

- Bugs

	+ Threading issues and fix to asset loading
	+ Fixed some very idiotic problems in the view manager regarding the view list add/remove logic.

#### 1.0-3 Initial public release