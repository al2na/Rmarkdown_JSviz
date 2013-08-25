# Markdown example with knitr and rCharts
===========================================
This is an example file showing how to use rCharts with knitr/markdown. **rCharts** an R package to create, customize and publish interactive javascript visualizations from R.

Let's first install it, it lives on github, not on CRAN yet.

```r
require(devtools)
install_github("rCharts", "ramnathv", ref = "dev")
```



## Scatter plot using Polycharts


```r
require(rCharts)
```

```
## Loading required package: rCharts
```

```r

names(iris) = gsub("\\.", "", names(iris))
rPlot(SepalLength ~ SepalWidth | Species, data = iris, color = "Species", type = "point")
```

<iframe src=figure/unnamed-chunk-2.html seamless></iframe>


## Multi barchart using NVD3

```r
add_lib_assets("NVD3", cdn = TRUE)
```

[1] "<link rel='stylesheet' href=http://nvd3.org/src/nv.d3.css>\n<script type='text/javascript' src=http://ajax.googleapis.com/ajax/libs/jquery/1.8.3/jquery.min.js></script>\n<script type='text/javascript' src=http://d3js.org/d3.v2.min.js></script>\n<script type='text/javascript' src=http://nvd3.org/nv.d3.js></script>\n<script type='text/javascript' src=http://nvd3.org/lib/fisheye.js></script>"

```r
hair_eye_male <- subset(as.data.frame(HairEyeColor), Sex == "Male")
n1 <- nPlot(Freq ~ Hair, group = "Eye", data = hair_eye_male, type = "multiBarChart")
n1$print("nvd3mbar")
```


<div id = 'nvd3mbar' class = 'rChart nvd3'></div>
<script type='text/javascript'>
 $(document).ready(function(){
      drawnvd3mbar()
    });
    function drawnvd3mbar(){  
      var opts = {
 "dom": "nvd3mbar",
"width":    800,
"height":    400,
"x": "Hair",
"y": "Freq",
"group": "Eye",
"type": "multiBarChart",
"id": "nvd3mbar" 
},
        data = [
 {
 "Hair": "Black",
"Eye": "Brown",
"Sex": "Male",
"Freq":     32 
},
{
 "Hair": "Brown",
"Eye": "Brown",
"Sex": "Male",
"Freq":     53 
},
{
 "Hair": "Red",
"Eye": "Brown",
"Sex": "Male",
"Freq":     10 
},
{
 "Hair": "Blond",
"Eye": "Brown",
"Sex": "Male",
"Freq":      3 
},
{
 "Hair": "Black",
"Eye": "Blue",
"Sex": "Male",
"Freq":     11 
},
{
 "Hair": "Brown",
"Eye": "Blue",
"Sex": "Male",
"Freq":     50 
},
{
 "Hair": "Red",
"Eye": "Blue",
"Sex": "Male",
"Freq":     10 
},
{
 "Hair": "Blond",
"Eye": "Blue",
"Sex": "Male",
"Freq":     30 
},
{
 "Hair": "Black",
"Eye": "Hazel",
"Sex": "Male",
"Freq":     10 
},
{
 "Hair": "Brown",
"Eye": "Hazel",
"Sex": "Male",
"Freq":     25 
},
{
 "Hair": "Red",
"Eye": "Hazel",
"Sex": "Male",
"Freq":      7 
},
{
 "Hair": "Blond",
"Eye": "Hazel",
"Sex": "Male",
"Freq":      5 
},
{
 "Hair": "Black",
"Eye": "Green",
"Sex": "Male",
"Freq":      3 
},
{
 "Hair": "Brown",
"Eye": "Green",
"Sex": "Male",
"Freq":     15 
},
{
 "Hair": "Red",
"Eye": "Green",
"Sex": "Male",
"Freq":      7 
},
{
 "Hair": "Blond",
"Eye": "Green",
"Sex": "Male",
"Freq":      8 
} 
]
  
      var data = d3.nest()
        .key(function(d){
          return opts.group === undefined ? 'main' : d[opts.group]
        })
        .entries(data)
      
      nv.addGraph(function() {
        var chart = nv.models[opts.type]()
          .x(function(d) { return d[opts.x] })
          .y(function(d) { return d[opts.y] })
          .width(opts.width)
          .height(opts.height)
         
        
          
        

        
        
        
      
       d3.select("#" + opts.id)
        .append('svg')
        .datum(data)
        .transition().duration(500)
        .call(chart);

       nv.utils.windowResize(chart.update);
       return chart;
      });
    };
