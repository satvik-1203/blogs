---
name: Intro Git And Github
description: Basics of git and github, explaining the tree structure
date: 10/02/2022
---

![banner](https://raw.githubusercontent.com/satvik-1203/blogs/git-github/images/git-github.jpg)

# Git and Github

If you are coming to my blog, I would assume you know nothing about git and github. This is the perfect place to understand what each of it is.

In short, Git is the version control and github is the cloud storage where the project folder is stored.

## What is a version control?

Ever had times where you were like Oh Shit!, this entire code is wrong and I somehow need to go back to the code I written before?
You start Clt - Z ing till you get back to the code you want. But its impossible if you code is distributed to multiple files.
You can't undo all changes in all the files you made changes to. So what other ideas could we use inorder to not mess up our code from one point to another?
Back when I started coding, I used to make copies of the folder before I make new edits to the code.
Suppose I had a project and was just with navbar, and now I want to add extra code to the navbar, instead of adding the code in the same folder, I use to make a copy of the folder and if at all I messed up some code, I used to just go back to my old copy, else I delete my old copy and continue in the new one.

I think reading the above para gives a basic understanding of what version controlling is. Git is way more than just that.

Using git, you can simply make screenshots of your checkpoints and go back to which ever one you want. The cooler thing about git is its branch features.
Suppose you reach a version 1 and you want to start writing code for version 2, and at any give point you want to have a copy of both versions, thats basically branching.
For example, I released a v1 of my app, and now I'm working on Ui changes for v2, once I finish v2, I want to deploy v2 but store the v1 branch just so that, if any problem arises, I could always switch to stable version v1.

At this point you might think, "Ohh I thought this was all Github thing and not Git".
Don't feel bad if you thought that as well, many of us, including me thought that.

Github is basically just a place that stores you codebase. Since it's integrated to Git, we can see stuff like commits, branches, Pull Requests and stuff like that.

There is Github actions and other fancy stuff like, I'll just give an idea what they mean at the end of the article.

The entire idea of git is just a `tree` data structure.

> Each node in the tree is a commit, and each branch is a new branch.

Each commit is a screenshot, or from the example above a copy of the codebase, and branch is a version.
