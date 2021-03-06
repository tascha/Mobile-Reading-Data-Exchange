---
title: "Exploratory Data Analysis"
date: 2018-02-22 
featured: /assets/images/Top10Countries_Map_CNT_Readers.png
layout: post
author: "Bree Norlander"
---
In the article, <a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4552232/">“Creating a Data Analysis Plan: What to Consider When Choosing Statistics for a Study,”</a> Scot Simpson states that “the first step in a data analysis plan is to describe the data collected in the study” (2015 p. 312). In a previous <a href="{{ site.baseurl }}/2018/01/02/data-variables.html">blog post</a>, Lucas outlined the data variables in our dataset. With those variables in mind, I will present some descriptive statistics of our overall data, and two smaller segments of the overall data.

### Overall Data

We are initially focusing on a static dataset which includes all activity from June 1, 2016 through November 30, 2017. By choosing a static set of data we can be sure that all members of the team are working on the same data.

The static dataset contains 558,548,651 rows (each row is an action taken by a user) and uncompressed takes up 316.4GB of space. We are currently evaluating the best options for sharing data of this size amongst the team and will address our process in a later blog post.

As Lucas mentioned in the <a href="{{ site.baseurl }}/2018/01/02/data-variables.html">data variables blog post</a>, each device is assigned a client_id number. It is important to note that the client_id number is not an accurate representation of unique users. Worldreader users may share devices amongst several people, they may sell/trade their device, or their device may register a new client_id for a variety of different hardware/software-related reasons.

With those caveats in mind, our dataset contains 62,463,086 unique client_ids. Of those, 871,020 have unique user_ids. User_ids indicate that a user has registered either by logging in with Facebook, Google, or by creating a username and password. Registration is not required but allows users to save information about the books they are reading and create a library of titles. As researchers, we value registered users because they are easier to track in the data. Unlike client_ids, user_ids should be consistent over time (assuming a registered user always logs in to use Worldreader and does not share their registration account with other users). Registered users often provide some demographic data in the form of gender and/or age which helps us more readily understand the Worldreader user base and may allow us to pursue social science questions related to age and gender and the use of mobile reading technologies. However, and this is a big caveat, no matter how many users register, we are still drawing from a convenience sample of users who choose to interact with Worldreader. Convenience samples make it difficult, if not impossible, to generalize to the greater population. See more regarding sampling in Jason’s earlier <a href="{{ site.baseurl }}/2018/02/06/challenges-of-working-with-big-data.html">post on big data</a>.

 <p align="center">
  <img src="{{ site.baseurl }}/assets/images/WR_SignIn.jpg" alt="Worldreader Sign In Screen" style="max-width:300px;vertical-align:middle;margin:0px 0px 0px 0px;" /><br>
  <em p style="font-size:11px">A screenshot of the Worldreader Mobile Website's Sign In Screen. December 2017.
</em></p>

### Registered Users

In a *Forbes* article, <a href="https://www.forbes.com/sites/metabrown/2015/07/30/big-data-analytics-first-steps/#75e67218123f">“Big Data Analytics: First Steps,”</a> Meta Brown wisely wrote, “The way to approach a big data problem is to split it into little data problems first. The process for analyzing big data is the same as the process for eating an elephant; you do it one bite at a time” (2015). Our first bite was the approximately 1% of devices being used by registered users. This was a useful first chunk of data because we could rely upon the stability of user_ids over time and we had some demographic information to work with. This is the only sample of data in which we can explore demographics of Worldreader users. Here is what we’ve found from this select group:

- Registered users[^1] have interacted with 25,633 unique book titles in 87 unique languages
- Registered users access Worldreader from 197 different countries
- 54.3% (n = 472,799) of registered users provided some demographic data via the registration portal
    - Of those:
        - Count Female: 146,961 (31.1%)
        - Count Male: 310,294 (65.6%)
        - Count Null (no gender recorded): 15,544 (3.3%)
        - Age Range: 1-160
            - Mean Female Age: 22
            - Median Female Age: 20
            - Mean Male Age: 23
            - Median Male Age: 21

[^1]:One “registered user” may equal one individual or several individuals sharing an account.

  <p align="center">
  <img src="{{ site.baseurl }}/assets/images/AllRegUsers_Age_Gender_BoxPlot.jpg" alt="Self-Identified Gender for Registered Worldreader Users" style="max-width:800px;vertical-align:middle;margin:0px 0px 0px 0px;" /><br>
  <em p style="font-size:11px">Plot created with matplotlib 2.0.2 and seaborn 0.7.1 in Python 3.5.3.
