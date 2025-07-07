# Past-projects
---
title: "ECON 125 Problem Set 1"
author: "Mia Yu"
output: pdf_document # can change to pdf_document if you have LaTeX

---

```{r, message = FALSE, include = FALSE}
# This code block sets up the R environment for you
# You do not need to edit it

# Clear the R environment
rm(list=ls())

# Load tidyverse
library(tidyverse)

# Load data into data frame and call it df
df <- read_csv(url("https://github.com/tomvogl/econ125/raw/main/data/UN_pop_change_country_year.csv"))

# Ask R to only report 2 significant digits
options(digits = 2)
```

## Summary statistics for the full dataset

```{r}
mean(df$pop, na.rm=TRUE)
max(df$pop, na.rm=TRUE)
min(df$pop, na.rm=TRUE)
```

The largest population in the dataset is 1438070000 people.

## Summary statistics for 1950 and 2023

```{r}
df_filtered <- df %>%
  filter(year==1950 | year==2023) %>%
  group_by(year) %>%
  summarise(mean=mean(pop),
            min=min(pop),
            max=max(pop))

print(df_filtered)
```

 In 1950 the largest population is 544044000 people and in 2023 the largest population is 1438070000 people.
