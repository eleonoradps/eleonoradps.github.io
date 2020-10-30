# Game Design Document - Hunting Turtles
## 1.Introduction
### 1.1 Elevator Pitch
"Hunting Turtles" is a two-player online Top-Down 2D game in which you play as a turtle and must get as much eggs as possible.
### 1.2 Gameplay Overview

![IMG_3046](https://user-images.githubusercontent.com/55788730/97707557-bef50c80-1ab7-11eb-9788-2dfc35017084.jpg)

## 2.Game Mechanics
### 2.1 3C (Character, Camera, Control)
**Character:**
- The two players are on the same map.
- They have to move box by box.
- There is an egg on each box.
- Players can't be on the same box at the same time.
- There is a point system which counts how many eggs each player picked up.

**Camera:**

It is a fixed camera, and it shows both players playing the game.

**Controls:**

![](https://eleonoradps.github.io/GDDNetwork/NetworkGameplayOverview.PNG)

### 2.2 Win/Lose:
**Win:**

If one of the two players has a higher score than the other, they win.

**Lose:**

If one of the two players has a lower score than the other, they lose.

**Tie:**

If they both have the same score, it is a tie.

## Coding language & Engine
For this game, I am coding in C++ on Visual Studio and using the Neko Engine(https://github.com/EliasFarhan/NekoEngine).



