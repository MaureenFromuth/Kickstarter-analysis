# Kickstarting with Excel

## Overview of Project

### Purpose  

Our core customer, Louise, initiated a Kickstarter campaign in order to fund her play, *Fever*, which she wants to launch in the UK.  She asked us to look at data from [Kickstarter](https://github.com/MaureenFromuth/Kickstarter-analysis/blob/master/Kickstarter_Challenge-Fromuth.zip) on multiple categories of fundraising campaigns to provide her our assessment on the best approach to successfully raise money for her play and to provide insight into how well she was once she executed her campaign.  We provided Louise our analysis based on the Kickstarter data set, which includes the name of the project, a brief description of the project, and the parent and subcategory that project falls into.  It also includes various metrics such as the following:

- country of the campaign
- fundraising goal
- amount pledged
- the currency of the funding
- the number of backers
- the start and end date of the funraiser, and
- if the fundraiser was a spotlight on the Kickstarter site.  

Prior to the launch of her campaign, Louise ultimately wanted to understand probability of a successful Kickstarter campaign for the theater parent category and the play sub-category within the UK, given the time of year she launched her campaign and the goal of her campaign.  Recently, Louise launched her campaign but now wants understant how well she could expect to finish her campaign by compairing her achievements to other Kickstarter theater and play campaigns that launched at the same time and with a similar goal.  The purpose of this analysis was to provide Louise insights into the outcomes of Kickstarter campaigns for theater based on their launch date.  Similarly, this report analyzed the outcome of plays based upon their Kickstarter fundraising goal.  Identifying this information will allow Louise to assess what outcome similar campaigns to hers experience.  

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date

In order to provide Louise insight into how the time of year impacted the outcome of her Kickstarter campaign, we created a pivot chart with outcomes in the column and the date created in the rows.  We chose to look specifically at the month of the year as our specific unit of measure for the rows, and created a filter for the year of launch and parent category for further analysis.  Analyzing the outcome by month provided us a reasonable unit of time to break up the year, rather than quarter or days which would have been too large and small respectively.  

The existing data on the date of launch, however, included the entire date.  As a result, we needed to transform the data within this column again, creating a new column for 'launch year'.  We used the following formula to transform and load the new column:

```
=YEAR(N*), where N is the original column for the Standard Time Stamp launch date and * is the specific row
```  

Using the pivot table fields mentioned above, we added 'year of launch' to the filter and sum of 'outcomes' into the values.  This provided us a table that listed the sum of the outcomes per month.  Of note, in the event we wanted to select a different unit of measure, such as days instead of by month, we could click on the row and then select the 'Grouping' feature under analysis.  Within this feature we can select different groupings for the rows.  

We fitlered the table to look only at the parent category of Theater, and limited the columns to the following outcomes:

- Successful
- Failed
- Canceled

We then highlighted the table and created the following line chart to display the outcome of Theater Kickstarter Campaigns by Month of Launch Date.  On the X-axis is the month of the year, and on the Y-axis is the total number of campaigns for that given outcome.  Each line represents one of the three outcomes: successful, failed, or canceled. 

![Outcome of Theater Campaign Based on Launch Date](https://github.com/MaureenFromuth/Kickstarter-analysis/blob/master/Theater_Outcomes_vs_Launch.png)

Using this graph, you can see that with the exception of December, there were always a greater number of successful theater kickstarter campaigns than failed and cancelled campaigns.  Additionally, the greatest number of failed theater projects was in the month of May.  That said, the months of February and May have the highest number of successful theater campaigns.  Finally, there is the largest difference between successful and failed outcomes during the months of May, June, and July.  

### Analysis of Outcomes Based on Goals

We also conducted analysis on the outcome of other Kickstarter campaigns for plays based on their fundraising goal.  We started our analysis by looking at the overall fundraising goals in column D and breaking these goals into twelve separate groups, which acted as our rows:

- Less than 1000
- 1000-4999
- 5000-9999
- 10000-14999
- 15000-19999
- 20000-24999
- 25000-29999
- 30000-34999
- 35000-39999
- 40000-44999
- 45000-49999
- Greater than 50000
  
Using the three outcomes identified in the previous analysis as columns, we counted the number of campaigns in the subcategory of 'plays' for each of those outcomes. We used the following Excel formula to count and sum the results per cell:

```
=COUNTIFS(Kickstarter!H2:H4115, "successful", Kickstarter!D2:D4115, ">4999", Kickstarter!D2:D4115, "<10000", Kickstarter!U2:U4115, "plays")
where the criteria of "successful" was changed for "failed" and "canceled" for column H, and the criteria for column D was changed based on the goal range 
```

Using the following formula, we added up the total projects per fundraising goal range:

```
=SUM(B*:D*), where B is the Number of Successful projects, C is the Number of Failed Projects, D is the number of Canceled projects, and * relates to the row for a given goal range
```

Finally, we calculated the percentage of successful, failed, and canceled projects per goal range using the following formula:

```
=($*/E*), where $ is either B (number of successful), C (number of failed), or D (number of canceled); E is the total number of projects; and * related t othe row for a given goal range

```

Using the resulting table, we created a line chart representing the percentage of each of the primary outcomes per goal range.  On the X-axis is the goal range, and on the Y-axis is the total percentage.  Each of the three lines represents one of the three outcomes.  Of note, we did need to correct the graph to show a maximum of 100% on the Y-axis.

![Outcome of Play Campaign Based on Goal](https://github.com/MaureenFromuth/Kickstarter-analysis/blob/master/Outcomes_vs_Goals.png)

This graph highlights that there are more successful play campaigns with fundraising goals under $19,999 and between $35,000 and $44,999.  Additionally, there are zero successful play campaigns who attempted to raise money between $45,000 and $49,999. 

### Challenges and Difficulties Encountered

Overall there were very few issues in conducting the analysis for the customer Louise.  The Kickstarter data was complete with few errors.  Transformations, however, were required in order to create new fields from the existing data.  

For example, the Launch Date as well as the campaign Termination Date was given in the Unix timestamp, and a conversion formula was needed to translate these dates into a simple date format.  We utilized the following formulas for those conversions:

```
 =(((K*/60)/60)/24)+DATE(1970,1,1), where K is the original column for the deadline and * is the specific row
 =(((M*/60)/60)/24)+DATE(1970,1,1), where M is the original column for the date launched and * is the specific row
```

Additionally, we needed to break out the data within the 'Category and Subcategory' column.  To execute this, we used the "Text to Columns" feature within Microsoft Excel with a '/' or backslash as the delimiter.  This allowed for us to separate out the Parent Category from the Subcategory.  This left us with nine Parent Categories and 41 Subcategories.  

While data challenges were limited, there is often issues with completeness of data and data formatting.  These issues can be identified by using the Filter feature within Excel and looking for blank cells, mis-formatted rows or columns, and any cells that look as though they may be incomplete (e.g. missing years in the dates).  Additionally, you can conduct statistical analysis such as quartiles and standard deviations to look for outliers that may be inaccurately reported data.

## Results

Based off of the prelimary analysis we conducted for Louise, we can make a few conclusions on how launch dates and goals may impact the outcome of a Kickstarter campaign.  

For example, our preliminary analysis leads us to the conclusion that the most optimal time to launch a kickestarer campaign for a theater is in the months of May, followed by June, and then July.  This is due to the fact that, despite the highest number of failed theater projects is also being in May, the difference between successful and failed outcomes is greatest during that month and is actually more than twice the number of failed projects.  Additionally, the worst month to launch a kickstarter campaign for a theater project is in the month of December.  Therefore, Louise should launch her theater Kickstarter campaign ideally in the month of May, and if she launched in December, she is has the least likely chance of a successful campaign.

Additionally, the analysis on the impact of the fundraising goal on the outcome leads to the conslusion that the most optimal goal is less than $5,000 for plays, and between $35,000 and $45,000.  Similarly, Louise should avoid setting a goal at $45,000 or above.  

These results, however, are prelimary and should be suplemented by additional data and analysis.  More specifically, although the data is relatively complete there are a few issues.  For example, the currency data for the goal was not consistent, and we did not convert the currency of the each goal into a common currency.  This may have an impact on the overall assessment, and should either be converted in the future or analysis should be done for a specific country.  Likewise, there was no information related to the way in which these campaigns were advertised.  For example, was the Kickstarter campaigns all advertised via the primary Kickstarter website?  If so, what was the amount traffic to these websites?  Additional information on the financial status of the project owners would also be beneficial.  In knowning this, it may be helpful to understand the drivers of successful campaigns rather than merely the time of year and goal.  

Absent additional data, however, there is additional analysis that can be conducted to see the potential impact of adveristing or highlighting on the outcome of a campaign.  More specifically, you could look at how many staff picks were successful, failed, and canceled to determine if the staff has any influence over fundraising outcomes.  Similarly, you could assess how many highlighted campaigns have successful, failed, and canceled outcomes.  This could give insight as to whether highlighting a campaign leads to a greater potential for a successful fundraising effort.  Finally, you could compare the impact of all of these attributes (goal, launch date, highlight, and staff pick) on the outcome per year.  This would provide insight into any trends these attributes have had over the years, which ones are still relevant and which ones are not.   
