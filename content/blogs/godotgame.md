---
title: "Godot 2D Platformer Prototype"
description: "A playable level-one platformer prototype focusing on crisp player movement, tilemap integration, and sprite animations."
timestamp: 2026-05-15
---

<video autoplay loop muted playsinline width="100%" style="border-radius: 8px; margin-top: 20px;">
  <source src="\images\game.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>
*A quick gameplay demo of the compiled Level 1 executable.*

## Overview
This is a 2D platformer prototype I built using the **Godot Engine**, drawing visual inspiration from classic 8-bit titles. While it is scoped to a single "Level 1" environment rather than a fully polished commercial release, it represents a complete start-to-finish engine workflow that I successfully compiled into a playable standalone `.exe` file. 

## Technical Implementation
My primary focus for this build was establishing a clean asset pipeline and writing solid foundational code in **GDScript**.

* **Player Movement & Physics:** Programmed fluid horizontal movement, gravity scaling, and crisp jumping mechanics from scratch to ensure the platforming felt responsive.
* **Collision Detection:** Configured tilemap boundaries and kinematic body physics so the character interacts accurately with the environment's platforms and obstacles.
* **Audio Integration:** Imported external audio files and scripted looping background music (BGM) to bring the level to life.

---

## Character Art & Animations
To give the game its retro feel, I designed and sliced all the custom assets myself. 

![Character Sprite Sheet Breakdown](/images/char.png)
![Character Sprite Sheet Breakdown](/images/enemy.png)
![Character Sprite Sheet Breakdown](/images/coin.png)
*Custom character states including idle, walk cycles, and jumping frames.*

![Environment Tilemap](/images/tile1.png)
![Environment Tilemap](/images/tile2.png)
![Environment Tilemap](/images/tile3.png)
*The seamless tilemap pieces used to paint the level environment, including platforms, water, and background elements.*