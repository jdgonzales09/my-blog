---
layout: post
title: "My First Alexa Skill"
date: 2016-07-13
excerpt: ""
tags: [alexa, skill, amazon, echo, game, thrones, trivia]
feature: http://i.imgur.com/rz5JYlL.png
comments: true
---


After finishing programming foundations with Bloc, I then had to decide on a set of projects to complete. I'm required to complete at least two, but with how fast the curriculum has gone, I have time for three or four. After developing my first gem called 'Kele', I decided to try out the Alexa project. I actually had decided to try it out long before I got to that point in my curriculum... before I even started at [Bloc]('http://bloc.io').

I submitted my very first skill for submission today. It wasn't anything complicated or even amazing or original, just something simple, to wrap my brain around how Alexa works. It's called "Game of Trivia" a trivia skill for Game of Thrones fans.

Here we go...

## Why

In my research, while searching for a coding bootcamp, or school, or degree, I came across a [Course Report]('http://coursereport.com') talk about Bloc and how it wasn't like a normal bootcamp. So that lead me to their website naturally. Then I immediately looked at the price, and was disheartened. Even though it wasn't what I was expecting as far as cost, I decided to keep looking, and I found that Bloc had a program in place for building skills for Alexa. A real world application, where you didn't just build something to test locally, or for just a small group of fellow students, but something that would be released to the public and available for download.

Bloc just started to sit right with me, cause a company that would go through that much effort to set their students up for success was one I'd be ok investing that much time and money in. So, in just browsing through the course material the night before I started, I decided right away I would build an Alexa skill.

## How

Thankfully, the program does a good job of holding your hand and providing the right resources to make this skill. It's built based on Amazon's documentation and example app that new Alexa developers can access from a sample repo. The thing that I struggled with the most was understanding the set up of Amazon's developer portal and their Web Services set up, but it became clear once things got going.

After that, interaction models were interesting. You define exactly how a user interacts with Alexa while your skill is running, so you have to think of every way you would say something. You realize very quickly that there are an absurd amount of ways to say the same thing, especially if you get excited and forget to form complete sentences. I want people to be able to have fun and not have to use 100% amazing grammar and talk awkwardly into this little black cylinder. Conversational, is a good word I think.

## Going Forward

I do have small plans for this going forward. I don't expect it to be maintained on a daily basis, especially cause it's such a basic skill, but I do want to add a couple things to it, maybe for my next sections Alexa project.

* More questions. Currently she only has twenty, as seeding questions for Game of Thrones was difficult at first, but now I know where to look.

* Multiple players and scores. I want friends to be able to compete and Alexa save scores for each turn a player has.

* Maybe eventually also add season functionality, so she can ask season specific questions. If you'd like, it's just a thought.

If you have any suggestions you can leave them in the comments. I can't think of everything.

## Learns

The majority of what I learned was setting up an Alexa skill, testing, setting up proper voice interaction models, and the submission process.

Voice interaction is completely different from visual or touch. The amount of information that can be said by a website or app, or amount of information that can be input from the user from a keyboard, is astounding compared to voice. If you want to develop for voice, keep these things in mind.

* You can only query for very specific pieces of information. General information or long paragraphs being read by Alexa isn't always the most pleasent user experience.

* You can perform quick easy tasks, easily explained by the user in one sentence or less (you know what I mean). If the user has to tell their life story to a talking cylinder, again, it's not a good user experience.

* Options need to be few. If Alexa reads off 20 options, chances are, you won't remember 1-5. Keeping her interaction as concise as possible from both the user standpoint and Alexa responses standpoint will make for happy users.

## That's it

Hopefully the approval process will go well, and I can update you all with a link to the skill. For the few of you that have Echo's, you can download it and try it out for yourself!