</script>



## Scatter Plot from NVD3
Scatter plot example with rCharts using NVD3 JS library

```r
data(iris)
sepal <- iris[, c(1:2, 5)]

n2 <- nPlot(Sepal.Length ~ Sepal.Width, data = sepal, type = "scatterChart", 
    group = "Species")
n2$xAxis(axisLabel = "Sepal.Width")
n2$yAxis(axisLabel = "Sepal.Length")
n2$print("nvd3Scatter")
```


<div id = 'nvd3Scatter' class = 'rChart nvd3'></div>
<script type='text/javascript'>
 $(document).ready(function(){
      drawnvd3Scatter()
    });
    function drawnvd3Scatter(){  
      var opts = {
 "dom": "nvd3Scatter",
"width":    800,
"height":    400,
"x": "Sepal.Width",
"y": "Sepal.Length",
"type": "scatterChart",
"group": "Species",
"id": "nvd3Scatter" 
},
        data = [
 {
 "Sepal.Length":    5.1,
"Sepal.Width":    3.5,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.9,
"Sepal.Width":      3,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.7,
"Sepal.Width":    3.2,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.6,
"Sepal.Width":    3.1,
"Species": "setosa" 
},
{
 "Sepal.Length":      5,
"Sepal.Width":    3.6,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.4,
"Sepal.Width":    3.9,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.6,
"Sepal.Width":    3.4,
"Species": "setosa" 
},
{
 "Sepal.Length":      5,
"Sepal.Width":    3.4,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.4,
"Sepal.Width":    2.9,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.9,
"Sepal.Width":    3.1,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.4,
"Sepal.Width":    3.7,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.8,
"Sepal.Width":    3.4,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.8,
"Sepal.Width":      3,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.3,
"Sepal.Width":      3,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.8,
"Sepal.Width":      4,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.7,
"Sepal.Width":    4.4,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.4,
"Sepal.Width":    3.9,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.1,
"Sepal.Width":    3.5,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.7,
"Sepal.Width":    3.8,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.1,
"Sepal.Width":    3.8,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.4,
"Sepal.Width":    3.4,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.1,
"Sepal.Width":    3.7,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.6,
"Sepal.Width":    3.6,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.1,
"Sepal.Width":    3.3,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.8,
"Sepal.Width":    3.4,
"Species": "setosa" 
},
{
 "Sepal.Length":      5,
"Sepal.Width":      3,
"Species": "setosa" 
},
{
 "Sepal.Length":      5,
"Sepal.Width":    3.4,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.2,
"Sepal.Width":    3.5,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.2,
"Sepal.Width":    3.4,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.7,
"Sepal.Width":    3.2,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.8,
"Sepal.Width":    3.1,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.4,
"Sepal.Width":    3.4,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.2,
"Sepal.Width":    4.1,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.5,
"Sepal.Width":    4.2,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.9,
"Sepal.Width":    3.1,
"Species": "setosa" 
},
{
 "Sepal.Length":      5,
"Sepal.Width":    3.2,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.5,
"Sepal.Width":    3.5,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.9,
"Sepal.Width":    3.6,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.4,
"Sepal.Width":      3,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.1,
"Sepal.Width":    3.4,
"Species": "setosa" 
},
{
 "Sepal.Length":      5,
"Sepal.Width":    3.5,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.5,
"Sepal.Width":    2.3,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.4,
"Sepal.Width":    3.2,
"Species": "setosa" 
},
{
 "Sepal.Length":      5,
"Sepal.Width":    3.5,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.1,
"Sepal.Width":    3.8,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.8,
"Sepal.Width":      3,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.1,
"Sepal.Width":    3.8,
"Species": "setosa" 
},
{
 "Sepal.Length":    4.6,
"Sepal.Width":    3.2,
"Species": "setosa" 
},
{
 "Sepal.Length":    5.3,
"Sepal.Width":    3.7,
"Species": "setosa" 
},
{
 "Sepal.Length":      5,
"Sepal.Width":    3.3,
"Species": "setosa" 
},
{
 "Sepal.Length":      7,
"Sepal.Width":    3.2,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.4,
"Sepal.Width":    3.2,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.9,
"Sepal.Width":    3.1,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.5,
"Sepal.Width":    2.3,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.5,
"Sepal.Width":    2.8,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.7,
"Sepal.Width":    2.8,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.3,
"Sepal.Width":    3.3,
"Species": "versicolor" 
},
{
 "Sepal.Length":    4.9,
"Sepal.Width":    2.4,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.6,
"Sepal.Width":    2.9,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.2,
"Sepal.Width":    2.7,
"Species": "versicolor" 
},
{
 "Sepal.Length":      5,
"Sepal.Width":      2,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.9,
"Sepal.Width":      3,
"Species": "versicolor" 
},
{
 "Sepal.Length":      6,
"Sepal.Width":    2.2,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.1,
"Sepal.Width":    2.9,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.6,
"Sepal.Width":    2.9,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.7,
"Sepal.Width":    3.1,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.6,
"Sepal.Width":      3,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.8,
"Sepal.Width":    2.7,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.2,
"Sepal.Width":    2.2,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.6,
"Sepal.Width":    2.5,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.9,
"Sepal.Width":    3.2,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.1,
"Sepal.Width":    2.8,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.3,
"Sepal.Width":    2.5,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.1,
"Sepal.Width":    2.8,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.4,
"Sepal.Width":    2.9,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.6,
"Sepal.Width":      3,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.8,
"Sepal.Width":    2.8,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.7,
"Sepal.Width":      3,
"Species": "versicolor" 
},
{
 "Sepal.Length":      6,
"Sepal.Width":    2.9,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.7,
"Sepal.Width":    2.6,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.5,
"Sepal.Width":    2.4,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.5,
"Sepal.Width":    2.4,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.8,
"Sepal.Width":    2.7,
"Species": "versicolor" 
},
{
 "Sepal.Length":      6,
"Sepal.Width":    2.7,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.4,
"Sepal.Width":      3,
"Species": "versicolor" 
},
{
 "Sepal.Length":      6,
"Sepal.Width":    3.4,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.7,
"Sepal.Width":    3.1,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.3,
"Sepal.Width":    2.3,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.6,
"Sepal.Width":      3,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.5,
"Sepal.Width":    2.5,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.5,
"Sepal.Width":    2.6,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.1,
"Sepal.Width":      3,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.8,
"Sepal.Width":    2.6,
"Species": "versicolor" 
},
{
 "Sepal.Length":      5,
"Sepal.Width":    2.3,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.6,
"Sepal.Width":    2.7,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.7,
"Sepal.Width":      3,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.7,
"Sepal.Width":    2.9,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.2,
"Sepal.Width":    2.9,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.1,
"Sepal.Width":    2.5,
"Species": "versicolor" 
},
{
 "Sepal.Length":    5.7,
"Sepal.Width":    2.8,
"Species": "versicolor" 
},
{
 "Sepal.Length":    6.3,
"Sepal.Width":    3.3,
"Species": "virginica" 
},
{
 "Sepal.Length":    5.8,
"Sepal.Width":    2.7,
"Species": "virginica" 
},
{
 "Sepal.Length":    7.1,
"Sepal.Width":      3,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.3,
"Sepal.Width":    2.9,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.5,
"Sepal.Width":      3,
"Species": "virginica" 
},
{
 "Sepal.Length":    7.6,
"Sepal.Width":      3,
"Species": "virginica" 
},
{
 "Sepal.Length":    4.9,
"Sepal.Width":    2.5,
"Species": "virginica" 
},
{
 "Sepal.Length":    7.3,
"Sepal.Width":    2.9,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.7,
"Sepal.Width":    2.5,
"Species": "virginica" 
},
{
 "Sepal.Length":    7.2,
"Sepal.Width":    3.6,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.5,
"Sepal.Width":    3.2,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.4,
"Sepal.Width":    2.7,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.8,
"Sepal.Width":      3,
"Species": "virginica" 
},
{
 "Sepal.Length":    5.7,
"Sepal.Width":    2.5,
"Species": "virginica" 
},
{
 "Sepal.Length":    5.8,
"Sepal.Width":    2.8,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.4,
"Sepal.Width":    3.2,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.5,
"Sepal.Width":      3,
"Species": "virginica" 
},
{
 "Sepal.Length":    7.7,
"Sepal.Width":    3.8,
"Species": "virginica" 
},
{
 "Sepal.Length":    7.7,
"Sepal.Width":    2.6,
"Species": "virginica" 
},
{
 "Sepal.Length":      6,
"Sepal.Width":    2.2,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.9,
"Sepal.Width":    3.2,
"Species": "virginica" 
},
{
 "Sepal.Length":    5.6,
"Sepal.Width":    2.8,
"Species": "virginica" 
},
{
 "Sepal.Length":    7.7,
"Sepal.Width":    2.8,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.3,
"Sepal.Width":    2.7,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.7,
"Sepal.Width":    3.3,
"Species": "virginica" 
},
{
 "Sepal.Length":    7.2,
"Sepal.Width":    3.2,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.2,
"Sepal.Width":    2.8,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.1,
"Sepal.Width":      3,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.4,
"Sepal.Width":    2.8,
"Species": "virginica" 
},
{
 "Sepal.Length":    7.2,
"Sepal.Width":      3,
"Species": "virginica" 
},
{
 "Sepal.Length":    7.4,
"Sepal.Width":    2.8,
"Species": "virginica" 
},
{
 "Sepal.Length":    7.9,
"Sepal.Width":    3.8,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.4,
"Sepal.Width":    2.8,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.3,
"Sepal.Width":    2.8,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.1,
"Sepal.Width":    2.6,
"Species": "virginica" 
},
{
 "Sepal.Length":    7.7,
"Sepal.Width":      3,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.3,
"Sepal.Width":    3.4,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.4,
"Sepal.Width":    3.1,
"Species": "virginica" 
},
{
 "Sepal.Length":      6,
"Sepal.Width":      3,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.9,
"Sepal.Width":    3.1,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.7,
"Sepal.Width":    3.1,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.9,
"Sepal.Width":    3.1,
"Species": "virginica" 
},
{
 "Sepal.Length":    5.8,
"Sepal.Width":    2.7,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.8,
"Sepal.Width":    3.2,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.7,
"Sepal.Width":    3.3,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.7,
"Sepal.Width":      3,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.3,
"Sepal.Width":    2.5,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.5,
"Sepal.Width":      3,
"Species": "virginica" 
},
{
 "Sepal.Length":    6.2,
"Sepal.Width":    3.4,
"Species": "virginica" 
},
{
 "Sepal.Length":    5.9,
"Sepal.Width":      3,
"Species": "virginica" 
} 
]
  
      var data = d3.nest()
        .key(function(d){
          return opts.group === undefined ? 'main' : d[opts.group]
        })
        .entries(data)
      
      nv.addGraph(function() {
        var chart = nv.models[opts.type]()
          .x(function(d) { return d[opts.x] })
          .y(function(d) { return d[opts.y] })
          .width(opts.width)
          .height(opts.height)
         
        
          
        chart.xAxis
  .axisLabel("Sepal.Width")

        
        
        chart.yAxis
  .axisLabel("Sepal.Length")
      
       d3.select("#" + opts.id)
        .append('svg')
        .datum(data)
        .transition().duration(500)
        .call(chart);

       nv.utils.windowResize(chart.update);
       return chart;
      });
    };
