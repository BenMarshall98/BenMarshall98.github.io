---
name: 3D Graphics Part 1
shortname: 3DGraphicsP1
shortcontent: The aim for this coursework was to build a 3D scene using basic graphics techniques in OpenGL.
languages: C#, GLSL
softwareAPI: OpenTK, OpenGL
video: <iframe width="1280" height="720" src="https://www.youtube.com/embed/TgdZnvIz0Zo" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
---
The aim for this coursework was to build a 3D scene using basic graphics techniques in OpenGL. This included vertex buffers, shaders, texturing, lighting, cameras and framebuffers.

To load in each model into the program I implemented a OBJ loader, that would not only load in the model but would optimise the vertices so that shared vertices were only passed into OpenGL once, and would created a file with the pre-optimised version of the model (loaded instead if it existed) resulting in faster load times.

Each model would either be rendered using a texture or a material (diffuse, specular, etc defined within the program) using Phong lighting. While implementing texturing and lighting I was looking ensuring that the normal also faced in the right direction (using the inverse transpose model matrix), during which I ended up looking at normal mapping. I decided to have a go at implementing normal mapping.

The first step that I looked at with normal mapping was creating the tangent, bitangent from the existing model data. This was a step that I added to the end of the OBJ loader, also outputting to the pre-optimised file. In cases where the vertex was shared, I calculated the average for both the tangent and bitangent giving a more accurate look to the textured shape.

Once the tangent and bitangent was calculated I then sent the data to the GPU, where a TBN matrix could be calculated and applied to the normal map texture. This step ended up causing a few issues, where the data for both the tangent and bitangent was not being sent up. While this ended up being a simple fix where I did not enable the vertex attribute, by the time I realized that the data was not being sent up, I had implemented the entire process. Which led to me spending a while looking at each step of the process to check if it was right. It was not until I tried to output the tangent / bitangent as the color that I realized that I was not sending the data up, at the time I did not realize that I had to enable the attribute. Since this project I have started to use a software called RenderDoc to aid with the debugging of shaders, which at the time would have been useful.

One of the more advanced requirements of the coursework was implementing Framebuffers, luckily I managed to get framebuffers done without any major issues. With the framebuffer I decided to apply a range of different graphical effects, from grayscale to blur to a 8-bit pixelated effect. For most of the effects I used a kernel to change each pixel. With the 8-bit effect got the average color within a region of pixels, then turned each color channel into one of 8 shades, the whole region would then be given the same color.