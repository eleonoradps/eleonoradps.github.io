# Hierarchy window : Technical Document
## Context

I had to make a hierarchy window tool for the AerRacers project of the 3rd years. I am using the Neko Engine and the tool is for the Neko Engine as well.

## Needs for the tool

The hierarchy needs to be able to view entities, their children, select an entity, drag and drop them as well as add or delete an entity.

## Interface overview

The window is called Hierarchy and you can see each entity and their children.

![](https://eleonoradps.github.io/BlogpostTool/UM4.PNG)

## Description
### View and select entities
To see an entity's children, you need to click on the arrow. When you do so, the entity you selected is highlighted.

![](https://eleonoradps.github.io/BlogpostTool/UM5.PNG)

![](https://eleonoradps.github.io/BlogpostTool/UM4.PNG)

You can select children as well.

![](https://eleonoradps.github.io/BlogpostTool/UM3.PNG)

### Add/Delete entity

To add an entity, you need to make a right click in the Hierarchy window.

![](https://eleonoradps.github.io/BlogpostTool/UM9.PNG)

Then you select the "Add Entity" option and you have now a new entity.

![](https://eleonoradps.github.io/BlogpostTool/UM10.PNG)

You can add as many entities as you want.

![](https://eleonoradps.github.io/BlogpostTool/UM11.PNG)

## Encountered problems
### Show entities individually

My first problem was showing each entity individually. What I had in the beginning was the Hierarchy showing the number of entities :

![](https://eleonoradps.github.io/BlogpostTool/part1.PNG)

With this code :

![](https://eleonoradps.github.io/BlogpostTool/hierarchycpppart1.PNG)

### Show children and loop
### Select an entity

