---
layout: post
title: "Install Kivy on Raspberry Pi"
date: 2014-11-22 19:15:30 +0000
comments: false
categories: 
  - How To
  - Linux
  - Kivy
  - Python
  - Raspberry Pi
---

[Kivy](http://kivy.org) is my favorite UI framework. Here is how to install and use it on Raspberry Pi.  More documentation in [the docs](http://kivy.org/docs/).


## Install Kivy

Follow the [docs](http://kivy.org/docs/installation/installation-rpi.html) for installing on Raspberry Pi.


### Update apt for gstreamer:

    % sudo echo 'deb http://vontaene.de/raspbian-updates/ . main' > /etc/apt/sources.list.d/gstreamer.list


### Install system package dependencies

    % sudo apt-get update
    % sudo apt-get install pkg-config libgl1-mesa-dev libgles2-mesa-dev \
       python-pygame python-setuptools libgstreamer1.0-dev git-core \
       gstreamer1.0-plugins-{bad,base,good,ugly} gstreamer1.0-{omx,alsa}


### Install cython with pip

The Debian package is out of date..

    % sudo pip install cython


### Get the Kivy source

Kivy's support for Raspberry Pi and touchscreen hardware is under active development, it is simpler to run the code directly.


### Clone the kivy repo to ~

    % cd ~
    % git clone https://github.com/kivy/kivy
    % cd kivy


### Build c source

    % make


### Update `~/.profile` to include `$PYTHONPATH`

    % echo "export PYTHONPATH=$(pwd):\$PYTHONPATH" >> ~/.profile
    % source ~/.profile
