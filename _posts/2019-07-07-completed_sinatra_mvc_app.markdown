---
layout: post
title:      "Completed Sinatra MVC App!"
date:       2019-07-07 22:07:16 +0000
permalink:  completed_sinatra_mvc_app
---


I know it has been a really long time since my last blog post. I have been busy learning coding with Flatiorn but have also taken time off for myself for vacation, starting a new job, and spending time with friends and family. I did struggle with learning and got a little burned out but I am feeling good and have completed my Sinatra MVC app. For this project, I decided to make an app so people (and myself) can track their workouts, specifically crossfit workouts.

**Project Requirements**
1. Build an MVC Sinatra application.
2. Use ActiveRecord with Sinatra.
3.Use multiple models.
4. Use at least one has_many relationship on a User model and one belongs_to relationship on another model.
5. Must have user accounts - users must be able to sign up, sign in, and sign out.
6. Validate uniqueness of user login attribute (username or email).
7. Once logged in, a user must have the ability to create, read, update and destroy the resource that belongs_to user.
8. Ensure that users can edit and delete only their own resources - not resources created by other users.
9. Validate user input so bad data cannot be persisted to the database.
BONUS: Display validation failures to user with error messages. (This is an optional feature, challenge yourself and give it a shot!)

Lot of work todo! First, I let people sign up by using there email and password. Once in, users can add a new crossfit workout with the workout name (crossfit workouts have names, usually after a person, like "Cindy"), workout details, time completed, and rounds completed. Next users can edit or delete their own workouts. Users can view other crossfit workouts in the all workouts section tab up top. Users can also log out of there account and log back in because they signed up (duh.) Users cannot edit or delete other users workouts.

To create the file structure for this app, i used a gem called [corneal](https://github.com/thebrianemory/corneal). This set up the basic MVC set up. For Models, I have a user model and a crossfit workout model. The purpose of the model is to set up the relationships to the SQL table. For example, users in this app have many workouts and crossfit workouts belongs to a user.

Next up are the controllers. The controllers are like the waiters/waitresses in this scenario. They bring the information from the kitchen(model) to the table(views). In this app i have a users controller, crossfit workouts controller, both of which inherit from the application controller. With the Application Controller, I was able to enable sessions and register Sinatra::Flash.

Finally, the views page. The view page is what a user sees when going through the website. Views displays the data given to it by the controllers and the information requsted by the user. This is where the html and CSS go.

check out my code [here](https://github.com/tpope0928/crossfit-tracker) and the walkthrough [video](https://youtu.be/WkX4Mi4XCnw)







