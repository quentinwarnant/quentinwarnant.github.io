---
title: "Vertex Animation Textures"
date: 2025-11-01
draft: false
description: "a description"
Type: "highlight"
weight: 700
---
![Alt text](featured.png "400px")

As part of the NBA licensed basketball game I prototyped, we needed to fill the court seats with many animated characters, on mobile devices. The affordable technique we found was to animate the vertices on the GPU, based on textures, often called Vertex Animation Textures (VAT).

Each texel along a row, represents a vertex in the mesh, at a specific frame.
The colour values represent the vertex position in object space.
multiple rows are stacked below each other in the texture, to snapshot specific frames of the source animation.
In the vertex shader, we gradually move along this stack, and interpolate between the 2 rows we are sampling vertically. The vertex UVs will map to the correct texels themselves.

Interpolation between rows is done manually instead of letting the hardware do it, because as we reach the end of the stack, we need to interpolate between the last row and the first row, which are not next to each other.

In the image below, you can observe we actually packed 2 animations together.
I built a system to mark up metadata, to interpolate between multiple animations, so we could have characters transition from idle into cheer, and back

![Alt text](topshot-animtex_vertex_crowd-1.png "500px")
