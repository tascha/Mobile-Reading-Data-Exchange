---
title: "Starting a project with big data: where to begin?"
date: 2018-03-19 
featured: /assets/images/database-schema.png
layout: post
author: "Lucas Koepke"
---
Being handed the keys to a new dataset is exciting (even if it is just the exchange of a password and login information, and whitelisting an IP address). Perusing documentation, learning variable names and the database schema, and other preparatory work doesn’t compare to seeing the results of your first query show up on screen. In this post I’ll describe some of the initial steps I took to become familiar with the Worldreader dataset, to give you insight into how a data analyst approaches a new big data project.

The full log data for this project is well over 600 million rows, with an average of over 1.1 million rows added per day. Worldreader stores all of this data on Amazon Redshift. My previous big data experience topped out at about 4 million rows, which was much easier to handle. Because I was using using a server with nearly 200 GB of memory, I did not need to be especially careful in how I analysed that smaller dataset. In that case I used my usual analysis language, R, along with the parallel apply functions, and that was sufficient to work through the data in a reasonable amount of time.

That strategy would immediately choke on the Worldreader data. Not only is there vastly more data, but there are more dimensions to consider in analysis (users, countries, books, time, etc.). Thus I turned to an analysis tool that is much better for big data: Python + Pandas. The short-term solution for analysis, while we set up an AWS infrastructure plan (more on this in a future blog post!), was to temporarily cache and process data locally on my workstation and share aggregated and otherwise condensed datasets with the rest of the team. This actually worked pretty well, since I enjoy the hardware side of big data analysis as well and have set up a fairly powerful workstation at home (8 core/16 thread Ryzen CPU, 32 GB memory, Nvidia GTX 1080 GPU, 128 GB SSD for data, and connected to my 24 TB storage array).

<p align="center">
  <img src="{{ site.baseurl }}/assets/images/data-bigdata.jpg" alt="Big Data Image" style="max-width:300px;vertical-align:middle;margin:0px 0px 0px 0px;" /><br>
</p>

With others on the team using laptops for analysis, the resulting limitations on memory and CPU made sharing csv files mostly impossible (too big to load into memory). My first solution was to use an SQLite database, however this failed for two reasons: 1) data is not natively compressed, and 2) queries are very slow. A far superior solution was to use an <a href="https://github.com/apple/turicreate">SFrame</a>  to store the data, since it provides an on-disk dataframe with parallelized queries and group-by/apply functions, and the data is automatically stored highly compressed. Compared with an SQLite database, the parallelized queries combined with storing the sframe on an SSD drive provided vastly superior performance.

Making the aggregated and condensed datasets pushed the limits of my workstation, with the biggest challenge working through hundreds of GB of data using only 32 GB of memory. The SFrame helped immensely, but I still ended up working in memory on smaller datasets using Pandas. A plus for Python vs R in this case (at least on a Linux system), is that Python uses swap space when it runs out of memory, whereas R does not. Although at least an order of magnitude slower than memory, swap space on an SSD drive at least allows for some flexibility.

Now that we’ve discussed some of the technical and hardware considerations, how did I actually start working on the data? Part of the fun is that there is zero chance of loading the whole dataset into Excel to browse through and build up an understanding of how the data looks that way. Rather, understanding the data involves looking at tiny subsets of the data and devising code to look for the patterns and features that can’t be seen directly. On a database of this size, start small and limit the queries to return just a few rows (definitely don’t do SELECT *) and slowly build up. In this case, Worldreader helped immensely, going so far as to start me off with a read-only view of the log data, which returned data on just the last 7 days. This let me begin writing and testing the Python code to process and analyze the data, while preventing me from making mistakes that could impact the entire database in terms of uptime and access for others. Once we were all confident that I was accessing the data correctly, I connected to the full database.

The general rule of thumb on a production database is to run queries that finish in 10 seconds or less. Additionally, since I am not the only user of the database, it helps to leave plenty of time in between queries to allow other activity to occur. Understanding that analysis would initially be simple descriptives, but quickly progress to more complex computations, with Worldreader permission some data was temporarily cached locally for analysis. This solved multiple challenges: 1) queries to the production database were simple, since all the complex computations were done locally, 2) locally cached data could be used repeatedly with no additional queries to Redshift. The only minor downside to this approach was the increased network traffic to transfer the data locally. However, this is easily offset by the fact that it only needs to be done once, not repeated for additional queries or fixing bugs in my analysis code.

As I started digging into the data, I generally followed these steps:

- Do the most high-level summaries possible: number of rows, what are the columns, what is stored in separate tables
- Summarize key variables, such as number of unique id’s, dates, countries, books, etc.
- Start checking consistency: is there data for every date? Are there columns that contain data that should clearly be in a different column?
- Start digging deeper with tables and graphs:
  - # of log events by day and by user_id
  - Events by country
- Use small part of data to build out analysis strategy, such as restricting the time scale or geography, before rolling out to the full data.
- Use previous big data experience to anticipate problems and improve analysis, for example:
    - Many algorithms can work independently on different subsets of the data, combining results at the end for summarizing and visualization. Examples include working by date, country, or user.
    - Are some users only active on one day? If so, it may be important to consider them separately in certain analyses.

Future posts will describe results and specific analysis strategies with this rich dataset. We’ll also talk more about our long-term data strategies, which included migrating the dataset to our own AWS architecture.
