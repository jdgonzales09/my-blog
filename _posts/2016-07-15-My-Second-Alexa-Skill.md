---
layout: post
title: "My Second Alexa Skill"
date: 2016-07-15
excerpt: "The point of the skill was to simply give you a fact about a certain subject when you ask for it. The subject I chose? Leonardo da Vinci"
tags: [alexa, skill, amazon, echo, leonardo, vinci, fact]
feature: http://i.imgur.com/iRLHrEh.jpg
comments: true
---


So, this week has been a week of examining javascript used to invoke Alexa and deal with her various commands and with users voice input. It's been a great learning experience. I started on my second skill, a simple fact skill.

The point of the skill was to simply give you a fact about a certain subject when you ask for it. The subject I chose? Leonardo da Vinci

![Leo](http://i.imgur.com/IUckhOb.jpg)
{: .image-right}



## The Project

This being my second Alexa skill, I was vaguely familiar with the process of creating one using AWS and of course the Alexa Skills Kit. It simply just varied in behavior from my last skill, which was a trivia skill that you can read about [here]('http://jd.netlify.com/my-first-alexa-skill/').

Upon a command such as  `tell me a da Vinci fact`  and Alexa will rattle off some interesting fact about Leo that you may or may not know. He's one of my favorite people in all of history because he did **everything**.

## Take Aways

Even though I am not that familiar with JavaScript at the moment, the toughest part I encountered during this process, was learning how to correctly compress the files I needed for AWS to read them properly as a lambda function. Weird right?

On top of that, I made it a point to examine as much of the code as I possibly could. I know, my facts are placed into an array to be called upon by the function directly below in order to pick a random one out of the group of 30+ facts.

    function handleNewFactRequest(response) {
                var factIndex = Math.floor(Math.random() * FACTS.length);
                    var randomFact = FACTS[factIndex];

JavaScript is still a little foreign to me, but as I develop one more skill in this cycle, I plan to learn a whole lot more.

## Plans

I don't have many plans to extend this skills functionality, except maybe to add a function to ensure that it's doesn't call the same fact twice, until the entire array of facts has been said. Currently it doesn't do that, but I would like to develop that feature on this at some point in the near future.

As for my plans for Alexa Skills, well I have something I'm going to be working on that's pretty cool. I'm in discussion with my mentor about the circumstances surrounding it, but hopefully it'll be something to be released to you in the coming months, and if everything goes like I want it in my head to go, it's going to be amazing.

## As always

Thanks for reading and checking it out! If you have suggestions, inquiries, or feedback, please feel free to leave them in the comments below, or on any other post for that matter.

### Thank You