</script>


## Histogram Plot from NVD3
Let's try to plot a multihistogram with rCharts using NVD3 library. We need to first calculate break points and mid points for the histogram bars and produce a single data frame that has the counts, mid-points for bars and group information.

```r
data(iris)
sepalw <- iris[, c(1, 5)]
hst = hist(sepalw[, 1], plot = FALSE, breaks = 20)

data = by(sepalw, sepalw$Species, function(x) data.frame(mid = hst$mids, counts = hist(x[, 
    1], breaks = hst$breaks, plot = FALSE)$counts, Species = rep(x[1, 2], length(hst$breaks) - 
    1)))
data = do.call("rbind", data)
head(data)
```

```
##          mid counts Species
## setosa.1 4.3      4  setosa
## setosa.2 4.5      5  setosa
## setosa.3 4.7      7  setosa
## setosa.4 4.9     12  setosa
## setosa.5 5.1     11  setosa
## setosa.6 5.3      6  setosa
```

We got the data in the right format, now let's plot the histogram with **multiBarChart**

```r
n2 <- nPlot(counts ~ mid, data = data, type = "multiBarChart", group = "Species")
n2$xAxis(axisLabel = "Sepal.Width")
n2$yAxis(axisLabel = "counts")
n2$print("nvd3Hist")
```


