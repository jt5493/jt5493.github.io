---
layout: post
title:      "My CLI Project"
date:       2020-03-15 18:29:19 -0400
permalink:  my_cli_project
---

For my project I decided to do something that could possibly be a fun and useful tool in my everyday. Something that I enjoy doing is going to events (mainly concerts). So the tool I created will help me find events in whatever area I may be in.

One of the more popular websites to get information on events happening anywhere is TicketMaster.com. For my project I decided to use an API instead of scraping because it gave me a chance to learn something new while doing my project and also it seems like API's are something that is used often in the development field. 

My application is fairly simple which was one of my goals for this project. I wanted to apply the knowledge I have gathered thus far and make sense of how it works. Because of the simplicity and the fact that you can just go to ticketmaster's website and type in your zipcode to get the same results I decided to not publish this gem. This does not mean that I am not extremely proud of what I have acomplished. To be honest, this was probably one the harder things I have had to do in my life. I was very close to calling it quits in the beginning stages of the project. Instead I decided to just keep chipping away at it one step at a time and watching lots of videos and eventually things started to click. That being said, I still do not completely understand everything I did, but I don't think I am supposed to yet. I am very proud of what I created no matter how simple it is. 

Okay, so now for my actual project description. The gem is called EventFinder. The purpose of the gem is to find any future events happening in a given zipcode. It will first, ask the user for a zipcode. If the zipcode is invalid or there are no events in that area the user will get a message saying that there are no events in that area and to provide a new zipcode. Once a valid zipcode is provided, a list of indexed future events will pop up in date order. The user will then be asked if they would like to see additional information on any of the given events and if so to provide the number corresponding with the event. Once the number is provided, a list of details will pop up including: date, name of the venue,  what genre the event falls into, and whether the event is sold out or not. The user will then be asked if they would like to see information on purchasing tickets. If they select yes they will be provided the ticketmaster url to purchase tickets. If they select no, they will be asked if they would like to see details on any other events. From there, it will either loop back to the beginning or exit.

On a more technical note, I will go through my process of how I went about building my project. I started with my API. As I mentioned before I decided to go with an API as opposed to a scraper to get my information. Turns out they are very pretty straight forward after reading all the instructions that they put on the API’s website. First (see below), I used the starting URL that they provide and add on any parameters that meet the needs of what you are trying to accomplish followed by the apikey. From there, I used the gem `HTTParty` to grab the information from the URL that I meshed together.  To get the information that I wanted from hash-like object that was provided, I iterated through the object and assigned keys to each of the details that I was looking for. Finally, I created new instances of my`::Events` and`::Details` classes.

