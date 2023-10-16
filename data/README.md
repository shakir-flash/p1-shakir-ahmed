# Data

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

# `brazil_loss.csv`

Loss of Brazilian forest due to specific types.

|variable                        |class     |description |
|:-------------------------------|:---------|:-----------|
|entity                          |character | Country |
|code                            |character | Country code |
|year                            |double    | Year |
|commercial_crops                |double    | Commercial crops |
|flooding_due_to_dams            |double    | Flooding |
|natural_disturbances            |double    | Natural disturbances |
|pasture                         |double    | Pasture for livestock |
|selective_logging               |double    | Logging for lumber |
|fire                            |double    | Fire loss |
|mining                          |double    | Mining|
|other_infrastructure            |double    | Infrastructure |
|roads                           |double    | Roads |
|tree_plantations_including_palm |double    | Tree plantations |
|small_scale_clearing            |double    | Small scale clearing |

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

# `vegetable_oil.csv`

Vegetable oil production by crop type and year.

|variable   |class     |description |
|:----------|:---------|:-----------|
|entity     |character | Country |
|code       |character | Country code |
|year       |double    | Year |
|crop_oil   |character | Crop that was used to produce vegetable oil |
|production |double    | Oil production in tonnes |

# `forest-area-km.csv`

Change in global forest area of global forest area.

|variable    |class     |description |
|:-----------|:---------|:-----------|
|entity      |character | Country|
|code        |character | Country Code |
|year        |integer   | Year |
|forest_area |double    | Percent of global forest area |

# Codebook for the Dataset
```{r}
# GETTING THE LIBRARIES
if (!require(pacman))
  install.packages(pacman)


pacman::p_load(tidyverse,
               tidytuesdayR,
               here)
               
# Getting all the underlying data in the dataset
forest        <- read.csv(here("data", "forest.csv"))
forest_area   <- read.csv(here("data", "forest_area.csv"))
brazil_loss   <- read.csv(here("data", "brazil_loss.csv"))
soybean_use   <- read.csv(here("data", "soybean_use.csv"))
vegetable_oil <- read.csv(here("data", "vegetable_oil.csv"))
total_forest  <- read.csv(here("data", "forest-area-km.csv"))
deforestation_by_source <- read.csv(here("data", "deforestation_by_source.csv"))

```



