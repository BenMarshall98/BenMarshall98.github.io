---
name: Games Architecture and Networking
shortname: GamesNetworking
shortcontent: Using Entity-Component-System architecture, implement a game engine capable of running a game across multiple PC's.
languages: C++, HLSL, GLSL
softwareAPI: DirectX, OpenGL, Winsock
video: <iframe width="1280" height="720" src="https://www.youtube.com/embed/jXsB46iVNao" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
---
The aim for the coursework for this module was to develop a game engine based around Entity - Component - System (ECS) architecture that was capable of running a game across a network.

The game itself was fairly simple, in the center of the screen there was a pyramid of balls. This pyramid could have a different number of layers, from 3 - 50, affecting how many balls were on the screen. A projectile could be fired from the camera to the center of the pyramid knocking any balls it hits off the pyramid.

The only graphics required was simple lighting on the balls and the floor, however I soon found that rendering each ball individually caused the graphics to be very resource intensive. To combat this I implemented a 'smart' renderer that noted how many times a particular set of resources were being used, if it was over a threshold it would try to load in a instanced version of the shader and render the set of resources using instancing. This allowed even the biggest pyramid to render at a smooth frame rate.

I also decided to implement the rendering as that it would work for OpenGL and DirectX, for this I used OpenGL 4.3 and DirectX 11 as they both had constant buffers allowing the shaders to work in the same way. In the end the only changes required from a end developer point of view was changing a macro value (changing if OpenGL or DirectX was compiled), and providing the equivalent shaders.

Another limiting factor to the game was the physics. For this I used a octree to reduce the number of times it had to run collision detection. The physics also ran on a seperate thread to the graphics allowing both to run for longer without impacting on the frame rate. To prevent the graphics from stopping the physics to request information I used a double buffer which allowed the sycnoization process to happen at the end of the frame.

The most interesting part of the project was the networking side. For this I built two copies of the game scene, one would work with a server and the other a client. The server acts like a master copy, it runs the game at a fixed frame rate, and sends updates to each client as and when required (on a seperate thread).

Each client can run at different frame rates, to compensate for this the server sends a message stating its current time (from projectile first being fired), and the client keeps updating that value, until it told a new value. It then interpolates between the servers time and the clients time and the client / servers ball positions to get the correct client ball positions.