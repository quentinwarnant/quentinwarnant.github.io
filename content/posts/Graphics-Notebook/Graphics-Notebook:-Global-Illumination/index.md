---
title: "Graphics Notebook: Global Illumination"
date: 2025-11-01
draft: false
description: "a description"
tags: ["notebook", "gi"]
---
> This page is part of my "graphics notebook" series, where I keep notes on graphics concepts as I learn about them, to serve as a reference.

# Global Illumination

Global illumination is the phenomenon describing all lighting contributions in a scene, which would occur in real-life scenarios.

It includes Direct lighting, Indirect lighting, reflection, refraction, diffraction, subsurface scattering, Dispersion

## Direct Lighting
This is the simplest form of lighting, it represents the direct line of sight between a surface and a light. if there are any blockers in between, then the surface is in "shadow".

## Indirect lighting
This is caused by light bouncing against surfaces, and reaching points that were not directly lit. The intensity is reduced as some of the energy is lost during the bounce, but it is still key to convey realistic lighting. Most scenes are in fact indirectly lit. Think of light bouncing around  in a room after entering through a window, the interrior wall in which the window sits is lit despite being on the opposite side of the entering source light.

Even diffuse lighting will bounce around the scene, and causes "colour bleeding", where the colour of one surface appears on another nearbyone.

Global Illumination's biggest job is to solve for this.

## Reflection
Depending on how glossy a material is, light reflects against it in a clean & uniform way or in lots of random directions. This produces different results. a mirror like surface will produce a sharp reflection of a different part of the scene. Whereas a rougher surface will cause rays to travel in many different directions and produce a more diffuse end result.
The product of relfection is a ray of light, bouncing against Surface B, then bouncing into Surface A (the glossy surface) and showing the lighting of Surface B on Surface A, before reaching our eye.

## Refraction
During the light ray collision with a surface, some of the light is reflected, and some enters the surface of the object, which can be observed in Tranparent or translucent materials. The direction of the penetrating ray is changed based on the "index of refraction" concept, and causes a bending of this incoming ray.
The index of refraction is calculated as a property of the mediums through which the incoming ray was traveling, and the new surface. Scientists have documented different IoR values by observing the real world, and produced values for glass, plastic, etc.
Refraction is important to model non-opaque materials in the scene, and light ray accumulation in spots due to multiple areas refracting to the same location, or to produce distorted views.

### Subsurface Scattering
SSS is a result of refraction, where light bounces once or many times within the surface of the object before exiting and reaching our eye. This can be seen in candle wax illuminated from the flame within, or earlobes illuminated from behind

## Diffraction
Bending of the light waves, around the edges of an opaque surface or through a narrow gap. Light accelerates coming out of the gap and fill the space behind it to expand into it.
Exemplified as the rainbow effects on CDs.

## Dispersion
This is the effect of light waves phases are accelerating at different rates, separating the white light into it's components. Also seen in chromatic aberation effects

# Radiance Caching
Global illumination requires many (infinite) light bounces across the scene and end up in our eye to experience it correctly. This is very expensive to do in real-time.
One way to help address this is to cover a scene in light probes, which will encode the direction light is travelling in space, so that they can be re-lit at runtime, but don't need to figure out the direction of all the rays, over and over again - each frame, this is called Radiance Caching.
Spherical Harmonics are used to encode this information on each probe.
Probes are usually placed at the surface of the geometry, not in empty space - to closely represent the light at those geometrical surfaces.

It's impractical to cover the whole scene with probes at a very high density, so we interpolate between nearby probes instead

## Irradiance
Irradiance is the amount of light arriving at a location in space, it's dirrectionless and informs diffuse lighting.

# Ray-Tracing vs Path-Tracing
Ray-Tracing and Path-Tracing are similar algorithms that shoot rays in a scene and light up the world surfaces which are then experienced by the camera. This differs from Rasterisation, where the objects would first be rasterised onto the screen, and then lit. This older approach didn't properly allow us to have a representation of the scene, outside the view frustum impact the part of the scene we could see.
For example, reflection in mirrors would struggle to render the front of the character in a third person game, or other parts of the room outside the view.

Ray-Tracing bounces rays around the scene (helped by a BVH - bounding volume hierarchy acceleration structure), from the perspective of the camera, into the scene, finding light sources at bounce locations to determine if the surface is lit or not.

Path-Tracing flips the model on it's head (and is more in line with the real-world, but also much more expensive), where light rays are emitted from the light sources, and left to bounce around the scene, until hopefully those rays hit the camera/eye.

The amount of bounces are usually capped, to keep performance in check, but that means the image is not fully resolved and results in noise, that needs to be removed using denoising algorithms.

Some approaches, like ReSTIR re-use previous frame information to guide the current frame decisions on directions to bounce rays - in a hopefully more productive way, to achieve better result - ie less noise, for the same amount of rays than truly random would offer.
