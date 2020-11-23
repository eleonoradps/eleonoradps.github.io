# Technical Document : Hunting Turtles
## Context

For this project I had to make an online game using the Neko Engine and the rollback for the GPR5100.1 module at SAE Institute Geneva. In this blogpost, I'm going to talk about a few bugs I went through while working on this project.

## Pitch and decisions

Hunting Turtles is a two-player online Top-Down 2D game in which you play as a turtle and must get as much eggs as possible, moving from tile to tile.

That was my idea. However, I went through some troubles and as I kept on losing time trying to make things work, I decided to remove the tile by tile movement from the game.

## Spawning eggs

The first bug I had was when I wanted to spawn an egg. After doing some code I compiled the game and what happened was that my egg would spawn during the start game countdown :

![](https://eleonoradps.github.io/DocTechNetworkNeko/secondbug.PNG)

But when that countdown was over, it would disappear :

![](https://eleonoradps.github.io/DocTechNetworkNeko/secondbug2.PNG)

After going through all the code again and asking for help from colleagues, we finally found the problem which was here :

![](https://eleonoradps.github.io/DocTechNetworkNeko/secondbug3.PNG)

The problem was that BULLET and EGG had the same component ID, making my egg disappear when the game started after the countdown.

## Picking up eggs, score & win

My next problem was picking up eggs and making them count in the score. I was able to make the eggs disappear when the player went on them just fine, however, the score wouldn't update. That was due to the fact that there was health instead of score in the game. I only had to change the code from "health" to "score" and change a few lines of code.
Here's the result :

![cinquiemebug](https://user-images.githubusercontent.com/55788730/99970102-acf74880-2d9b-11eb-9501-1c56ca5da80c.gif)







