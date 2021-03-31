---
title: "IO & Econometrics workshop - PS1"
author: Doron Zamir
output: 
  html_document: 
    keep_md: yes
---
This is a markdown file created using RStudio.

### Using Packeges
I used these packages to create the data:


```r
library(tidyverse)
library(knitr)
library(magrittr)
```


## Tidy the Data
### Importing Data
 
I used the data from [David Card's website](https://davidcard.berkeley.edu/data_sets.html) 
The relevant file is `nls.dat` saved in the `Data` directory.


```r
data <- read.table("Data/nls.dat") %>% as_data_frame()
head(data)
```

```
## # A tibble: 6 x 52
##      V1    V2    V3    V4    V5    V6    V7    V8    V9   V10   V11   V12    V13
##   <int> <int> <int> <int> <int> <int> <int> <int> <dbl> <int> <dbl> <int>  <int>
## 1     2     0     0     0     0     7     5    29  9.94     1  10.2     1 158413
## 2     3     0     0     0     0    12    11    27  8        0   8       0 380166
## 3     4     0     0     0     0    12    12    34 14        0  12       0 367470
## 4     5     1     1     1     0    11    11    27 11        0  12       0 380166
## 5     6     1     1     1     0    12    12    34  8        0   7       0 367470
## 6     7     1     1     1     0    12    11    26  9        0  12       0 380166
## # ... with 39 more variables: V14 <int>, V15 <int>, V16 <int>, V17 <int>,
## #   V18 <int>, V19 <int>, V20 <int>, V21 <int>, V22 <int>, V23 <int>,
## #   V24 <int>, V25 <int>, V26 <int>, V27 <int>, V28 <int>, V29 <chr>,
## #   V30 <chr>, V31 <int>, V32 <int>, V33 <int>, V34 <chr>, V35 <int>,
## #   V36 <chr>, V37 <chr>, V38 <int>, V39 <chr>, V40 <chr>, V41 <chr>,
## #   V42 <int>, V43 <int>, V44 <int>, V45 <chr>, V46 <chr>, V47 <chr>,
## #   V48 <chr>, V49 <chr>, V50 <chr>, V51 <chr>, V52 <chr>
```
### Changing col names & type

Using variable names from `code_bk.txt'


```r
colnames(data) <-(c("id","nearc","nearc4","nearc4a","nearc4b","ed76","ed66  ","age76","daded ","nodaded","momed","nomomed","weight","momdad14 ","sinmom14","step14","reg661","reg662","reg663","reg66","reg665","reg666","reg667","reg668","reg669","south66","work76","work78","lwage7","lwage78","famed","black","smsa76r","smsa78r","reg76r","reg78r","reg80r","smsa66r","wage76","wage78","wage80","noint78","noint80","enroll76","enroll78","enroll80","kww","iq","marsta76","marsta78","marsta80","libcrd14"))

data %>% mutate_if(is_character,as.numeric)
```

```
## # A tibble: 3,613 x 52
##       id nearc nearc4 nearc4a nearc4b  ed76 `ed66  ` age76 `daded ` nodaded
##    <int> <int>  <int>   <int>   <int> <int>    <int> <int>    <dbl>   <int>
##  1     2     0      0       0       0     7        5    29     9.94       1
##  2     3     0      0       0       0    12       11    27     8          0
##  3     4     0      0       0       0    12       12    34    14          0
##  4     5     1      1       1       0    11       11    27    11          0
##  5     6     1      1       1       0    12       12    34     8          0
##  6     7     1      1       1       0    12       11    26     9          0
##  7     8     1      1       1       0    18       16    33    14          0
##  8     9     1      1       1       0    14       13    29    14          0
##  9    10     1      1       1       0    12       12    28    12          0
## 10    11     1      1       1       0    12       12    29    12          0
## # ... with 3,603 more rows, and 42 more variables: momed <dbl>, nomomed <int>,
## #   weight <int>, momdad14  <int>, sinmom14 <int>, step14 <int>, reg661 <int>,
## #   reg662 <int>, reg663 <int>, reg66 <int>, reg665 <int>, reg666 <int>,
## #   reg667 <int>, reg668 <int>, reg669 <int>, south66 <int>, work76 <int>,
## #   work78 <int>, lwage7 <dbl>, lwage78 <dbl>, famed <int>, black <int>,
## #   smsa76r <int>, smsa78r <dbl>, reg76r <int>, reg78r <dbl>, reg80r <dbl>,
## #   smsa66r <int>, wage76 <dbl>, wage78 <dbl>, wage80 <dbl>, noint78 <int>,
## #   noint80 <int>, enroll76 <int>, enroll78 <dbl>, enroll80 <dbl>, kww <dbl>,
## #   iq <dbl>, marsta76 <dbl>, marsta78 <dbl>, marsta80 <dbl>, libcrd14 <dbl>
```




