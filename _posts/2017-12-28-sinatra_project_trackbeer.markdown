---
layout: post
title:      "Sinatra Project: TrackBeer"
date:       2017-12-28 13:44:28 -0500
permalink:  sinatra_project_trackbeer
---

# **Intro**

[TrackBeer](https://github.com/TheInvalidNonce/TrackBeer) is a Sinatra web application built in Ruby that allows you to keep track of your favorite beers. My inspiration for this concept is that like many of you reading this (if any)...I enjoy drinking beer, and not your usual kinds. I also tend to only be able to remember some elements of what I had drank, such as a cool label, or outrageous ABV (alcohol by volume), etc. I figured this would be a good way to solidify one of the main features of Sinatra, a Ruby Library that is similar to Rails, that allows your to utilize CRUD (Create, Read, Update, Destroy). I also personally took some time to go ahead of the curriculum into Ruby on Rails module to have a more solid understanding of how the Model, View, Controller architecture of my app would be designed.

# **Features**

* Users can signup with a unique username, email, and password to create an account.

* Once a user has signed up, users can login to their account in order to Create, Read, Update, and Delete information about their specific beer using RESTful routes.

* Users can add/edit beer information such as Name, A.B.V, Style, Color, Rating, and add comments/notes about the beer.

* Users can also add Brewery information such as Name, Town, State/Region, and Country.

* Only users that created the beer can edit or delete the information for that beer. Currently all beers that are created are viewable if an account is logged in.

# **Application Development Workflow**

Before I got started on writing code, I had to do some research on what features my app I wanted to have, and keep the expectations realistic, but intuitive, and established what was important and relevant for the user to have. By writing out on paper these associations and their related attributes, this helped me understand how many models I would need and what attributes each model should have. Next, I drew out the relationships between my models. 

## **Corneal gem: Get coding now, not later**

It is here that I want to give a shout out to a former Flatiron School student Brian Emory for creating the [Corneal Gem](https://github.com/thebrianemory/corneal). This gem allowed me to dedicate more time towards developing and adding features with the help of setting up a Rails-like application scaffolding for Sinatra. I felt for the purposes of this project, it did not do much work for me that would otherwise have been mundane. It basically set up the file structure of my app, and left me with an organized blank slate to start adding features quickly and give me the opportunity to see how the views of my app would be, without being overkill like some of the generators that exist natively in Rails.

## **Models: Something I am told I am not**

Once I had a good understanding of how I wanted my models to interact with one another, I created the database migrations, along with their attributes. I began to write my models and went into the rake console to test out how the attributes were going to be related. I settled on three models: User, Beer, and Brewery. For the purposes of this app, I mostly utilized User and Beer models, with Brewery being more of a place where I could expand on future features.

## **Controllers: Like the PS4 kind, but for code, and no joysticks**

After making sure that my models were communicating properly, I started to begin working on the signup controller actions first. I implemented RESTful routes in my design pattern when creating controller actions, in addition to the standard ones that the Corneal gem generated for me. 

Once my associations were rock solid I implemented features to validate user-submitted data. I found that most of my time developing was split between the controllers and the views. I had to make sure that I was making commits a few lines at a time, and mostly on one file at a time. 

Since I ran into many issues where editing a controller action for a view would break my app, I had to keep my momentum at a reasonable pace. I very much enjoyed coding the controller actions since they were pretty straightforward in what was needed to be rendered into the view as well as running the logic of each action.

I focused primarily on getting the signup action to work, the login and logout actions, as well as the actions for CRUD functionality. However, I could not just work on the controllers alone, I had to essentially code these in tandem with my least favorite part, but most rewarding aspect of the MVC architecture, the views.

## **Views: See the change you wish to see in the world (of code)**

After a few less than stellar commits towards the beginning of developing this app, I began to get into a good habit of adding one feature of a controller, comitting, then trying to add code to my view to see how my forms, view pages, and necessary redirects were being implemented. I found the views to be the most challenging because of the way Sinatra will error out on you when something was wrong in your controller, or your view.

There were truly some times that Sinatra's backend error page straight up lied to me about what error the line was in. In this case, it was usually about adding an attribute to an object that didn't exist because of the way ActiveRecord keeps track of the information being supplied to it.

After some days of this, I finally got the app looking good enough to be submission ready, with ample room for feature implementations.

# **Future Development**

I really enjoyed developing this app. As I got into a good momentum, I found myself coding for hours and getting excited about adding features that were much more similar to real world applications. However, for the purposes of completing the Flatiron curriculum, I will be only adding some more stylistic features in the future since I have other ideas for the next portfolio project as I reach the last 1/3rd of the Rails module.

Some ideas that come to mind:

* Implement bootstrap to give the app some style
* Give users the ability to have favorite breweries.
* Allow users to share their lists of favorite beers
* Allow users to upload images of their favorite beers

I hope this blog post was helpful to you. 

```<insert shameless donation request>```

If you are feeling overtly generous, feel free to donate to my beer fund here: 13Rc9xCX1wACh1MWwCNmTua61yqk7jPb4G

```
</insert shameless donation request>
```

**And now time for a beer...**


