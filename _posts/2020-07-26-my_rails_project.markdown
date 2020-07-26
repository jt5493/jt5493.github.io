---
layout: post
title:      "My Rails Project"
date:       2020-07-26 05:33:33 +0000
permalink:  my_rails_project
---


For my rails project I decided to upgrade my Sinatra project. It is called Chief's Challenge 2.0. It's purpose is to provide a place for U.S. Navy personel that are participating in the Chiefs Challenge to record their statistics instead of writing them down by hand which is what they are currently doing. There is already a set list for the exercises and their point values. For this article, I am going to briefly go over how I met each one of the requirements.

The first requirement was to "Use the Ruby on Rails framework." As you can probably tell this was the easiest requirment. I created my application with `rails new` and only ran `rails g resource` to build out my framework. 

The second requirement was for my models to include at least on `has_many`, at least one `belongs_to`, and at least two `has_many :through` relationships. I ended up with four models in total: User, Workout, Exercise, and WorkoutExercise. The User model has many workouts, and has many exercises through workouts. The workout model was one of two join models. It belongs to user, has many workout exercises (other join model), and has many exercises through workout exercises. The exercise model has many workout exercises, many workouts through workout exercises, and many users through workouts. I used two join models to create more flexibility for any future changes I will make.

For validations, I used enough to prevent bad data or any duplications in Users, but did not go too crazy with the validations. The user, upon creation, will be validated for presence of username and password, and also uniqueness of the username. Upon creation of a workout the date and `exercise_ids` will need to be filled in. I had to use `exercise_ids` because that is the data method being used in the `collection_check_box` in the workout form.

For my class level scope method, I decided to sort all of the workouts on a user's page by the ascending total point values of the workouts. I accomplished this by adding `scope :most_points, -> { order(:points_total)}` to the workout model, and then chaining the `most_points` method in my index action in the workouts controller.

I provided standard authentication for the application. There are log in and sign up on the nav bar only when there is no session, and log out amongst other buttons available only when there is a valid user session. I used the bcrypt gem for this project and `has_secure_password` in the user model for secure passwords. I also implemented the means to sign up with google.

For the nested resource, I nested workouts under user so that I could create the means to access all the workouts for a specific user. First, I nested the workout's index resource in the user's resources so that it would create '/users/:id/workouts' . Then I added a nav bar link in the application view that included `user_workouts_path` with the `session[:user_id]` as the argument so that when ever the user clicked the link it would take them directly to their workout index.

I provided validation error displays on the user sign up form and when creating a workout. So if they do not provide the required attributes then the form will re-render and the error messages will pop up on the top telling the user what they must provide in order to continue.

I did most of the refactoring towards the end trying to eliminate as much of the repeated code that I could. I think once I get a little more knowledge under my belt then I could do a lot better. I used the typical `current_user` and `logged_in?` helper methods to eliminate some of the logic from the views. I also created a `points_sum` helper method to perform some basic arithmetic in my views. To get rid of the repeated redirecting if not logged in, I created a `redirect_if_not_logged_in` method, and used it in the `before_action` macro in the controllers so that those actions can not be called unless the user is logged in.

All in all, I really enjoyed this project. Even though the application is not very pretty to look at, I am super proud of what I created. And I am very excited to juice it up more once I know more of course. 
