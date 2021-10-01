# CubeViewTexture
A simple Godot project shows strange behavior when using Viewport as texture in CubeMesh

I tried to texture one face of the CubeMesh at one time. Using UV1 (3,2,1) and an image texture, it works fine. But if I change image texture to Viewport texture, it works strangely. Here is how to reproduce the issue.
- Create a root Spatial node.
- Add Viewport Node -> close HDR / change usage to 2D.
- Create ColorRect under Viewport, with the canvas shader code void fragment() { COLOR = vec4(step(UV.x, 0.5), 0, 0, 1);}
- Create a MeshInstance with a CubeMesh under Spatial
- In CubeMesh, Material -> New Spatial Material -> set UV1(3,2,1)
- Set resource to local only
- In Albedo, create viewport texture and load the viewport we create

I expected to see all 6 faces has the same texture, but the "bad.png" is what I got.