<div id = 'nvd3Hist' class = 'rChart nvd3'></div>
<script type='text/javascript'>
 $(document).ready(function(){
      drawnvd3Hist()
    });
    function drawnvd3Hist(){  
      var opts = {
 "dom": "nvd3Hist",
"width":    800,
"height":    400,
"x": "mid",
"y": "counts",
"type": "multiBarChart",
"group": "Species",
"id": "nvd3Hist" 
},
        data = [
 {
 "mid":    4.3,
"counts": 4,
"Species": "setosa" 
},
{
 "mid":    4.5,
"counts": 5,
"Species": "setosa" 
},
{
 "mid":    4.7,
"counts": 7,
"Species": "setosa" 
},
{
 "mid":    4.9,
"counts": 12,
"Species": "setosa" 
},
{
 "mid":    5.1,
"counts": 11,
"Species": "setosa" 
},
{
 "mid":    5.3,
"counts": 6,
"Species": "setosa" 
},
{
 "mid":    5.5,
"counts": 2,
"Species": "setosa" 
},
{
 "mid":    5.7,
"counts": 3,
"Species": "setosa" 
},
{
 "mid":    5.9,
"counts": 0,
"Species": "setosa" 
},
{
 "mid":    6.1,
"counts": 0,
"Species": "setosa" 
},
{
 "mid":    6.3,
"counts": 0,
"Species": "setosa" 
},
{
 "mid":    6.5,
"counts": 0,
"Species": "setosa" 
},
{
 "mid":    6.7,
"counts": 0,
"Species": "setosa" 
},
{
 "mid":    6.9,
"counts": 0,
"Species": "setosa" 
},
{
 "mid":    7.1,
"counts": 0,
"Species": "setosa" 
},
{
 "mid":    7.3,
"counts": 0,
"Species": "setosa" 
},
{
 "mid":    7.5,
"counts": 0,
"Species": "setosa" 
},
{
 "mid":    7.7,
"counts": 0,
"Species": "setosa" 
},
{
 "mid":    7.9,
"counts": 0,
"Species": "setosa" 
},
{
 "mid":    4.3,
"counts": 0,
"Species": "versicolor" 
},
{
 "mid":    4.5,
"counts": 0,
"Species": "versicolor" 
},
{
 "mid":    4.7,
"counts": 0,
"Species": "versicolor" 
},
{
 "mid":    4.9,
"counts": 3,
"Species": "versicolor" 
},
{
 "mid":    5.1,
"counts": 2,
"Species": "versicolor" 
},
{
 "mid":    5.3,
"counts": 1,
"Species": "versicolor" 
},
{
 "mid":    5.5,
"counts": 10,
"Species": "versicolor" 
},
{
 "mid":    5.7,
"counts": 8,
"Species": "versicolor" 
},
{
 "mid":    5.9,
"counts": 6,
"Species": "versicolor" 
},
{
 "mid":    6.1,
"counts": 6,
"Species": "versicolor" 
},
{
 "mid":    6.3,
"counts": 5,
"Species": "versicolor" 
},
{
 "mid":    6.5,
"counts": 3,
"Species": "versicolor" 
},
{
 "mid":    6.7,
"counts": 4,
"Species": "versicolor" 
},
{
 "mid":    6.9,
"counts": 2,
"Species": "versicolor" 
},
{
 "mid":    7.1,
"counts": 0,
"Species": "versicolor" 
},
{
 "mid":    7.3,
"counts": 0,
"Species": "versicolor" 
},
{
 "mid":    7.5,
"counts": 0,
"Species": "versicolor" 
},
{
 "mid":    7.7,
"counts": 0,
"Species": "versicolor" 
},
{
 "mid":    7.9,
"counts": 0,
"Species": "versicolor" 
},
{
 "mid":    4.3,
"counts": 0,
"Species": "virginica" 
},
{
 "mid":    4.5,
"counts": 0,
"Species": "virginica" 
},
{
 "mid":    4.7,
"counts": 0,
"Species": "virginica" 
},
{
 "mid":    4.9,
"counts": 1,
"Species": "virginica" 
},
{
 "mid":    5.1,
"counts": 0,
"Species": "virginica" 
},
{
 "mid":    5.3,
"counts": 0,
"Species": "virginica" 
},
{
 "mid":    5.5,
"counts": 1,
"Species": "virginica" 
},
{
 "mid":    5.7,
"counts": 4,
"Species": "virginica" 
},
{
 "mid":    5.9,
"counts": 3,
"Species": "virginica" 
},
{
 "mid":    6.1,
"counts": 4,
"Species": "virginica" 
},
{
 "mid":    6.3,
"counts": 11,
"Species": "virginica" 
},
{
 "mid":    6.5,
"counts": 4,
"Species": "virginica" 
},
{
 "mid":    6.7,
"counts": 7,
"Species": "virginica" 
},
{
 "mid":    6.9,
"counts": 3,
"Species": "virginica" 
},
{
 "mid":    7.1,
"counts": 4,
"Species": "virginica" 
},
{
 "mid":    7.3,
"counts": 2,
"Species": "virginica" 
},
{
 "mid":    7.5,
"counts": 1,
"Species": "virginica" 
},
{
 "mid":    7.7,
"counts": 4,
"Species": "virginica" 
},
{
 "mid":    7.9,
"counts": 1,
"Species": "virginica" 
} 
]
  
      var data = d3.nest()
        .key(function(d){
          return opts.group === undefined ? 'main' : d[opts.group]
        })
        .entries(data)
      
      nv.addGraph(function() {
        var chart = nv.models[opts.type]()
          .x(function(d) { return d[opts.x] })
          .y(function(d) { return d[opts.y] })
          .width(opts.width)
          .height(opts.height)
         
        
          
        chart.xAxis
  .axisLabel("Sepal.Width")

        
        
        chart.yAxis
  .axisLabel("counts")
      
       d3.select("#" + opts.id)
        .append('svg')
        .datum(data)
        .transition().duration(500)
        .call(chart);

       nv.utils.windowResize(chart.update);
       return chart;
      });
    };
</script>

