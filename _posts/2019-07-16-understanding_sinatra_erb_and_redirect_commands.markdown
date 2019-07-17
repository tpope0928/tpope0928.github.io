---
layout: post
title:      "Understanding Sinatra ERB and Redirect Commands"
date:       2019-07-17 01:09:34 +0000
permalink:  understanding_sinatra_erb_and_redirect_commands
---


My Sinatra project with Flatiron went well! Until I was asked what I seemed was an easy question: What is the difference between a redirect or erb command to handle the routing of a view page? It stumped me! I had the logic correct but I could not explain why? So in this blog post i will dive deeper into erb command and redirect.

After doing some digging, I have found the term idempotency, which is where the application makes the same request multiple times and recieving the same result. This applys to CRUD applications. "Whenever you are writing action routes in Sinatra to create, update and/or delete data, you’re essentially looking to change the state of your application." A GET request simply retreives the data that is there and displays it, whereas POST, PATCH, and DELETE change data. 

Can you guess where I am going with this??

Since POST, PATCH, and DELETE changes data, redirect is used to show that change of state. When doing a GET request,  data is not being changed, you are simply retreiving a page and data that already exists!
