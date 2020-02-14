---
layout: post
title:      "The Time Has Come"
date:       2020-02-14 03:02:03 +0000
permalink:  the_time_has_come
---


I did it! I finally did it! After alot of trial and tribulation my rails project for Flatiron is complete! For this project I have decided to create a way to track concerts users hae gone too and share their experience at said concert. Although I have built a MVP of the app at this moment I will continue to build more features in the future. For now, users can create a concert that includes artist, venue, city, state, and date. Nex to that you can add your experience of the show the user has seen or see other experiences from other users. Any user can add their experience to a concert, even if not created by the user! I have also added info next to the artist in the concerts index route.


To begin, I defined my mondels and set up my routes. I knew I wanted the models to be users, artists, concerts, and experiences. How they would all relate was the tougher question. To me, it made sense to have the concerts as the center piece. I ended up with a concert having many experiences and many users through experiences.  Concerts belong to an artist. Below is the routes set up:

```
 
  resources :concerts do
    resources :experiences
  end

  resources :experiences
  resources :artists
  
  resources :users do
    resources :concerts
  end
```

This model and route set up allows for access to all routes associated with all users, artists, shows, and experiences. The concerts and users are nested to allow concerts to have access to all experiences and experience attributes and users to have access to all concerts and concert attributes. 

**Controllers**

it was important to me to seperate he controllers and controller actions. After setting up routes and the models, I created a simple login and logout within the user controller. The controller is fairly simple with a create, new, and show actions and then redirecting to the correct path. A sessions controller was then added for authorization and omniauth, which was added alter. Once logged in, I added the concert controller to to let user create a concert. Next is the obvious experience controller which allows a user to share their experience at the concert they went to . You can also add an experience to other concerts that other users have created, if you have been to. This leads me into my next step: Validations

**Validation**

There were some easy and obvious validations. I mentioned Sessions controller and Session. This allows the app to store some data and hold some data about a user that can be read during later requests. I added some more validations in each appropriate model. Rails allows us the :validates option, which makes sure certain attributes are there before submitting to the database. For example, check out the code below:

```validates :venue, presence: true
    validates :city, presence: true
    validates :state, presence: true
    validates :date, presence: true, uniqueness: { scope: :date, message: "already taken" }

```

The venue, city, and state validation makes sure those attributes are filled out before creating a concert. The date has an additional validation of uniqueness where a user cannot attend two concerts on the same date. Therefore, A user cannot create more than one concert on the same date. I am also proud of the custom validation i added to list concerts in decending order on the show page. A user will see the concerts he attended starting with the most recent.

```
def self.concert_date
      order(date: :desc)
  end
```

I know, pretty simple. But i was excited about it! 


**Final Thoughts**

Overall, this was an eye opening experience. I am excited with how far I have come and already have ideas on how to improve this app. I would like to make the app look and "pop" better. I would also like to add more to the artist and add artists page. Maybe a user can create an artist to help track artists they want to see in the future. I can add a feature to track upcoming concerts. Sky is the limit. You can find a link to the Github code [here](https://github.com/tpope0928/Concert-Experience)
