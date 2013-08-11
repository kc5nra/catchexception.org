---
layout: docs
title: Installation
prev_section: home
next_section: creating-a-plugin
permalink: /docs/installation/
---

Installation of OBS plugins is as simple as placing the plugin dll and other plugin
dependencies in the `plugins` directory found inside your OBS installation directory.

Most plugins will contain a 32bit version (x86) and a 64bit version (x64).

<div class="note info">
  <h5>Confirm your platform!</h5>
  <p>
    The default OBS installation contains two platforms (a 32bit version and a 64bit version).  
    The 64bit version can be found as a subdirectory inside your OBS installation.  
    So if your normal installation is <code>C:\Program Files (x86)\OBS</code> then your 64bit 
    installation will be found at <code>C:\Program Files (x86)\OBS\64bit</code>.
  </p>
</div>

The default OBS installation directory layout resembles this:

{% highlight bash %}

OBS
├── OBS.exe (32bit)
├── plugins (32bit)
|   └── plugin1.dll (32bit)
├── ...
└── 64bit
    ├── OBS.exe (64bit)
    ├── plugins (64bit)
    |       └── plugin1.dll (64bit)
    └── ...

{% endhighlight %}

For CLR (.NET) Plugins it will look like this:

{% highlight bash %}

OBS
├── OBS.exe (32bit)
├── plugins (32bit)
|   ├── plugin1.dll (32bit)
|   └── CLRHostPlugin (32bit)
|       └── clrplugin1.dll (universal/32bit) 
├── ...
└── 64bit
    ├── OBS.exe (64bit)
    ├── plugins (64bit)
    |   ├── plugin1.dll (64bit)
    |   └── CLRHostPlugin (64bit)
    |       └── clrplugin1.dll (universal/64bit) 
    └── ...

{% endhighlight %}

<div class="note info">
  <h5>CLR Universal Plugins</h5>
  <p>
    Some, if not most, CLR (.NET) plugins are universal.  This means they are able to be loaded
    from either 32bit or 64bit versions of OBS.   The main CLR Host Plugin, however, <em>is</em> platform
    dependent.
  </p>
</div>

Having completed this, you should be able to begin using your plugin from
within OBS.