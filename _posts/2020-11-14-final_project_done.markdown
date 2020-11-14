---
layout: post
title:      "Final Project... DONE"
date:       2020-11-14 06:11:22 +0000
permalink:  final_project_done
---


Finally. It has been a bumpy road to say the least, but I have come a long way. I am extremely proud of the work I have done, and am very excited to see what comes next. From imposter syndrome to hectic schedules, there has been no shortage of obstacles on my Flatiron journey. For anybody that happens to read this, just keep grinding. Believe me, I doubted myself the entire time, but you just need to trust the process and do not be afraid to ask questions and demand answers whether you find someone who knows more or you spend hours on Google and come inches away from losing your sanity. As the saying goes, nothing worth having is easy.

Well I guess I should talk about my project! So for my React-Redux project I decided to build something that I can continuously work on after I graduate. It is call PCS (permanent change of station) Binder. It is a very simple yet useful application. For those that are not familiar with the military lifestyle, every couple of years military personnel are asked to pick up and move to a new location. Sometimes it could be in the States or on the other side of the world. Regardless of where your are moving to, it always comes with a ton of complications and a huge to-do list. For every move I have done I have always created a PCS Binder to try and keep track of all the documents and important information that comes pouring in. So I thought it would be nice to create a digital version where I could upload digital copies of everything and not worry about losing everything important and have access to it anywhere.

So I will break down how I met all of the project requirements. First, I was required to write in ES6 (ECMAScript 6). I used quite a few key features from ES6. One of the big ones are arrow functions. These are helpful because they adopt the context in which they reside and therefore the ```this``` keyword adopts the parent context. Another big one I used are JavaScript classes which provides templates for creating JavaScript objects. I also used the very helpful ```Array.find()``` method which made finding whatever I was looking for much easier.

Next, I was required to use ```create-react-app```. This provides a basic scaffold setup for an application which makes starting to build an application much less daunting. Also, only one HTML page that renders the application which also comes along the scaffold.

I was required to have at least 5 stateless components also known as functional components. First, a NavBar component which speaks for its self. It holds the NavBar which I brought from Bootstrap. Then I have a BinderShow component which is the component that shows a specific Binder and all its information. It renders the Documents, Links, and Notes containers. Next, I have a BinderList component which is the Binder index component. It lists all the created binders as links to each binder show page. Lastly, I have Document, Link, and Note list components which are responsible for rendering its respective resource along with the capability for deleting said resource.

I used a total of 8 routes. The application has the capability to see and create the main resource, Binder. For the children resources, I gave the capability to create and delete so there are routes for each of those.

At the top level, ```index.js```, I added ```BrowserRouter``` and nested my entire app within to give all children the power of Router. Then, I used ```Route``` nested in ```Switch``` within the BinderContainer. This gave the application the routes needed to organize the components where I wanted them. It also gave me the capability to pass in ```routerProps``` to the BinderShow and BinderList so that they could access some key props needed to provide the components with the information they needed.

In order to create my store I used Redux. This gave me access to some key features such as ```Provider``` which I used at the top level of my application to give all components access to the store. It also gave me access to ```compose``` which allowed me access to the Redux Dev Tools which were very helpful in debugging and locating information within my store. Redux also allowed me to us ReduxThunk which allowed me to dispatch actions within my fetch calls.

My backend Rails API uses PostgreSQL for the database, and is responsible for all persistence and data manipulation. Each one of the action creators has a ```fetch()``` call to the API to ```GET```, ```POST```, and ```DESTROY``` actions within each controller. The front end side does not handle any data manipulation.

As far as styling goes, this is the first time I really put any effort into styling due to the lack of time on my previous projects. I had to learn how to implement Bootstrap which was very helpful my NavBar and button styling, but that was about the extent of the Bootstrap that I implemented. I added some custom CSS like a custom background that looks cheesy and dumb which I also had to learn how to do. I would still say that my application is not very appealing but it does look better than my previous projects. It was definitely a lot of fun to add styling and I plan do a lot more styling on this application after I graduate and have more time to perfect it.

Though this was my most stress-filled project, I had a ton of fun with it. I am excited to keep working on this project and also to try and implement React/Redux into previous and future projects. Once again if you happen to be reading this, do not give up! If it wasn’t difficult everyone would be doing it, but they aren’t, you are!
