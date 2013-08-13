---
layout: post
title: "jekyll setup with gh pages"
category: posts
---


In this post I will show how to set up a jekyll blog on github pages set by step

### 1. create a new reposity

name it to whatever you want, for example in my case I set repo name to jekyll

### 2. clone repos and check out gh-pages branch

(use my repos as example)

<pre><code>
git clone https://github.com/airbob/jekyll.git
cd jekyll/
git init
git checkout --orphan gh-pages
</code></pre>

### 3. create a new jekyll blog in your local environment

I suppose you have installed all the neccessary gems,etc, if not you can refer to [resource here](http://jekyllrb.com/docs/installation/)

you can create the blog under the same directory you just ```git clone```

<pre><code>
cd jekyll
cd ..
jekyll new jekyll
</code></pre>

### 4. change themes
I use [UP](http://carlosbecker.com/posts/up-a-jekyll-theme/)

Here is set up of ```UP theme```

<pre><code>
git clone https://github.com/caarlos0/up
cd up
bundle
rake preview
</code></pre>

I encountered this error during bundle install dependencies

<pre><code>
Canot install RMagick 2.13.1. Canot find MagickWand.h.
*** extconf.rb failed ***
</code></pre>

This is how to solve this issue:
check whether you installed rmagick:

<pre><code>
convert --version
</code></pre>
If you do, you probably either installed it with fink or macports (maybe homebrew?). What is happening is that rvm canot find the imagemagick directory.
after that, add this line to your ```~/.bash_profile``` (suppose you use mac)

<pre><code>
$ export PKG_CONFIG_PATH="/opt/local/lib/pkgconfig:$PKG_CONFIG_PATH"
</code></pre>
restart the terminal and try ```bundle``` again and it works for my case.


### 4. update **_config.yml**
since we are creating project pages, it will be located at username.github.io/projectname as subdirectory

add this line to _config.yml

<pre><code>
baseurl: /jekyll
</code></pre>

### 5. modify files needed
same explanation as step 4, you might need modify few files to make the link path correct

since we are creating project pages, it will be located at username.github.io/projectname as subdirectory, listed a few files need to change:

modify ```index.html```

<pre><code>
<div id="home">
  <h1>Blog Posts</h1>
  <ul class="posts">
    {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
</code></pre>



modify ```_layout/default.html```

<pre><code>
        <link rel="stylesheet" href="{{ site.baseurl }}/css/syntax.css">
        <link rel="stylesheet" href="{{ site.baseurl }}/css/main.css">
</code></pre>



### 6. deploy to github:

<pre><code>
git add .
git commit -m "first commit"
git remote add origin https://github.com/airbob/jekyll.git
git push origin gh-pages
</code></pre>

after around 10 mins, check your new jekyll blog at username.github.io/projectname !

demo:

![](http://media.tumblr.com/72f5de7b975fddd26c706940798af245/tumblr_inline_mptfgjjfLa1qz4rgp.png)


- some basics:

<pre><code>
rake post title="Hello World"
git add .
git commit -m "commit message"
git push origin gh-pages
</code></pre>


Have fun!

