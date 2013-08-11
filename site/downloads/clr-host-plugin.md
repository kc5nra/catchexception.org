---
layout: downloads
title: CLR Host Plugin
permalink: /downloads/clr-host-plugin/
---

The latest version of the CLR Host Plugin is *1.0-2*.

There are several flavors so be sure to select the correct download for the version of OBS that you are using.

## Prerequisites

If you do not understand which version of the plugin to install and where to put it please refer to this [plugin installation documentation](../../docs/installation).

## Download

[CHP 1.0-3 32bit](http://catchexception.org/plugins/chp/CHP-1.0-3-g4e483c5-x86.7z)

[CHP 1.0-3 64bit](http://catchexception.org/plugins/chp/CHP-1.0-3-g4e483c5-x64.7z)

[Source Code](https://github.com/kc5nra/CLRHostPlugin)

<div class="note info">
  <h5>Confirm your platform!</h5>
  <p>
	Make *sure* that you download the correct platform and put it in the correct plugin directory.
	If you are at all unsure check the <a href="../../docs/installation">plugin installation documentation</a> again.
  </p>
</div>

## Changelog

### 1.0-3 `Current Version`
- Changes
	
	+ Added API Log method for hosted plugins

- Bugs

	+ Fixed a bug when a plugin fails to load it would try to use an uninitialized variable

### Previous versions

### 1.0-2
- Bugs

	+ Texture::SetImage with a nullptr for the initial texture data would cause an invalid memory access

#### 1.0-1 Initial public release