---
layout: post
title: "Running Docker without sudo"
date: 2014-11-30 12:15:00 +0000
published: true
comments: false
categories:
  - How To
  - Linux
  - Docker
---

Information about [Docker](http://docker.io) suggests running `docker` commands with `sudo`, but I would prefer to use docker as my regular user.

Supposedly this is a documented topic, but I did not look hard enough to locate those details. Either way, it is pretty easy to do.


## For an unpriviledged user..

### Ensure the user is in the `docker` group

    % usermod -G docker <user>


### Restart the `docker` service

    % service restart docker


### Test with `id`

If you have not logged out, `id` will not include the docker group:

    % id
    uid=1000(user) gid=1000(user) groups=1000(user),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),124(sambashare)


Forcing the login, we will see this change:

    % su -l user
    Password: 
    % id
    uid=1000(user) gid=1000(user) groups=1000(user),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),109(lpadmin),124(sambashare),999(docker)


### docker run should work!

    % docker run -i -t ubuntu /bin/bash
    Unable to find image 'ubuntu' locally
    ubuntu:latest: The image you are pulling has been verified
    511136ea3c5a: Pull complete 
    5bc37dc2dfba: Pull complete 
    61cb619d86bc: Pull complete 
    3f45ca85fedc: Pull complete 
    78e82ee876a2: Pull complete 
    dc07507cef42: Pull complete 
    86ce37374f40: Pull complete 
    Status: Downloaded newer image for ubuntu:latest
    root@a91029463b28:/# 


## Done!
