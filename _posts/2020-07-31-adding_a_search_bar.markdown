---
layout: post
title:      "Adding a Search Bar"
date:       2020-07-31 05:43:15 +0000
permalink:  adding_a_search_bar
---


In order to add a very simple search bar to my application so that a user can search for other users; I needed to work in three different spots.

First, I created a form in my user index view utilizing a `form_tag` and assigning the parameter the value of `:search`. The `form_tag` also needs to have a `get` request in order to send the params. With this code alone you will have a non-functional search bar.

![](https://i.postimg.cc/9fkYTGmz/index-page.png)





Next, I created a class method in the user's model which performed a simple query on the database.

![](https://i.postimg.cc/527R7Q9W/model-page.png)

Lastly, I updated my index action to include the newly created class method. I only wanted the search to happen if the params included a search so I had to include some logic to check the params. If there are search params then reassign the `@users` variable to equal the results of the search result which is what will be displayed.

![](https://i.postimg.cc/vTchk30r/controller-page.png)


Now a user can search for a specific user or all the users will be displayed on the same page.

![](https://i.postimg.cc/pXD9JKZy/Annotation-2020-07-30-224212.png)
