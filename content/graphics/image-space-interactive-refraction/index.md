---
title: "Glass refraction"
date: 2025-11-01
draft: false
description: "a description"
Type: "highlight"
weight: 250
---
{{< youtube u6jS27ch6h0 >}}

This is the first white paper I implemented, by Chris Wyman 

[An Approximate Image-Space Approach for Interactive Refraction](https://cwyman.org/papers/sig05_approxISRefr.pdf). 

It implements glass refraction, by doing a cubemap lookup, based on the refraction of a look-at ray direction to the surface. It then bends the ray at the surface of the mesh, and again at the back faces. The scene depth is rendered twice, once with the model's backfaces, and once with the model's front faces. which gives us a thickness map, to calculate the refraction angles from. The index of refraction for the material is being animated over the duration of the animation above.

Here we can see a view of the double depth map rendered 
{{< youtube idctX8O8zcs >}}
