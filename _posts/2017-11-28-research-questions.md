---
title: "Research Questions"
date: 2017-11-28 
featured: /assets/images/OpenLibraryAndroid.jpg
layout: post
author: "Jason Young"
---
On 27-28th of September, the research teams from Worldreader and TASCHA met to kick off the Mobile Reading Data Exchange. During these two days of meetings we began exploring the dataset, generated some of the research questions that will guide the project,and developed our plan for analysis. This post discusses the research questions that we generated throughout the meetings.

We cast a very wide net, as you can see by the long list below. This is largely due to the nature of big data research – due to the size and changing nature of big datasets, it is often quite difficult to know what types of questions the data will support until some initial research has been completed. This is why many big data research projects begin with an exploratory data analysis stage. This stage, which uses highly inductive and descriptive methods to get a better sense of the data, is important for identifying potential explanatory variables and generating research questions and hypotheses. As a result, there will be questions in our list that we will be able to answer, some that we will be able to partially answer with serious qualifications, and others that we won’t be able to answer at all. It is also likely that we will come across answers to questions that we didn’t ask about in the first place!

Nevertheless, this list will help guide some of our initial explorations of the data, and also offers a good starting point for understanding the intellectual goals of our project. We came up with several different clusters of questions, with topical areas including user demographics; device use; user engagement; linguistic, temporal, and geographic patterns; reading speed; education and content; and research methods. Below, we describe the overall research goals related to each cluster, and then list some of the questions that we came up with during brainstorming. We will post updates as our exploratory analysis leads to shifts and revisions in these initial questions!

### User Demographics

These questions all explore who is engaging with Worldreader, and how those users are interacting with the site. We are particularly interested in whether there are different profiles of users - for example, are there ways to identify power users, short-term users, long-term users, etc.? From Worldreader’s perspective, this type of information might be used to direct improved services to particular types of users - for example, to try to find ways to increase the retention of short-term users. From TASCHA’s perspective, we would love to be able to generalize answers to these questions to get insight, more broadly, into the identities and behaviors of digital readers in the Global South. While these are some of the most interesting questions that this project will ask, they are also some of the most difficult to answer. This is because we do not have a lot of demographic information - only registered users are able to contribute any demographic information at all, and not all of them choose to do so[^1].

[^1]:Worldreader has chosen to make registration for their app optional in order to reduce the barriers to people reading on the app.

- Can we identify different user groups or profiles based upon demographic or behavioral characteristics? Clusters of users might be identified based on characteristics such as time spent reading, long-term engagement with the application, book preferences, location, language, gender, age, and more.
- Who are the users that have registered for the application? In other words, what patterns in location, language, gender, and age can we identify amongst registered users?
- Are there behavioral differences between users that do and do not register with the site?
- What are the demographic and behavioral characteristics of users that fall within Worldreader’s most engaged geographies, such as Nigeria and South Africa?
- What are the behaviors and needs of various user engagement categories? This has particular value to Worldreader, because it may help them address the needs of particular types of users or help them to move a user from one category to another. For example, this may help them to move someone from being a ‘one-time user’ or ‘occasional user’ to a ‘regular user’.
- What initial behavioral differences exist between users that read a lot over the long term, and those that read little or quit the application?
- What are the behaviors and needs of ‘top’ users? How can Worldreader serve them better?
- What patterns can be observed across demographics in the following areas: reading, genre/book categories, time reading, time as registered user, and location?
- Who are the users that explore multiple genres, and what content do they end up engaging with?
- What registration patterns exist? For example, how many users register via Facebook vs. Google accounts?

In answering these questions about demographics, the following variables were flagged as being of interest:

- Gender
- Age
- Location (via IP address)
- Language
- Type of phone (smart vs. feature)
- Time spent reading
- Reading frequency
- Reading speed
- Increases in reading
- Content interests (genre and book titles)
- Breadth of interests
- Queries
- Time spent as a registered user
- Account setup
- Registration status (registered vs. unregistered)

### Devices

