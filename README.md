# Forests in Transition: Visualizing Global Deforestation
Uncovering Global Deforestation and Soy Bean Consumption  \

## Overview
This project delves into two crucial aspects of global environmental dynamics using the Global Deforestation dataset, a comprehensive resource published by Hannah Ritchie and Max Roser in the Our World in Data journal in 2021. The dataset encompasses a wide array of attributes related to global forest cover, deforestation rates, and associated factors. Two distinct questions guide our exploration.

## Question 1: What does the global forest area look like over past decades, highlighting the trends of forest area conversion?
To address this question, we implemented a choropleth map visualization highlighting the forest conversion for specific decades and spotlighting few countries with extensive forest conversion. We began to scout the data for getting relevant information and noteworthy details. The whole approach can be categorized into Data Preparation and Pre-processing, Visualizing the data and Animating the plots.

## Dynamic display of forest conversion across the countries over the past decades

![World Forestation](https://github.com/INFO526-DataViz/project-01-The-Plotting-Pandas/blob/main/images/world_forestaion.gif)

## Question 2: How has the consumption of Soybean in Brazil changed over time, and how does it impact the afforestation or deforestation rates?
### Cleaning and processing of the dataset includes the following steps:

*Soybean consumption in Brazil:*

- Created a new column for calculating the total soybean consumption. Removing totals of countries whose total consumption is 0 using the subset function.
- Filtering for Brazil under the entity column, and year between 1990 and 2013.

*Forest coverage in Brazil:*

- Filtering for year between 1990 and 2013 in the forest_brazil dataset.
- There is a parameter ‘World’ which shows the overall forest coverage data. Filtering out entity as ‘World’ and year between 1990 and 2013, and grouping by year.
- Using `left_join` we merge the two tables based on the year column.
- Since we now have percentage data and total data per year, we can calculate the change in forest coverage for Brazil by doing `forest_area.x` * `forest_area.y`.

## Dynamic display of soybean consumption and forest conversion in Brazil
<div id="header" align="center">
  <img src="https://github.com/INFO526-DataViz/project-01-The-Plotting-Pandas/blob/main/images/soybean_brazil_animation.gif"/>

  <img src="https://github.com/INFO526-DataViz/project-01-The-Plotting-Pandas/blob/main/images/forest_brazil_animation.gif"/>
</div>

## Primary Dataset used

# `forest.csv`

Change every 5 years for forest area in conversion.

|variable              |class     |description |
|:---------------------|:---------|:-----------|
|entity                |character | Country |
|code                  |character | Country code |
|year                  |double    | Year |
|net_forest_conversion |double    | Net forest conversion in hectares|

# `forest_area.csv`

Change in global forest area as a percent of global forest area.

|variable    |class     |description |
|:-----------|:---------|:-----------|
|entity      |character | Country|
|code        |character | Country Code |
|year        |integer   | Year |
|forest_area |double    | Percent of global forest area |

# `soybean_use.csv`

Soybean production and use by year and country.

|variable    |class     |description |
|:-----------|:---------|:-----------|
|entity      |character | Country|
|code        |character | Country Code |
|year        |double    | Year |
|human_food  |double    | Use for human food (tempeh, tofu, etc) |
|animal_feed |double    | Used for animal food |
|processed   |double    | Processed into vegetable oil, biofuel, processed animal feed |


## Resources used:
TidyTuesday Data - [Global Deforestation 2021 Data](https://github.com/rfordatascience/tidytuesday/tree/master/data/2021/2021-04-06)

Total forest coverage data- Hannah Ritchie (2021) - "Forest area". Published online at OurWorldInData.org. Retrieved from: 'https://ourworldindata.org/forest-area' [Online Resource]

#### Disclosure:
Template derived from the original course by Mine Çetinkaya-Rundel @ Duke University
