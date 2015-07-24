---
layout: post
title: "The Subversion Fanboy's Guide to Git, Part 1: Why Git is Better"
---

Over the weekend, I made the switch from [Subversion](http://en.wikipedia.org/wiki/Subversion_(software)) to [Git](http://en.wikipedia.org/wiki/Git_(software)). After seeing so many developers and open source projects moving to this new version control system, I decided to do a little research for myself. As many of you might now, Git has recently taken the software development world by storm. It began development in April 2005 by [Linus Torvalds](http://en.wikipedia.org/wiki/Linus_Torvalds), the mastermind behind [Linux](http://en.wikipedia.org/wiki/Linux). After 8 months of development by Torvalds and several colleagues, the 1.0 release of Git came in December of that same year. As for the name, he has this to say: "I'm an egotistical bastard, and I name all my projects after myself. First Linux, now Git."

Now what makes Git so much better (in my opinion) than the rest is that it was designed around the pros and cons of the existing version control systems. Subversion has been around for over 10 years, and [CVS](http://en.wikipedia.org/wiki/Concurrent_Versions_System) has been around for over 20 years. These systems are outdated and many features, such as branching, merging, etc. were added in after the fact. Git however, was built around this idea of branching and merging and makes it easy to visualize your software repository and to execute these functions.

One of the big reasons many developers are switching to Git is because of [Github](http://github.com/). GitHub has exploded with popularity, touting it's "social coding" tagline. At the time of writing, GitHub has a community of 361,000 developers hosting over 1,116,000 Git repositories. The website makes it easy to host source code, manage projects, collaborate with other developers, and explore different open source projects.

Enough about the background, let's talk about Git. Unlike Subversion, Git uses a local repository to store files. As a developer, you would work on some changes and then commit these changes to your local repository or "staging area" as many like to call it. When you are satisfied with all of the changes you've committed to your "staging area", you can then push these changes to a public/private server. Take a look at the image below to get a better idea of typical Git workflow.

![typical git workflow](/images/2012/05/local-remote.png)

Another reason why I switched to Git is because it is much faster than Subversion. I no longer wait for a checkout, a commit, or an update. Git is nearly instant with all of these actions. Take a look at the comparison below:

![git subversion comparison](/images/2012/05/graph.png)

Now let's get into how Git differs from what we're used to in Subversion. Instead of `checkout` like we are used to, Git uses the command `clone` to make a copy of a public repository on our local workstation. To `update` our local copy like we did in Subversion, we would use `pull` in Git.

Like we discussed earlier, when you `commit` in Git, your changes are simply committed to your local repository. Your development team doesn't have access to these changes, yet. To make that happen, you have to `push` your changes. Instead of entering a login credential to access your Git repository, the server looks for a SSH public key.

Another very notable feature of Git is that it allows local branching of repositories. So say you are experimenting with a new feature, but it really isn't worth keeping on the central repository. You can `branch` on your local repository, something that we couldn't even fathom in Subversion. `switch`, `merge`, and `patch` away- all from your local repository. When you're ready to integrate your changes to the public repository, just `push` them out there.

Since Git was designed for Linux users, it's not too friendly for Windows users. However after using it for a while, I really took a liking to Git. It is faster, cleaner, and the features truly outweigh Subversion. My next post will talk about the actual switch, including step by step instructions on how I did it. Stay tuned!
