# Forests in Transition: Visualizing Global Deforestation
## Project 1 repo for INFO 526 - Fall 2023
Uncovering Global Deforestation and Soy Bean Consumption  \
Authors: Megan, Shakir, Maria, Eshaan, Bharath   \
Affiliation: School of Information, University of Arizona\  

## Overview
This project delves into two crucial aspects of global environmental dynamics using the Global Deforestation dataset, a comprehensive resource published by Hannah Ritchie and Max Roser in the Our World in Data journal in 2021. The dataset encompasses a wide array of attributes related to global forest cover, deforestation rates, and associated factors. Two distinct questions guide our exploration.

## Question 1: What does the global forest area look like over past decades, highlighting the trends of forest area conversion?
To address this question, we implemented a choropleth map visualization highlighting the forest conversion for specific decades and spotlighting few countries with extensive forest conversion. We began to scout the data for getting relevant information and noteworthy details. The whole approach can be categorized into Data Preparation and Pre-processing, Visualizing the data and Animating the plots.

*Data Preparation and Pre-processing*

To generate a map plot we needed geographical information which is not present in the dataset and was achieved by utilizing the maps package in R. From this world data we retrieved all the unique countries for further processing and also filtered out Antarctica from the data.

A custom function, `processForest()`, is developed to handle the pre-processing of the forest conversion dataset. This function is used filter countries, ensuring all entities present in the map data are included. It also used to categorize countries based on their net forest conversion rates, grouping them into distinct categories. The processed forest conversion data is split into subsets for each decade (1990, 2000, 2010, and 2015). The split() function in R is employed to divide the data based on the year column.

A custom function, `filterCountries()`, is created to identify and extract specific countries of interest. These countries are singled out due to their significant forest conversion.

*Visualization the data and Animating the plots*

The ggplot2 package in R is utilized to create detailed visualizations for each decade. For each decade, a map is generated where countries are color-coded according to their forest conversion categories. The geom_map() function is employed to plot the world map, and additional layers are added to highlight the noteworthy countries, ensuring they stand out in the visual representation.We’ve encapsulated the common plotting logic for all decades within a function called generateForestConversionPlot(). This function streamlines the process of generating plots for each specific decade.

We also developed a function called generatePlotforAnimation(), designed specifically to adjust text sizes in the original plot to enhance clarity during animation and save the resulting plots. The individual plots for each decade are compiled into an animated GIF using the gganimate package. The resulting GIF provides a dynamic overview of the global forest conversion patterns, emphasizing the transformations occurring over the specified decades.

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

![Soybean](https://github.com/INFO526-DataViz/project-01-The-Plotting-Pandas/blob/main/images/soybean_brazil_animation.gif) 

![Brazil](https://github.com/INFO526-DataViz/project-01-The-Plotting-Pandas/blob/main/images/forest_brazil_animation.gif)


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
