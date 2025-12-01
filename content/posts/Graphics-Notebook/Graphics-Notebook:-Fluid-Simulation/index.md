---
title: "Graphics Notebook: Fluid Simulation"
date: 2025-11-01
draft: false
description: "a description"
tags: ["notebook", "fluid"]
---
> This page is part of my "graphics notebook" series, where I keep notes on graphics concepts as I learn about them, to serve as a reference.

# Eulerian Fluid Simulation (Grid based)
In an Eulerian fluid simulation, grid cells discretise a space and fluid information (like velocity, density, ink, ...) move from cell to cell following the velocity field.
Moving velocity on a grid naively, causes Divergence - aka sinks and sources of fluid. In fluid simulations it is often preferred to follow the Navier Stokes equations, one of which specifies an incompressibility of the fluid, ie no sinks or sources. Therefore Divergent parts of the velocity field need to be removed.
This is achieved through the realisation that any divergent velocity field is a sum of a non divergent and divergent velocity field. The computation of this "divergent" part, is done through first computing the Pressure of the velocity field, and taking the gradient off that pressure field.

Then quantities on the grid like density, ink, ... can be advected along the velocity field - and so is the velocity itself as well.


# Lagrangian Fluid Simulation (Particle Based)
In a Lagrangian fluid simulation, the fluid volume is discretised by particles which represent quantities like described above, and have a position value. Then then undergo velocity forces to move them in 2D or 3D space. Divergence is now not a product of advecting information across cells, but instead from overlapping particles that need to be separated. 

Some key insight is that particles represent an "area" of liquid around themselves.

## PIC / FLIP
To help with resolving this information, a hybrid approach is often preferred, where particles information are interpolated onto a 2D/3D Grid , the pressure solver is applied, and then information from the cells are then interpolated onto the particles near those cells.

PIC and FLIP are two of these hybrid methods. PIC completely interpolates the velocity values onto the particles, whereas FLIP only adds the delta between the current particle velocity value and the change velocity on the grid cells being interpolated to the particle.
Both methods have strenghts and weaknesses, PIC has a large numerical dissipation - causing loss of fast moving fluid detail, whereas FLIP is less numerically stable and prone to exploding.
So it is a popular approach to mix them both together, by running both solvers, and taking 10% PIX and 90% FLIP

# SPH
...