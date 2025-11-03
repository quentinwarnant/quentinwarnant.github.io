---
title: "NBA mobile game"
date: 2019-01-01
draft: false
tags: ["game"]
Type: "other"
weight: 310
---
### Description
This cancelled game was an officially licensed NBA mobile game, which integrated the NBA Top Shot collectibles as part of it's meta game. Players would play quick time events to shoot hoops and avoid blocks from other players on the court. Featuring an async online multiplayer component.

### Role: Senior engineer

#### Contributions:
I headed the prototyping of this game, heading a small team in developig the core game logic and hoop shooting logic. I also developed graphics systems to efficient render animated crowds using vertex animation textures, enable visual variety and integrate efficient SDF-based shadows to attenuate the model's lighting. As a mobile game, a key factor was to support low-spec mobile devices whilst developing these systems. I also developed a system to dynamically customisation player jerseys to feature their names and numbers.

I implemented an efficient crowd animation system using "Vertex Animation Textures". Vertices and normals are over the duration of an animation clip get stored on a row of a texture. Each keyframe is a new row in the texture. In a shared we sample these rows, panning over time, to interpolate between authored keyframes and animate the mesh vertices. I also added support for multiple different animations per character, so they could swap between idle, cheering, etc.

#### Rendering
![Alt text](topshot-animtex_vertex_crowd-1.png "300px")
![Alt text](topshot-crowd_thumbnail_square.png "300px")

A few different character albedo textures could be picked from to add variety. Key pieces of clothing were encoded as greyscale so it could be recoloured at runtime to provide even more variety in colour, whilst sharing the same mesh.
![Alt text](topshot-crowd_atlas.png "300px")

To immerse the crowd into the arena, I implemented an efficient 2D SDF based shadow pass on the crowd charaters
{{< youtube WEnQ27bolQY >}}

I build tools to randomly generate crowd density in the arena, based on texture samples.
{{< youtube Qe-NbNvINy4 >}}

I developed a tool to generate unique jersey player number and name texture assets at runtime. This was key as it wouldn't have been efficient to generate texture for all possible players, or to allow for player customisation. It involved creating a TextMeshPro text asset, with the chosen team colours, distorting the vertices of the mesh to be bent. Then rendering into a render target, which would then be assigned to the player jersey material to be sampled.
![Alt text](topshot-jerseyrenderer.png "300px")
![Alt text](topshot-jerseyrenderer3.png "300px")

#### Gameplay
At one point the game involved a quick-time-event mechanic. I used quadratic functions to calculate the arc the ball should follow when thrown to land at a calculated location (either successful or not depending on the player's input) At other points the game involved more tactical decisions to get through opponents before shooting at the hoop. With meta-game elements having an impact on action success rate.

![Alt text](nbagame_ball.gif "300px")
{{< youtube QdYHWJSn_gM >}}