---
name: Development Project
shortname: DevelopmentProject
shortcontent: Use the SCRUM process to design and develop a game within a group.
languages: C++, GLSL
softwareAPI: OpenGL
video: <iframe width="1280" height="720" src="https://www.youtube.com/embed/3yyszO3zhdg" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
---
The development project looked at using the SCRUM methodology with a group project to produce a game. This game was based on the 2D arcade game Tank!

I started off by working on the basic framework for the game, this included classes for using shaders / textures, rendering models and a basic game object. The basic game object class was then extended to create the different types of required game objects. While initial I had wanted to use Entity-Component-System (ECS) architecture to build the game, we ended up using a inheritence architecture as I was the only person in the team to have used ECS at that point.

For most of the project I worked on adding collision detection to the game. For the most part the only collision detection required was OBB-OBB, which dealt with most of the walls and tanks. However, this was extended to include ray-casting to check for line of sight (used in AI), and custom collision detection functions for rounded corners. The custom collision detection functions split the object into more basic shapes, with the collision being detected depending on which of the shapes detected a collision. With the large maps, physics started to become very slow, to deal with this I added a quick check to see if the two shapes were within a given distance.

By the time I got physics done most of the game objects were created and tested on a smaller scale, so I worked on putting the game scenes / objects together. This included testing functionality, fixing or informing the required team member about any bugs / missing features.

Towards the end of the project, we decided to include online multiplayer (at this point local multiplayer was implement by another member of the team). We decided to use a API called Airsoft. While the API was simple to work with from a implementation perspective, we found that for what we needed we could not test the game properly. Since this was late in the development of the project, we decided to drop the feature, however looking back we could have built a custom API for what we needed (had we a bit more time left in development).