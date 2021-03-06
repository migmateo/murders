Report on Gun Murders
================
Miguel Mateo
08/08/2021

`{r setup, include=FALSE}  knitr::opts_chunk$set(echo = TRUE)`

## Introduction

This is a report on 2010 gun murder rates obtained from FBI reports. The
original data was obtained from [this Wikipedia
page](https://en.wikipedia.org/wiki/Murder_in_the_United_States_by_state).

We are going to use the following library:

`{r loading-libs, message=FALSE}  library(tidyverse)`

and load the data we already wrangled:

``` {r}
library(dslabs)

data("murders")

murders <- mutate(murders, rate = total / population * 100000)
```

## Murder rate by state

We note the large state to state variability by generating a barplot
showing the murder rate by state:

`{r murder-rate-by-state, echo=FALSE}  murders %>% mutate(abb = reorder(abb, rate)) %>%   ggplot(aes(abb, rate)) +   geom_bar(width = 0.5, stat = "identity", color = "black") +   coord_flip()`
