---
layout: post
title: "How to Start the Docker Service with Custom Options"
date: 2014-12-01 00:55:00 +0000
published: true
comments: false
categories:
  - Docker
  - How To
  - Linux
---

This is pretty easy to do, but not easy to find in the [documentation](http://docs.docker.com/installation/ubuntulinux/).


### create /etc/default/docker with DOCKER_OPTS

    % echo "DOCKER_OPTS="--dns 8.8.8.8"" >> /etc/default/docker


### Restart the `docker` Service

    % service docker restart
