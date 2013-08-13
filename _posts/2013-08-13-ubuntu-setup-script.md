---
layout: post
title: "ubuntu setup script"
category: posts
---
## ubuntu setup script

> install needed tools when I have new ubuntu


- git

```shell
sudo apt-get install -y git
```

- setup.sh

I wrap up all the needed tools I normally use to a shell script, just let it do the configuration. Here is a list of the tools (vim,oh-my-zsh,uberwriter

```shell
git clone https://github.com/airbob/personal-backup/blob/master/setting/setup.sh
./setup.sh
```


###reference
[^1]:[Solarized](http://www.xorcode.com/2011/04/11/solarized-vim-eclipse-ubuntu/)
[^2]:[tmux](https://www.digitalocean.com/community/articles/how-to-install-and-use-tmux-on-ubuntu-12-10--2)
