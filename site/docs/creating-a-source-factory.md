---
layout: docs
title: Creating a Source Factory
prev_section: creating-a-plugin
next_section: bsp-configuration
permalink: /docs/creating-a-source-factory/
---

This part of the guide assumes you have successfully made a [Plugin](../creating-a-plugin).

## What is a Source Factory?

A source factory follows the [factory pattern](http://en.wikipedia.org/wiki/Factory_method_pattern) in providing
the OBS API the ability to create a new instance a plugin class when necessary.

All the factories have only one method; ``Create``.

The factory interfaces all follow this template:

{% highlight csharp %}
class ___SourceFactory : ___SourceFactory
{
    ___Source Create(Arguments)
    {
        return null;
    }
}
{% endhighlight %}

Where `___` is replaced by the factory type.

Each factory type may have additional methods that require overloading like configuration of the source, etc.

## Creating our ImageSourceFactory

`ImageSourceFactory` is the interface for a factory that creates `ImageSource` instances that render an image
to the active OBS scene.  This means they receive calls from OBS for important events like 'The scene just changed' and 
'I'm requesting you to render something'.

To create this factory we are going to extend the helper class `AbstractImageSourceFactory` which simplifies how one constructs
a `ImageSourceFactory`.  You are always able to implement the interface yourself if you want finer grained control over how
the class operates and interacts with the OBS API.

A barebones `ImageSourceFactory` looks like this:


{% highlight csharp %}
class MyImageSourceFactory : AbstractImageSourceFactory
{
    public override ImageSource Create(XElement data)
    {
        return null;
    }

    public override bool ShowConfiguration(XElement data)
    {
        return false;
    }
}
{% endhighlight %}


This alone is not enough for OBS graphical user interface to know about our new ImageSourceFactory.

We'll need to override the ``LoadPlugin`` method in our `MyImagePlugin` class we created in the previous section.

Your Plugin class should now look like this:

{% highlight csharp %}
public class MyImagePlugin : AbstractPlugin
{
    public MyImagePlugin()
    {
        Name = "Sample Image Plugin";
    }

    public override bool LoadPlugin()
    {
        return true;
    }
} 
{% endhighlight %}

We now have a chance to make a decision when the plugin is loaded by OBS.

We only have to add one line which should be fairly self-explanatory:

{% highlight csharp %}
public override bool LoadPlugin()
{
    API.Instance.AddImageSourceFactory(new MyImageSourceFactory());
    return true;
}
{% endhighlight %}

This registers our new `MyImageSourceFactory` with OBS so that it knows how to create an `ImageSource`
instance when necessary.

Your `Plugin` class should now resemble this:

{% highlight csharp %}
class SamplePlugin : AbstractPlugin
{
    public SamplePlugin()
    {
        // Setup the default properties
        Name = "Sample Image Plugin";
        Description = "Sample Image Plugin lets you show a picture";
    }
    
    public override bool LoadPlugin()
    {
        API.Instance.AddImageSourceFactory(new SampleImageSourceFactory());
        return true;
    }
}
{% endhighlight %}