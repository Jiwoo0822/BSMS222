---
title: "R Notebook"
output:
  pdf_document: default
  html_document:
    df_print: paged
---

This is an [R Markdown](http://rmarkdown.rstudio.com) Notebook. When you execute code within the notebook, the results appear beneath the code. 

Try executing this chunk by clicking the *Run* button within the chunk or by placing your cursor inside it and pressing *Ctrl+Shift+Enter*. 


```r
library(tidyverse)
```

```
## -- Attaching packages --------------------------------------- tidyverse 1.3.1 --
```

```
## v ggplot2 3.3.5     v purrr   0.3.4
## v tibble  3.1.4     v dplyr   1.0.7
## v tidyr   1.1.3     v stringr 1.4.0
## v readr   2.0.1     v forcats 0.5.1
```

```
## -- Conflicts ------------------------------------------ tidyverse_conflicts() --
## x dplyr::filter() masks stats::filter()
## x dplyr::lag()    masks stats::lag()
```

```r
library(readxl)
#install.packages('rio')

NSLC_6A = rio::import('https://ars.els-cdn.com/content/image/1-s2.0-S0092867420307431-mmc6.xlsx', sheet = 2)
NSLC_6A <- t(NSLC_6A)
NSLC_6A <- as.data.frame(NSLC_6A)
colnames(NSLC_6A)<-NSLC_6A[1,]
NSLC_6A<-NSLC_6A[-c(1,3,4,5),-c(9:15)]
NSLC_6A<-NSLC_6A[,-c(10:72)]

library(tidyverse)
graph1_A <- NSLC_6A %>%
  mutate(Age = as.numeric(Age)) %>%
  mutate(Q96HF1= as.numeric(Q96HF1)) %>%
  mutate(Age = case_when(
    between(Age, 40, 50) ~ "40-50",
    between(Age, 50.01, 60) ~ "50.01-60",
    between(Age, 60.01, 70) ~ "60.01-70",
    between(Age, 70.01, 80) ~ "70.01-80",
    TRUE ~ "80.01-90"
  )) %>%
  ggplot(aes(Age, Q96HF1)) +
  geom_boxplot(aes(fill = Gender, hue = Gender)) +
  geom_jitter(width = 0.1, alpha = 0.2) +
  xlab("") +
  theme(axis.text.x = element_text(angle = 90, hjust = 1))
```

```
## Warning in mask$eval_all_mutate(quo): 강제형변환에 의해 생성된 NA 입니다

## Warning in mask$eval_all_mutate(quo): 강제형변환에 의해 생성된 NA 입니다
```

```
## Warning: Ignoring unknown aesthetics: hue
```

```r
graph2_A <- NSLC_6A %>%
  mutate(Age = as.numeric(Age)) %>%
  mutate(O75339= as.numeric(O75339)) %>%
  mutate(Age = case_when(
    between(Age, 40, 50) ~ "40-50",
    between(Age, 50.01, 60) ~ "50.01-60",
    between(Age, 60.01, 70) ~ "60.01-70",
    between(Age, 70.01, 80) ~ "70.01-80",
    TRUE ~ "80.01-90"
  )) %>%
  ggplot(aes(Age, O75339)) +
  geom_boxplot(aes(fill = Gender, hue = Gender)) +
  geom_jitter(width = 0.1, alpha = 0.2) +
  xlab("") +
  theme(axis.text.x = element_text(angle = 90, hjust = 1))
```

```
## Warning in mask$eval_all_mutate(quo): 강제형변환에 의해 생성된 NA 입니다
```

```
## Warning in mask$eval_all_mutate(quo): 강제형변환에 의해 생성된 NA 입니다
```

```
## Warning: Ignoring unknown aesthetics: hue
```

```r
graph3_A <- NSLC_6A %>%
  mutate(Age = as.numeric(Age)) %>%
  mutate(Q96N03= as.numeric(Q96N03)) %>%
  mutate(Age = case_when(
    between(Age, 40, 50) ~ "40-50",
    between(Age, 50.01, 60) ~ "50.01-60",
    between(Age, 60.01, 70) ~ "60.01-70",
    between(Age, 70.01, 80) ~ "70.01-80",
    TRUE ~ "80.01-90"
  )) %>%
  ggplot(aes(Age, Q96N03)) +
  geom_boxplot(aes(fill = Gender, hue = Gender)) +
  geom_jitter(width = 0.1, alpha = 0.2) +
  xlab("") +
  theme(axis.text.x = element_text(angle = 90, hjust = 1))
```

```
## Warning in mask$eval_all_mutate(quo): 강제형변환에 의해 생성된 NA 입니다
```

```
## Warning in mask$eval_all_mutate(quo): 강제형변환에 의해 생성된 NA 입니다
```

```
## Warning: Ignoring unknown aesthetics: hue
```

```r
graph4_A <- NSLC_6A %>%
  mutate(Age = as.numeric(Age)) %>%
  mutate(P35442= as.numeric(P35442)) %>%
  mutate(Age = case_when(
    between(Age, 40, 50) ~ "40-50",
    between(Age, 50.01, 60) ~ "50.01-60",
    between(Age, 60.01, 70) ~ "60.01-70",
    between(Age, 70.01, 80) ~ "70.01-80",
    TRUE ~ "80.01-90"
  )) %>%
  ggplot(aes(Age, P35442)) +
  geom_boxplot(aes(fill = Gender, hue = Gender)) +
  geom_jitter(width = 0.1, alpha = 0.2) +
  xlab("") +
  theme(axis.text.x = element_text(angle = 90, hjust = 1))
```

```
## Warning in mask$eval_all_mutate(quo): 강제형변환에 의해 생성된 NA 입니다
```

```
## Warning in mask$eval_all_mutate(quo): 강제형변환에 의해 생성된 NA 입니다
```

```
## Warning: Ignoring unknown aesthetics: hue
```

```r
graph5_A <- NSLC_6A %>%
  mutate(Age = as.numeric(Age)) %>%
  mutate(P12107= as.numeric(P12107)) %>%
  mutate(Age = case_when(
    between(Age, 40, 50) ~ "40-50",
    between(Age, 50.01, 60) ~ "50.01-60",
    between(Age, 60.01, 70) ~ "60.01-70",
    between(Age, 70.01, 80) ~ "70.01-80",
    TRUE ~ "80.01-90"
  )) %>%
  ggplot(aes(Age, P12107)) +
  geom_boxplot(aes(fill = Gender, hue = Gender)) +
  geom_jitter(width = 0.1, alpha = 0.2) +
  xlab("") +
  theme(axis.text.x = element_text(angle = 90, hjust = 1))
```

```
## Warning in mask$eval_all_mutate(quo): 강제형변환에 의해 생성된 NA 입니다
```

```
## Warning in mask$eval_all_mutate(quo): 강제형변환에 의해 생성된 NA 입니다
```

```
## Warning: Ignoring unknown aesthetics: hue
```

```r
library(cowplot)
plot_grid(graph1_A, graph2_A,graph3_A, graph4_A,graph5_A,  labels = "AUTO")
```

```
## Warning: Removed 1 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 1 rows containing missing values (geom_point).
```

```
## Warning: Removed 1 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 1 rows containing missing values (geom_point).
```

```
## Warning: Removed 4 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 4 rows containing missing values (geom_point).
```

```
## Warning: Removed 1 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 1 rows containing missing values (geom_point).
```

```
## Warning: Removed 1 rows containing non-finite values (stat_boxplot).
```

```
## Warning: Removed 1 rows containing missing values (geom_point).
```

![](Example_files/figure-latex/unnamed-chunk-1-1.pdf)<!-- --> 

```r
#plot_grid(graph3_A, graph4_A, labels = "AUTO")
#plot_grid(graph5_A, graph6_A, labels = "AUTO")
#plot_grid(graph7_A, graph8_A, labels = "AUTO")
#plot_grid(graph9_A, graph10_A, labels = "AUTO")
```

Add a new chunk by clicking the *Insert Chunk* button on the toolbar or by pressing *Ctrl+Alt+I*.

When you save the notebook, an HTML file containing the code and output will be saved alongside it (click the *Preview* button or press *Ctrl+Shift+K* to preview the HTML file).

The preview shows you a rendered HTML copy of the contents of the editor. Consequently, unlike *Knit*, *Preview* does not run any R code chunks. Instead, the output of the chunk when it was last run in the editor is displayed.
