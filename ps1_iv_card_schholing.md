---
title: "IO & Econometrics workshop - PS1"
author: Doron Zamir
output: 
  html_document: 
    keep_md: yes
    df_print: paged
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

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["V1"],"name":[1],"type":["int"],"align":["right"]},{"label":["V2"],"name":[2],"type":["int"],"align":["right"]},{"label":["V3"],"name":[3],"type":["int"],"align":["right"]},{"label":["V4"],"name":[4],"type":["int"],"align":["right"]},{"label":["V5"],"name":[5],"type":["int"],"align":["right"]},{"label":["V6"],"name":[6],"type":["int"],"align":["right"]},{"label":["V7"],"name":[7],"type":["int"],"align":["right"]},{"label":["V8"],"name":[8],"type":["int"],"align":["right"]},{"label":["V9"],"name":[9],"type":["dbl"],"align":["right"]},{"label":["V10"],"name":[10],"type":["int"],"align":["right"]},{"label":["V11"],"name":[11],"type":["dbl"],"align":["right"]},{"label":["V12"],"name":[12],"type":["int"],"align":["right"]},{"label":["V13"],"name":[13],"type":["int"],"align":["right"]},{"label":["V14"],"name":[14],"type":["int"],"align":["right"]},{"label":["V15"],"name":[15],"type":["int"],"align":["right"]},{"label":["V16"],"name":[16],"type":["int"],"align":["right"]},{"label":["V17"],"name":[17],"type":["int"],"align":["right"]},{"label":["V18"],"name":[18],"type":["int"],"align":["right"]},{"label":["V19"],"name":[19],"type":["int"],"align":["right"]},{"label":["V20"],"name":[20],"type":["int"],"align":["right"]},{"label":["V21"],"name":[21],"type":["int"],"align":["right"]},{"label":["V22"],"name":[22],"type":["int"],"align":["right"]},{"label":["V23"],"name":[23],"type":["int"],"align":["right"]},{"label":["V24"],"name":[24],"type":["int"],"align":["right"]},{"label":["V25"],"name":[25],"type":["int"],"align":["right"]},{"label":["V26"],"name":[26],"type":["int"],"align":["right"]},{"label":["V27"],"name":[27],"type":["int"],"align":["right"]},{"label":["V28"],"name":[28],"type":["int"],"align":["right"]},{"label":["V29"],"name":[29],"type":["chr"],"align":["left"]},{"label":["V30"],"name":[30],"type":["chr"],"align":["left"]},{"label":["V31"],"name":[31],"type":["int"],"align":["right"]},{"label":["V32"],"name":[32],"type":["int"],"align":["right"]},{"label":["V33"],"name":[33],"type":["int"],"align":["right"]},{"label":["V34"],"name":[34],"type":["chr"],"align":["left"]},{"label":["V35"],"name":[35],"type":["int"],"align":["right"]},{"label":["V36"],"name":[36],"type":["chr"],"align":["left"]},{"label":["V37"],"name":[37],"type":["chr"],"align":["left"]},{"label":["V38"],"name":[38],"type":["int"],"align":["right"]},{"label":["V39"],"name":[39],"type":["chr"],"align":["left"]},{"label":["V40"],"name":[40],"type":["chr"],"align":["left"]},{"label":["V41"],"name":[41],"type":["chr"],"align":["left"]},{"label":["V42"],"name":[42],"type":["int"],"align":["right"]},{"label":["V43"],"name":[43],"type":["int"],"align":["right"]},{"label":["V44"],"name":[44],"type":["int"],"align":["right"]},{"label":["V45"],"name":[45],"type":["chr"],"align":["left"]},{"label":["V46"],"name":[46],"type":["chr"],"align":["left"]},{"label":["V47"],"name":[47],"type":["chr"],"align":["left"]},{"label":["V48"],"name":[48],"type":["chr"],"align":["left"]},{"label":["V49"],"name":[49],"type":["chr"],"align":["left"]},{"label":["V50"],"name":[50],"type":["chr"],"align":["left"]},{"label":["V51"],"name":[51],"type":["chr"],"align":["left"]},{"label":["V52"],"name":[52],"type":["chr"],"align":["left"]}],"data":[{"1":"2","2":"0","3":"0","4":"0","5":"0","6":"7","7":"5","8":"29","9":"9.94","10":"1","11":"10.25","12":"1","13":"158413","14":"1","15":"0","16":"0","17":"1","18":"0","19":"0","20":"0","21":"0","22":"0","23":"0","24":"0","25":"0","26":"0","27":"1","28":"1","29":"6.30627529","30":"6.07484616","31":"9","32":"1","33":"1","34":"1","35":"0","36":"0","37":"0","38":"1","39":"548","40":"500","41":"755","42":"0","43":"0","44":"0","45":"0","46":"0","47":"15","48":".","49":"1","50":"1","51":"1","52":"0"},{"1":"3","2":"0","3":"0","4":"0","5":"0","6":"12","7":"11","8":"27","9":"8.00","10":"0","11":"8.00","12":"0","13":"380166","14":"1","15":"0","16":"0","17":"1","18":"0","19":"0","20":"0","21":"0","22":"0","23":"0","24":"0","25":"0","26":"0","27":"1","28":"0","29":"6.17586727","30":".","31":"8","32":"0","33":"1","34":"1","35":"0","36":"0","37":"0","38":"1","39":"481","40":".","41":"769","42":"0","43":"0","44":"0","45":"0","46":"0","47":"35","48":"93","49":"1","50":"4","51":"4","52":"1"},{"1":"4","2":"0","3":"0","4":"0","5":"0","6":"12","7":"12","8":"34","9":"14.00","10":"0","11":"12.00","12":"0","13":"367470","14":"1","15":"0","16":"0","17":"1","18":"0","19":"0","20":"0","21":"0","22":"0","23":"0","24":"0","25":"0","26":"0","27":"1","28":"0","29":"6.58063914","30":".","31":"2","32":"0","33":"1","34":".","35":"0","36":".","37":".","38":"1","39":"721","40":".","41":".","42":"1","43":"1","44":"0","45":".","46":".","47":"42","48":"103","49":"1","50":".","51":".","52":"1"},{"1":"5","2":"1","3":"1","4":"1","5":"0","6":"11","7":"11","8":"27","9":"11.00","10":"0","11":"12.00","12":"0","13":"380166","14":"1","15":"0","16":"0","17":"0","18":"1","19":"0","20":"0","21":"0","22":"0","23":"0","24":"0","25":"0","26":"0","27":"1","28":"0","29":"5.52146092","30":".","31":"6","32":"0","33":"1","34":".","35":"0","36":".","37":"0","38":"1","39":"250","40":".","41":".","42":"1","43":"0","44":"0","45":".","46":"0","47":"25","48":"88","49":"1","50":".","51":"5","52":"1"},{"1":"6","2":"1","3":"1","4":"1","5":"0","6":"12","7":"12","8":"34","9":"8.00","10":"0","11":"7.00","12":"0","13":"367470","14":"1","15":"0","16":"0","17":"0","18":"1","19":"0","20":"0","21":"0","22":"0","23":"0","24":"0","25":"0","26":"0","27":"1","28":"1","29":"6.59167373","30":"6.54484979","31":"8","32":"0","33":"1","34":"1","35":"0","36":"0","37":".","38":"1","39":"729","40":"800","41":".","42":"0","43":"1","44":"0","45":"0","46":".","47":"34","48":"108","49":"1","50":"1","51":".","52":"0"},{"1":"7","2":"1","3":"1","4":"1","5":"0","6":"12","7":"11","8":"26","9":"9.00","10":"0","11":"12.00","12":"0","13":"380166","14":"1","15":"0","16":"0","17":"0","18":"1","19":"0","20":"0","21":"0","22":"0","23":"0","24":"0","25":"0","26":"0","27":"1","28":"1","29":"6.21460810","30":"6.19351769","31":"6","32":"0","33":"1","34":"1","35":"0","36":"0","37":"0","38":"1","39":"500","40":"563","41":"630","42":"0","43":"0","44":"0","45":"0","46":"0","47":"38","48":"85","49":"1","50":"4","51":"4","52":"1"}],"options":{"columns":{"min":{},"max":[10]},"rows":{"min":[10],"max":[10]},"pages":{}}}
  </script>
