# Post Mortem - Voliday
# GPR919 - Lorna Dupuis
![voliday_blogpost](https://user-images.githubusercontent.com/55788730/164717020-52abdd1d-6640-4478-9227-cc1c51ccec76.png)

## Context

At the beginning of my final year in Games Programming at SAE Institute Geneva, my classmates and I were told that we had to work together as a team and make a game. This project lasted 8 months. 

We had to work in collaboration with students from other sections as well, the Art team and the Sound team. 

## Constraints

We had a few constraints for this game : 

- It had to be a city-building game
- Playable on PC Windows and in English
- Using what is used in the game industry (Unreal Engine 4, Perforce)
- With the artistic direction inspired by “The Legend of Zelda : Link’s Awakening
- Collaborating with Game Art students and Sound Design students
- Submit the final product April 26, 2022

## Team

For this project, the Programmers team (my classmates and I) were a total of 7 people with each of us having a distinct role : 

- Oleg Loshkin : Project Manager, Gameplay Programmer
- Solange Schmid : Game Designer, Gameplay Programmer
- William Pepin : Producer, Gameplay Programmer
- Marvin Scharding : UI/UX Designer, Gameplay Programmer
- Vincent Dworak** : Lead Programmer, Gameplay Programmer
- Guillaume Jeannin : R’n’D, Gameplay Programmer
- and I Lorna Dupuis : DevOps, Gameplay Programmer

Including us, we were in total 39 people on this project :
- 4 Stakeholders
- 6 Mentors
- 7 Gameplay Programmers
-  Tool Programmers
and other people working in the game industry who helped us and gave feedback to our game.

## Project

We called our team “Volcano” and the game is called “Voliday”. Voliday is a city-building game that we developed on Unreal Engine 4 with the artistic direction of “The Legend of Zelda : Link’s Awakening”.

![voliday_blogpost](https://user-images.githubusercontent.com/55788730/164717020-52abdd1d-6640-4478-9227-cc1c51ccec76.png)

The players have to use the different resources and buildings they are given at the beginning of the game to get tourists to come to their island. If they correctly build their islands, they will get more tourists, a good reputation, and increase their income each month and years that pass, eventually giving them the opportunity to have richer tourists and unlock luxurious buildings for the latter.

## Artistic Direction
As said in the other chapters, the main visual inspiration for this game is “The Legend of Zelda : Link’s Awakening”.

![dalinks](https://user-images.githubusercontent.com/55788730/164717663-75461b65-5115-4d9e-8828-9f89ed141c9c.png)

## Production tools

The platform we used to make our game is Unreal Engine 4.27. Just like any other project, we also needed to save our work somewhere in order to not lose our progress. Therefore, we had a repository on GitHub and later used Perforce.

![logopostmort](https://user-images.githubusercontent.com/55788730/164717806-8513a97b-bb47-4a7c-b605-ed9f3e3875ae.png)

## Organisation

We had 8 months to do this project. Our team, the gameplay programmers, started working on the game in September. Later, during development, the Art team and the Sound Team joined our project. The Art team, instructed by their teachers, had to make the visual assets for our game. The Sound team had to make the soundtracks and sounds of the game.

In order to keep everyone updated on everyone’s progress during development, we had two types of meetings per week. We usually had meetings between us, programmers, with one Lead from the Art Team and one Lead from the Sound team to keep us updated on what was happening in their sections. We called those meetings the “weekly team meetings”. As for the other type of meeting, it was between us, the programmers, and Elias Farhan, our teacher and Head of Games Programming section, who acted as a stakeholder for our game. We made presentations to show him how the project was going, updates from the Art and Sound team, progress of our tasks, etc.

We regularly had these meetings every week for 8 month.

## My role

Just like my fellow classmates, I had the role of a Gameplay Programmer, but, as I said in a previous chapter, we all had another distinct role. Mine was the team’s DevOps.

Being a DevOps in the industry involves a lot of other tasks, but for a project like ours (knowing the fact we are still students in a school), the amount of work I had to do as a DevOps was not as heavy compared to someone who was hired for it in a company.

First, I had to make a coding style document. I needed to write it as quickly as possible, so the team could have some kind of guide when coding for our game. We needed the code to be clear and understandable to make sure everything was organized.

I created the GitHub repository for our game as well. We had to have a platform where we could save everything we would do for this game. Due to the scale of the project, as well as using Unreal Engine, I had to install an extension called GitLFS (Git Large File Storage) to store all the large files we were going to have.

![sommativecmn6204_3](https://user-images.githubusercontent.com/55788730/164717965-b5014b50-cbfd-4c3a-af40-faf69ff5e549.png)

I also gave a naming convention for each branch of the git repository. we had the main branch called “prototype_gameplay” where we would merge our features that were done and working. To work on that specific feature, everyone had to make a new branch and call it “features/name_of_the_feature”.

## Problems encountered

This project felt very mentally draining to me personally. It was my first time working on a game of this scale with so many people and I felt a lot of pressure even though I didn’t have a role as big as being the Project Manager or Lead Game Design.

Due to Covid being there as well, it was hard staying motivated for the work that needed to be done for the school and the game. 

We never used Unreal Engine to make a game before this project, so when we started, we had to learn how the engine worked and it took us some time to get used to it.

Communication was one of the major issues we had as a team. Of course, we knew that it was really important, but we didn’t really know how to do it. Everyone says that communication is key, but it’s easier said than done. We wouldn’t have any news from certain people, or some other people would take other team members' tasks without asking or talking about it. As a DevOps, I was supposed to take care of Perforce, and at the time, it really was something I wanted to do because it was an opportunity for me to learn more about it and broaden my skills. However, a team member was really anxious about us being late in our tasks for the game, and decided to replace me and take care of Perforce without telling me about it. I felt really disappointed at the time.

Another problem I encountered was that I didn’t expect the fact that the team members wouldn’t read the documents I wrote for the coding style. When we did the refactoring, the code was unorganized, unreadable, and we lost a lot of time trying to put it all back together.

I also have a feeling that each team member had a hard time figuring out what our roles involved and what we had to do, which brought a lot of confusion as well.

## What I learned

This project helped me to learn more about Unreal Engine, as we had never used that engine before. I have a better understanding of how Blueprints work now even though it’s still a bit difficult.

I also was able to learn what I was like to be a DevOps and what it involved. I learned that people wouldn’t really read the documents you would make, and therefore should check that everyone’s respecting the rules and naming conventions.

I learned that talking about communication is not enough. Yes we talk about it, we know about it, but actually doing it efficiently is a whole other thing that takes practice in my opinion. And this project helped me see what kind of problems you encounter and how you could possibly solve them.


## Conclusion

During this project, I’ve learned a lot about my strengths and weaknesses.

I still have a lot to learn when it comes to programming, and I need to improve my logic skill. I still have a hard time understanding what things do in the code.

The whole situation with Covid-19 also impacted my motivation and the way I use my time to focus on work.

I am overall glad to have been part of this project, as I’ve learned a lot about what working on a project with many other people from different fields involves and the responsibilities you have when you have a certain role in a team.

In the end, I am proud of what we were able to do.

Here is the link of the release of the game if you'd like to play it : [https://volcanoteam.itch.io/voliday](https://volcanoteam.itch.io/voliday).

