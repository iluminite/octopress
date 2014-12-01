---
layout: post
title: "Wrangling in those Misbehaving Docker Containers"
date: 2014-12-01 06:10:00 +0000
published: true
comments: false
categories:
  - Docker
  - How To
---

While docker is all the rave, and for good reason, it is not without its drawbacks. One of the primary reasons we use Docker is to get more done with less work, but there are times when the boxed solution you have found does not work. Fortunately, we can easily take a broken Docker image and fix it up into shape.

## Fix a Bad Image


### `Dockerfile` to the rescue!

Use a `Dockerfile` to create a new image as an extension of the original:

{% codeblock lang:Dockerfile %}
# extend the broken image with your patches
FROM broken/image
# patch up the original
RUN touch /that/missing/file
RUN chmod -R user:user /home/user
{% endcodeblock %}


### Build a replacement image!

    % docker build -t <tag> .
    Sending build context to Docker daemon  2.56 kB
    Sending build context to Docker daemon
    Step 0 : FROM broken/image
     ---> 78ee0694f929
    Step 1 : RUN touch /that/missing/file
     ---> Running in 78ee0694f929
     ---> ade3d87907de
    Step 2 : RUN chown -R user:user /home/user/
     ---> Running in ade3d87907de
     ---> f1cdcfa9ffb8
    Removing intermediate container ade3d87907de
    Successfully built f1cdcfa9ffb8


### Run with your new image!

    % docker run -p 8080:8080 <tag>

