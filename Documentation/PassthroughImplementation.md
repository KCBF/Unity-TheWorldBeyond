# Passthrough Implementation

We've summarized masking Passthrough using the Insight SDK [here.](https://developers.meta.com/horizon/documentation/unity/unity-passthrough-gs/#compositing-and-masking) The approach in The World Beyond sets Passthrough as an underlay and reveals it by modifying the application's alpha level. This can be done in two ways:

## Depth Test
The Depth Test solution takes advantage of the standard rendering flow. Apply a DepthOnly material to objects you'd like to be Passthrough (e.g., the hand mesh). This "invisible" DepthOnly material exists in `Assets/MultiToy/Materials`. Note that the render queue is under 2,000.

Caveats with this approach:
* It only works on the entire mesh.
* It doesn't use textures and can't soft fade.
* It doesn't truly erase prior pixel alpha; it just occludes objects physically behind the object.

## Shader Masking
The Shader Masking technique provides more control at the cost of complexity. There are shaders in the project you can use directly (any shaders with "Passthrough" in the name), but for special cases, you'll need custom shaders. When writing masking shaders, consider:
* *Zwrite/ZTest:* Defines if the object's mesh should write its depth to the Z-buffer and read from the Z-buffer for depth testing.
* *Vertex Shader:* Converts the object's mesh vertex positions into a screen position.
* *Fragment Shader:* Colors the screen-space pixel on the object. Sample a texture map here.
* *Output:* Returns some variation of float4(R,G,B,A).
* *Blending:* Defines how the system blends the shader's Output pixel with the existing pixel on the screen.
