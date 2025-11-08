---
title: "Parallax-corrected cubemap"
date: 2025-11-01
draft: false
description: "a description"
Type: "highlight"
weight: 400
---
![Alt text](featured.gif "300px")

This technique uses a box approximation around reflected geometry, that represents the volume captured in the cubemap. The cubemap sampling position is then determined by the position at the boundary of the box, after reflecting a ray against the ground, when starting from the camera. A final sampling ray is generated from the origin of the cubemap towards this boundary location, and used to sample the cubemap itself.

This fixes some stretching and discontiuation in reflections we'd normally see in cubemap reflections, at the cost of a bit more computational cost. 

See Sebastien Lagarde & colleagues [paper](https://seblagarde.wordpress.com/wp-content/uploads/2012/08/parallax_corrected_cubemap-siggraph2012.pdf)