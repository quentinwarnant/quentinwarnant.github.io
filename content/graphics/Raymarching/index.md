---
title: "Raymarching"
date: 2025-11-01
draft: false
description: "a description"
Type: "highlight"
weight: 500
---
![Alt text](featured.gif "400px")

I have always found the topic of Raymarching signed distance fields a fascinating method to generate images procedurally, with infinite resolution.
I followed some of [The art of Code](https://www.youtube.com/@TheArtofCodeIsCool/videos)'s youtube videos to learn my way around the principles, and implemented the effect above in shadertoy [link](https://www.shadertoy.com/view/3d3czj)

I expanded a bit on the tutorials by implementing tri-planar texture mapping, and different texture IDs are returned as part of the raymarching loop, based on metadata in the scene objects.