These questions focus on the types of devices that Worldreader users utilize in order to access the application.

- What differences exist in reading patterns across different types of devices (i.e., smart vs. feature phones)?
- What type of device is correlated with higher reading rates?This will be a very tricky question to answer, because it requires us to create an operational definition of ‘reading rates’ that can apply to both smart and feature phones. Given how difficult it is to get accurate reading data from feature phones, finding a good definition will not be easy. See the section on ‘Speed’, below, for more discussion of these difficulties.
- Do users share devices? Do they use multiple devices?

### Engagement

This is another highriority area of research, since it explores user engagement with the Worldreader app. This is particularly valuable to Worldreader, since they are always looking for ways to increase the engagement both in terms of quantity and quality of their users. Some of these questions are more theoretical in nature, such as questions about how ‘engagement’ should best be measured given the data we have. Other questions are much more practical what drives user engagement, what behaviors predict long or short term engagement by an individual user, etc.

- How can we effectively measure engagement by users?
- To what extent does content drive user engagement?
- What are common content engagement behaviors? Can these be clustered into groups?
- What are the behavioral patterns of the most engaged users?
- What behavior predicts long or short term engagement? What behavior predicts that a user will stop reading?
- For users that are active within the application for more than 1 year, what types of changes in behavior can be observed?
- What is the user journey through the reading process? In other words, what sequence of actions do users tend to follow upon entering the application?
- How do people discover books?
- Is there a dropff in users if they cannot succeed with their queries?
- What search terms do readers use to find books, and do these vary by geographic region?

### Language, Time, and Geography

These questions all focus on reading patterns across different language groups, different times of the day or year, and different countries.

- How does reading behavior change over time?
- What events spark spikes in engagement? What times of day see higher levels of engagement? Do these vary by geography?
- What is the correlation between weekends, holidays and reading patterns?
- Do different languages have different reading patterns?
- Does language use shift over time, or depend on age?
- Do reader profiles or behaviors differ by geographic region?
- Does interest in content vary by geographic region?

### Speed

Questions about reading speed can be quite useful, for example, in exploring whether digital reading has a correlation with reading fluency over the long run. If we can track the longerm speed of a reader, then we can also analyze whether that speed increases over time. Unfortunately, it is also quite difficult to operationalize reading speed as a research variable. Given current data constraints, it is difficult to determine whether a reader is just very slow on a particular page, or whether they have become distracted from a book. A number of other conditions might also disrupt a correlation between speed and reading fluency for example, we don’t have data on the reading difficulty of the reading material, which can have an impact on reading speed. In other cases, where users are just learning to read (e.g., kids or people starting to read in a second language), reading speed may have little to no correlation to reading fluency. These issues make this category of questions very interesting, but perhaps not something that we can currentlyultimately answer through backend data alone.

- Can we discern reading speed? Does this correlate with other behaviors?
- Can we use reading speed as an indicator of reading fluency?

### Education and Content

Here we ask questions about the content that is (1) accessible from Worldreader and (2) being used by readers. 

- How is the application used, for pleasure or reference?
- How is the application being used for educational, personal and professional purposes?
- To what degree are textbooks being utilized within the application? What grade levels are using these textbooks, and where?
- Roughly how many teachers are using the application, and how are they using it? This would require an inpplication questionnaire to discover these teachers.
- What is the availability and use of books and genres across different geographies? By language?
- How can data be used to inform investment in book collections?
- Do particular genres have different reading patterns?
- Is local content an incentive that increases reading frequency and extent?
- What types of content engage readers the most?
- What effect does promoting content have on reading behavior?
- Under what circumstances is local content preferred?

### Research Methods

These are metaevel questions focused on the methods that we use to perform the research itself.

- How do issues of open data and access complicate this research?
- What are the structural barriers to this type of big data research?
- How does one transform a database like this for research purposes?

### Definitions/Measures

Finally, to answer some of these questions we will have to define a number of tricky measures. These include the following:

- Top reader
- Top user
- Active user
- Popularity (of books and genres)
- Engagement
- User typologies





