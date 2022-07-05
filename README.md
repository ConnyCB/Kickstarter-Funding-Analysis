# Data Analysis - Kickstarter Dataset 

## Project Description
Under the domain www.kickstarter.com, the US company Kickstarter offers an online platform on which creatives from a wide range of industries and genres can present their projects to a broad mass of potential supporters and create crowdfunding campaigns to finance them.

The realization of a Kickstarter campaign is complex and time-consuming. We investigated whether and how category, country of origin, target amount and duration affect the success of the campaign in order to evaluate the prospects of success at an early planning stage. to assess the likelihood of success at an early planning stage. 

For this purpose, we have a dataset with 378661 Kickstarter projects.

Campaigns in the following areas have proven to be particularly promising with over 50% chance of success Dance (65.44%), Theater (63.8%), Comics (59.14%), and Music (52.66%) proved to be particularly promising. Smaller target amounts up to $5,000 also have a good chance of success, with the value varies between the individual countries. Above USD 15,000 target amount funding presents a challenge. The optimal duration of a campaign was determined to be 8 to 38 days.

## Technologies:
- Jupyter Notebook
- Python
- Pandas
- Numpy
- Seaborn
- Matplotlib

## Data Source: 
Kickstarter dataset: https://www.kaggle.com/kemical/kickstarter-projects#ks-projects-201801.csv 
(provided on Kaggle.com by Mickaël Mouillé,open license, CC BY-NC-SA 4.0).
The data was downloaded directly from the Kickstarter platform and appears plausible and trustworthy. 
The dataset contains 378661 projects, each with 15 variables.
Most attributes are self-explanatory, usd_pledged_real and usd_goal_real were
additionally generated and provided to convert the different currencies into USD to achieve comparability.
An initial data quality check is performed using Panda's profiling report and provides the following insights:

## Missing Data:
With 0.1% missing values, the data set is nearly complete. 
The variable name has 4 missing values, usd_pledged has 3794 missing values. 
The name of the project is not relevant to clarification of the research question. 
The variable usd_pledged is not included in the analysis because it contains only support amounts in USD. 
All other currencies are not included in it. Instead, a complete picture of pledged support in USD is provided by the variable usd_pledged_real.

## Coding Issues:
Some data were not available in a suitable form to be analyzed directly. 
This data will be processed appropriately prior to analysis.

## Anonymity:
The dataset contains variables that allow identification of crowdfunding recipients. 
This data (ID and name) is deleted from the dataset.

## Data Cleaning
Cleaned dataset **clean_data**:
The present dataset contains 5 different instances of the variable project status.
(state): failed (52.22%), successful (35.38%), canceled (10.24%), live (0.74%) and suspended (0.49%).
The projects with undefined, live, and suspended status do not provide usable information on the success of the campaign, as they are either still running, have been halted, or cannot be clearly assigned. With less than 1% each, this data can be dispensed with in the analysis. It is somewhat more difficult to evaluate the status canceled, which accounts for a considerable share of just over 10%. The reasons for discontinuing a project are manifold and presumably often lie outside the variables under consideration.
There may be changes that cause the project to fall behind schedule, or the promised counter-performance cannot be provided. Furthermore, the status does not allow inference about success or failure. Our research question relates directly to the success or failure of a campaign. Therefore, these projects were deleted from the dataset.

The cleaned dataset contains 331675 projects.

New variable: **clean_data_country**:
The Kickstarter dataset contains information about the country where the project was launched.
210 projects have "N/0" as the country designation. A search for the meaning of this designation did not yield an explanation.
It can be assumed that these are projects for which no country was specified
or the entry could not be clearly assigned. Therefore, for analyses involving the impact of country on the likelihood of campaign success, 
the dataset was cleaned of projects without a country designation. 


The cleaned dataset contains 331465 projects.

New variable: **lifespan** (campaign duration):
The newly created variable represents the campaign lifespan in days and results from
the start and end of the campaign.

New variable: **goal_group** (classification of the target amounts in 6 blocks)
The target amount of the campaigns has a high bias with values between 0.01
USD and 1.000.000.00 USD. The majority of the target amounts are between 2,000 and
15,000 USD, with the average at 41,510 USD.6
Therefore, the values were summarized in the following 6 steps:
(1) Target amount (USD) 0-500 27588 projects.
(2) Target amount (USD) 501-1000 27868 projects
(3) Target amount (USD) 1001-5000 112411 projects
(4) Target amount (USD) 5001-15000 84344 projects
(5) Target amount (USD) 15001-100000 69636 projects
(6) Target amount (USD) >100000 9828 projects