</em>
  </p>

Yes, you read the age range correctly. While it might be that there are many more 160-year-olds living on the planet than we previously knew, it’s probably more likely that many of the input ages are not accurate. A quick search for data regarding the accuracy of demographics in online registration reveals that this information can be highly unreliable (see for example: <a href="https://thenextweb.com/facebook/2017/03/22/facebook-demographics-analysis-startling-truths/">Kemp 2017</a>; <a href="https://varn.co.uk/11/30/can-trust-social-media-profiles-get-facebook-targeting/">Aimee 2017</a>; <a href="https://www.theregister.co.uk/2017/09/06/facebook_claims_more_users_than_exist/">McCarthy 2017</a>; <a href="http://www1.janrain.com/rs/janrain/images/Industry-Research-Value-of-Social-Login-2013.pdf">Goings and Abel n.d.</a>; <a href="https://conversionxl.com/blog/social-login/">Soni 2017</a>). Ages were gathered from users who created an account with Worldreader and chose to provide their age. The Worldreader registration input box errors with any age over 160. Ages are recorded in whole numbers rather than calculated from a birthdate. This field is static and does not change over time unless a user updates their profile information. For all of the above reasons, we will need to be cautious about any observations we make from the age variable and the gender variable.

### Registered Users Top 10 Countries

