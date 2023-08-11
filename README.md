
<br>

<div align = center>

[![Badge License]][License]   
[![Badge Likes]][#]

<br>
<br>
    
# Buttons
         
**Links  ➞  Buttons**

<br>
<br>

[<kbd> <br> KeyBinding Button <br> </kbd>][KBD]

[![Button Shield]][Shield]

</div>

<br>
<br>


<!---------------------------------------------------------------------------->

[Button Shield]: https://img.shields.io/badge/Shield_Buttons-37a779?style=for-the-badge

[License]: LICENSE
[Shield]: Types/Shield.md
[KBD]: Types/KBD.md
[#]: #


<!---------------------------------[ Badges ]---------------------------------->

[Badge License]: https://img.shields.io/badge/-BY_SA_4.0-ae6c18.svg?style=for-the-badge&labelColor=EF9421&logoColor=white&logo=CreativeCommons
[Badge Likes]: https://img.shields.io/github/stars/MarkedDown/Buttons?style=for-the-badge&labelColor=d0ab23&color=b0901e&logoColor=white&logo=Trustpilot

-
title: "Untitled"
output: 
    ioslides_presentation:
        fig_width: 7
        fig_height: 6
        fig_caption: true
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = FALSE)
```

## R Markdown

This is an R Markdown presentation. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document.

## Slide with Bullets

- Bullet 1
- Bullet 2
- Bullet 3

## Slide with R Output {.flexbox .vcenter}

```{r message=FALSE}
library(highcharter)
library(tidyverse)
library(lubridate)

Moisture_kurokawa <- read_csv("./raw.csv") %>%
  na.omit() %>%
  mutate(timestamp = mdy_hms(sprintf("%s %s", Date, Time)))

hc <- highchart(type="stock")
for (k in names(Moisture_kurokawa)[3:7]) {
  hc <- hc_add_series_times_values(hc=hc, dates=Moisture_kurokawa$timestamp, 
                               values=pull(Moisture_kurokawa, k), name = k)
}
hc %>% 
    hc_legend(enabled=TRUE)

```
