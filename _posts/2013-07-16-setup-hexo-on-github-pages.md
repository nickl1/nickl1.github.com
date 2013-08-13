---
layout: post
title: "setup hexo on github pages"
category: posts
---

## get source code

<pre><code>
npm install -g hexo
npm update -g
</code></pre>

## create project

<pre><code>
hexo init project
cd project
</code></pre>

## configuration

since we are seting hexo project on github pages under gh-pages branch, configuration file is most important, here is my **_config.yml** file

<pre><code>
url: http://airbob.github.io/hexo
root: /hexo/
deploy:
  type: github
  repository: https://github.com/airbob/hexo.git
  branch: gh-pages
</code></pre>

deploy to gihub by:

<pre><code>
hexo deploy --generate
</code></pre>

## basics to post

<pre><code>
hexo new "New Post"
</code></pre>
