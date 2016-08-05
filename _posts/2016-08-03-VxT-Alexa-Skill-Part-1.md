---
layout: post
title: "VxT Alexa Skill - Part 1"
date: 2016-08-03
excerpt: "This is part 1 of a series of who knows how many parts, that will follow my journey along making this app."
tags: [alexa, skill, distance, project, vxt, google, api,]
feature: http://i.imgur.com/YfuBQW6.png
comments: true
---


# Summary - VxT Alexa Skill

For my final Alexa Skill in this round of projects, I decided to make a custom skill that interacted with the Google Distance Matrix API to calculate travel times to specific locations that you can name. I needed to learn a lot to get this accomplished.

This is part 1 of a series of who knows how many parts, that will follow my journey along making this app. I'm going to cover the tools I've chosen and why as well as the basic function of the app to handle simple handlers before getting into the crazy stuff.

## Tools

I'm using Amazon Web Services to host my app in a lamda function. Luckily, Amazon also has a great simple, lightweight solution for storing user data called DynamoDB. DynamoDB is a noSQL database, meaning it stores everything in what looks like a JSON hash with key/value pairs. It also integrates easily with AWS Lambda. These technologies were simple enough. Next was the API. Now there are a few API's out there for getting distance, but none as roboust as the Google Distance Matrix API. Using a
simple URL that includes my API key, I can find out how far something is from something else, by coordinates, or full address, or just street name and zip code. It's very flexible, and perfect for an interaction model based on voice. There are some API call limits though, so hopefully before then I can think of a way to monetize it. (Not really in it for the money though.)

I'm also basing my skill off some of the sample skills that have been done, cause as my mentor says it, "If someone has already done part of the work, why do it yourself?" **BOOM**

With all this, I'm using Node.js to test it on my local machine with the Alexa-app npm package and alexa-app server. That's something that's been really difficult to figure out thus far, but enough about the tools.

## Problem

I *hate* traffic. I also hate dealing with the Apple's native Maps app, Google Maps, and Waze. I hate typing in an address, and waiting for it to find. I'd rather just ask "Hey how long will it take me to get to work?" and have Alexa tell me while I'm at home. Most people don't like dealing with a maps service, and want to just find out the specific information they need very quickly, without a whole lot of fluff. This is a very simple problem I'm hoping to solve. (Obviously, don't get me started with Siri)

## Proposed Solution

My solution is exactly what I briefly outlined in the problem, a simple app that you can just ask how long it is to a saved location like work, or a friends house, or a hospital (if you're having a baby or something), or a meet up. That's the basic functionality. Now the implementation will be rolled out in a few different versions. Of course, everything will be generated with the Googles DM API to pull information, which is great, cause it'll automatically calculate for traffic information and handle
multiple locations. So if you have multiple stops right in the middle of rush hour, it'll be easy enough to figure out all the estimated travel times for those specific routes. Now that's just the first iteration.

## Steps

The first thing I had to do was design a basic interaction model, which set the framework for how the user will interact with the app, and consequentially how all the functions should work and what the intents are. Now the first one I came up with was not to impressive but it was simple enough for me to get an idea.

    {
    "intents": [
      {
          "intent": "getDistanceIntent",
          "slots": [
            {
              "name": "OriginAddress"
              "type": "ADDRESSES"
            },
            {
              "name": "DestinationAddress"
              "type": "ADDRESSES"
            }
         ]
       },... # More of Amazon's built in intent's are below.

 So as you can see it's just looks like a JSON object, but let me try and clear it up for you.

 * An `Intent` is an action. A function that is triggered by some sort of user interaction. So in my case, the intent is the `getDistanceIntent` and it's function is going to, you guessed it, *get the distance* from the Google DM API.

 * A `slot` is the type of input the user is going to give, so in this case, I have 2 custom slots, `OriginAddress` and `DestinationAddress`. These provide what the values are for what I need from the user.
 <br>
 <br>

 Next I had to set up my actual functions for starting sessions and managing events.

 <br>

 * Event's are exactly what they sound like. Much like the `onClick` in JS, it's configured to listen to an `SessionStarted` event, `OnLaunch` event, and a `SessionEnded` event. Each calls it's own function.

 Here's a snippet of what I did to handle these.

       VxTSkill.prototype.eventHandlers.onSessionStarted = function (sessionStartedRequest, session) {
        console.log("VxTSkill onSessionStarted requestId: " + sessionStartedRequest.requestId
        + ", sessionId: " + session.sessionId);
       };

This was the easy part of the code. The hard part is what I'm currently working on, which is my storage functions.


## The Future as it Stands

There's a handful of features I hope to integrate with this skill as it develops.
  * Picking the best route. There's of course another Google Maps API that can pick the best route to travel so you don't have to do anything but just ask for it.
  * Along with the routes, I want to integrate a texting service, using Twilio, to send people links to their mobile devices with the route already pulled up. So they don't have to type, or wait for location to find they simply:
      1. Ask Alexa how far something is
      2. She response with the travel time for the current time and a best route suggestions
      3. She texts you the link to open up that travel route
      4. You walk out of the house while clicking that link, and hopefully maps is already pulled up by the time you start your car.
  * A location feature so you can simply say the name of a place, and she'll do all ^ that stuff with it.


## Thanks for Reading

I know this was a long one, but I don't expect the rest of these to be short, as this project is a little daunting for where I currently am in my developing journey. Stay tuned for the next post where I'll be discussing the database functions and setup.

**I'm sure you've all been wondering why I've called it VxT instead of something like GetRide or some other silicon valley-esque startup-y name... I'll leave it as a fun little puzzle. If you're clever enough you can figure it out**
