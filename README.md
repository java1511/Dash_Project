The purpose of this exercise it to build a picture of wealth and revenue distribution across France's counties (Departements)
This exercise will allow us to practice all every aspect of Exploratory Data Analysis:

  	- Collect data for an external source and turn it into a workable dataframe
	- Remove unnecessary columns
	- Group the data per county code bearing in mind the following rules : they can be 2 digits long for codes ranging from 01 to 95 and 3 digits long for overseas territories ranging from 971 to 988. They are also two territories (Corsica) with codes mixing numeric and alphanumeric (2A and 2B). It is understood that the statistical value becomes less relevant as means within a county will not take into account the discrepancies in that county. This exercise focus on the Python coding and data analysis techniques.

Data Exploration
———————————————-

Looking at the data counts for the different columns, we observe that all the columns have balanced number of data in them:
- 12395 populated fields in columns 0, 24
- 12394 populated fields for columns 3 to 14, 17, 18, 22, 23
- 12355 populated fields for column 16
- 11954 populated fields for columns 19 to 21
- 11740 populated fields for column 15
- 11390 populated fields for column 1
- 10598 populated fields for column 2


The metadata file provides me with the meaning of the different fields in the data set. The field named DEC_NOTE18 was of particular importance as it rates the quality of each record. The different categorical values are:

 - 0 - no particular issue.
 - 1 - strong increase from previous year (might be due to fiscal changes in the rules). Acceptable.
 - 5 - information too inconsistent to be released. Not reliable.

We need to assess the reliability of the data. To do so, we check the number of occurrences for each categorical value. The distribution is as follows:

- 12262 out of 12395 records are rated 0
- 132 out of 12395 records are rated 1
- 1 out 12395 records is rated 5

12262 records are rated 0 (showing n particular issue). It amounts to 98.92% of the data set. The data looks reliable.


To achieve the exercise's objective, the dataset must be manipulated. The final result should be a dataframe with one record per county code. To do so:

   - Several columns must be removed (not necessary)
   - The IRIS code must be manipulated so that each county code is isolated, bearing in mind the constraints stated at the beginning of this exercise
   - The data must be grouped per county code

County codes rules:
Mainland France's county codes are two-digit long and range from 01 to 95.
Corsica's county codes are a mix of alpha and numerical characters : 2A and 2B.
French overseas territories are three-digit long and range from 972 to 988.
I could not think of a single approach to extract the county codes from the IRIS codes. I decided to break up the main dataset in three subsets (one for main land, one for corsica and one for the overseas territories) in order to use different filtering methods. Once the three subsets are created, we group the records in each one of the subsets. Finally, we combine the three subsets into a main one that will be used for visualization.


Data analysis
—————————————

Regarding the diagram ‘Unemployment rate vs inequality’:
Regarding the top bar charts: We observe that the inequality is limited to values ranging from 0.32 to 0.50. The average index for France, in 2018 was 0.32. Slightly above the EU average standing at 0.29.

2 of the top 10 unequal counties are overseas territories.
The top 10 equal counties have an index of 0.32 or 0.33.

There seems to be a light correlation. The counties with the highest Inequality index are also the one with the highest proportion of unemployment recipients. The lower the number of unemployment benefits, the lower the inequality index.

Regarding the diagram ‘employment rate vs inequality’

This graph comes to nuance the previous diagram. Although the trend is respected in that counties with the biggest number of employed population seem to have a lower inequality index, there are more factor to explain the inequality index. Counties such as La Réunion show a high rate of employment and yet score badly in terms of inequality.

Data Visualization
   - Visualise the data in different ways:
        - Top 10 unequal counties
        - Top 10 equal counties
        - Interactive dashboard to provide the revenue breakdown for a particular county
        - Build a geographical heat map to display the data.
