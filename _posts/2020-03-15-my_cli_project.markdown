---
layout: post
title:      "My CLI Project"
date:       2020-03-15 22:29:18 +0000
permalink:  my_cli_project
---

For my project I decided to do something that could possibly be a fun and useful tool in my everyday. Something that I enjoy doing is going to events (mainly concerts). So the tool I created will help me find events in whatever area I may be in.

One of the more popular websites to get information on events happening anywhere is TicketMaster.com. For my project I decided to use an API instead of scraping because it gave me a chance to learn something new while doing my project and also it seems like API's are something that is used often in the development field. 

My application is fairly simple which was one of my goals for this project. I wanted to apply the knowledge I have gathered thus far and make sense of how it works. Because of the simplicity and the fact that you can just go to ticketmaster's website and type in your zipcode to get the same results I decided to not publish this gem. This does not mean that I am not extremely proud of what I have acomplished. To be honest, this was probably one the harder things I have had to do in my life. I was very close to calling it quits in the beginning stages of the project. Instead I decided to just keep chipping away at it one step at a time and watching lots of videos and eventually things started to click. That being said, I still do not completely understand everything I did, but I don't think I am supposed to yet. I am very proud of what I created no matter how simple it is. 

Okay, so now for my actual project description. The gem is called EventFinder. The purpose of the gem is to find any future events happening in a given zipcode. It will first, ask the user for a zipcode. If the zipcode is invalid or there are no events in that area the user will get a message saying that there are no events in that area and to provide a new zipcode. Once a valid zipcode is provided, a list of indexed future events will pop up in date order. The user will then be asked if they would like to see additional information on any of the given events and if so to provide the number corresponding with the event. Once the number is provided, a list of details will pop up including: date, name of the venue,  what genre the event falls into, and whether the event is sold out or not. The user will then be asked if they would like to see information on purchasing tickets. If they select yes they will be provided the ticketmaster url to purchase tickets. If they select no, they will be asked if they would like to see details on any other events. From there, it will either loop back to the beginning or exit.

All in all, it was very difficult, but once I started to get a hang of things it was very satisfying and a lot of fun. I am excited to see what challenges are to come in the course!

