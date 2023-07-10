---
layout: post
title:  Making the (old) website using Pelican and GitHub Part 2
date:   2019-03-22 00:00:00
description: Part 2 of steps to create the {old} website using Pelican and GitHub. This post shows how to use Pelican themes and plugins.
tags: pelican
categories: builds
---

### NOTE: This post is part of the old blog, where I used Pelican to create it, still useful for archival purposes

{% include figure.html path="assets/img/default_theme_pelican.png" class="img-fluid rounded z-depth-1" zoomable=true %}

This is the default theme from Pelican, which looks fine and achieves most of the stuff you need. 

I needed a cleaner looking theme though and one that I could customize. Thus, started the hunt for the theme.

### Hunt for the theme

Here are the resources I found after Googling. Maybe you'll find better.

* [https://github.com/getpelican/pelican-themes](https://github.com/getpelican/pelican-themes)
* [http://www.pelicanthemes.com/](http://www.pelicanthemes.com/)

However, none of them seemed to look good to me. Also, most of them were updated a while ago, and might break in the future.

The one which I liked was the ['pelican-bootstrap3'](https://github.com/getpelican/pelican-themes/tree/master/pelican-bootstrap3) theme.Its regularly updated and [widely used](https://github.com/getpelican/pelican-themes/blob/master/pelican-bootstrap3/EXAMPLES.md). 

But I felt something was missing. So I turned elsewhere.

I stumbled upon this [blog post](https://www.svenkreiss.com/blog/pelican-2018/) by Sven Kreiss. I liked the website and the fact that both of us are kind of in the same domain. He is using a customized theme named 'pure' available [here](https://github.com/svenkreiss/pure).

The pelican-themes github repo mentioned above also has a version of the [pure](https://github.com/danclaudiupop/pure/tree/9c58a20c1ed86a26c456ac1f3a736838b6409fc1) theme, if you want to check that out.

### Decided on the theme. What now?

Honestly, you can find a lot of themes in the wild online. However, there are some commonalities between all of them.

What are those you might ask? Here we look at the all important **pelicanconf.py** file.

### pelicanconf.py

This file is generated after the quick start step and contains, as the name suggests, all the different configurations for your website.

For example the SOCIAL variable. Here's what it can look like:

```python
SOCIAL = (
    ('twitter', 'https://twitter.com/sauravsen111'),
    ('linkedin', 'https://www.linkedin.com/in/saurav-sengupta/'),
)

```

Which results in:

{% include figure.html path="assets/img/default_theme_pelican-social.png" class="img-fluid rounded z-depth-1" zoomable=true %}

This ease of use is so awesome that it almost makes me believe in God. Its great living in the 21st century.

Pelican does not have emoji support though.. so I am back to being...agnostic..?

That went off-track soon. Back to website building. It gets tricky from here on out.

### Getting the themes you want

Somewhere outside your checked out repository folder create a **pelican-themes** folder and checkout the theme you want. For example,

```
git clone https://github.com/svenkreiss/pure.git
```

or checkout the whole [pelican-themes](https://github.com/getpelican/pelican-themes) repo, if you want to be that way about it.

### Installing and using themes

Just do

```
pelican-themes -i /path/to/themes/pure
```

Check if the theme is installed

```
pelican-themes -v -l
```

Go to the **pelicanconf.py** file and do

```python
THEME='pure'
```

Generate the pages using

```
pelican content -D -s pelicanconf.py -o output
```

Barring any errors, your theme should start working the next time you start your server using
```
make devserver
```

### Installing and using plugins

Go ahead and checkout the whole [pelican-plugins](https://github.com/getpelican/pelican-plugins) GitHub repo in the folder of your choice.

We will talk about the all purpose [liquid_tags](https://github.com/getpelican/pelican-plugins/tree/master/liquid_tags) plugin here.

It has pretty good documentation on how to use it but still I'll go over how to use it here.

Add the following to your configuration file-

```python
PLUGIN_PATH = '/path/to/pelican-plugins'
PLUGINS = ['liquid_tags.img', 'liquid_tags.video',
           'liquid_tags.youtube', 'liquid_tags.vimeo',
           'liquid_tags.include_code', 'liquid_tags.notebook']
```

To insert the image in your markdown use this inside your markdown-

```markdown
{% include figure.html path="assets/img/blog_snapshot.png" class="img-fluid rounded z-depth-1" zoomable=true %}
```

Hold up. 

Where do you store your images and files?

### Where to store files and images

Create folders named **images** and **files** inside your content directory.

Set the following parameter in your configuration file-

```python
STATIC_PATHS = ['images', 'files']
```

Put your images inside the **images** folder.

Done.

Phew.

This part 2 should give you enough of a head-start to make a working, good looking website.

Explore themes and other people who have used those themes to find out and learn more about the ones you want to use.

Stay golden people. Peace.