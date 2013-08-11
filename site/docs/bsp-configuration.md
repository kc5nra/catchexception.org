---
layout: docs
title: Browser Configuration
prev_section: creating-a-source-factory
next_section: bsp-assets
permalink: /docs/bsp-configuration/
---

## Prerequisites

If you haven't installed the Browser Source Plugin yet you must follow these [download instructions](../../downloads/browser-source-plugin).

After you'ved installed you can quickly confirm this fact by checking which plugins are installed and active.

<a href="/img/docs/bsp-check-plugin.png"><img src="/img/docs/bsp-check-plugin.png" width="400px" /></a>

1. Click the Plugins button in the bottom right corner above exit and you should see `Browser Capture Plugin`.

If you see this then you have successfully installed (or have installed in the past) the Browser Source Plugin.  

2. Select `Browser Capture Plugin` in the listbox and on the right hand side of the listbox you should see
which version you have installed.  

3. Confirm that this is the latest version accord to [the download page](../../downloads/browser-source-plugin).

## Adding your first Browser Source to the scene.

If you haven't created a Scene yet do so now.  Right click on your sources Add&rarr;Browser and then confirm
the new Source named `Browser`.

<a href="/img/docs/bsp-add-browser.png"><img src="/img/docs/bsp-add-browser.png" width="400px" /></a>

## Configuring your Browser Source

This is where most of the complication lies due to unfamiliar terms.

Here is the default configuration scene with its 4 logical sections highlighted.

<a href="/img/docs/bsp-configuration.png"><img src="/img/docs/bsp-configuration.png" width="400px" /></a>

### (1) Simple URL or asset URL

When I refer to scheme, I am referring to what comes before the `://`.  The asset scheme (`asset://`) and http scheme (`http://`)
are the most common.

The browser plugin will handle any *normal* URL using the `http`, `https` and `file` scheme such as:

* http://www.obsproject.com
* http://youtube.com
* http://twitch.tv
* file:///...

It also has a custom scheme handler called `asset` which gives you more control over the files being served.  For more information take a look at the [asset documentation](../bsp-assets).

<div class="note warning">
  <h5>Flash files, movies, and non-html URLs</h5>
  <p>
    You <b>must</b> use the <code>asset</code> scheme when referring to these file types.  For more information
    refer to the <a href="../bsp-assets">asset documentation</a> on how to correctly include these types of files.
  </p>
</div>

### (2) Browser Width and Height

This should be fairly basic and self-explanatory.  The width and height refer to the amount of pixels the *virtual* browser window will be.  In most cases this will be
directly related to the size of the content you want to show. 

### (3) Custom CSS

The custom CSS allows you to change the base stylesheet loaded by all requests.

Note: This feature does *not* require you to be using the `asset` scheme.

The default looks like this:

{% highlight css %}
::-webkit-scrollbar { visibility: hidden; }
body { background-color: rgba(0, 0, 0, 0); }
{% endhighlight %}

The first line disables the scrollbar and the second line sets the default background color to transparent.  

This means that if you don't have any opaque items
in the site being loaded then you will be able to see sources behind your browser source.

One common request is to remove the default margin on the top and left side.  If you see that there is a black border to the left and top
you can disable it by changing your default css to:

{% highlight css %}
::-webkit-scrollbar { visibility: hidden; }
body { 
	background-color: rgba(0, 0, 0, 0);
	margin: 0 auto;
}
{% endhighlight %}

### (4) Asset Wrapping

This is directly related to [assets](../bsp-assets) and more information can be found in the asset documentation.

To use `asset` wrapping you **must** be using the `asset` scheme in the URL and have the 'Wrap the asset in an html body' checkbox selected.

Asset Wrapping is a very simple templating system that has 3 variables.

- `$(FILE)` replaced by the URL specified in section 1 according to the image
- `$(WIDTH)` replaced by the width specified in section 2
- `$(HEIGHT)` replaced by the height specified in section 2

When Asset Wrapping is enabled **and** an `asset` scheme is specified as the URL then the template in section 4 according to image 
gets served after replacing the variables.

This may appear to be complicated but it's only due to terminology.

Here is an example of how it works.

{% highlight html %}
1: URL: asset://local/plugins/BrowserSourcePlugin/movie.webm
2: Width: 250
3: Height: 40
4: [x] Wrap the asset in an html body

5:

<html>
  <head></head>
  <body>
  	File: $(FILE)
  	Width: $(WIDTH)
  	Height: $(HEIGHT)
  </body>
</html>

{% endhighlight %}

For this example only I changed the opaqueness of the background to 100%

{% highlight css %}
::-webkit-scrollbar { visibility: hidden; }
body { background-color: rgba(255, 255, 255, 255); }
{% endhighlight %}

This results in this:

<a href="/img/docs/bsp-asset-wrapping.png"><img src="/img/docs/bsp-asset-wrapping.png" width="400px" /></a>

The document being presented is generated dynamically based on the wrapped asset found in section 5 according to the image.

This makes it much simpler to include movies, flash files, etc. without having to create a physical html file for each one.

<div class="note protip">
  <h5>Relative requests in wrapped assets</h5>
  <p>
    All requests made in the wrapped asset are relative to the path in the URL excluding the filename.
    For example <code>asset://local/files/file.txt</code> will make further relative requests (images, css, etc.) in the <code>files</code> directory.  
    This includes flash files loading dynamic files.
  </p>
</div>