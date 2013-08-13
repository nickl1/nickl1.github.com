---
layout: post
title: "script to post to tumblr wordpress octopress jekyll hexo in one go"
category: posts
---

> A python script to post markdown file to your wordpress/tumblr/octopress/jekyll/hexo blog in one go

I wrote a script to deploy a post in markdown format to multi blog platforms in one go. As a blogger, probably you do have not several blog places, but if you have, say you are tech editor and need to post same post to several places, this script might help you.

### Script info:

[source](https://github.com/airbob/personal-backup/blob/master/scripts/post2blog/post2blog.py)

[ReadMe](https://github.com/airbob/personal-backup/blob/master/scripts/post2blog/ReadMe.md)

#### Set up 

- wordpress
fill this section if you want to post on wordpress blog

<pre><code>
wp_url = "http://yourdomain.com/xmlrpc.php"
wp_username = "username"
wp_password = "password"
</code></pre>

leave it empty if do not want to set up wordpress blog
<pre><code>
wp_url=""
</code></pre>

you need to install **markdown2** to post to wordpress, since the format of the post is in html and we need markdown2 to convert markdown data to html data
<pre><code>
git clone git@github.com:trentm/python-markdown2.git
cd python-markdown2
sudo python setup.py install
</code></pre>


- tumblr

It needs some extra steps to set up tumblr settings in the script.
You need to [register application](http://www.tumblr.com/oauth/register) first, after you obtain **consumer key** and **consumer secret** go to [this address](https://api.tumblr.com/console/calls/user/info) to authoize the app to access your blog, then you obtain **oauth token** and **oauth secret** , file this 4 parameters accordinglly

<pre><code>
client = pytumblr.TumblrRestClient(
    'consumer_key',
    'consumer_secret',
    'oauth_token',
    'oauth_secret',
)
</code></pre>

Leave this variable empty if do not want to set up tumblr

<pre><code>
TUMBLR=""
</code></pre>

You need to install **pytumblr** to post to tumblr
<pre><code>
git clone git@github.com:tumblr/pytumblr.git
cd pytumblr
sudo python setup.py install
</code></pre>


- octopress

You need to have local enviroment for your octopress blog, then set path of octopress environment

<pre><code>
OCTOPRESS="/Users/username/octopress";
POSTOCTOPRESS=OCTOPRESS + "/source/_posts";
</code></pre>

Leave this variable empty if do not want to set up tumblr

<pre><code>
OCTOPRESS=""
</code></pre>

- jekyll

You need to have local enviroment for your jekyll blog, then set path of jekyll environment

<pre><code>
JEKYLL="/Users/airbob/jekyll";
POSTJEKYLL=JEKYLL + "/_posts";
</code></pre>

Leave this variable empty if do not want to set up tumblr

<pre><code>
JEKYLL=""
</code></pre>

- hexo

You need to have local enviroment for your hexo blog, then set path of hexo environment

<pre><code>
HEXO="/Users/airbob/hexo";
POSTHEXO=HEXO + "/source/_posts";
</code></pre>

Leave this variable empty if do not want to set up tumblr

<pre><code>
HEXO=""
</code></pre>

### Let's post

so now after all set up done, let's post!
create a markdown file and write the content you intend to post, then execute as this:

<pre><code>
vim post_name.md
----
./post2blog.py post_name.md

</code></pre>

voila, after script execution finished, the same post deployed to your wordpress,tumblr,octopress,jekyll,hexo blog now(same as this post I did).

Have fun!