</div>
### Changing col names & type

Using variable names from `code_bk.txt'


```r
colnames(data) <-(c("id","nearc","nearc4","nearc4a","nearc4b","ed76","ed66  ","age76","daded ","nodaded","momed","nomomed","weight","momdad14 ","sinmom14","step14","reg661","reg662","reg663","reg66","reg665","reg666","reg667","reg668","reg669","south66","work76","work78","lwage7","lwage78","famed","black","smsa76r","smsa78r","reg76r","reg78r","reg80r","smsa66r","wage76","wage78","wage80","noint78","noint80","enroll76","enroll78","enroll80","kww","iq","marsta76","marsta78","marsta80","libcrd14"))

data %<>% mutate_if(is_character,suppressWarnings(as.numeric))
head(data)
```

<div data-pagedtable="false">
  <script data-pagedtable-source type="application/json">
{"columns":[{"label":["id"],"name":[1],"type":["int"],"align":["right"]},{"label":["nearc"],"name":[2],"type":["int"],"align":["right"]},{"label":["nearc4"],"name":[3],"type":["int"],"align":["right"]},{"label":["nearc4a"],"name":[4],"type":["int"],"align":["right"]},{"label":["nearc4b"],"name":[5],"type":["int"],"align":["right"]},{"label":["ed76"],"name":[6],"type":["int"],"align":["right"]},{"label":["ed66  "],"name":[7],"type":["int"],"align":["right"]},{"label":["age76"],"name":[8],"type":["int"],"align":["right"]},{"label":["daded "],"name":[9],"type":["dbl"],"align":["right"]},{"label":["nodaded"],"name":[10],"type":["int"],"align":["right"]},{"label":["momed"],"name":[11],"type":["dbl"],"align":["right"]},{"label":["nomomed"],"name":[12],"type":["int"],"align":["right"]},{"label":["weight"],"name":[13],"type":["int"],"align":["right"]},{"label":["momdad14 "],"name":[14],"type":["int"],"align":["right"]},{"label":["sinmom14"],"name":[15],"type":["int"],"align":["right"]},{"label":["step14"],"name":[16],"type":["int"],"align":["right"]},{"label":["reg661"],"name":[17],"type":["int"],"align":["right"]},{"label":["reg662"],"name":[18],"type":["int"],"align":["right"]},{"label":["reg663"],"name":[19],"type":["int"],"align":["right"]},{"label":["reg66"],"name":[20],"type":["int"],"align":["right"]},{"label":["reg665"],"name":[21],"type":["int"],"align":["right"]},{"label":["reg666"],"name":[22],"type":["int"],"align":["right"]},{"label":["reg667"],"name":[23],"type":["int"],"align":["right"]},{"label":["reg668"],"name":[24],"type":["int"],"align":["right"]},{"label":["reg669"],"name":[25],"type":["int"],"align":["right"]},{"label":["south66"],"name":[26],"type":["int"],"align":["right"]},{"label":["work76"],"name":[27],"type":["int"],"align":["right"]},{"label":["work78"],"name":[28],"type":["int"],"align":["right"]},{"label":["lwage7"],"name":[29],"type":["dbl"],"align":["right"]},{"label":["lwage78"],"name":[30],"type":["dbl"],"align":["right"]},{"label":["famed"],"name":[31],"type":["int"],"align":["right"]},{"label":["black"],"name":[32],"type":["int"],"align":["right"]},{"label":["smsa76r"],"name":[33],"type":["int"],"align":["right"]},{"label":["smsa78r"],"name":[34],"type":["dbl"],"align":["right"]},{"label":["reg76r"],"name":[35],"type":["int"],"align":["right"]},{"label":["reg78r"],"name":[36],"type":["dbl"],"align":["right"]},{"label":["reg80r"],"name":[37],"type":["dbl"],"align":["right"]},{"label":["smsa66r"],"name":[38],"type":["int"],"align":["right"]},{"label":["wage76"],"name":[39],"type":["dbl"],"align":["right"]},{"label":["wage78"],"name":[40],"type":["dbl"],"align":["right"]},{"label":["wage80"],"name":[41],"type":["dbl"],"align":["right"]},{"label":["noint78"],"name":[42],"type":["int"],"align":["right"]},{"label":["noint80"],"name":[43],"type":["int"],"align":["right"]},{"label":["enroll76"],"name":[44],"type":["int"],"align":["right"]},{"label":["enroll78"],"name":[45],"type":["dbl"],"align":["right"]},{"label":["enroll80"],"name":[46],"type":["dbl"],"align":["right"]},{"label":["kww"],"name":[47],"type":["dbl"],"align":["right"]},{"label":["iq"],"name":[48],"type":["dbl"],"align":["right"]},{"label":["marsta76"],"name":[49],"type":["dbl"],"align":["right"]},{"label":["marsta78"],"name":[50],"type":["dbl"],"align":["right"]},{"label":["marsta80"],"name":[51],"type":["dbl"],"align":["right"]},{"label":["libcrd14"],"name":[52],"type":["dbl"],"align":["right"]}],"data":[{"1":"2","2":"0","3":"0","4":"0","5":"0","6":"7","7":"5","8":"29","9":"9.94","10":"1","11":"10.25","12":"1","13":"158413","14":"1","15":"0","16":"0","17":"1","18":"0","19":"0","20":"0","21":"0","22":"0","23":"0","24":"0","25":"0","26":"0","27":"1","28":"1","29":"6.306275","30":"6.074846","31":"9","32":"1","33":"1","34":"1","35":"0","36":"0","37":"0","38":"1","39":"548","40":"500","41":"755","42":"0","43":"0","44":"0","45":"0","46":"0","47":"15","48":"NA","49":"1","50":"1","51":"1","52":"0"},{"1":"3","2":"0","3":"0","4":"0","5":"0","6":"12","7":"11","8":"27","9":"8.00","10":"0","11":"8.00","12":"0","13":"380166","14":"1","15":"0","16":"0","17":"1","18":"0","19":"0","20":"0","21":"0","22":"0","23":"0","24":"0","25":"0","26":"0","27":"1","28":"0","29":"6.175867","30":"NA","31":"8","32":"0","33":"1","34":"1","35":"0","36":"0","37":"0","38":"1","39":"481","40":"NA","41":"769","42":"0","43":"0","44":"0","45":"0","46":"0","47":"35","48":"93","49":"1","50":"4","51":"4","52":"1"},{"1":"4","2":"0","3":"0","4":"0","5":"0","6":"12","7":"12","8":"34","9":"14.00","10":"0","11":"12.00","12":"0","13":"367470","14":"1","15":"0","16":"0","17":"1","18":"0","19":"0","20":"0","21":"0","22":"0","23":"0","24":"0","25":"0","26":"0","27":"1","28":"0","29":"6.580639","30":"NA","31":"2","32":"0","33":"1","34":"NA","35":"0","36":"NA","37":"NA","38":"1","39":"721","40":"NA","41":"NA","42":"1","43":"1","44":"0","45":"NA","46":"NA","47":"42","48":"103","49":"1","50":"NA","51":"NA","52":"1"},{"1":"5","2":"1","3":"1","4":"1","5":"0","6":"11","7":"11","8":"27","9":"11.00","10":"0","11":"12.00","12":"0","13":"380166","14":"1","15":"0","16":"0","17":"0","18":"1","19":"0","20":"0","21":"0","22":"0","23":"0","24":"0","25":"0","26":"0","27":"1","28":"0","29":"5.521461","30":"NA","31":"6","32":"0","33":"1","34":"NA","35":"0","36":"NA","37":"0","38":"1","39":"250","40":"NA","41":"NA","42":"1","43":"0","44":"0","45":"NA","46":"0","47":"25","48":"88","49":"1","50":"NA","51":"5","52":"1"},{"1":"6","2":"1","3":"1","4":"1","5":"0","6":"12","7":"12","8":"34","9":"8.00","10":"0","11":"7.00","12":"0","13":"367470","14":"1","15":"0","16":"0","17":"0","18":"1","19":"0","20":"0","21":"0","22":"0","23":"0","24":"0","25":"0","26":"0","27":"1","28":"1","29":"6.591674","30":"6.544850","31":"8","32":"0","33":"1","34":"1","35":"0","36":"0","37":"NA","38":"1","39":"729","40":"800","41":"NA","42":"0","43":"1","44":"0","45":"0","46":"NA","47":"34","48":"108","49":"1","50":"1","51":"NA","52":"0"},{"1":"7","2":"1","3":"1","4":"1","5":"0","6":"12","7":"11","8":"26","9":"9.00","10":"0","11":"12.00","12":"0","13":"380166","14":"1","15":"0","16":"0","17":"0","18":"1","19":"0","20":"0","21":"0","22":"0","23":"0","24":"0","25":"0","26":"0","27":"1","28":"1","29":"6.214608","30":"6.193518","31":"6","32":"0","33":"1","34":"1","35":"0","36":"0","37":"0","38":"1","39":"500","40":"563","41":"630","42":"0","43":"0","44":"0","45":"0","46":"0","47":"38","48":"85","49":"1","50":"4","51":"4","52":"1"}],"options":{"columns":{"min":{},"max":[10]},"rows":{"min":[10],"max":[10]},"pages":{}}}
  </script>
</div>



```r
data %>% ggplot(aes(ed76,lwage78,color = iq)) + geom_point() +geom_smooth(method = lm)+facet_grid(cols = vars(as_factor(nearc)))
```

![](ps1_iv_card_schholing_files/figure-html/unnamed-chunk-5-1.png)<!-- -->

```r
data %>% filter(!is.na(iq)) %>% ggplot() +geom_bar(aes(x = ed76, fill=as_factor(cut_width(iq,30))),position = position_stack(reverse = TRUE)) 
```

![](ps1_iv_card_schholing_files/figure-html/unnamed-chunk-6-1.png)<!-- -->

```r
data %>% filter(!is.na(iq)) %>% ggplot() +geom_bar(aes(x = ed76, fill=as_factor(cut_width(iq,30))),position = position_stack(reverse = TRUE)) +facet_grid(cols = vars(as_factor(nearc))) 
```

![](ps1_iv_card_schholing_files/figure-html/unnamed-chunk-7-1.png)<!-- -->

data