One of the important aspects of analyzing large datasets is to understand the context or information landscape from which the data is being gathered. Researching the literacy landscape of 197 countries is unmanageable within the short timeframe of this study. We decided to focus on the top 10 countries. To determine the top ten countries, we used the registered users data to pull out the count of unique user_ids where a user_id was classified as a “Reader.” This is the method Worldreader uses to count users in a given country. (Classification as reader varies slightly by country but in general a user_id account holder must have viewed at least two pages of a book on a single day.) Below are the top 10 countries and the counts of registered user_ids:

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;border-color:#aabcfe;margin:0px auto;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-color:#aabcfe;color:#669;background-color:#e8edff;border-top-width:1px;border-bottom-width:1px;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-color:#aabcfe;color:#039;background-color:#b9c9fe;border-top-width:1px;border-bottom-width:1px;}
.tg .tg-mb3i{background-color:#D2E4FC;text-align:right;vertical-align:top}
.tg .tg-lqy6{text-align:right;vertical-align:top}
.tg .tg-9hbo{font-weight:bold;vertical-align:top}
.tg .tg-l2oz{font-weight:bold;text-align:right;vertical-align:top}
.tg .tg-6k2t{background-color:#D2E4FC;vertical-align:top}
.tg .tg-yw4l{vertical-align:top}
</style>
<table class="tg">
  <tr>
    <th class="tg-9hbo">Country</th>
    <th class="tg-l2oz">Count of Unique Readers</th>
  </tr>
  <tr>
    <td class="tg-6k2t">Nigeria</td>
    <td class="tg-mb3i">55,963</td>
  </tr>
  <tr>
    <td class="tg-yw4l">Kenya</td>
    <td class="tg-lqy6">36,940</td>
  </tr>
  <tr>
    <td class="tg-6k2t">Ghana</td>
    <td class="tg-mb3i">20,656</td>
  </tr>
  <tr>
    <td class="tg-yw4l">Uganda</td>
    <td class="tg-lqy6">16,819</td>
  </tr>
  <tr>
    <td class="tg-6k2t">Côte d'Ivoire</td>
    <td class="tg-mb3i">12,830</td>
  </tr>
  <tr>
    <td class="tg-yw4l">India</td>
    <td class="tg-lqy6">14,906</td>
  </tr>
  <tr>
    <td class="tg-6k2t">South Africa</td>
    <td class="tg-mb3i">12,601</td>
  </tr>
  <tr>
    <td class="tg-yw4l">Ethiopia</td>
    <td class="tg-lqy6">10,911</td>
  </tr>
  <tr>
    <td class="tg-6k2t">Zambia</td>
    <td class="tg-mb3i">10,653</td>
  </tr>
  <tr>
    <td class="tg-yw4l">Zimbabwe</td>
    <td class="tg-lqy6">8,149</td>
  </tr>
</table>
<br>

  <p align="center">
  <img src="{{ site.baseurl }}/assets/images/Top10Countries_Map_CNT_Readers.png" alt="Map Visual of the Top 10 Countries by Count of Unique Readers" style="max-width:800px;vertical-align:middle;margin:0px 0px 0px 0px;" /><br>
  <em p style="font-size:11px">Map created with Tableau Desktop 10.4.
</em>
</p>

It might also make sense to normalize the number of readers by population, to recognize that countries with larger overall populations are also likely to have relatively more Worldreader users. In the table below we calculated the top 10 countries based on readers per capita (see the variables readers_per_pop and readers_per_100,000), using <a href="http://data.un.org/Data.aspx?q=population&d=PopDiv&f=variableID%3a12%3btimeID%3a77&c=2,4,6,7&s=_crEngNameOrderBy:asc,_timeEngNameOrderBy:desc,_varEngNameOrderBy:asc&v=1">UN data from 2013</a>. It does affect which countries make the top ten. However, our team wanted to focus on larger populations of Worldreader users, so that we can base our in-country analysis on a decent number of individuals. Swaziland, at only 1,425 readers, does not meet this requirement. It’s also a priority for Worldreader to focus on larger populations of their users. We’ve therefore decided to target the raw count data rather than per capita data.

<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;border-color:#aabcfe;margin:0px auto;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-color:#aabcfe;color:#669;background-color:#e8edff;border-top-width:1px;border-bottom-width:1px;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:0px;overflow:hidden;word-break:normal;border-color:#aabcfe;color:#039;background-color:#b9c9fe;border-top-width:1px;border-bottom-width:1px;}
.tg .tg-mb3i{background-color:#D2E4FC;text-align:right;vertical-align:top}
.tg .tg-lqy6{text-align:right;vertical-align:top}
.tg .tg-9hbo{font-weight:bold;vertical-align:top}
.tg .tg-l2oz{font-weight:bold;text-align:right;vertical-align:top}
.tg .tg-6k2t{background-color:#D2E4FC;vertical-align:top}
.tg .tg-yw4l{vertical-align:top}
</style>
<table class="tg">
  <tr>
    <th class="tg-9hbo">Country</th>
    <th class="tg-l2oz">Count of Unique Readers</th>
    <th class="tg-l2oz">2013 Population</th>
    <th class="tg-l2oz">Readers Per Population</th>
    <th class="tg-l2oz">Readers per 100,000</th>
  </tr>
  <tr>
    <td class="tg-6k2t">Swaziland</td>
    <td class="tg-mb3i">1,294</td>
    <td class="tg-mb3i">1,271,456</td>
    <td class="tg-mb3i">0.001018</td>
    <td class="tg-mb3i">101.773</td>
  </tr>
  <tr>
    <td class="tg-yw4l">Kenya</td>
    <td class="tg-lqy6">36,940</td>
    <td class="tg-lqy6">44,826,849</td>
    <td class="tg-lqy6">0.000824</td>
    <td class="tg-lqy6">82.406</td>
  </tr>
  <tr>
    <td class="tg-6k2t">Ghana</td>
    <td class="tg-mb3i">20,656</td>
    <td class="tg-mb3i">26,346,251</td>
    <td class="tg-mb3i">0.000784</td>
    <td class="tg-mb3i">78.402</td>
  </tr>
  <tr>
    <td class="tg-yw4l">Namibia</td>
    <td class="tg-lqy6">1,684</td>
    <td class="tg-lqy6">2,316,520</td>
    <td class="tg-lqy6">0.000727</td>
    <td class="tg-lqy6">72.695</td>
  </tr>
  <tr>
    <td class="tg-6k2t">Zambia</td>
    <td class="tg-mb3i">10,653</td>
    <td class="tg-mb3i">15,153,210</td>
    <td class="tg-mb3i">0.000703</td>
    <td class="tg-mb3i">70.302</td>
  </tr>
  <tr>
    <td class="tg-6k2t">Zimbabwe</td>
    <td class="tg-mb3i">8,149</td>
    <td class="tg-mb3i">15,054,506</td>
    <td class="tg-mb3i">0.000541</td>
    <td class="tg-mb3i">54.13</td>
  </tr>
  <tr>
    <td class="tg-yw4l">Benin</td>
    <td class="tg-lqy6">5,252</td>
    <td class="tg-lqy6">10,004,451</td>
    <td class="tg-lqy6">0.000525</td>
    <td class="tg-lqy6">52.497</td>
  </tr>
  <tr>
    <td class="tg-yw4l">Uganda</td>
    <td class="tg-lqy6">16,819</td>
    <td class="tg-lqy6">37,553,726</td>
    <td class="tg-lqy6">0.000448</td>
    <td class="tg-lqy6">44.787</td>
  </tr>
  <tr>
    <td class="tg-6k2t">Botswana</td>
    <td class="tg-mb3i">851</td>
    <td class="tg-mb3i">2,128,507</td>
    <td class="tg-mb3i">0.000400</td>
    <td class="tg-mb3i">39.981</td>
  </tr>
  <tr>
    <td class="tg-yw4l">Cameroon</td>
    <td class="tg-lqy6">8,136</td>
    <td class="tg-lqy6">21,655,715</td>
    <td class="tg-lqy6">0.000376</td>
    <td class="tg-lqy6">37.57</td>
  </tr>
</table>
<br>

Within the top ten countries by count, here are the statistics:

- 279,205 registered users[^2] have interacted with 17,826 different book titles in 64 languages
    - The most popular book category is “Love”
        - When broken down by country the top book category is “Love” for Nigeria, Kenya, Ghana, Uganda, South Africa, Ethiopia, Zambia, and Zimbabwe; “Story Books” for India; and “Classics” for Ivory Coast.
- 58.8% (n = 164,109) of registered users in the top ten countries have provided some demographic data via the registration portal
    - Of those:
        - Count Female: 54,387 (33.1%) 
        - Count Male: 104,970 (64%)
        - Count Null (no gender recorded but did include age): 4,752 (2.9%)
        - Age Range: 1-160
            - Mean Female Age: 22
            - Median Female Age: 20
            - Mean Male Age: 23
            - Median Male Age: 21

[^2]:One “registered user” may equal one individual or several individuals sharing an account.

  <p align="center">
  <img src="{{ site.baseurl }}/assets/images/Top10Countries_Age_Gender_BoxPlot.jpg" alt="Self-Identified Gender for Registered Worldreader Users in Top 10 Countries" style="max-width:800px;vertical-align:middle;margin:0px 0px 0px 0px;" /><br>
  <em p style="font-size:11px">Plot created with matplotlib 2.0.2 and seaborn 0.7.1 in Python 3.5.3.
</em>
</p>

  <p align="center">
  <img src="{{ site.baseurl }}/assets/images/Top10Countries_Gender_Percentage_Plot.jpg" alt="Self-Identified Gender Percentage Breakdown for Registered Worldreader Users in Top 10 Countries  by Country" style="max-width:800px;vertical-align:middle;margin:0px 0px 0px 0px;" /><br>
  <em p style="font-size:11px">Plot created with matplotlib 2.0.2 in Python 3.5.3.
</em>
</p>

### Conclusion

In conclusion, summary statistics are useful for gaining a broad perspective on a dataset. When faced with a large dataset like ours, it is necessary to break the dataset into smaller pieces. Deciding how to slice and dice a dataset will be a team decision based on the size and available variables. For example, we chose to look at the top ten countries. This was an arbitrary decision but felt right to the team. We also needed to define “top 10” to determine how we would retrieve that slice of the data. 

These early exploratory analyses are also useful in that they help us to generate new questions about the dataset, which can direct additional, more targeted rounds of analysis. For example, some of the discrepancies related to the self-reported age of users raises questions about the veracity of our data. This has led us to think more about the context of our data, and to perform additional research on big data, demographic information, and reliability. This has further encouraged us to perform additional tests of the log data against real-world uses of the application. Second, there is variability across the top ten countries in terms of the gender of registered users, which leads to interesting questions about digital access and gender inequalities. Why is it that South Africa and India have a higher relative percentage of women users, compared to the other top 10? Is the gender disparity in the other countries a result of hardware access (i.e., women don’t have as much access to phones), time (i.e., women are too busy taking care of gendered roles), education, stigma around technology use (that either prevents them from using the application, or just prevents them from registering), or something else altogether? In order to examine these dimensions more, we are working on country-specific dashboards that will allow users to compare Worldreader data with other datasets on development. And, these are just two areas of questioning presented by these summary statistics! You can expect posts on these new areas soon!
