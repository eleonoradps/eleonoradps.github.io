# Technical document - Voliday
# GPR919 - Lorna Dupuis 

## Introduction

This blogpost will focus on some features I have worked on for this project as a Gameplay Programmer. I have done other features on the project but for this blogpost I decided to focus on only two of them.

## Context

During my final year in Games Programming at SAE Institute Geneva, my classmates and I were told that we had to work together as a team and make a game. This project lasted 8 months. 

We had to work in collaboration with students from other sections as well, the Art team and the Sound team. 

## Project

We called our team “Volcano” and the game is called “Voliday”. Voliday is a city-building game that we developed on Unreal Engine 4 with the artistic direction of “The Legend of Zelda : Link’s Awakening”.

![voliday_blogpost](https://user-images.githubusercontent.com/55788730/164717020-52abdd1d-6640-4478-9227-cc1c51ccec76.png)

The players have to use the different resources and buildings they are given at the beginning of the game to get tourists to come to their island. If they correctly build their islands, they will get more tourists, a good reputation, and increase their income each month and years that pass, eventually giving them the opportunity to have richer tourists and unlock luxurious buildings for the latter.

## Some features I worked on
### AI Prototype

At one point during development, we had to have a prototype of our game where all the main features would be implemented and the game somewhat playable. For this prototype, I had to take care of the AI. 

Our game has an AI that goes to different buildings and spends money then leaves the island. For the prototype, we only needed the AI to move at a certain location, stop for a few seconds, then move again to a different location.

I needed several things to make my AI work :

![aiproto](https://user-images.githubusercontent.com/55788730/164728263-ec32a205-0deb-416f-8a4f-aed110cc56b9.png)

From left to right we have : 

- FindRandomLocation, which is a task where you code a certain type of action you want your AI to do.
- NPC, which is a Blueprint Class Character. We will be able to see it in the scene moving.
- NPC_AI, which is an AI Controller. As it is not something that can be controlled by the player, we need the AI Controller to make our character move on its own.
- NPC_BB, which is a BlackBoard. The BlackBoard works with the Behavior Tree, to make decisions based on what happens.
- NPC_BT, which is the Behavior Tree. This is where we’ll put the list of actions our AI can do.

After linking the NPC with the NPC_AI through the AI Controller Class, we tell the AI Controller to run the Behavior Tree’s code when we start playing. Now that everything is tied together, we can focus on the Behavior Tree.

The Behavior Tree is a decision-making tree. In Unreal, you have the Root that is there, you cannot get rid of it. Then, you can either choose a Selector or Sequence :

- A Selector is a node that executes their children from left to right. They stop executing when one of their children succeeds. If a Selector's child succeeds, the Selector succeeds. If all children fail, the Selector fails.

- A Sequence is a node that will visit each child in order in the Tree, starting with the first, and when that succeeds will call the second, and keeps going down the list. If any child fails it will return failure to the parent and go back up.

![aiproto2](https://user-images.githubusercontent.com/55788730/164729100-62397e85-77dc-49de-8803-f310f053179d.png)

Image source : [https://blog.zhaytam.com/2020/01/07/behavior-trees-introduction/](https://blog.zhaytam.com/2020/01/07/behavior-trees-introduction/)

To make the AI navigate into our world, we also need to put a NavMesh in our scene. To add the NavMesh in Unreal, you can search it in Unreal’s search modes and click on NavMesh Bounds.

![navmesh](https://user-images.githubusercontent.com/55788730/164729333-acc76b3e-eb40-4c0e-998b-c44a997c1b49.png)

This picture is an example of what the NavMesh visually looks like in Unreal :

![navmesh2](https://user-images.githubusercontent.com/55788730/164729419-35541ee3-8903-45b5-8935-bb857ce9aebd.png)

Now, we will make our own custom task in our Behavior Tree called Find Random Location. A task is an instruction we are going to give to the AI.

To make the AI move at a random location in the NavMesh, we use the Get Random Point In Navigable Radius, which is a node that finds all the points inside the NavMesh we put in our scene.

First we get our actor’s location (our character), then in the Get Random Point in Navigable Radius, there’s a radius variable where we can put how far away we want our character to look for a point. But how do we set that random location ? How do we link it ? This is where the BlackBoard comes in. It allows you to communicate between tasks.

In our BlackBoard, we can add a new vector key called TargetLocation.

![blackboard](https://user-images.githubusercontent.com/55788730/164730155-d1b9c4fb-12f8-47a7-8d17-814763bf0030.png)

Now we can tell our task to look for that TargetLocation and link it with the RandomLocation variable through the Set BlackBoard value as Vector function.

Now in our Behavior Tree, we add the already built-in tasks from Unreal Engine called “Move To” and “Wait” :

- Move To tells the actor to move to a certain location and don’t move on until it’s reached its target location.
- Wait is a task that tells the actor to wait for a certain time until going back to execute again the tasks in the Behavior Tree.

Here is how our Behavior Tree looks :

![postmortbt](https://user-images.githubusercontent.com/55788730/164730440-393b3318-0286-4702-a327-3565fec10c17.png)

It goes from the Root down to the Selector and Sequence. Then from the Sequence, it will go from left to right, executing FindRandomLocation (to find a point in the NavMesh where you can move to), then Move To (where the character moves to that point we found earlier) and wait for 2 seconds before going back to FindRandomLocation.

Here is a Gif to show the results.

![techdocai](https://user-images.githubusercontent.com/55788730/164732149-ad9d1d97-0599-49c3-b971-a80342e84451.gif)

### Camera rotation

At some point in our project, we made people play our game to have some feedback on what worked and what didn’t. We realized that all of them at one point wanted to rotate the camera but couldn’t. We decided to add that feature in our game.

What we wanted was that when we right clicked, the camera would rotate around a point on the screen.

To explain a bit better, in our code, we’re going to get the Spring Arm, which is a component that controls the camera depending on what we do with it. It’s “attached” to the camera.

![springarm](https://user-images.githubusercontent.com/55788730/164732412-78e9a100-de7b-4a6b-bfb8-3adfaa140359.png)

With this Spring Arm, we’ll be able to rotate around the Z axis.

We have a function called “Rotate” in our Camera Behavior Blueprint, where we take a 90° clockwise rotation and multiply it by the mouse’s X input and the mouse’s sensitivity. Then we set that actor’s rotation.

In the Update function, we call our Rotate function and use the Is Input Key Down in our Blueprint and set it to Right Mouse Button. Now we can rotate our camera around.

![postmortcam](https://user-images.githubusercontent.com/55788730/164732827-37c28642-3bdf-45c3-99ba-61f0238ae5fe.gif)

## Conclusion

To conclude, it was pretty difficult for me to work on Unreal Engine. I’m not a very good programmer in the first place and it was the first time we did a project on that Engine, meaning I had to learn everything from scratch. I would sometimes lose a lot of time just figuring out how Blueprints worked.#

Even if there were some hardships, I am glad I was able to know more about Unreal Engine and increase my knowledge and skills, which I think will definitely be more useful for me in the future.

Here is the link of the release of the game if you'd like to play it : https://volcanoteam.itch.io/voliday 

