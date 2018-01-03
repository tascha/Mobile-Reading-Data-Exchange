---
title: "Data Variables"
date: 2018-01-02 
featured: /assets/images/VariablesCloud.png
layout: post
author: "Lucas Koepke"
---

This is a short entry that just describes the dataset with which we are working. Each time a user interacts with the Worldreader application, the app collects information about that interaction. The following data may be collected for each interaction, although not all interactions will include data for every variable.

*Client_id*: This is a unique ID number that is designed to track Worldreader usage on a device over time. It is designed just like a browser cookie, and is intended to be unique per device for 2 years. This essentially allows us to identify all of the interactions a particular user has with Worldreader, without them needing to register for the service. However, there are some behavioral issues that complicate the picture – for example, this variable becomes less useful if multiple unregistered users share the same device, or if a device is sold to a different Worldreader user. These behaviors would prevent us from equating a device to a unique user.
 
*User_id*: If the user is registered, they have been assigned a user id. It is worth noting here that Worldreader does not require their users to register for the service. They do this to ensure that the registration process does not become a deterrent for users. While this is a good decision that ensures that the books on their app are placed in as many hands as possible, it presents considerable research challenges. Many of our research questions revolve around the demographics of Worldreader users (e.g., research questions about gender gaps in reading). We only have access to any of this demographic data if a user has registered for the service and then provided the information. Because only a small number of users have registered, we can only examine our demographic questions with a much smaller dataset than would have been possible if registration were required. We’ll discuss some of these research challenges in later posts.
 
*Ip_address*: This variable provides the IP Address being used by the user, which we can then use to determine the location of the user. In an ideal world this would allow us to identify a very specific geographic location for the user. Unfortunately, though, we can only tie IP Addresses to a more generalized location, making it mostly useful for identifying location at the country level.
 
*Controller*: This records the type of interaction the user is having with the application, such as clicking a menu item or turning the page of a book.
 
*Action*: A sub-category of the Controller variable.
 
*Book_id*: Every book in the Worldreader database receives a unique ID number. This allows us to know which book a user is interacting with.
 
*Book_page*: This records the page number of the book with which the user is interacting.
 
*Book_page_size*: This records the page size of the page with which the user is currently engaging. This is typically 4800 bytes, which roughly equals 4800 characters.
 
*Book_screen_size*: Like book_page_size (see above), this records the page size of the page with which the user is engaging. This variable, however, only provides information about smartphone page sizes, which have much higher resolution pages.
 
*Book_screen_progress*: This is a higher-resolution version of book_progress (see below).
 
*Book_rating*: This records a book rating as an integer provided by a user. It is not currently being populated, so we do not have access to this information.
 
*Book_progress*: This provides a record of the percent of progress a user has made through a book, determined by page number.
 
*Query*: This provides information about any queries the user makes. If they perform an action that is a search or a request for author details, this is the text of the query that is recorded.
 
*Book_title*: This provides the title of the book with which the user is interacting.
 
*Book_author*: This provides the author of the book.
 
*Book_publisher*: This provides the publisher of the book.
 
*Category*: Books are classified in different categories. For example, ‘love’ is a category that includes romance novels. A book can be attached to multiple categories, and there is no hierarchy in terms of which category is more or less associated with the book. In other words, there is a many-to-many relationship between books and categories. 
 
*Language*: This records the language in which the book is written.
 
*User_gender*: This variable is only populated for some registered users. It stores the gender of the user, as provided by the user. Possible values include male, female, or unknown.                           
 
*User_age*: This variable is only populated for some registered users. It stores the age of the user, as provided by the user upon registration. This is stored as an integer. This is a static field, meaning that it really only reflects the age at which the user first registered for Worldreader (i.e., it is not updated dynamically over time).
 
*User_haseditedpreferredlanguages*: This variable is only populated for some registered users. It indicates whether the registered user has entered a preferred language.

We also have access to various date and time stamps related to the interactions.

