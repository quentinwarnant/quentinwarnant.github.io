---
title: "Stencil Buffer cutouts"
date: 2025-11-01
draft: false
description: "a description"
Type: "highlight"
weight: 650
---
![Alt text](cutout1.gif "400px")
This is a stencil based effect, we render the scene (or part of it) twice, and use the stencil of a invisible mesh to pick between the two versions. This allowed to create dynamic holes in the geometry and even see through it, as well as having custom shading at the boundary.

It's an effect I implemented as part of the Age of Sigmar: Realm War game, to create fractures in the world when a character crashes a large battle-axe into the ground.

![Alt text](featured.png "400px")