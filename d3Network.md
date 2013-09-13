# Markdown example with d3Network
===========================================
Here is a demo of **d3Network** package with markdown. **d3Network** can create interactive network diagrams using the
infamous **d3.js** JavaScript library. Here are some examples of what d3.js can do for you:

https://github.com/mbostock/d3/wiki/Gallery

Now let's make a simple network with d3Network

```r
library(d3Network)
data(MisLinks)
data(MisNodes)

head(MisNodes)
```

```
##              name group
## 1          Myriel     1
## 2        Napoleon     1
## 3 Mlle.Baptistine     1
## 4    Mme.Magloire     1
## 5    CountessdeLo     1
## 6        Geborand     1
```

```r
head(MisLinks)
```

```
##   source target value
## 1      1      0     1
## 2      2      0     8
## 3      3      0    10
## 4      3      2     6
## 5      4      0     1
## 6      5      0     1
```




```r
# Create graph
d3ForceNetwork(Links = MisLinks, Nodes = MisNodes, Source = "source", Target = "target", 
    Value = "value", NodeID = "name", Group = "group", opacity = 0.7, standAlone = TRUE, 
    iframe = TRUE, zoom = TRUE, file = "ForceNetwork.html")
```

<iframe src='ForceNetwork.html' height=642 width=927></iframe>



# Session info
===========================================

```r
sessionInfo()
```

```
## R version 3.0.1 (2013-05-16)
## Platform: x86_64-apple-darwin10.8.0 (64-bit)
## 
## locale:
## [1] en_US.UTF-8/en_US.UTF-8/en_US.UTF-8/C/en_US.UTF-8/en_US.UTF-8
## 
## attached base packages:
## [1] stats     graphics  grDevices utils     datasets  methods   base     
## 
## other attached packages:
## [1] d3Network_0.3.3 knitr_1.4.1    
## 
## loaded via a namespace (and not attached):
## [1] digest_0.6.3   evaluate_0.4.7 formatR_0.9    plyr_1.8      
## [5] rjson_0.2.13   stringr_0.6.2  tools_3.0.1    whisker_0.3-2
```

