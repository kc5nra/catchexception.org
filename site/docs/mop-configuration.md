---
layout: docs
title: Mumble Overlay Configuration
prev_section: bsp-javascript-plugins
next_section: 
permalink: /docs/mop-configuration/
---
## Prerequisites

If you haven't installed the Mumble Overlay Plugin yet you must follow these [download instructions](../../downloads/mumble-overlay-plugin).

<div class="note info">
  <h5>Plugin dependencies</h5>
  <p>
    This plugin <em>requires</em> the CLR Host Plugin.  To install it follow <a href="../../downloads/clr-host-plugin">these instructions.</a>
  </p>
</div>

## What is Mumble Overlay Plugin?

The Mumble Overlay Plugin is a plugin that allows you to add the overlay as a source so that viewers seeing your stream can see the overlay as well. 

Because of how game capture works, applications like Mumble that contribute to the rendering pipeline of a game through hooking or other mechanisms may
not be visible in the final result.

## Configuration of the plugin

The configuration and usage of the plugin is very trivial with minimum setup.

<a href="/img/docs/mop-configuration.png"><img src="/img/docs/mop-configuration.png" width="400px" /></a>

You'll notice there are only a *width* and a *height* in the source's configuration.

## Configuration of Mumble

In order to setup the overlay in mumble, a few settings must be changed/verified.

<a href="/img/docs/mumble-configuration.png"><img src="/img/docs/mumble-configuration.png" width="400px" /></a>

Open mumble preferences by going to Configure&rarr;Settings in the menu.

1. Select the Overlay section on the left-hand side.
2. Check `Advanced` so that the `Overlay Exceptions` tab becomes available.
3. Check `Enable Overlay` to enable third-party access to the mumble overlay (our plugin).
4. Uncheck `Show FPS counter` because it is distracting and unnecessary.
5. Select the `Add...` button and navigate to the OBS.exe that you are using (32bit or 64bit).
6. Verify that the OBS.exe has been added to the Blacklist of applications to NOT hook

<div class="note warning">
  <h5>Mumble Blacklist</h5>
  <p>
    If you do not correctly setup the blacklist Mumble will agressively hook any and all applications that use DirectX.  This <em>will</em> 
    cause any .NET plugins (including the Mumble Overlay Plugin) you are using to potentially act erratically (not respond to user interaction, not repainting, etc.).
  </p>
</div>