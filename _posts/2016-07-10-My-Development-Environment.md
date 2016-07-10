---
layout: post
title: "My Development Environment"
date: 2016-07-10
excerpt: "I’ve only been at it full-time for 6 weeks as a student at Bloc so I have a lot of learning surrounding my development environment, but here’s what I’m currently learning and using."
tags: [vim, environment, apps, tools, workflow, tmux]
feature: http://i.imgur.com/7itocGg.png
comments: true
---

I’m new to Web Development. I’ve only been at it full-time for 6 weeks as a student at Bloc so I have a lot of learning surrounding my development environment, but here’s what I’m currently learning and using.
At the very bottom of this post is the video which inspired me to take on the learning curve of these tools.

![Screenshot](http://i.imgur.com/7itocGg.png)
{: .image-right}

## Text Editor

I used Atom for the majority of my first project with Bloc and for most projects I did before Bloc. It’s a great functional and customizable editor. However, it crashed **ALOT**. I had it on my list to learn Vim as I saw many developers fly through editing with it. I’ve also always been a keyboard shortcut guy. I hate using my mouse when I don’t have to and I love keeping my hands on the keyboard. Vim is perfect for that.

It was really difficult at first, and learning how to set it up and customize it is almost as difficult to learning it. It’s a “model” editor, you’ll understand that in a second.

For example, you don’t navigate around with your mouse, it doesn’t take ANY mouse input by default. You navigate with `h j k l` on your keyboard in what’s called Normal Mode. Then you hit `i` to enter into Insert Mode and you can actually start editing your document. A quick hit of the `esc` key and your back into Normal Mode.

There’s hundreds of shortcuts for Vim. The `>` is just an indication that the keys are pressed in a sequence and not at the same time. All these shortcuts are in Normal Mode. Here’s a few that I use the most:


* ` } or {` to jump by paragraph up or down

* `e` to jump to the end of the next word

* `w` to jump to the beginning of the next word

* `b` to jump back a word

* `A` to start editing at the end of a line

* `I` to start editing at the beginning of a line

* `o` to start a new line below the current one

* `O` to start a new line above the current one.

* `c > a > w` to 'change' the whole word and throw me into insert mode where I can start typing.


These are just a few that I’ve picked up. There’s many more I realized I know by starting to make a list. But if you’re going to try Vim, there’s a few to get your started.

For configuration, that’s a whole world. Instead of spending time managing my own config, I used [“The Ultimate Vim Configuration”]('https://github.com/amix/vimrc') which has plugins like NerdTree to help workflow. It’s been awesome.

### Vim Macros
A great thing about Vim is the ability to record macros. I have one mapped to create div tags if I just type a word and a set of keystrokes after that, so I can create divs very quickly.

## Tmux

Tmux stands for Terminal Multiplexer and it’s use, at least for me, is really simple. I can have multiple terminal sessions in panes within a single terminal window. So I typically have Vim on the entire left half of my screen and then the right half is split vertically into two more panes for my command line. I use  the bottom one for console, IRB, Pry, or my Rails server, and the top one for running tests or executing commands like git, rake, or generation commands.

It’s really nice to not have to constantly switch between a window or tab for Vim, my command line, and then for irb or whatever tool I’m using at the moment. I can see everything update on one screen.

## Command Line

I use [iTerm2]('https://www.iterm2.com/') with [Oh-My-Zsh]('https://github.com/robbyrussell/oh-my-zsh/wiki/Installing-ZSH') installed to just make the terminal display my current git branch and git status. It’s also a bit easier to read and manipulate. Love the configurations I have. I’m experimenting with aliases at the moment, more on that coming soon.

## Google Chrome

This is my browser of choice. I used to love Firefox back in the day, but it became to runtime heavy. Chrome did too, but the amount of developer tools for Chrome, makes it a no brainer for someone who does what I do.

Safari, sorry old friend….

## Final Notes & Video

It’s important to note that Tmux & Vim go way way way farther than what I’m doing with them, but they make my workflow a little bit better so I’ll use them to their full potential once I get there.

Here is a video that inspired me to use such advanced tools, even though I’m a beginner. This man is a Vim and Tmux master and blows my mind every time I watch it.

<iframe width="560" height="315" src="https://www.youtube.com/embed/5r6yzFEXajQ?list=PLM6NV6GkaKAJiLqfuHQq-XisAyNGwgtUo" frameborder="0" allowfullscreen></iframe>

**Happy coding!**
