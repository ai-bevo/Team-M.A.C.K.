# Team M.A.C.K. Repo

Data Visualization Bootcamp—Team Project One

Team M.A.C.K: Michael Lambert, Allan Ivey, Caroline Sudhakar and Kristen Pollok


Abstract:

Type -2 Diabetes is a significant issue facing the United States.  According to the Center for Disease Control, “More than 37 million Americans have diabetes (about 1 in 10), and approximately 90-95% of them have type 2 diabetes. 
Type 2 diabetes most often develops in people over age 45.” (LINK) Our study is an attempt to look at specific, quantifiable correlations.  

Study: 

Analyzed two null hypotheses and their relationship to type-2 diabetes.

Hypothesis One: Analyze population density at the county level and compared to the diagnosis of type-2 diabetes.  Does living in a rural or urban county affect the diagnosis of type-2 diabetes?

Null Hypothesis: There is no statistically significant difference between diagnosis of type-2 diabetes and county size.

Hypothesis Two: Analyze median income at the county level and compare that to the diagnosis of type-2 diabetes. Is there a relationship between how “affluent” a community is and Type-2 diabetes diagnoses?

Null Hypothesis: There is no statistically significant difference between the diagnosis of type-2 diabetes and median income at the county level.


Questions to answer:
 
1. How should this data be organized? Should it be at the State level, County level ?
	County level worked best with the datasets obtained

 2. Population data, how should the data be sliced (binned)?  What would give a good method of organization creating relatively similar sample sizes?
County Size and Type-2 Diabetes:  population bins <10,000, 10,000 to 25,000, 25,001 to 50,000, 50,001 to 100,000, > 100,000
Median Income/County and Type-2 Diabetes: median income bins <50,000, 50,001 to 60,000, 60,001 to 90,000, > 90,001

 3. Once the data is binned what type of test should we run to test our null hypothesis? The following test were performed: ANOVA, Kruskal-Wallis, and  Alexander-Govern 
 4. Can we use the same dataframe to effectively look at diabetes type-2 diagnoses for median income?
	All statistical tests and data visualizations were generated from a merged data frame made up of data pulled from the census API and a CDC CSV file 

Team Responsibilities

In order to adequately divide up the roles and responsibilities we have decided to break the project into four parts.  Each member will be assigned a role.

1.	Data gathering/cleaning: Two people will be assigned to gather the data from each of the agreed upon API/data sources
2.	Data Hypothesis testing: One person assigned
3.	Data Visualization: Two people Assigned: Assigned to create the 6-8 plots.
4.	Project finalization and conclusions: One person assigned
(ADDL): The whole group will write the conclusions and summarize them in a written presentation using PowerPoint or google docs.

Datasets: Census.gov API and CSV from the CDC

Process

Data Sources: Census.gov (via API) & CDC.gov (via csv)

Data Gathering:
Navigating nomenclature for Census API
Collecting all the county data per state concatenate to the dataframe
Use str.split() to separate State & County names
Merging the datasets - always check .astype() before merging
Removing white space in text strings- str.strip()
Use .lower() before merging to match formatting
Cleaning
Convert .str back to .float for analysis
Writing to .csv to easily browse datasets
Locate bad data (ex from data ‘County median income’:  -$66666666)
Dropped 9 rows out of 3142


NULL HYPOTHESIS ONE

Data Visualization 
Map Plot: Percentage type-2 Diabetes by State
Scatter Plot: Percentage Type-2 Diabetes by county
Pie Chart: County Population Size Distribution
Box Plot: Grouped by County Population and Diabetes per 1,000 Population


Statistical Test for Null Hypothesis One (Null Hypothesis: There is no statistically significant difference between diagnosis of type-2 diabetes and county size.)

Performed a one-way (right-tailed) ANOVA test. The one-way ANOVA tests the null hypothesis that two or more groups have the same population mean.  The test is applied to samples from two or more groups, possibly with differing sizes.

Utilized an alpha of .05

The ANOVA test returned a p-value = 4.07e-16

Since the p-value result  < 0.05, therefore we rejected  the null hypothesis. There is a difference based on type 2 diabetes diagnosis and population size.

“The ANOVA test has important assumptions that must be satisfied in order for the associated p-value to be valid.

The samples are independent.
Each sample is from a normally distributed population. (County data is NOT normally distributed)
The population standard deviations of the groups are all equal. This property is known as homoscedasticity.

If these assumptions are not true for a given set of data, it may still be possible to use the Kruskal-Wallis H-test (scipy.stats.kruskal) or the Alexander-Govern test 
(scipy.stats.alexandergovern) although with some loss of power.”

Because of this outcome an additional Kruskal-Wallis H-Test and the Alexander-Govern Test was performed

Kruskal-Wallis Result:

KruskalResult(statistic=78.12, p-value=4.33e-16)

Alexander-Govern Result:

AlexanderGovernResult(statistic=87.86, p-value=3.73e-18)

Both the  results had a p-value <.05 therefore we can still reject the null hypothesis.

NULL HYPOTHESIS TWO

Data Visualization: 
Map Plot: Median Income by County
Scatter Plot: Percentage Type-2 Diabetes per 1,000 people and median household income
Pie Chart: Median Income Distribution
Box Plot: Grouped by Median Income and Diabetes per 1,000 Population

Statistical Test for Null Hypothesis Two (Null Hypothesis: There is no statistically significant difference between the diagnosis of type-2 diabetes and median income at the county level)

Performed a one-way (right-tailed) ANOVA test.  The one-way ANOVA tests the null hypothesis that two or more groups have the same population mean.  The test is applied to samples from two or more groups, possibly with differing sizes.

Utilized an alpha of .05
The ANOVA test returned a p-value = 7.04e-80

The result p-value < 0.05, therefore we reject the null hypothesis. There is a difference based on type 2 diabetes diagnosis and county level median income.

“The ANOVA test has important assumptions that must be satisfied in order for the associated p-value to be valid.

The samples are independent.
Each sample is from a normally distributed population. (County data is NOT normally distributed)
The population standard deviations of the groups are all equal. This property is known as homoscedasticity.

If these assumptions are not true for a given set of data, it may still be possible to use the Kruskal-Wallis H-test (scipy.stats.kruskal) or the Alexander-Govern test 
(scipy.stats.alexandergovern) although with some loss of power.”

Because of this we also ran the additional Kruskal-Wallis H-Test and the Alexander-Govern Test

Kruskal-Wallis Result:
KruskalResult(statistic=356.34, p-value=6.32e-77)

Alexander-Govern Result:
AlexanderGovernResult(statistic=376.08, p-value=3.35e-81)

Both the  results had a p-value <.05 therefore we can still reject the null hypothesis




Citations:

CDC Data: https://gis.cdc.gov/grasp/diabetes/diabetesatlas-surveillance.html# 
Census Data: https://www.census.gov/data/developers/guidance.html 

