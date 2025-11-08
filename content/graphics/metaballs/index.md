---
title: "Meta balls"
date: 2025-11-01
draft: false
description: "a description"
Type: "old"
weight: 1000
---
![Alt text](featured.gif "400px")

I explored implementing metaballs using [Processing](https://processing.org/), quickly learning the performance cost increases rapidly when resolution increases. To resolve this I learned to also implement the marching square algorithm, and interpolate the lines in each square to make the shapes look smooth.

Without using Marching Square:
<video controls src="01_MetaBalls.mov" width="300px" title="Title"></video>

With the marching square algorithm:
<video controls src="Metaballs_interpolated_uniform.mov" width="300px" title="Title"></video>

Then I decided to explore what it would visually look like to only draw the outline, and not clear the backbuffer, letting the image continuously evolve.
It made for some interesting visuals

![Alt text](metaballs1.png "300px")
![Alt text](metaballs2.png "300px")
![Alt text](metaballs3.png "300px")
