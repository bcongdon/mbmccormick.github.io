---
layout: post
title: "Continuous Deployment to Webscript from GitHub, Using Webscript"
---

I have been playing around with [Webscript](https://www.webscript.io/) a lot lately and it has quickly become one of my favorite cloud services. Webscript allows you to create web-based scripts in [Lua](http://www.lua.org/) that can do any number of things. Each script runs on a unique URL and can respond to various HTTP requests or be invoked through scheduled cron jobs. It has a beautiful user interface and it functions as an amazingly powerful IDE right from your browser. You can easily write code, test it, and debug requests from their website.

I've been using this service for a while now for a lot of different things, like: scanning my calendar for birthdays and adding them to my Rememeber The Milk reminders list, checking forecasts to see if I need an umbrella for the next day and adding that to my Remember The Milk list, reminding me to charge my Fitbit if the battery gets low using the Fitbit API, feeding weather data as a PNG to my Kindle display, and tons of other things. You can find the source code to all of the above scripts on my [GitHub page](https://github.com/mbmccormick).

Recently, I was playing around with GitHub webhooks and wanted to create a continuous deployment mechanism for Webscript. This would allow me to keep my webscripts under source control and deploy them as soon as I pushed my changes. I took a look at the [GitHub documentation](https://help.github.com/articles/post-receive-hooks) and the [Webscript API documentation](https://www.webscript.io/documentation#api) and found everything I needed to do this. I created a small script, on Webscript, that reads the GitHub post-receive hook payload and makes a few HTTP requests to the Webscript API to sync the changes. Take a look at the code below:

{% gist mbmccormick/5447302 %}

To use this on your own GitHub repository, just add a webhook with the URL `https://code.webscript.io/github?email=YOUR_EMAIL_ADDRESS&key=YOUR_API_KEY`. Then every time you push to GitHub, your Lua scripts will be deployed to your Webscript account. This is a great way to keep your scripts under source control and streamline the deployment process.

You can check out the full source code and documentation for this [project on GitHub](https://github.com/mbmccormick/webscript-github-hook).
