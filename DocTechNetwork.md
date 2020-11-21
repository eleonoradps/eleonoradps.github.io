# Technical Document : Hunting Turtles
## Context

For this project I had to make an online game using the Neko Engine and the rollback for the GPR5100.1 module at SAE Institute Geneva. In this blogpost, I'm going to talk about a few bugs I went through while working on this project.

## Pitch and decisions

Hunting Turtles is a two-player online Top-Down 2D game in which you play as a turtle and must get as much eggs as possible, moving from tile to tile.

That was my idea. However, I went through some troubles and as I kept on losing time trying to make things work, I decided to remove the tile by tile movement from the game.

## Spawning Eggs

The first bug I had was when I wanted to spawn an egg. After doing some code I compiled the game and what happened was that my egg would spawn but disappear after the start game countdown :

![](https://eleonoradps.github.io/DocTechNetworkNeko/secondbug.PNG)