![](https://p4xv6g.by.files.1drv.com/y4m8rP0wzcKkplMNnCEuIaOsFZgu4waGd7JXsgIhzmLdpdC6dyywj360IgC35KjERg6F7bgqxnqT_U7rIhPbFu3zZKzYrNmpDgI2WQbONZQ3DlA1Trw4VMB8Aom2Wz7WWnWkM11ekPOJV0LRdbRA7_Ao_fGUx53C7INBm53X0AjV_xVLpcNmgSHQhD2ch37F8mKQvYq18OUGD6zW5ZEF7tpHw?width=1005&height=479&cropmode=none)

The next class I worked on was my actual CLI page which consists of all my user interface. The `call` instance method is what gets everything started which is initiated in the `eventFinder` file. It essentially welcomes the user and asks for their input in the form of a zip code. The user’s input will be stripped and converted into an integer so it can be plugged into the `fetch_data` class method for the `::Scraper` class. If the user’s input is invalid it will display an error message and ask them to try again. Once a valid zip code is entered it will then move onto the `display_events` instance method.

![](https://qixv6g.by.files.1drv.com/y4mfrLFW3mBpHJdCrYm0H2sQFJyGiGmN-2U1ALl9O03wyWHNrPIJTp5GCrY9-ewEmjEFyw9-u3duRHNfSIcoj1Kcfk7gCSyLjpODM4UrPNB9G4r2x_3hUVthdd1RX6AZ21j24XtsEGw1ZSNYZz15iLSTpXfCL3YRZRm1dpFbudAQkwnD8OG9S0fe4V7Bqb1eZQ6AwbEn1e6Jm4-tn7iHdIsfg?width=868&height=269&cropmode=none)


The `display_events` method calls on the ‘all’ class method in `::Events` class. It then will list each indexed event.

![](https://qyxv6g.by.files.1drv.com/y4m7viD0LdDD1KemvM0pYOApTzmtndwYrqTebrS19_qTt4_VGMavf17EBzg5LtUOb45MvmJItvNuc5S5Z3YJsMXSxWktWYS38h-Zgid6vSvYQlzTGsV06r-JkndZgjtkWa9Bq5eUfcK-ufA9g8eySOpx7K8e_aEnZYxtxHkMmfUBbpqTYRlqDV4wRLk_KiNWfI7dncoC1pfGcPQskCiSyqh7g?width=520&height=134&cropmode=none)

The `display_details` method asks the user if they would like to see more details on a specific event. The input taken in will be stripped, converted to an integer, and plugged into the `all` class method for the `::Details` class. It will then print out each of the details which were first assigned to keys in the `::Scraper` class and then organized in the `::Details` class created an `attr_accessor` for each of the different details. After the details are displayed, the user will be asked if they would like to see information on buying tickets. If the user answers yes, then the URL will be displayed. The URL was one of the items that was scraped from the API and then assigned to one of the `attr_accessor` in the `::Details` class. The user will then be asked if they would like to see information on another event and if answered yes, the method will loop back to the start. If no the program will exit.

![](https://qoxv6g.by.files.1drv.com/y4m_n9BC4EiLu6g3hLNVz5bOBq0EbVF4LydDLMqBXiy5DZookArwznzACRkn6d6RtO0jorDJPHm8s8cFhAnhLehVyT-TeDOqlok8XBq3YmopLf9imEf6A3V3Ts4zW_gG2_3nTqYrKKE4v5HFq22iB33B0m2TE1kp0EGJ3sJkggsecpSpTTuAvBlXep-EmMYtfsuuJleKITuwFJkXc-yo8wRaA?width=834&height=437&cropmode=none)

The other two classes I created for this program, `::Events` and `::Details`, were just simple classes with the basics such as:  `attr_accessor` , initialization, `all` to access the information saved on initialization, and a `delete` class method which was needed in the `::Cli` class so that information would not be repeated if the user looped back.

![](https://q4xv6g.by.files.1drv.com/y4myCdOlrVfyccsOylqGArKqbdJL5NRhbflSd7_7lH4_djTPbNuqie5FokKI_Vz0X5-fE0vcmvfUYL2yF8gy5v4AQ1cucd7Op6GK08Q6ob8ouqelPtzMcBnALiow5qIBHM5Wd7a1QFxf3sC8i6bkn1OHXlsXFlRSeiy4wk7GsX5gdEotZIwFQKgsv3b1grAln0jTbvRhfLZPeFvXVNL-4X20w?width=220&height=379&cropmode=none)

![](https://rixv6g.by.files.1drv.com/y4mspyBvFA8I5JPu8B8_LD5tTNoUhqvy5hryWpr-IkSid8R66xoiH4LnsHOINgyF1LuuR-S7pv8nPQ7tXzWUE7oSOl87Qvm0ck9YIYimBR3QNMX_1QdQ_3uWQhwjcvqgRd2WUlUeT_9S5KfLCU6n3U4GNRQ8UQRCHVANj47JpsOyvddECHcn1UdWC2jDGg-EXFqKrenUC5B-TD7i4R2Kkfyqg?width=590&height=420&cropmode=none)

There is definitely a lot more that I can do with this program, and perhaps when I get through this coding bootcamp I will come back and fine tune it and make it accessible. Going through this project showed me that I actually learned something as opposed to just trying to keep up and feeling lost most of the time. 

All in all, it was very difficult, but once I started to get a hang of things it was very satisfying and a lot of fun. I am excited to see what challenges are to come in the course!

