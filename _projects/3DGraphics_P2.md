---
name: 3D Graphics Part 2
shortname: 3DGraphicsP2
shortcontent: The aim for this coursework is to create GLSL shader effects in the software RenderMonkey.
languages: GLSL
softwareAPI: RenderMonkey
---
While 3D Graphics Part 1 was focused on the implementation of basic OpenGL objects and their use, such as texture, VBOs, and shaders. This coursework was focused on the creation of shader effects, as such the software RenderMonkey was used to provide the framework for the coursework.

For this coursework I was tasked with creating a dungeon style scene, using various types of shader effects. As I had focused on Normal Mapping in the previous coursework, this time my focus was on Parallax Mapping. This ended up being the effect used on most of the objects within the scene.

To bring the dungeon to life there were various moving objects such as a snake and bat. Both of which used the vertex shader to move parts of the model in a fashion that would make sense for the given object.

Around the dungeon I paced several touches, each of which had a fire particle effect. This effect simply produced a coloured circle, which would change colour and move upwards depending on the age of the particle. The particles were then blended together to produce the final fire effect.

There were a few glowing objects around the scene. Each object was first rendered into a framebuffer, then from the framebuffer rendered onto a billboard with a different glowing effect.

For certain parts of the coursework the use of RenderMonkey made it easier to complete, for example whereas I had issues with Normal Mapping in the previous coursework due to incomplete data, I had no such issues with Parallax Mapping (which uses mostly the same data) in RenderMonkey as it sorts the data for you. However, I did end up having issues with the software itself partly due to its age. At times the software would inexplicably crash, which seemed to affect newer machines more than older machines. 