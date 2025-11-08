---
title: "Ocean waves"
date: 2025-11-01
draft: false
description: "a description"
Type: "highlight"
weight: 200
---
{{< youtube 4TIY-2peKpo >}}

This effect implements ocean waves using Tessendorf's [paper](https://people.computing.clemson.edu/~jtessen/reports/papers_files/coursenotes2004.pdf), using the Fast Fourrier Transform. This [Tutorial](https://dev.epicgames.com/community/learning/tutorials/qM1o/unreal-engine-ocean-simulation) was extremely useful to implement it.

The same technique was used in Sea of Thieves, for it's ocean waves - except it wasn't implemented in Niagara.

Prior to that implementation, I also implemented without the tutorial mentioned above, in  Unity3D, although it visually doesn't shine as much, it did functionally just the same
{{< youtube 1lkvZZXtb-o >}}

And a visualisation of the displacement buffers
{{< youtube 906IWg9-jE0 >}}

Prior to this, I also explored Gersner waves. This combines a series of sine-curve based displacement. It's much more simple, but doesn't scale as well when looking to get the same amount of defail as the (I)FFT approach affords.
{{< youtube QVU7t1wW2yw >}}