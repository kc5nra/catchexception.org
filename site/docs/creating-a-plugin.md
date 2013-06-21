---
layout: docs
title: Creating a Plugin
prev_section: installation
next_section: source-factories
permalink: /docs/creating-a-plugin/
---

Creating a OBS .NET Plugin is a simple and straightforward process that can be accomplished in a matter of minutes.
All languages based on Microsoft's Common Language Runtime (.NET) should be fine.  This includes C#, C++/cli, Visual Basic
and others.

## Prerequisites

This tutorial will assume you have some knowledge of .NET languages (I will use C# in my examples) and how to configure 
various dependencies in the Visual Studio Environment.

If you haven't already, you must [download](../download-chp) and [install](../installation) the CLR Host Plugin before
continuing on with this tutorial.

## Creating a project

Regardless of the language you choose, the project type will always be `Class Library`.

Let's create the Project by File&rarr;New Project...&rarr;Visual C#&rarr;Class Library and name it `MyImagePlugin`.

In the references you will want to add `CLRHost.Interop.dll`.

<div class="note info">
  <h5>VS2010 and VS2012 differences</h5>
  <p>
    If you are having trouble adding a reference you may look at these guides: <a href="http://msdn.microsoft.com/en-us/library/vstudio/wkze6zky(v=vs.100).aspx">VS2010</a>
    , <a href="http://msdn.microsoft.com/en-us/library/vstudio/wkze6zky(v=vs.100).aspx">VS2012</a>.
  </p>
</div>

## Creating the Plugin class

There are currently two ways of creating a OBS `Plugin` class:

- Implementing the `Plugin` interface
- Extending the `AbstractPlugin` class

  If you want finer grained control over the class then you may freely choose implementing the `Plugin` interface.
  For the sake of brevity we will be using the `AbstractPlugin` class.

  Rename the default Class file generated when you created the project to `MyImagePlugin.cs`.

  Open MyImagePlugin.cs and it should look like this:

{% highlight csharp %}
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace MyImagePlugin
{
    public class MyImagePlugin
    {
    }
}

{% endhighlight %}


The first thing we want to do is include the `CLROBS` namespace that all interfaces and classes the CLRHost.Interop belong to.

The using statements should now look like this:

{% highlight csharp %}
using CLROBS;
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
{% endhighlight %}

Then we need to extend the `AbstractPlugin` class so that when the library is loaded by the CLR Host Plugin it will recognize and register 
the plugin correctly.

{% highlight csharp %}
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace MyImagePlugin
{
    public class MyImagePlugin : AbstractPlugin
    {
    }
}

{% endhighlight %}

At this point we actually have a completely valid and functional plugin.  Let's try building and copying the MyImagePlugin.dll to the `CLRHostPlugin` directory
that was created when you installed the CLRHostPlugin.

Unfortunately, it appears nothing changed!  We haven't actually added any features for OBS to display so the only thing to indicate success at this point is if we
look in the log.

You *should* see something like this:

{% highlight text %}
16:33:38: CLRHost::LoadPlugins() attempting to load the plugin assembly MyImagePlugin
16:33:38: CLRHost::LoadPlugins() successfully added CLR plugin [Type: MyImagePlugin.MyImagePlugin, Name: Default Plugin Name]
{% endhighlight %}

Well... `Default Plugin Name` doesn't look very good.  Let's change this by overriding the default plugin name in the constructor of `MyImagePlugin`.

{% highlight csharp %}
public class MyImagePlugin : AbstractPlugin
{
    public MyImagePlugin()
    {
        Name = "Sample Image Plugin";
    }
}
{% endhighlight %}

Build, copy and running again shows us this in the log:

{% highlight text %}
16:41:05: CLRHost::LoadPlugins() attempting to load the plugin assembly MyImagePlugin
16:41:05: CLRHost::LoadPlugins() successfully added CLR plugin [Type: MyImagePlugin.MyImagePlugin, Name: Sample Image Plugin]
{% endhighlight %}

<div class="note info">
  <h5>Constructor Visibility</h5>
  <p>
    If you are implementing the <code>Plugin</code> interface or subclassing the <code>AbstractPlugin</code> class you <em>must</em> have a public no-argument constructor.
  </p>
</div>