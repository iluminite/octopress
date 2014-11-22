---
layout: post
title: "Initial Octopress Setup"
date: 2014-11-22 18:00:06 +0000
comments: false
categories:
  - How To
  - Linux
  - Octopress
  - Github
---

Since we've gotten [this thing](http://octopress.org/) to work, why don't we actually document how we did it.

Start with the [Octopress Docs](http://octopress.org/docs/).

## Ruby Setup

It makes a lot of sense to install virtual environments for Ruby as we would Python. This will keep the Ruby and gems installed for Octopress separate from the host system's Ruby and gems.

[More details here](http://octopress.org/docs/setup/rvm/).


### Install RVM

    % curl -L https://get.rvm.io | bash -s stable --ruby


You can review the script first - it is good to be paranoid, you will give this script full system access through `sudo`.

    % curl -L https://get.rvm.io | less


### Install Ruby 1.9.3 with RVM

    % rvm install 1.9.3 && rvm use 1.9.3 && rvm rubygems latest


Output will be similar to:

    Searching for binary rubies, this might take some time.
    Found remote file https://rvm_io.global.ssl.fastly.net/binaries/ubuntu/12.04/x86_64/ruby-1.9.3-p551.tar.bz2
    Checking requirements for ubuntu.
    Requirements installation successful.
    ruby-1.9.3-p551 - #configure
    ruby-1.9.3-p551 - #download
      % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                     Dload  Upload   Total   Spent    Left  Speed
    100 11.3M  100 11.3M    0     0  1312k      0  0:00:08  0:00:08 --:--:-- 3065k
    No checksum for downloaded archive, recording checksum in user configuration.
    ruby-1.9.3-p551 - #validate archive
    ruby-1.9.3-p551 - #extract
    ruby-1.9.3-p551 - #validate binary
    ruby-1.9.3-p551 - #setup
    ruby-1.9.3-p551 - #gemset created /home/luminous/.rvm/gems/ruby-1.9.3-p551@global
    ruby-1.9.3-p551 - #importing gemset /home/luminous/.rvm/gemsets/global.gems....................................
    ruby-1.9.3-p551 - #generating global wrappers........
    ruby-1.9.3-p551 - #gemset created /home/luminous/.rvm/gems/ruby-1.9.3-p551
    ruby-1.9.3-p551 - #importing gemsetfile /home/luminous/.rvm/gemsets/default.gems evaluated to empty gem list
    ruby-1.9.3-p551 - #generating default wrappers........
    Using /home/luminous/.rvm/gems/ruby-1.9.3-p551
    ruby-1.9.3-p551 - #downloading rubygems-2.4.4
      % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                     Dload  Upload   Total   Spent    Left  Speed
    100  433k  100  433k    0     0  4068k      0 --:--:-- --:--:-- --:--:-- 10.3M
    No checksum for downloaded archive, recording checksum in user configuration.
    ruby-1.9.3-p551 - #extracting rubygems-2.4.4....
    ruby-1.9.3-p551 - #removing old rubygems.........
    ruby-1.9.3-p551 - #installing rubygems-2.4.4..............


### Test Ruby to confirm version

    % ruby --version
    ruby 1.9.3p551 (2014-11-13 revision 48407) [x86_64-linux]


## Octopress setup

More details [documented here](http://octopress.org/docs/setup/).


### Get Octopress source

    % git clone git://github.com/imathis/octopress.git octopress

    Cloning into 'octopress'...
    remote: Counting objects: 10653, done.
    remote: Compressing objects: 100% (24/24), done.
    remote: Total 10653 (delta 7), reused 5 (delta 1)
    Receiving objects: 100% (10653/10653), 2.79 MiB, done.
    Resolving deltas: 100% (5134/5134), done.


### Install Bundler

    % cd octopress
    % gem install bundler
    Fetching: bundler-1.7.7.gem (100%)
    Successfully installed bundler-1.7.7
    Installing ri documentation for bundler-1.7.7
    1 gem installed


### Install Octopress dependencies

    % bundle install


Output will look similar to:

    Fetching gem metadata from https://rubygems.org/........                                                                                                                                                 [18/2888]
    Resolving dependencies...
    Installing rake 10.3.2
    Installing RedCloth 4.2.9
    Installing blankslate 2.1.2.4
    Installing hitimes 1.2.2
    Installing timers 4.0.1
    Installing celluloid 0.16.0
    Installing chunky_png 1.3.3
    Installing fast-stemmer 1.0.2
    Installing classifier-reborn 2.0.2
    Installing coffee-script-source 1.8.0
    Installing execjs 2.2.2
    Installing coffee-script 2.3.0
    Installing colorator 0.1
    Installing fssm 0.2.10
    Installing sass 3.2.19
    Installing compass 0.12.7
    Installing ffi 1.9.6
    Installing tilt 1.4.1
    Installing haml 4.0.5
    Installing jekyll-coffeescript 1.0.1
    Installing jekyll-gist 1.1.0
    Installing jekyll-paginate 1.1.0
    Installing jekyll-sass-converter 1.2.1
    Installing rb-fsevent 0.9.4
    Installing rb-inotify 0.9.5
    Installing listen 2.8.0
    Installing jekyll-watch 1.1.2
    Installing kramdown 1.5.0
    Installing liquid 2.6.1
    Installing mercenary 0.3.5
    Installing posix-spawn 0.3.9
    Installing yajl-ruby 1.1.0
    Installing pygments.rb 0.6.0
    Installing redcarpet 3.2.0
    Installing safe_yaml 1.0.4
    Installing parslet 1.5.0
    Installing toml 0.1.2
    Installing jekyll 2.5.1
    Installing jekyll-sitemap 0.6.3
    Installing octopress-hooks 2.2.1
    Installing octopress-date-format 2.0.2
    Installing rack 1.5.2
    Installing rack-protection 1.5.3
    Installing rdiscount 2.1.7.1
    Installing rubypants 0.2.0
    Installing sass-globbing 1.0.0
    Installing sinatra 1.4.5
    Installing stringex 1.4.0
    Using bundler 1.7.7
    Your bundle is complete!
    Your bundle is complete!
    Use `bundle show [gemname]` to see where a bundled gem is installed.
    Post-install message from haml:

    HEADS UP! Haml 4.0 has many improvements, but also has changes that may break
    your application:

    * Support for Ruby 1.8.6 dropped
    * Support for Rails 2 dropped
    * Sass filter now always outputs <style> tags
    * Data attributes are now hyphenated, not underscored
    * html2haml utility moved to the html2haml gem
    * Textile and Maruku filters moved to the haml-contrib gem

    For more info see:

    http://rubydoc.info/github/haml/haml/file/CHANGELOG.md


### Install Octopress

    % rake install
    ## Copying classic theme into ./source and ./sass
    mkdir -p source
    cp -r .themes/classic/source/. source
    mkdir -p sass
    cp -r .themes/classic/sass/. sass
    mkdir -p source/_posts
    mkdir -p public


## Configure

### Edit `_config.yaml`

Set `url` at the very least, but might as well customize `title`, `subtitle`, `author`, and `simple_search`. We also remove/comment config for all 3rd party services except Github. Still need to verify if this worked as expected.


## Deploy to Github.io

Read and follow [the docs](http://octopress.org/docs/deploying/github/).

Create a new repo up on Github. For the simplest path, keep it empty. In case it matters, Octopress will not step on any existing commits, only add to them.


### Initial github.io setup

    % rake setup_github_pages

### Create an empty post

### Render HTML from source

    % rake generate

### Deploy to Github.io

    % rake deploy


## Setup Octopress source repo

Using Octopress `rake setup_github_pages` and `rake deploy` will manage commits and publishing to Github.io with the `<user>.github.io` repo. We also need a place to store the blog source.

### Create a new git repo to keep the source.

Some people like to put both in the same repo (on separate branches). We will try something simpler for now - two repos. Octopress is managing the repo we deploy HTML to (created as part of `setup_github_pages` and with commits made/pushed by Octopress `rake deploy`), so it makes sense.


### Add the remote URL

Jump to the Octopress repo root and run:

    % git remote add origin git@github.com:user/octopress.git


### Create branch for `source`

    % git checkout -b source


### Initial commit with custom config

    % git add .
    % git commit -m 'Initial commit with empty Octopress blog'


### Push changes to remote git

    % git push origin source


## Using the blog

More [docs here](http://octopress.org/docs/blogging/).


### Generate a new post

Escaping the `[` and `]` was necessary for my shell setup with zsh. This will need to change.

    % rake new_post\["Hello-Octopress"\]


### Edit the post

The YAML header for a post looks like:

    ---
    layout: post
    title: "Hello Octopress"
    date: 2014-11-22 18:00:06 +0000
    comments: true
    categories:
    ---


Disable comments and define some categories:

    ---
    layout: post
    title: "Hello Octopress"
    date: 2014-11-22 18:00:06 +0000
    comments: false
    categories:
      - How To
      - Linux
      - Octopress
    ---

Add content below the header. For help with Markdown, compare [a doc](http://octopress.org/docs/plugins/backtick-codeblock/) against the [doc source code](https://raw.githubusercontent.com/octopress/docs/master/source/docs/plugins/backtick-codeblock/index.markdown).


### Use watch and preview

This will regenerate the HTML with changes made to the blog source and setup an HTTP server on `localhost:4000` and available at `http://localhost:4000`. Use `tmux` to open a window/pane just for this, and be sure to activate the rvm first.

    % rvm use 1.9.3
    % rake watch &
    % rake preview &


## Setup SSH port forwarding

If the source is on a remote system, we can keep `rake preview` on the remote host but view the blog on http://localhost (with our browser), with all communication over SSH.


### Forward localhost:4000 to a remote host

    % ssh -L 4000:remote.host:4000 user@remote.host


### Load http://localhost:4000 and revel with Octopress!

Done.
