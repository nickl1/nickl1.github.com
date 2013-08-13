---
layout: post
title: "setup octopress on github pages"
category: posts
---




In this post I will show how to set up a octopress blog on github pages set by step and deploy to gh-pages branch

### 1. create a new reposi

name it to whatever you want, for example in my case I set repo name to octopress

### 2. install all dependencies

here I suppose you have a clean Mac, and the following services need to be installed:

- [git](http://git-scm.com/)

- rvm 

```
curl -L https://get.rvm.io | bash -s stable --ruby
```

- Ruby 1.9.3

```
rvm install 1.9.3
rvm use 1.9.3
rvm rubygems latest
```

### 3. get octopress source code

```
git clone git://github.com/imathis/octopress.git octopress
cd octopress    # If you use RVM, You'll be asked if you trust the .rvmrc file (say yes).
/bin/bash --login
ruby --version  # Should report Ruby 1.9.3
rake install
```


### 4. configuration

modify ```_config.yml```

```
root: /octopress  #this is important since we intend the blog to be project page, instead of organization page
```


### 4. Blogging basics

- new post
```
rake new_post["title"]
```

- new page

```
rake new_page[super-awesome]
```

- generate and preview

```
rake generate   # Generates posts and pages into the public directory
rake watch      # Watches source/ and sass/ for changes and regenerates
rake preview    # Watches, and mounts a webserver at http://localhost:4000
```




### 6. deploy to github:

```
rake setup_github_pages
```

For my case, I found after this my ```_config.yml``` files root variable is changed, I need manually change my root back to ```/octopress```

then, type

```
rake generate
rake deploy

```


if everything works fine, after around 10 mins, check your new octopress blog at username.github.io/projectname !


Have fun!