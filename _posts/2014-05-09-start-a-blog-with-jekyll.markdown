---
layout: post
title:  "Start a blog with Jekyll"
date:   2014-05-09 23:15:18
categories: tutorials jekyll
---

## What's Jekyll

[Jekyll] is a static content generator, especially useful for writing blogs. The main idea is to take raw files in developer-friendly format like markdown and compile them to ready-to-publish complete websites. 

This is very convenient when you don't really need a heavy stack with a database and web server with support for some programming language[^comments]. You could write posts in plain HTML, but any later layout changes would be very painful. With Jekyll you can separate content in markdown files from presentation layer, compile it once, and publish on basically any hosting you like, because it's simply HTML, CSS and JS files.

Another great benefit is that [Github Pages][github-pages] provide free hosting of Jekyll websites, which I'll cover later.

### Installation

Prerequisites are[^prerequisites]:

* Ruby
* Ruby devKit
* Python

Following commands will install Jekyll and bootstrap a sample project (you can replace `blog` with project name):

{% highlight bash %}
gem install jekyll
jekyll new blog
cd blog
{% endhighlight %}

### Test server

Jekyll comes with a simple HTTP server. This command will start it on [http://localhost:4000](http://localhost:4000), compile your project, and re-compile on file changes:

{% highlight bash %}
jekyll serve --watch
{% endhighlight %}

Note that if you change site configuration or add new post you have to manually restart the server, `--watch` doesn't help.

### Basic settings

Before writing your first post you might want to fill basic information about yourself and change some environment settings. What I changed in `_config.yml` is:

{% highlight yaml %}
email: # Empty, because every email harvester could get it
username: msulima # Used in github/twitter links

encoding: utf-8 # If you use Ruby >= 2.0.0 then it's default, but I'm on 1.9.3
timezone: Europe/Warsaw
{% endhighlight %}

## First post

`jekyll new blog` command generated a sample markdown file with some content in `_posts` directory. The simplest solution is to rename it and overwrite it's content. Note that posts names must be in `YEAR-MONTH-DAY-title.MARKUP` format.

I can't tell you what you want to put there, but the syntax is: 

* [markdown] -- with [kramdown] implementation as default[^markdown]. You can replace it with textile though.
* [Liquid] -- template engine with syntax really similar to Django templates.
* [Front-matter] -- Jekyll's own templating solutions, allows to specify post layout and some extra variables.

### Publish on Github Pages

[Github Pages][github-pages] is a free of charge service which allows you to host a website using a Github repository. It will use your `$username/$username.github.io` repo to publish at `http://$username.github.io` address.

Jekyll is supported out-of-the box, so you just need to commit your blog's source files (without `_site` directory). To start your Github Page firstly [create repository] with name `$username.github.io`.

In directory with blog content initialize a git repository, add remote branch that you just created, add all needed files, commit them and push to Github.

{% highlight bash %}
git init
git remote add origin https://github.com/$username/$username.github.io.git
git add _includes _layouts _posts _config.yml css
git add about.md index.html feed.xml .gitignore
git commit -m "First commit"
git push -u origin master
{% endhighlight %}

Your website should be available under `http://$username.github.io` in 5-15 minutes. Unfortunately there's no way to check progress, so if it doesn't appear you might want to check [troubleshooting] page.

## Conclusions and further reading

Drafts

## Footnotes

[Jekyll]:            http://jekyllrb.com/
[markdown]:          http://daringfireball.net/projects/markdown/
[kramdown]:          http://kramdown.gettalong.org/
[Liquid]:            http://docs.shopify.com/themes/liquid-basics
[Front-matter]:      http://jekyllrb.com/docs/frontmatter/
[create repository]: https://github.com/new
[troubleshooting]:   https://help.github.com/articles/troubleshooting-github-pages-build-failures
[github-pages]:      https://help.github.com/articles/troubleshooting-github-pages-build-failures

[^comments]: If you need comments, you can include JS scripts provided by Disqus or Google+.
[^prerequisites]: You should find on Google how to install them.
[^markdown]: Github Flavored Markdown and others are also available.
