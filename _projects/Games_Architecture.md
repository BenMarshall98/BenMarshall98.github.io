---
name: Games Architecture
shortname: GamesArchitecture
shortcontent: Using Entity-Component-System architecture, implement a game engine. Then use the game engine to build a 3D pacman game.
languages: C#, GLSL
softwareAPI: OpenTK, OpenGL
---
The aim for the coursework for this module was to develop a game engine based around Entity - Component - System (ECS) architecture, then use the game engine to build a 3D pacman game.

From a graphics point of view, this coursework was relatively easy with only a simple HUD, texture objects and a skybox required. I decided to use this coursework to help practice my knowledge from the 3D Graphics module, on top of the required graphics techniques I decided to add Phong lighting to the game and add a minimap of the ‘maze’ to the HUD. At the start of the module I did want to have a go at implementing shadows for this coursework, however by the time I had the core features done, plus a couple of extra features done, I did not have enough time to implement shadows and get it tested.

Of the required graphical techniques I had yet to implement a skybox, while not overly challenging I did initially run into problems where I had the skybox cube rendering at the wrong time, or without depth testing disabled / enabled at the right time, leading to a couple of rendering artifacts. However, once implemented properly the skybox worked no matter where Pacman was.

The minimap proved quite simple to implement, this was achieved by rendering the scene into a framebuffer using a camera above the maze. While there are better ways of achieving the minimap, this showed the location of pacman and the ghosts in relation to the board, which was the main goal for the minimap.

While the game that was being developed was visually a 3D game, all of the objects in the game could only move in two directions X / Z, which ultimately meant that the physics could be simplified to 2D. Each object could be represented using either a circle or a square.

Of all the components / systems in the game the most challenging to write was the artificial intelligence for the ghosts. Each of the ghosts used A* algorithm to build paths to find the player Most of the problems that I had with the AI was with the ghosts moving into walls, leading to the ghost getting stuck until the player moved to a location that caused the algorithm to build a different path. From the start the maze was designed to be 3 units wide, with the ghosts / pacman being 1 unit wide, mainly to prevent collision detection from stopping movement around the board. This proved useful for the AI, the implemented AI was locked to the middle of the path, unless the player was very close to the ghost.

Normally the A* algorithm is good at dealing with concave areas in the map, however whenever the ghost went into a concave area the game would freeze, while unsuccessfully trying to calculate a way out. I believe part of the issue was due to the algorithm trying the same path multiple times, at the time I decided to rewrite most of the AI making sure to include some way of preventing the same path to be taking multiple times, which did seem to resolve the issue.