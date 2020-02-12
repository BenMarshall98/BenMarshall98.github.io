---
name: Global Game Jam - 2020
shortname: GlobalGameJam20
shortcontent: Global Game Jam is an annual event that is run around the globe, with schools and universities hosting it at various locations. The event lasts over the weekend, with the aim for teams of students to build a game based around a theme. This year the theme was ‘Repair’.
languages: C#
softwareAPI: Unity
---
Global Game Jam is an annual event that is run around the globe, with schools and universities hosting it at various locations. The event lasts over the weekend, with the aim for teams of students to build a game based around a theme. This year the theme was ‘Repair’.

I decided to take part in the event for the 2020 edition, forming a team with 2 other people. Like Three Thing Game each member of the team either had very little experience or had not used Unity within the last few years. I had not used Unity since Three Thing Game. As a team we decided to build a 3D game around the idea that a spaceship had crashed landed on an unknown planet, and the astronaut (the player) was required to collect materials dotted around the planet to fix the spaceship. At the same time, the player would need to keep an eye on oxygen levels, the player could either go back to the spaceship or collect oxygen tanks to refill.

We decided that the terrain and the material / oxygen placement would be randomly generated. For this game we saw as a team three separate main tasks; terrain generation, object placement and player movement. I decided to work on the terrain generation.

For terrain generation I started out by using the [following](https://gamedevacademy.org/complete-guide-to-procedural-level-generation-in-unity-part-1/) tutorial to get the base tile, then adapting it to only render tiles around the players current position. Each vertex in the tile was height adjusted using perlin noise to build, based on its position in the world. Which allowed each tile to be removed and added back with the exact same terrain layout, as long as it was in the same place. Once each tile could be created, I worked on a script which would generate / destroy tiles so that tiles only existed within a certain radius around the player.

The material / oxygen placement was done in a similar fashion where each object was placed in a random location within a given radius. Both each object was placed a ray cast was done to ensure that the object was placed at the right height.

At the start of the project we had decided to have the camera first person, which would allow us to avoid making sure that we had a working character model. However, the person working on the camera quickly realised that it would be easier for him to implement the camera using a third person camera, so we ended up changing it to third person.

Once I had finished with the terrain, I worked on the HUD. The HUD served as a way for us to keep track of the number of items collected / oxygen, allowing us to call the required end scene. With the HUD I implemented a simple compass that would allow the player to know where the spaceship was according to the current camera direction.

Like Three Thing Game we made use of Unity’s Collab package, which for most of the event worked in our favor. However towards the end of the event we looked at bringing everyone's contribution together, we had done a few tests with bringing a few of components together, which lead to conflicts in some of the scripts that we had written. While we were joining parts of the code together, we were editing some of the same scripts at the same time with the assumption that Unity had a built-in difference tool, which are version did not (and we did have the means to install one. Luckily, it was only a couple of lines of code that was affected.
