---
title: "pulsating worm and pustules"
date: 2025-11-01
draft: false
description: "a description"
Type: "highlight"
weight: 700
---
![Alt text](featured.gif "400px")

This effect is some relatively simple vertex offset animation shader I implemented to create rather disgusting worms swallowing things. Secondly the pustules on the side also grow and glow.
The technique uses vertex colour channels to mark up gradients in one channel, and random values in another channel which is used to offset animations along the gradient.
The offset itself is a simple sine wave curve following the normals of the geometry.

This was used in the Warhammer 40K: Freeblade game