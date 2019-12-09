---
layout: post
title:      "CLI Gem Project"
date:       2019-12-09 01:11:16 -0500
permalink:  cli_gem_project
---


For my first project at Flatiron I had to build a CLI gem that uses an API or scraper to gather data from a database published by companies for free to the public, or general information off of the website. I chose to use the poke api resource because well... I love pokemon. When executing the file, the user is prompted simply to type yes or no to the given berry from the list of possible berries. If yes, the URL for the berry's description is pulled and printed. If no, the next berry is listed and the same prompt is given.

The biggest challenge was creating a loop that circled back into the same array of data pulled from the API. I needed to find a way to make this happen because the name of the berry and URL were nested within the same hash. Sometimes I found my stuck in an infinite loop and that was frustrating. I found a simple command CTRL + C that allowed me to exit the loop being run and felt like that really increased my productivity. 

Although this is a very haggard and rough draft of what I would love for a perfect version of this project to be. I feel as though I'm not yet capable to do it in a timely manner. Once I am better at coding I will perhaps return to this project and change certain things. Maybe I could return the URL's contents of the specific berry  pulled. Either way, I feel like I've accomplished another milestone as API's are a very powerful resource. And the capability to manipulate them is now possible.
