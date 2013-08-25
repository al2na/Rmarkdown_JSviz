Controlling knitr output
========================================================
You can control what is output from code chunks by changing knitr options.
options are described [here](http://yihui.name/knitr/options) in detail.

Below some of the options I most use are shown.


Code evaluation
-------------------------
`eval=FALSE` will turn the code evaluation off. The code still will be shown.
  
with `eval=TRUE`

```r
summary(cars)
```

```
##      speed           dist    
##  Min.   : 4.0   Min.   :  2  
##  1st Qu.:12.0   1st Qu.: 26  
##  Median :15.0   Median : 36  
##  Mean   :15.4   Mean   : 43  
##  3rd Qu.:19.0   3rd Qu.: 56  
##  Max.   :25.0   Max.   :120
```

with `eval=FALSE`

```r
summary(cars)
```



Supressing warnings
-------------------------
You can supress warnings in the code output by setting `warning=FALSE`

`warning=TRUE`

```r
cor(c(1, 1, 1), c(1, 1, 1))
```

```
## Warning: the standard deviation is zero
```

```
## [1] NA
```


`warning=FALSE`

```r
cor(c(1, 1, 1), c(1, 1, 1))
```

```
## [1] NA
```


Supressing messages
-------------------------
You can suppress messages from the code by setting `message=FALSE`

`message=TRUE`

```r
library(GenomicRanges)
```

```
## Loading required package: BiocGenerics Loading required package: parallel
## 
## Attaching package: 'BiocGenerics'
## 
## The following objects are masked from 'package:parallel':
## 
## clusterApply, clusterApplyLB, clusterCall, clusterEvalQ, clusterExport,
## clusterMap, parApply, parCapply, parLapply, parLapplyLB, parRapply,
## parSapply, parSapplyLB
## 
## The following object is masked from 'package:stats':
## 
## xtabs
## 
## The following objects are masked from 'package:base':
## 
## anyDuplicated, as.data.frame, cbind, colnames, duplicated, eval, Filter,
## Find, get, intersect, lapply, Map, mapply, match, mget, order, paste,
## pmax, pmax.int, pmin, pmin.int, Position, rank, rbind, Reduce, rep.int,
## rownames, sapply, setdiff, sort, table, tapply, union, unique, unlist
## 
## Loading required package: IRanges
```


`message=FALSE` for the R chunk.

```r
library(GenomicRanges)
```



Evaluate code but hide figures
-------------------------

  

```r
plot(cars)
```

![plot of chunk unnamed-chunk-7](figure/unnamed-chunk-7.png) 


You can also execute code but hide the figures with `fig.show='hide'` option for the R chunk.


```r
plot(cars)
```

```r
summary(cars)
```

```
##      speed           dist    
##  Min.   : 4.0   Min.   :  2  
##  1st Qu.:12.0   1st Qu.: 26  
##  Median :15.0   Median : 36  
##  Mean   :15.4   Mean   : 43  
##  3rd Qu.:19.0   3rd Qu.: 56  
##  Max.   :25.0   Max.   :120
```


