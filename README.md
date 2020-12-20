# Kickstarting with Excel

Analysis of several thousand crowdfunding projects from Kickstarter to uncover hidden trends

## Overview of Project

The brief for this project is to help an up and coming playwright, Louise, who wants to start a crowdfunding campaign for her upcoming play *Fever*. Louise's budget for the play is estimated at over $10,000. The goal is to organize, sort, and analyze thousands of crowdfunding data from Kickstarter projects to discover if there are specific factors that influence successful campaign outcomes. 

### Purpose

The findings will be presented to Louise visually to provide essential information at a glance and allow her to make decisions that ensure her own plan is successful. Any insights gained will aim to provide a greater understanding of campaigns from start to finish, and allow her to set her own campaign to mirror other successful campaigns of a similar type. This will help her establish a realistic timeline, funding goal, and location for her play.

## Dataset Preparation

### Calculating Supplementary Data Fields

The data and analysis used in this project can be found at [Kickstarter Analysis](https://github.com/jkenning/Kickstarter-analysis/blob/main/data-1-1-3-StarterBook.xlsx). Several calculations were required to get the data set ready for analysis:

1. Conditional formatting was performed to color code the project 'outcome' column based on whether it was "successful", "failed", or "cancelled"

2. In order to observe how much of each individual campaign was funded, a new column for 'Percentage Funded' was created using the 'ROUND' formula on 'pledged' and 'goal' values and then value shaded using the conditional formatting menu

3. To calculate the average amount an individual backer paid for the project a column for 'Average Donation' was created

4. Debugged 'Percentage Funded' column to remove errors created by projects with zero backers using an 'IFERROR()' formula

5. Split the 'Category and subcategory' column into 'Parent category' and 'Subcategory' respectively using the Convert Text to Collumns Wizard

6. Converted unix timestamps representing 'deadline' and 'launched_at' vales into a readable date format 

## Analysis

### Campaign Category Performance

The analysis performed in [Kickstarter Analysis](https://github.com/jkenning/Kickstarter-analysis/blob/main/data-1-1-3-StarterBook.xlsx) provides some helpful information for Louise and her campaign preparation: 

A pivot table was created to count how many campaigns were either "successful", "failed", or "cancelled" for each 'category'. The resulting stacked collumn chart in Figure. 1 shows that out of all project categories in the United States, 'Theater' Kickstarters are the most numerous and have had the most successfully funded campaigns.

![Image of Parent Category Outcomes](https://github.com/jkenning/Kickstarter-analysis/blob/main/Resources/Parent_category_outcomes.png)

Figure. 1 - Parent Category Outcomes - United States

Another pivot table was created to assess the number of "successful, "failed", or "cancelled" campaigns for each 'subcategory'. To improve specificity for Louise's project, another pivot chart filtered to 'country' and 'category' was created. The chart in Figure. 2 demonstrates that within the 'Theater' category, 'Plays' have been the most successful subcategory, outnumbering other categories by a large margin. These are positive findings for Louise.

![Image of Subcategory Outcomes](https://github.com/jkenning/Kickstarter-analysis/blob/main/Resources/Subcategory%20outcomes.png)

Figure. 2 - Subcategory Outcomes - United States

Figure. 3 provides more detail on outcomes for Kickstarter Campaigns in the 'Play' subcategory within the United States.

![Image of Play Outcomes](https://github.com/jkenning/Kickstarter-analysis/blob/main/Resources/plays_outcomes.png)

Figure. 3 - Play Outcomes - United States

### Descriptive Statistics

The Descriptive Statistics tab found in [Kickstarter Analysis](https://github.com/jkenning/Kickstarter-analysis/blob/main/data-1-1-3-StarterBook.xlsx) provides some additional information of use:

- Failed campaings typically have significantly higher funding goals than successful campaigns
- With a projected budget of $10,000, Louise is asking for over twice the mean funding goal of successful projects

However, the lower values of pledged funds for failed projects suggest that having a higher funding goal that cannot be reached is not necessarily the only reason a project may fail and there are likely other reasons to account for. Although "Plays have been most successful over the observed timeframe, Louise should consider looking into more information to better determine her plan for success. 

### Analysis of British Musicals

Louise also wanted to look into musicals based in Great Britain. From the plot in Figure. 4 we can visualize the distribution of goals and pledged amounts for British musicals. The mean and median pledged amounts are much lower than successful pledges and 25% of Kickstarter projects recieve no pledges, supporting the hypothesis that other reasons are responsible for failure than asking for too much money. The mean campaign goal is about $4,000, which is outside the range of outliers for amount pledged. Half of all campaign goals are less than $2,000 which is greater than the 3rd quartile for pledged amounts. This analysis suggests Louise should try to get her play produced for less than $4,000, and based on amounts pledged - possibly lower.

![Image of Goal and Pledged for British Musicals](https://github.com/jkenning/Kickstarter-analysis/blob/main/Resources/Goal_pledged_distribution_british_musicals.png)

Figure. 4 - Goal and Pledged for Musicals - Great Britain

### Analysis of Edinburgh Festival Fringe plays

Louise was inspired by five specific plays at the Edinburgh Festival Fringe and wanted to know more about how they were funded. 'VLOOKUP' was used to find and pull data for the five plays, including 'Goal', 'Pledged', 'Average Donation', and 'No. of Backers' fields. All of these plays recieved a greater amount pledged than the goal and were successful, with all funding goals $4,000 or lower and average donations between $33-52.

## Challenge

The result was that Louise's play *Fever* came close to its funding goal in just a short timeframe. Because of this, she would like to see well how different campaigns did based on both their launch date and funding goals. Two main factors were analyzed and visualized:

1. Outcomes based on launch date
2. Outcomes based on Goals

### Analysis of Outcomes Based on Launch Date

Analyis of outcomes based on launch date provide a few important insights that will help Louise. To assess how campaign performance is affected by the time of year launched, a pivot table was created to compare "successful", "failed", and "cancelled" outcomes, filtered by month. From Figure. 4, we can see both May and June are the best months to launch and December is the worst. 

![Image of Outcomes based on launch date](https://github.com/jkenning/Kickstarter-analysis/blob/main/Resources/Theater_Outcomes_vs_Launch.png)

Figure. 5 - Theater Outcomes Based on Launch Date

### Analysis of Outcomes Based on Goals

Next, it can be observed whether outcomes based on goals have a correlation with successful project outcomes. A new table was created to bin projects into fundraising goal ranges, with the number and percentage of "successful", "failed", and "cancelled" projects calculated using a 'COUNTIFS()' formula on the original data set. Figure. 5 below suggests that overall, the higher the goal the higher the sum of failed projects vs. successful and vice versa. The exception to the trend are projects with goals between $35,000 and $44,999, however there is a significant increase in the ratio of failed vs. successful projects with goals above $45,000.

![Image of Outcomes based on goals](https://github.com/jkenning/Kickstarter-analysis/blob/main/Resources/Outcomes_vs_Goals.png)

Figure. 6 - Theater Outcomes Based on Goals

### Challenges and Difficulties Encountered

One of the main challenges encountered during the project was deciding how to address outliers in the data and whether eliminating outliers could help better plan her campaign. Changing or removing data points can change the story and results provided by the data. There are certainly outliers in the dataset which are more likely to be errors or non-representative, such as a project with a goal of $100,000,000, but others can be less obvious and their inclusion can impact results one way or another. 

On the visualization side, learning how best to write and format this report as a readme file for GitHub required some trial and error, particularly researching how to properly embed image files to display charts and demonstrate results in a clear and effective format. 

## Results

Conclusions from Outcomes Based on Launch Date:
- May and June are the months with the highest number of successful project outcomes and may be the best time for Louise to launch her campaign
- The slightly higher numbers of failed campaigns during the summer months are significantly offset by the significantly larger increase in successful campaigns during this time of year
- December is the worst month to launch, with virtually as many failed campaigns as those that were successful

Conclusions from Outcomes based on Goals?
- Generally, the sum of percentage for failed projects increases with larger funding goals, and conversely, the sum of percentage for successful projects decreases
- Only projects with goals less than $20,000 have a higher proportion of successful projects than failed, with the exception of projects with goals in the $35,000-44,999 range - which could suggest other factors at play
- The proportion of failed projects increases significantly for projects with goals over $45,000, where less than 20% of projects are successful; indiciating a potential hard cut off for project success

Limitations of the dataset:
- The analysis involved only a little over 4000 entries from Kickstarter, other crowdfunding sites may provide additional data with different outcomes that could be compared
- The dataset is from projects launched between 2014-2016, to provide more accurate conclusions for Louise, data from more recent years should be added and may prove more relevant if trends have changed
- Little information regarding the backers themselves, it would be useful to see how many potential backers were active on the crowdfunding sites during the times these data were collected, and what their donation preferences were
- We do not know the reasons why some projects were cancelled
- It would be useful to know how long Louise plans to run her project
- We do not know how good an individual project idea/scope is and how well it is implemented

Additional analysis and visualizations that could be created:
- Circumstances for individual projects differ, it could be useful to analyze more detailed information such as subcategories within the "Play" subcategory, e.g. genre
- In addition to looking at the best month to launch a project, displays could be made to see if the day of the week or time of day to launch also has an impact
- Plot project success and failure percent by year to see if project success for theaters and plays is becoming easier or more difficult, including more recent data in the analysis
- Compare success and failure for different countries to see if there are potentially better locations for Louise to launch her play
- Assess relationships of the total numbers of backers and average amount pledged per backer and impact on project success - which types of projects attract more backers and/or greater individual contribution
- Impact of success rate vs. project duration
- Plot to show what percentage of a goal was funded rather than just whether it was successful, failed or cancelled
- Plots to show differences by country or even city
