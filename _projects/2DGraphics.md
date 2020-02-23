---
name: 2D Graphics
shortname: 2DGraphics
shortcontent: The aim for this module was to use basic 2D graphic techniques to create a 2D scene and use 2D physics to help animate / simulate the scene.
languages: HTML, JavaScript
softwareAPI: None
video: <iframe width="1280" height="720" src="https://www.youtube.com/embed/DlPHhv0hFQc" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
---
The aim for this module was to use basic 2D graphic techniques to create a 2D scene and use 2D physics to help animate / simulate the scene.

As part of the module I learnt about using a scene graph to store the transformations and drawing objects required to build the scene. In my scene I wanted the user to be able create either circles or regular polygons, within the scene. Allowing them to decide the positions, rotation and scale of the object. This did result in a fairly flat scene graph tree, where each object was in a separate branch from each over, only connected at the top.

Graphically the shapes were fairly simple, each polygon was based on a circle, where lines were drawn from regular points around the circle. This allowed the collision detection for the shapes to be simplified to one of three; sphere-sphere, sphere-polygon, polygon-polygon. During collision detection, each polygon was split into lines, where each line was compared to each line in the other polygon, or the sphere.

As part of the creation of each shape, the simulation would be paused, and the shape being created would be constantly checked against the other shapes to ensure that the create shape was not colliding with another shape. If the create shape was colliding it would change colour, and the user would not be able to create it. The user can also add an initial impulse to the shape, allowing it to move around the screen.

Each shape would have friction applied to it as it moved. During the creation of the shape the surface area of the shape is calculated, which allowed me to give each shape a mass proportional to its surface area.