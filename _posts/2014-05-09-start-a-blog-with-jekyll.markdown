---
layout: post
title:  "Start a blog with Jekyll"
date:   2014-05-09 23:15:18
categories: jekyll tutorials
---
Run your blog with:

{% highlight bash %}
jekyll serve --watch
{% endhighlight %}

_Fun fact:_ if you change site configuration or add new post you have to manually restart the server, `--watch` doesn't help.

## Basic settings

Before you write your first post you might want to fill basic info about yourself and change some environment settings. What I changed in `_config.yml` is:

{% highlight yaml %}
email: # Empty, because every email harvester could get it
username: msulima # Used in github/twitter links

encoding: utf-8 # If you use Ruby >= 2.0.0 then it's default, but I'm on 1.9.3
timezone: Europe/Warsaw
{% endhighlight %}

By default there are also some other settings, but they're pretty self-explaining.

## First post

`jekyll new blog` command generated a sample markdown file with some content. The easiest way is to rename it and overwrite it's content.

I can't tell you what you want to put there, but the syntax is simply:

* [markdown] -- with [kramdown] implementation as default[^markdown]. You can replace it with textile though.
* [Liquid] -- template engine with syntax really similar to Django templates.
* [Front-matter] -- Jekyll's own templating solutions, allows to specify post layout and some extra variables.

## Pushing to production

### Github Pages

[Github Pages][github-pages] is a free of charge service where you can deploy your public website using a Github repository. It will use your `$username/$username.github.io` repo to publish website under `http://$username.github.io` address.

Jekyll is supported out-of-the box, so you just need to commit your blog's source files (without `_site` directory). To start your Github Page firstly [create repository] with name `$username.github.io`.

### Publish

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

## Further reading

Drafts

[markdown]:     http://daringfireball.net/projects/markdown/
[kramdown]:     http://kramdown.gettalong.org/
[Liquid]:       http://docs.shopify.com/themes/liquid-basics
[Front-matter]: http://jekyllrb.com/docs/frontmatter/
[create repository]: https://github.com/new
[troubleshooting]: https://help.github.com/articles/troubleshooting-github-pages-build-failures
[github-pages]: https://help.github.com/articles/troubleshooting-github-pages-build-failures

[^markdown]: Github Flavored Markdown and others are also available.
