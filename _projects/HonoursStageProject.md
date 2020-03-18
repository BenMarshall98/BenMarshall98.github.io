---
name: Honours Stage Project
shortname: HonoursStageProject
shortcontent: As part of my dissertation I implemented a Component-Based Game Engine that is capable of producing 3D games.
languages: C++, GLSL, Lua
softwareAPI: OpenGL, Bullet Physics Engine, Lua, irrKlang, Assimp, GLM
---
My dissertation was on Component-Based Game Engines, as part of which I implemented a game engine using Entity-Component-System (ECS) architecture. During the start of the dissertation I was completing the Games Architecture module which also resulted in a ECS game engine. To differentiate the two projects I decided to make the game engine capable of producing ‘general’ 3D games, and to program it using C++ which I had just started to learn the year before.

To implement most of the advanced parts of the game engine, such as physics or audio, I used different libraries or API, allowing me to focus my work on the game engine itself. In each case I wrote an abstract class that would allow another API to be used in place.

At the start of the project I where the entity was just an ID and the components were stored in a set of lists in a component manager. The idea being that if a system used one type of component the list would be optimised for caching. However, towards the end of the project when I was profiling the game engine, I found that finding components took most of the CPU time. In the end I resulted in placing the components in the required entity greatly reducing the amount of time to find a component.

While the project was not graphics heavy, each of the objects were rendered using normal mapping, I did implement shadow mapping. Each of the models that I loaded in were ‘static’. I did have a go skeletal animation, however each time I tried to implement it the model would end up rendering as a mess of triangles. For this I was using Assimp to load in the models, including a few matrices that would be used, the matrices would then be converted to a glm matrix. While I ended up leaving the skeletal animation out of the project, I did do some further testing where I believe I was transposing matrices too many times and in some cases with the wrong matrix (A Assimp matrix is transposed to a GLM matrix).

During the implementation of the game engine, I decided to design it so that each game could be created without using C++. For this I used JSON to load / setup each level from the entities to the systems that would be used in the level, for example the shadow system might be used for one level but not another. Every part of the game engine that, at the time, I believed a developer  might need to interact with I implemented a Lua script that could be called instead. While Lua was quite easy to work with to implement the methods and the gameplay, it did make dealing with classes rather hard. Lua does have class like capabilities, called tables in Lua, however I found that they work best when just using Lua by itself and not for scripting.
