---
title: "Glitch hologram chromatic aberration"
date: 2025-11-01
draft: false
description: "a description"
Type: "old"
tags: [""]
weight: 1000
---
![Alt text](featured.gif "400px")
This is a simple yet effective effect to implement chromatic aberation in a hologram glitch.
The mesh is rendered 3 times, rendering only one channel of the final colour, using alpha blending. At intervals the position of the geometry is offset in different directions.
There is also a scanline effect applied in screenspace, in the pixel shader, that will darken every even set of rows - of a certain thickness.