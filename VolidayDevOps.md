## DevOps - Voliday
## GPR919 - Lorna Dupuis

![voliday_blogpost](https://user-images.githubusercontent.com/55788730/164717020-52abdd1d-6640-4478-9227-cc1c51ccec76.png)

## Introduction

This blogpost will focus on my experience as a DevOps for the first time in a game project. I will talk more precisely about my research, what I had to do, my thought process, difficulties encountered, my mistakes and what I learned.

## Context

During my final year in Games Programming at SAE Institute Geneva, my classmates and I were told that we had to work together as a team and make a game. This project lasted 8 months. 

We had to work in collaboration with students from other sections as well, the Art team and the Sound team. 

## Project

We called our team “Volcano” and the game is called “Voliday”. Voliday is a city-building game that we developed on Unreal Engine 4 with the artistic direction of “The Legend of Zelda : Link’s Awakening”.

![voliday_blogpost](https://user-images.githubusercontent.com/55788730/164717020-52abdd1d-6640-4478-9227-cc1c51ccec76.png)

The players have to use the different resources and buildings they are given at the beginning of the game to get tourists to come to their island. If they correctly build their islands, they will get more tourists, a good reputation, and increase their income each month and years that pass, eventually giving them the opportunity to have richer tourists and unlock luxurious buildings for the latter.


## Role distribution

For this project, the Programmers team (my classmates and I) were a total of 7 people with each of us having a distinct role : 

- Oleg Loshkin : Project Manager, Gameplay Programmer
- Solange Schmid : Game Designer, Gameplay Programmer
- William Pepin : Producer, Gameplay Programmer
- Marvin Scharding : UI/UX Designer, Gameplay Programmer
- Vincent Dworak : Lead Programmer, Gameplay Programmer
- Guillaume Jeannin : R’n’D, Gameplay Programmer
- And I, Lorna Dupuis : DevOps, Gameplay Programmer

## What is a DevOps ?

The word DevOps is a combination of the terms development and operations. It’s a combination of cultural philosophies, practices and tools that enhances a company’s ability to deliver better services to their customers.

Their purpose is to help collaborations between teams as a mean to empower them.

## Tools

The platform we used to make our game is Unreal Engine 4.27. Just like any other project, we also needed to save our work somewhere in order to not lose our progress. Therefore, we had a repository on GitHub and later used Perforce.

![logopostmort](https://user-images.githubusercontent.com/55788730/164717806-8513a97b-bb47-4a7c-b605-ed9f3e3875ae.png)

## How I started

At first I wasn’t sure what I was supposed to do as a DevOps. It was all new to me. The role in itself was very confusing to understand. After researching for a bit and talking to students from previous years, I had to adapt my role to the project. Being a DevOps in a big company is certainly not the same thing as being a DevOps in a student project.

As my colleague was in charge of organizing tasks and schedules, I, as DevOps, had to take care of the technical organization. Meaning that I needed to take care of the coding style, GitHub repository, naming conventions, etc. 

### Coding style 

When I first started writing the document, I had no idea what to refer to.

First, I decided to take a look at Unreal Engine’s coding style, since it was the engine we used for the game, to get a better idea how things should be organized and written. It’s a very complete and detailed document : [https://docs.unrealengine.com/4.27/en-US/ProductionPipelines/DevelopmentSetup/CodingStandard/](https://docs.unrealengine.com/4.27/en-US/ProductionPipelines/DevelopmentSetup/CodingStandard/)

However, I quickly realized I couldn’t rewrite all of this and adapt it to us. I wouldn’t have the time since I needed to quickly give the team something they could refer to.

I decided after that to look at what kind of coding style the students from previous years used and contacted them to get their insight and some feedback. It helped me a lot in figuring out how to write my document and make it readable and understandable.

In my document, in addition to the way we had to write variables and functions, I emphasized on the fact we had to put comments. We needed to understand each other’s code, and I also wanted the team to communicate to each other if anyone would find a bug in someone else’s code.

The document is 7 pages so here are a few pictures of what it looks like :

![devopscoding](https://user-images.githubusercontent.com/55788730/164722102-36c64012-fb97-428b-8ef0-ba7ebf2dd8a3.png)

Writing a coding style document for my fellow classmates was a harder task than I had initially thought. I had to take a lot of things into account, as well as all the possible code that could be written and how it could be written while still maintaining some kind of logic that would be easy to remember for everyone.

### Git repository and GitLFS

To save our progress during development, we needed a Git repository. However, we knew that with a project of this scale, we were going to hit the “size limits” of GitHub services. Which is why I had to install an extension called GitLFS (Git Large File Storage).


GitLFS is an extension used to manage large files and binary files in a separate Git repository. Here is a bit an explanation on how I did it :

First, to install GitLFS, I had to download it from this page :  [https://git-lfs.github.com/](https://git-lfs.github.com/)

![sommativecmn6204_3](https://user-images.githubusercontent.com/55788730/164717965-b5014b50-cbfd-4c3a-af40-faf69ff5e549.png)

After it’s downloaded, I made a new Git repository, including a Unreal Engine .gitignore. Then I initialized the repository on Git Bash, and wrote the “git lfs install” command.

![gitlfsmanual10](https://user-images.githubusercontent.com/55788730/164722861-5427132a-2ba1-49e5-9de6-5a60acfc06a0.PNG)

To be able to store all the large files that we want, we have to use the command : git lfs track “* .umap”. Here is a list of all the files that I added to be tracked :

 - git lfs track "*.umap"
 - git lfs track "*.uasset"
 - git lfs track "*.uproject"
 - git lfs track "*.wav"
 - git lfs track "*.fbx"
 - git lfs track "*.blend"
 - git lfs track "*.obj"
 - git lfs track "*.png"
 - git lfs track "*.jpg"
 - git lfs track "*.jpeg"
 - git lfs track "*.hdr"
 - git lfs track "*.exr"
 - git lfs track "*.mp3"
 - git lfs track "*.mp4"
 - git lfs track "*.mov"
 - git lfs track "*.psd"
 - git lfs track "*.mb"
 - git lfs track "*.tga"
 - git lfs track "*.cubemap"
 - git lfs track "*.tif"
 - git lfs track "*.bin.fbx"
 - git lfs track "*.upk"
 - git lfs track "*.udk"

After adding all these commands, I wrote the command “git add .gitattributes”. The .gitattributes file is the file that contains everything we stated earlier to be tracked in the project.

![gitlfsdevops2](https://user-images.githubusercontent.com/55788730/164724336-007e0ce1-237d-48aa-9b57-81d06ec0a969.png)

Then, when all is set, we just need to do as usual, commit and push our changes into our repository.

### Naming convention for each branch

To put a bit of structure and organisation into our repository, I asked the members of the team to name their branches a certain way.

Everytime someone makes a feature, they have to create a new branch with that specific feature in it. Which is why they have to call it “features/name_of_the_feature”. I wanted them to be able to have a branch where they could do their own work without having as many conflicts as we would have if we all worked on the same branch. Knowing our team members, I knew that all of us working on the same branch would have been quite chaotic.

When a feature was done and working, we would have to merge it into the main branch where all our work would be assembled together, called “prototype_gameplay”. We also used this branch as a way of recovering others’ work and use it if needed for our respective tasks.

## Difficulties encountered and my mistakes

In this project, I have made a lot of documentation on how to use GitLFS, the coding style, how to use Git and how to merge, but I quickly realised that nobody read it at all. Some team members weren’t doing the merges correctly or making comments and cleaning the code, everyone was doing things in their own way. At that point, I decided to make a presentation on how to use Git and its commands, as well as how they should be working on Unreal Engine. 

But it wasn’t enough. When we had to put everyone’s features together in one scene for the prototype, there were a lot of problems in understanding what everyone had done in Unreal Engine, it was completely unorganised and we lost a lot of time in refactoring all of it.

My mistakes were probably that I was a bit too trusting of the people I worked with, and therefore expected everyone to follow the rules I had stated for the code. I also did not put any code reviews in place, meaning everyone could do as they pleased. I think that I was also hindered by my personality, since I’m more of an introvert. We were all classmates and I knew that they had personal things to deal with, and in turn didn’t want to bother them.

As DevOps, I was supposed to take care of Perforce, and at the time, it really was something I wanted to do because it was an opportunity for me to learn more about it and broaden my skills. However, a team member was really anxious about us being late in our tasks for the game, and decided to replace me and take care of Perforce without telling me about it.

## What I learned

What I learned from this experience as DevOps is that it’s difficult to put that kind of technical organisation in place. I was often lost and didn't know what to do and how to do it. Considering that I experienced this while being on a small student project, I cannot imagine how difficult it would be to be a DevOps in a bigger company. I feel like it’s a challenging role for yourself, because you have to be meticulous and organised, and how you deal with others as well.

Even though I didn’t have the opportunity to use Perforce as I wanted to, I learned more about what it takes to organise a project on a technical aspect.

## Conclusion

To conclude, I have learned a lot about the specific role of being a DevOps in a team and what it takes. However, if I had to do it again, I would probably choose another role. I do not feel like this kind of job is made for me. Although it was a good first experience, I do not feel like I am the kind of person cut out for it. To me, it felt confusing and you need to be an organised type of person to be able to organise others and give structure in a team, which is something that I lack.

Here is the link of the release of the game if you'd like to play it : [https://volcanoteam.itch.io/voliday](https://volcanoteam.itch.io/voliday)




