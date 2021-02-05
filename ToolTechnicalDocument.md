# Hierarchy window : Technical Document
## Context

I had to make a hierarchy window tool for the AerRacers project of the 3rd years. This tool is for the Neko Engine, which is a custom engine in c++, and I am using DearImGui to make it.

## Needs for the tool

The hierarchy needs to be able to view entities, their children, select an entity, drag and drop them as well as add or delete an entity.

## Interface overview

The window is called Hierarchy and you can see each entity and their children.

![](https://eleonoradps.github.io/BlogpostTool/googledocsUM1.PNG)

## Description
### View and select entities
To see an entity's children, you need to click on the arrow. When you do so, the entity you selected is highlighted.

![BPTGif5](https://user-images.githubusercontent.com/55788730/107032555-50a99f80-67b4-11eb-9495-9e9bd6adb633.gif)

### Add/Delete entity

To add an entity, you need to make a right click near an entity in the Hierarchy window, then you select the "Add Entity" option and you have now a new entity.

![BPTGif6](https://user-images.githubusercontent.com/55788730/107032662-733bb880-67b4-11eb-9583-319ca62abf84.gif)

You can add as many entities as you want.

![](https://eleonoradps.github.io/BlogpostTool/googledocsUM7.PNG)

To delete an entity, you need to select it, right click, then click on the "Delete Entity" option.

![BPTGif7](https://user-images.githubusercontent.com/55788730/107035028-d9760a80-67b7-11eb-8c8c-9c0df6dc8027.gif)

### Drag and Drop entity

To drag and drop an entity, you need to left click on the entity of your choice and hold the mouse button down. Then you drag it over the entity of your choice and release the left mouse button. Entity 7 is now a child of Entity 6.

![BPTGif4](https://user-images.githubusercontent.com/55788730/107029753-db3bd000-67af-11eb-8e4e-8e7d44e1b21a.gif)

## Implementation
### Show window

First, in order to have a window for our Hierarchy we need to show it in the editor with the DrawImGui function.

![implementationBPT](https://user-images.githubusercontent.com/55788730/107040882-180fc300-67c0-11eb-8a80-294ed0a2c30e.PNG)

### Show entities

To show our entities, we use a string for the Entity text and add a number to differenciate them.

![implementationBPT2](https://user-images.githubusercontent.com/55788730/107042371-f57ea980-67c1-11eb-87c8-404d2f56d6a1.PNG)

![implementationBPT3](https://user-images.githubusercontent.com/55788730/107042635-45f60700-67c2-11eb-9f25-b0c2b6e04125.PNG)

### Display children

Now, we need to display their children. For this, you make a loop that checks all entities. After that, if the entity is a child of the entity you're checking, you display it in the Hierarchy.

![implementationBPT4](https://user-images.githubusercontent.com/55788730/107043010-b2710600-67c2-11eb-9842-02d866d79f6f.PNG)

However, when you do that there's a new problem. In the Hierarchy, there will be arrows on all entities, even those that don't have a child.

![UM3](https://user-images.githubusercontent.com/55788730/107043353-2d3a2100-67c3-11eb-9069-af4009641664.PNG)

What we want is that there is no arrow if there is no child.

![implementationBPT5](https://user-images.githubusercontent.com/55788730/107043625-915ce500-67c3-11eb-94c4-3f8d14fedf4e.PNG)

![googledocsUM10](https://user-images.githubusercontent.com/55788730/107043874-dd0f8e80-67c3-11eb-9d75-954ad058a0ba.PNG)

### Add and Delete entities menu




## Encountered problems
### Show entities individually

My first problem was showing each entity individually. What I had in the beginning was the Hierarchy showing the number of entities :

![](https://eleonoradps.github.io/BlogpostTool/part1.PNG)

Where entities were created in a Hierarchy test :

![](https://eleonoradps.github.io/BlogpostTool/testhierarchypart1.PNG)

With this code :

![](https://eleonoradps.github.io/BlogpostTool/hierarchycpppart1.PNG)

The problem was solved by making a loop that gets all entities and shows them all individually with a number.

![](https://eleonoradps.github.io/BlogpostTool/BPT.PNG)

### Show children and loop

The other problem was being able to have a child of a child of a child etc. At first the code was only able to check wether he was the child of the parent or not and show it in the Hierarchy. I made a DisplayChildren() function which makes it able to keep on having children with no limitations. The DisplayChildren() function is called in the DrawImGui() function.

![](https://eleonoradps.github.io/BlogpostTool/BPT1.PNG)

![](https://eleonoradps.github.io/BlogpostTool/UM3.PNG)

### Select an entity

I had a few problems with making an entity selectable. No matter what I did, it wouldn't show the entity being selected, or it would put a color on all entities. What I needed to do to make it work was to make sure the selected entity had a flag on it (because when I first tried making the entity selectable, I wasn't making sure that the entity was selected first before trying to show in the Hierarchy that it was).

![](https://eleonoradps.github.io/BlogpostTool/BPT2.PNG)

![](https://eleonoradps.github.io/BlogpostTool/BPT3.PNG)

![](https://eleonoradps.github.io/BlogpostTool/UM4.PNG)

![](https://eleonoradps.github.io/BlogpostTool/UM3.PNG)

## Links

**Engine** : Neko Engine [https://github.com/EliasFarhan/NekoEngine](https://github.com/EliasFarhan/NekoEngine).

**Hierarchy branch in AerRacers Project** : [https://github.com/SAE-Institute-Geneva/AerRacers/tree/tool/engine/inspector_hierarchy_prefabs](https://github.com/SAE-Institute-Geneva/AerRacers/tree/tool/engine/inspector_hierarchy_prefabs).




