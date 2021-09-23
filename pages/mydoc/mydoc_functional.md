---
title: Fuctional File (Rename Me Later)
sidebar: 
permalink: mydoc_functional.html
folder: mydoc
---

# Website Setup (Contribution) Documentation
## Overview

1. Installing Jeykll & Prerequisites on a Local Machine

2. Initializing the Site Repository

## 1. Installing Jeykll on a Local Machine

*Note: In this tutorial, sudo apt was used rather than other utilities such as cat. This turorial was performed on Ubuntu 18.04 and 20.04*

Jekyll is the static site generator used for the DANCEOrg site.

The Jekyll [website](https://jekyllrb.com/) is an excellent resource for the installation process. Most of the commands used in this documentation are from the site. 

### Pre-Reqs

Before installing Jekyll, there is a critical prerequisite called Ruby. 

Run command: `ruby -v` to see if ruby is already installed

If Ruby is not installed, here are the separate instructions for LTS 18.04 and 20.04. Both will install Ruby using Rbenv

#### For LTS 18.04:

Optional: sync your WSL clock with: `sudo hwclock -s`

First, update the `apt-get` utility with: `sudo apt-get update`

Install system dependencies: `sudo apt-get install openssl libssl-dev zlib1g zlib1g-dev`

*The following instructions adopted from the techiediaries [website](https://www.techiediaries.com/install-ruby-2-7-rails-6-ubuntu-20-04/)*

Copy, paste, and run in terminal:   

```
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
exec $SHELL
git clone https://github.com/rbenv/ruby-build.git "$(rbenv root)"/plugins/ruby-build
rbenv install 2.7.2
rbenv global 2.7.2
```
After cloning the rbenv installations, close and restart your shell. 

Run command: `ruby -v` and it will return 2.7.2

#### For LTS 20.04:
*Instructions for installation on 20.04 are from the linuxize [website](https://linuxize.com/post/how-to-install-ruby-on-ubuntu-20-04/)*

First, update the `apt-get` utility with: `sudo apt-get update`

Install required libraries and compilers:

```
sudo apt install git curl autoconf bison build-essential \
    libssl-dev libyaml-dev libreadline6-dev zlib1g-dev \
    libncurses5-dev libffi-dev libgdbm6 libgdbm-dev libdb-dev
```

Install the rbenv tool using *curl*: `curl -fsSL https://github.com/rbenv/rbenv-installer/raw/master/bin/rbenv-installer | bash`

To start using rbenv, add `$HOME/.rbenv/bin` to your `PATH` with Bash or Zsh *(Try Bash first)*: 

For Bash:

```
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
source ~/.bashrc
```

For Zsh:

```
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(rbenv init -)"' >> ~/.zshrc
source ~/.zshrc
```

Run: `rbenv -v` to confirm and it should return: `rbenv 1.1.2-30-gc879cb0` 

Now, install 2.7.1: 

```
rbenv install 2.7.1
rbenv global 2.7.1
```
Run command: `ruby -v` and it will return 2.7.2


#### Bundler Install 
Now bundler can be installed with: 

```
gem install bundler
rbenv rehash
```

Run command: `bundler -v` to confirm install. It will return the version that was installed. 

### How to get Jekyll

Now that bundler is installed, it can be used to install jekyll with: `gem install bundler jekyll`

Once complete, confirm with: `jekyll -v` and it should return: `jekyll 4.2.0`


## 2. Initializing the Source Repository

### Cloning the DANCEOrg Repo 
https://github.com/DANCEOrg/site was created to hold and host the DANCEOrg website. 

`cd` to a desired location and run: `git clone https://github.com/DANCEOrg/site` 

This will clone the DANCEOrg repository to a local location that will allow you to update and contribute to the site. Cloners may be asked for credentials. Login with the GitHub account associated with DANCEOrg. 

### Running the Website Locally
Now that access to the site's repository is availble, contributions can be made. 

Before editting any files, `git pull` to fetch all the latest changes from the site's repository into the current branch. 


Serving the site will automatically structure a simple site which can then be ran locally. When editing files, make sure to save the file. This allows for desrired changes to be reflected when the local site is generated for review.  

Run: `bundle exec jekyll serve` to serve the local site. 

The configuration file (.yml file), source, and destination will be set and a local site will be generated. The server address will be listed. Copy and paste the site in your browser or ctrl+click the link. This should present the local site. 

To shut down the serve, return to your terminal & `ctrl+c` to end the local session. 

When satisfied with contributions add then to the site via git: 

```bash
git add .                           # add current folder
git commit -m "<insert message>"    # save a snapshot of these files; there are other variations of commit 
git push                            # share your changes
git status                          # confirm that branch is up to date 
```