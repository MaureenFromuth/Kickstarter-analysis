# Kickstarting with Excel

## Overview of Project

Our core customer, Louise, initiated a Kickstarter campaign in order to fund her play, *Fever*, which she wants to launch in the UK.  She asked us to look at data from Kickstarter on multiple categories of fundraising campaigns to provide her our assessment on the best approach to successfully raise money for her play and to provide insight into how well she was once she executed her campaign.  We provided Louise our analysis based on the Kickstarter data set, which includes the name of the project, a brief description of the project, and the parent and subcategory that project falls into.  It also includes various metrics such as fundraising goal, amount pledged, the number of backers, the start and end date of the funraiser, and if the fundraiser was a spotlight on the Kickstarter site.

### Purpose  

Prior to the launch of her campaign, Louise ultimately wanted to understand probability of a successful Kickstarter campaign for the theater parent category and the play sub-category within the UK, given the time of year she launched her campaign and the goal of her campaign.  Recently, Louise launched her campaign but now wants understant how well she could expect to finish her campaign by compairing her achievements to other Kickstarter theater and play campaigns that launched at the same time and with a similar goal.  The purpose of this analysis was to provide Louise insights into the outcomes of Kickstarter campaigns for theater based on their launch date.  Similarly, this report analyzed the outcome of plays based upon their Kickstarter fundraising goal.  Identifying this information will allow Louise to assess what outcome similar campaigns to hers experience.  

## Analysis and Challenges

Overall there were very few issues in conducting the analysis for the customer Louise.  The [Kickstarter data](https://github.com/MaureenFromuth/Kickstarter-analysis/blob/master/Kickstarter_Challenge-Fromuth.zip) was relatively complete with few errors.  Transformations, however, were required in order to create new fields from the existing data.  

For example, the Launch Date as well as the campaign Termination Date was given in the Unix timestamp, and a conversion formula was needed to translate these dates into a simple date format.  We utilized the following formulas for those conversions:

```
 =(((K*/60)/60)/24)+DATE(1970,1,1), where K is the original column for the deadline and * is the specific row
 =(((M*/60)/60)/24)+DATE(1970,1,1), where M is the original column for the date launched and * is the specific row
```

Additionally, we needed to break out the data within the 'Category and Subcategory' column.  To execute this, we used the "Text to Columns" feature within Microsoft Excel with a '/' or backslash as the delimiter.  This allowed for us to separate out the Parent Category from the Subcategory.  

### Analysis of Outcomes Based on Launch Date

[Outcome Based on Goal](Outcomes_vs_Goals.png)

### Analysis of Outcomes Based on Goals

### Challenges and Difficulties Encountered

## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

- What can you conclude about the Outcomes based on Goals?

- What are some limitations of this dataset?

- What are some other possible tables and/or graphs that we could create? 
