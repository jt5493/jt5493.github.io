---
layout: post
title:      "My Javascript Project"
date:       2020-09-05 21:55:55 -0400
permalink:  my_javascript_project
---


This has by far been the most difficult module. Javascript is very fun, but it is definitely not easy. For this blog I am going to write about how I met the requirements (works great as my checklist to make sure I met everything). The application I created is called "Fitter." It will eventually be a social media application for people that enjoy being active. Its purpose is for a way to keep track of your activity and to share and see other friends activity. This project turned out to be way more complicated than anticipated so I did not get to code out all the desired functionality.

Firstly, I have created a rails API for the backend use. I have a workout and a category model with relationships established. They each have a controller using RESTful routing. For the workout model I used the routes: index, create and update, and made sure to use strong params in order to permit the attributes I needed to use. I did not create any routes for the category controller. I will eventually add more routes to increase functionality. I created both workout and category serializers, though I did not use the category serializer (yet). For the serializers I decided to use the fastJSONapi gem to create the JSON data structures that I needed to render. All calls to the server are handled asynchronously using `fetch()` and the data received is in JSON format. On a side not, I decided to use postgres for my database in case I wanted to publish later on.

Once I had all of my fetch calls working and the page was looking the way I intended it to, I started to do some object oriented refactoring. I used three different classed to handle logic that I felt was specific to that resource. The workout class handles assigning the attributes submitted specific to the workout created. I also added to the workout class the logic that renders the workout `div` itself and the edit form. So I did not have to type out the entire find function everytime I needed to grab a workout I added a static find function. The app class is responsible for attaching event listeners so that the edit function will work. Lastly, the adapter class held the functions provided the URL's when called in the index.js and app.js files. Mainly the GET and PATCH fetch calls.

I was required to have a `has_many` relationship in the backend. I accomplised this by having workouts belong to categories and categories having many workouts. The database shows that workouts has a foreign key for categories so that I can call `my_workout.category` to see the category that my workout belongs to and `run_category.workouts` to see all the workouts associated with a specific category.

Finally, I was required to demonstrate client-server communication. The rack-cors allows calls to be made from the frontend to the server when it is running. So far I have three different calls to the server: GET, POST, and PATCH which covers create, read, and update of CRUD. I made sure to use the RESTful routing by making the routes in the workout controller: index, create, and update.

I think I have said this after every project, but this module/project has been the hardest thing I have ever had to which makes me all the more proud to have made it through. I hope to bring this application to fruition.  I am very excited to become more proficient in Javascript mainly because it seems like it is a language with endless possibilities. 
