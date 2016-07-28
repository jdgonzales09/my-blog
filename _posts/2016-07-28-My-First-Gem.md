---
layout: post
title: "My First Gem"
date: 2016-07-28
excerpt: "Testing was a bit difficult as I had a total of 0 minutes spent with VCR and the http requests."
tags: [gem, kele, ruby, project, testing, api, http]
feature: http://i.imgur.com/kpd08a2.png
comments: true
---


# Project - Kele Gem

`require 'kele'`

I must have typed that one line of code 1,000 times. I loved every second of it though. With merely small suggestions from Bloc, I built a gem called Kele which interacted with Blocs API for numerous requests.

## The Goal

I was to create a gem that called the Bloc API to get user information, mentor availability, roadmap & checkpoint information, retrieving and creating messages, and creating submissions. The user stories looked a little something like this:

* As a user, I want to initialize and authorize Kele with a Bloc username and password
* As a user, I want to retrieve the current user as a JSON blob
* As a user, I want to retrieve a list of my mentor’s availability
*  As a user, I want to retrieve roadmaps and checkpoints
*  As a user, I want to retrieve a list of my messages, respond to an existing message, and create a new message thread
*  As a user, I want to submit checkpoint assignments
* As a developer, I want to test Kele using RSpec and VCR

## The Tools

This was my first project to solely use VIM & tmux (which I have a blog post about somewhere on here), but that’s entirely irrelevant. I’m just proud of that, and am currently a VIM+tmux promoter.

* HTTParty - generating http requests easily
* RSpec - testing
* VCR - testing HTTP requests without having to constantly actually call the API (more about that later)
* Dotenv - setting environment variables for my tests
* NyanCat Formatter (just for fun)
* Pry - for testing my gem in terminal

## Starting

I started over 3 times for this project. It’s suggested in the curriculum to build it from scratch, however, I decided to go off my own and use bundle to create my gem. After running my first few tests in IRB, I had trouble rebuilding my gem, so instead of fixing that problem (which is an easy fix), I decided to start over using the recommended path. I then went on and thought to myself “this would be so much easier with bundle.” So after encountering an issue that ended up being my development environment, I decided to use bundle yet again. FINALLY, I got truly started.

## My First Method

This was the most difficult. Thanks to the example documentation of HTTParty I was able to make it work. I successfully authenticated a user into the Bloc API with an initialize method. I then used IRB & Pry to directly test the functionality and pull an `auth_token`.

    def initialize(email, password)
      response = self.class.post("/sessions", body: { "email": email, "password": password } )
      @auth_token = response["auth_token"]
    end

It's a very simple method, sending a post request to generate a session using the arguments as the authorization credentials. So, in order to test in IRB, I just need to run `client = Kele.new(email, password)` of course with an actual email and password, and then I'd get an auth token as a response.

## Rebuilding

So I mentioned earlier that I had trouble rebuilding my gem, cause the `.gem` file would already exist after building it once, I figured out I needed to remove the file. I’m 100% positive there is a better workflow than what I did, but here’s a quick step by step that I did every time I had to make a change to my gem:

1. Make change
2. git rm kele-0.1.0.gem
3. `gem uninstall kele`
4. `gem build kele.gemspec`
5. `gem install kele`
6. Test
7. Make change
8. Repeat step 3-8

**E V E R Y  T I M E**

I did add it to my .gitignore, but that only kept it from being pushed not committed. You live and learn I guess.

## Testing

Testing was a bit difficult as I had a total of 0 minutes spent with VCR and the http requests. I was and still am as of the writing of this post, insecure about how I accomplished using it, but nonetheless it was completed.

#### VCR

For those of you who don’t know, VCR records http responses to an object called `cassette` and plays them back over whenever you run your tests, so you only have to make an HTTP request once during your testing workflow. For Bloc’s API it’s not particularly useful, but for something like Twitter’s it’s invaluable. Twitter has a limit on how many API requests you can make in a given time.

>Rate limits are divided into 15 minute intervals. Additionally, all endpoints require authentication, so there is no concept of unauthenticated calls and rate limits. There are two initial buckets available for GET requests: 15 calls every 15 minutes, and 180 calls every 15 minutes.
						>- Twitter API Documentation

So when dealing with limits like that, it’s useful to make the request to the actual API once, then to have it recorded and played back when you run your tests.

All of this was brand new information to me when I started with VCR a couple days ago.

My tests were fairly simple, and not too detailed as I was writing them on my own and for the first time. Looking back on them, I could probably make the more detailed but my project has been submitted already.

Dotenv was a quick and easy learn to configure environment variables for my testing purposes. I didn’t have an example user or anything to use, so instead I used my own credentials for Bloc for all testing, and Dotenv allowed me to do that without pushing my credentials up to GitHub. (Even though I initially forgot to include my `.env` file in my .gitignore, then fixed shortly after the fact.)

#### This is how I used Dotenv.

I generated a `.env` file where I put my credentials I wanted to call:

`EMAIL=[MYEMAIL]`
`PASSWORD=[MYPASSWORD]`

That was it for that, I then inserted `require 'dotenv'` & `Dotenv.load` in my spec and that was it.

When I needed to call those variables, I just put it in like this `example = App.new(ENV['EMAIL'], ENV['PASSWORD'])` and it was no big deal.

This goes beyond just emails and passwords. But auth keys and secret keys can all be used in a .env file that you pass in your .gitignore so as to not be shared with the world.

I’ll definitely use Dotenv in almost everything I do.

## The Worst Part

Probably the worst part, was that I believe Bloc’s API was malfunctioning at the time, and I kept getting error 500’s with post and put requests. I sought out answers and code reviewers, but they all said similar things, “it’s the API”. This was a bummer.

## Conclusion

All in all, I now have learned the basic framework surrounding a Ruby gem and can make my own. I have some ideas for some more in the future as I learn, I’m very happy with the project (with that one exception of course) and I had tons of fun doing it. You should try building a gem if you haven’t yet. Of course everything can be viewed on my GitHub page.
