---
layout: post
title: Docker for dummies (aka Product Owners)
excerpt_separator:  <!--more-->
comments: false
published: false
---

## Container Love
Docker entered the scene just around the time when I transitioned from development into a product owner role. Thus, I've never actually had any hands on experience with it myself, which I feel it's time to rectify.

As with other posts on this blog, this will most likely not be of interest to anyone but me and definitely not to people already familiar with Docker. This is primarily a way for me to process my own thoughts while learning on a new subject and might thus contain misunderstandings and what-not.

Oh, and the headline refers to the excellent song by **Philip Boa** by the way, which isn't at all related to Docker.

### What is it good for - absolutely ...?
>A Docker container is a software bucket comprising everything necessary to run the software independently.

Based on what feels like common sense; my interpretation of this is that assuming your computer runs a OS with Docker support, and you have Docker installed, all needed to install and run new software would be contained inside a single file that just needs to be uploaded to the server and then called with some type of execution command.

What problem this solves would be things like needing AMI images **insert link** to contain a full replica of the server **as they can't be combined?**, where Docker containers can be mixed and matched and deployed separately from each other.

Similarly, build scripts like Chef **insert link** which for a server setup need to be run to install all software every time a new server is started (which also means that if you perform an update to the environment, it would have to be replicated across all servers).

----------------------

**Question:** What does statements like `Debian is the base image` mean? Can Docker run without an OS already installed on the server?

**Answer:** Yes. The base image generally represents an operating system, and with additional images added on top of it. Unsure how this works though, is Docker itself an OS?

-------------------------

### Images, containers and question marks...

A **Docker image** is a collection of files that makes up the software application. Every update to the image creates a new layer. _This seems to suggest_ that images shouldn't be updated, rather when updates are performed, a new image would be created to keep the image single layer.

```Exactly what these layers mean remains unclear, as well as how they impact performance (which I assume they do). Let's leave that for now though.```

A **Container** in Docker world is a stack of images that are glued together by a read-write layer. When running the container, it assembles all the read-only images and performs the changes added in the container layer, meaning all the software contained within becomes one big executionable that can be run.

-------------------------

**Question:** What is the difference between running a container and using `docker commit`? Why use docker commit if it always creates a new image for the most recent changes?

**Answer:** You don't run a container, you run images. A container is a stack of images used for development, and will be transformed into an image itself (**???**) that then can be deployed into production

---------------------------

A docker container contains a base image, and a bunch of images stacked on top, of which some might be custom glue images created by committing the current state of changes added in the container.

When an image is complete and ready to be deployed, it is pushed to a **Docker Registry**, from where it can be fetched by anyone with access.

-----------------------------

**Question:** Why are the terms container and image used interexchangeably if they are two different things? Downloading a HelloWorld image, but then it says we ran a HelloWorld container.

**Answer:** You download an image, but when running it, it is automatically run as a container (**???**)

-----------------------------
