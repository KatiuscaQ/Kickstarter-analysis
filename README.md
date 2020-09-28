# Kickstarting with Excel

## Overview of Project
The purpose of this analysis is to explain to Louise how different campaigns fared in relation to their launch dates and their funding goals.

## Analysis and Challenges: 
### Analysis of Outcomes Based on Launch Date
Base on the data analyzed the optimal launch date should take place in May. The chart below shows the total amount of outcomes and how they change through the months.  As the legend in the chart shows: The darker blue line represents the successful outcomes, the grey line represents the failed outcomes, and the light blue line represents the canceled outcomes. The successful line rises from the months of January and peeks in May, after May a decline is noticed coming to the lowest point in December. The failed line does not present a dramatic raise and fall. Meanwhile the canceled line is close to zero (0). 

![Theater_Outcomes_vs_Launch](https://github.com/KatiuscaQ/Kickstarter-analysis/blob/master/Resources/Theater_Outcomes_vs_Launch.png)

### Analysis of Outcomes Based on Goals
The successful outcomes of the plays decrees steadily from less than $1000 to $29999, then increases dramatically from $30000 to $35000 where it levels off until $44999 and then shows a dramatic decrees from $450000 on. The failed outcome based on the goals acts the exact opposite to the successful outcome. 
Comparing Louise’s goal of $10000 with the kick-stater data of plays with goals between $10000-14999 there is a 54.17% chance that her play Fever will be successful.

![Outcomes_vs_Goals](https://github.com/KatiuscaQ/Kickstarter-analysis/blob/master/Resources/Outcomes_vs_Goals.png)
 
### Challenges and Difficulties Encountered
In order to come up with the analysis of the “Outcomes based on launch date” I compared all the outcomes (successful, failed, and canceled) of the theater campaigns with their launch dates. I populated a pivot table and filtered it with “parent categories” and “years,” and since I wanted to show Louise the comparison of the outcomes vs the launch dates, I placed the outcomes data in the columns and in the values (in that way I can show her the actual numbers of each outcome) and the launch dates in the rows.

One challenge encountered was that the Launch date originally was in Unix Timestamps which could be confusing if someone is expecting to see a date and instead, they see a large number. This challenge was overcome by converting the Unix timestamp in a more readable way with the formula =(((J2/60)/60)/24)+DATE(1970,1,1) in which the cell J2 (first cell with the launch dates) is divided by 60 (meaning 60 seconds), then divided by 60 (minutes), and then 24 (hours), and then added to the stablish date 1970,1,1 (this is called epoch and it is the date the Unix stamps start counting from). The cells where this formula is executed must be formatted to “date.”

Also, when populating the rows, I noticed all the row labels where quarters instead of months (screenshot shown below). In order to make it simple and clearer to my client (Louise) I had to show months. To solve this I dragged the “Quarters” field out of the row area and then my pivot table showed the months which is the information I wanted to share with Louise (also, I could just un-check the Quarters field in the field area to show month instead of quarters).
 ![Challenge_found_quarters](https://github.com/KatiuscaQ/Kickstarter-analysis/blob/master/Resources/Challenge_found_quarters.PNG)
 
For the analysis of the “Outcomes based on goals” I created a table with a goal column in which I showed ranges of different goals, these ranges were compared to the amount of successful, failed, and canceled outcomes of all the plays from the subcategory column in the kick-starter sheet. The way I did this was by using the formula =COUNTIFS which commands excel to look for “successful” outcomes while also looking for “plays” and at the same time looking for a specific goal range (example: from $10000 to $14999) and to count this findings. I did the same for the columns of failed and canceled outcomes. The following show how the formula works:

_**=COUNTIFS(Kickstarter!D:D,">=10000",Kickstarter!D:D,"<=14999",Kickstarter!F:F,"successful",Kickstarter!R:R,"plays")**_

**=COUNTIFS(criteria_rage1,criteria1,criteria_range2,criteria2,…)** this commands excel to look for certain criteria in within a range and count the amount of values that meet such criteria.

**Kickstarter!D:D,">=10000"** first Kickstarter!D:D is the criteria range and this tells excel to look in the column D of the sheet “Kickstarter”, nothing else. Second after the comma “,” and between quotation is ">=10000" this is the criteria and this tells excel “this is the exact thing you have to look for” (that is way the quotations are used for). After this two steps are met, in other words after excel looks in the column and finds the criteria, it will give a count of all the values that were found.

**Kickstarter!D:D,"<=14999"** this is the second criteria range and criteria of the formula, in which excel have to look in the same column for values less than or equal to 14999 and count them.

**Kickstarter!F:F,"successful"** this is the third criteria range and criteria of the formula, in this case excel is looking for all the cells that contained the word “successful” in the column F of the same sheet.

**Kickstarter!R:R,"plays"** this is the fourth and final criteria of the formula and it tells excel to look into the column R of the Kickstarter sheet and count the cells that contained the word “play”
 
Another value that I wanted to show Louise with this analysis was the percentages of each outcome. Percentages are easier to analyze than a counted number because it is a comparison between the counted number of certain criteria (outcomes in this case) and the total amount of all the criteria. Saying this, it is not the same to say the total of Kickstarter for plays that were successful with a goal of $10000-14999 is 39 when there is no knowledge of how many Kickstarter were taking in count, if it is a total of 39 kickcstarters that means 100% of the Kickstarter with this goal range is successful, but if the total is 1000 Kickstarter and only 39 were successful that means only 3.9% on the kickstarters with the goal is going to succeed.

In onder to show Louise these percentages I had to sum three values: number successful+number failed+number canceled, with that I have the total amount of Kickstarters for plays within the different goal ranges, which I called in the table “Total Projects.” I use the formula *=SUM(B2:D2)* which add all numbers from the selected cells (in this case from B2 to D2). For the percentage I use the formula *=B2/E2* (where B2 is the first Number Successful and E2 is the first Total Project), I dragged this formula vertically and did a similar formula for the next two columns *=C2/E2* and *=D2/E2* and dragged them down also, then I formatted all the cells from my last three columns *(F2:H13)* as Percentage.

I did not encounter any challenge with this analysis but I can see how using the formula *=COUNTIF* instead of *=COUNTIFS* could confuse, if not frustrate, somebody new to excel that does not know the difference between the two (the first is for one criteria, the second for countless criteria).

## Results
### What are two conclusions you can draw about the Theater Outcomes based on Launch Date?
Base on the line graph “Theater outcome based on launch date” I can conclude that:
1.	For Louise to have a successful launch date she will have to concentrate on making opening day in the months of April, May, June, July, or August. The data shows me that May is the optimal month when the most successful launches occurred. This might be due to the weather or the holidays, both are speculative, but the fact is that the most successful outcomes are showing during the hottest months of the northern hemisphere.
2.	The failed outcomes are more consistent and less volatile in regards to launch dates.
 
### What can you conclude about the Outcomes based on Goals?
The conclusion from the graph “Outcomes based on Goals” is as simple as the lower the goal the most success a play can have, the higher the goal the higher the possibility of failure.

### What are some limitations of this dataset?
There are more data points that could have been used i.e.: staff_pick, spotlight, etc., if there was an explanation of to what these values meant. For example: all the “successful outcomes” show “TRUE” in the spotlight column.

### What are some other possible tables and/or graphs that we could create?
I considered looking into the outcomes based on the backers count and found out that the number of backers that were behind a successful kick-starter campaign in the Theater category were over 53000 compared to the number of backers behind a kick-starter campaign that failed. Graph shown below:

![Outcome_based_on_backers_count](https://github.com/KatiuscaQ/Kickstarter-analysis/blob/master/Resources/Outcome_based_on_backers%20_count.png)

Another table and/or graph could have been “Outcomes based on country” which shows that the top three data sources were United States, Great Britain, and Canada, specially the US and GB when it comes to the Theater category. See below table and graph:
  
![Outcome_based__on_country_table](https://github.com/KatiuscaQ/Kickstarter-analysis/blob/master/Resources/Outcome_based%20__on%20_country_table.PNG)
![Outcome_based__on_country](https://github.com/KatiuscaQ/Kickstarter-analysis/blob/master/Resources/Outcome_based%20__on%20_country.png)

