---
name: Git Tree
Topics: Git
Date: 11/12/2022
---

# Git Tree

You have all probably heard of Git by now. One of the most popular software out there in the industry.
It's a version control software that lets us go back and forth in timelines.
In this blog, I assume you know the basic commands such as **commit**, **Branching**,**Merging**, and **Rebase**.
Since there are a ton of blogs on them, I don't want to spend time explaining the same things.

## Content

- Into To Trees
- Changes To The Tree By Commit
- Changes To The Tree By Branching
- Changes To The Tree By Merging
- Changes To The Tree By Rebase

### Into To Trees

Before we start, I want to give a brief introduction to trees. **What is a tree?** Tree is a data structure where each node **(parent)** is connected to multiple other nodes.
The connected nodes are `children`.

![example img](https://raw.githubusercontent.com/satvik-1203/blogs/main/images/git_tree_1.jpg)

The entire blog will be based on the same Tree, so I'm hoping you understand if the Tree grows huge.
And each node is just a copy of your codebase.

### Changes To The Tree By Commit

Assuming you used Git before, commits are just snapshots of your folder.
Suppose you commit at some point and want to return to that period. You could use a command, and your repo would look exactly like it did then.
Pretty cool how you can go back and forth whenever you want. Let's see how Git does it under the hood.

![example img](https://raw.githubusercontent.com/satvik-1203/blogs/main/images/git_tree_2.jpg)

Looking at the picture, we can say that whenever we make a commit, the head makes a pointer to the child, and the child becomes the new head.
The data structure looks like a linked list, but the differences will be apparent when we start talking about merging.

### Changes To The Tree By Branching

Branching is probably the most incredible thing Git has to offer.
The name version control also comes due to the feature branching provides.
By default, the initial branch is called `main` or `master`.
**What is branching?** Suppose your friend and you want to work on different features, and you want to avoid messing with each other codes by multiple commits overlapping.
You can make a branch, and then any code or commit you write will only exist in your branch, and vice versa, for your friend.

![example img](https://raw.githubusercontent.com/satvik-1203/blogs/main/images/git_tree_3.jpg)

Looking at the picture, branches are children of the node you use the branch command at.

### Changes To The Tree By Merging

Merging is a continuation of branching. Suppose the feature test-2 has been working on is finished.
Test-2 can push it to the main branch, and all the features he worked on will be on it.

![example img](https://raw.githubusercontent.com/satvik-1203/blogs/main/images/git_tree_4.jpg)

### Changes To The Tree By Rebasing

Out of all commands, rebasing looks the most confusing.
It's a lot like merging; however, it's a bit different. Imagine the test-2 and the main branches aren't merged but instead rebased.
Let's see how it turns out.

![example img](https://raw.githubusercontent.com/satvik-1203/blogs/main/images/git_tree_5.jpg)

From the Image, merging and rebasing look very similar. But rebasing is more like just moving the head to another node.
Rebasing can also be done on private branches can't say the same for merging.

I'm hoping by now. We have a clear idea of how the git tree works. Picturing this and making commits and merges, PRs will be much easier.
Instead of just looking at the commands.
