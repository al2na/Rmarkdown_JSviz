# Markdown example with knitr and googleVis
===========================================
This is a little Markdown example file. It uses googleVis package with knitr and markdown to produce interactive plots from **Google Visualization API**.

In this case change the behaviour of plot.gvis, so that it presents only 
the code for the chart rather than making a full web page.


```r
library(googleVis)
op <- options(gvis.plot.tag = "chart")
```

The following plot statements will automatically return  the HTML
required for the 'knitted' output. 
 

## Pie chart
example pie charts

Let's take a look at the data:

```r
head(CityPopularity)
```

```
##          City Popularity
## 1    New York        200
## 2      Boston        300
## 3       Miami        400
## 4     Chicago        500
## 5 Los Angeles        600
## 6     Houston        700
```

Now plot the pie chart

```r

Pie <- gvisPieChart(CityPopularity, options = list(width = 400, height = 200))
plot(Pie)
```

<!-- PieChart generated in R 3.0.1 by googleVis 0.4.5 package -->
<!-- Tue Sep  3 09:45:05 2013 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataPieChartID10f7d331cc8b1 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "New York",
200 
],
[
 "Boston",
300 
],
[
 "Miami",
400 
],
[
 "Chicago",
500 
],
[
 "Los Angeles",
600 
],
[
 "Houston",
700 
] 
];
data.addColumn('string','City');
data.addColumn('number','Popularity');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartPieChartID10f7d331cc8b1() {
var data = gvisDataPieChartID10f7d331cc8b1();
var options = {};
options["allowHtml"] = true;
options["width"] =    400;
options["height"] =    200;

    var chart = new google.visualization.PieChart(
    document.getElementById('PieChartID10f7d331cc8b1')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartPieChartID10f7d331cc8b1);
})();
function displayChartPieChartID10f7d331cc8b1() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartPieChartID10f7d331cc8b1"></script>
 
<!-- divChart -->
  
<div id="PieChartID10f7d331cc8b1"
  style="width: 400px; height: 200px;">
</div>


## Place two charts next to each other
Example of a gvisGeoChart with gvisTable
Let's have a look at the data first

```r
head(Exports)
```

```
##         Country Profit Online
## 1       Germany      3   TRUE
## 2        Brazil      4  FALSE
## 3 United States      5   TRUE
## 4        France      4   TRUE
## 5       Hungary      3  FALSE
## 6         India      2   TRUE
```



```r
Geo <- gvisGeoChart(Exports, locationvar = "Country", colorvar = "Profit", options = list(height = 300, 
    width = 350))
Tbl <- gvisTable(Exports, options = list(height = 300, width = 200))
plot(gvisMerge(Geo, Tbl, horizontal = TRUE))
```

<!-- GeoChart generated in R 3.0.1 by googleVis 0.4.5 package -->
<!-- Tue Sep  3 09:45:05 2013 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataGeoChartID10f7d26bbf6ae () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "Germany",
3 
],
[
 "Brazil",
4 
],
[
 "United States",
5 
],
[
 "France",
4 
],
[
 "Hungary",
3 
],
[
 "India",
2 
],
[
 "Iceland",
1 
],
[
 "Norway",
4 
],
[
 "Spain",
5 
],
[
 "Turkey",
1 
] 
];
data.addColumn('string','Country');
data.addColumn('number','Profit');
data.addRows(datajson);
return(data);
}


// jsData 
function gvisDataTableID10f7d7e402d5f () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "Germany",
3,
true 
],
[
 "Brazil",
4,
false 
],
[
 "United States",
5,
true 
],
[
 "France",
4,
true 
],
[
 "Hungary",
3,
false 
],
[
 "India",
2,
true 
],
[
 "Iceland",
1,
false 
],
[
 "Norway",
4,
true 
],
[
 "Spain",
5,
true 
],
[
 "Turkey",
1,
false 
] 
];
data.addColumn('string','Country');
data.addColumn('number','Profit');
data.addColumn('boolean','Online');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartGeoChartID10f7d26bbf6ae() {
var data = gvisDataGeoChartID10f7d26bbf6ae();
var options = {};
options["width"] =    350;
options["height"] =    300;

    var chart = new google.visualization.GeoChart(
    document.getElementById('GeoChartID10f7d26bbf6ae')
    );
    chart.draw(data,options);
    

}
  


// jsDrawChart
function drawChartTableID10f7d7e402d5f() {
var data = gvisDataTableID10f7d7e402d5f();
var options = {};
options["allowHtml"] = true;
options["height"] =    300;
options["width"] =    200;

    var chart = new google.visualization.Table(
    document.getElementById('TableID10f7d7e402d5f')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "geochart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartGeoChartID10f7d26bbf6ae);
})();
function displayChartGeoChartID10f7d26bbf6ae() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}


// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "table";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartTableID10f7d7e402d5f);
})();
function displayChartTableID10f7d7e402d5f() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartGeoChartID10f7d26bbf6ae"></script>


<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartTableID10f7d7e402d5f"></script>
 
<table border="0">
<tr>
<td>

<!-- divChart -->
  
<div id="GeoChartID10f7d26bbf6ae"
  style="width: 350px; height: 300px;">
</div>

</td>
<td>

<!-- divChart -->
  
<div id="TableID10f7d7e402d5f"
  style="width: 200px; height: 300px;">
</div>

</td>
</tr>
</table>


 
 
## Scatter Plot
Scatter plot example with googleVis

```r
head(women)
```

```
##   height weight
## 1     58    115
## 2     59    117
## 3     60    120
## 4     61    123
## 5     62    126
## 6     63    129
```

This time we will be able to edit the plot since we set `gvis.editor` argument.

```r

Scatter1 <- gvisScatterChart(women, options = list(gvis.editor = "edit", vAxis = "{title:'weight (lbs)'}", 
    hAxis = "{title:'height (in)'}"))
plot(Scatter1)
```

<!-- ScatterChart generated in R 3.0.1 by googleVis 0.4.5 package -->
<!-- Tue Sep  3 09:45:05 2013 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataScatterChartID10f7d52b78f89 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 58,
115 
],
[
 59,
117 
],
[
 60,
120 
],
[
 61,
123 
],
[
 62,
126 
],
[
 63,
129 
],
[
 64,
132 
],
[
 65,
135 
],
[
 66,
139 
],
[
 67,
142 
],
[
 68,
146 
],
[
 69,
150 
],
[
 70,
154 
],
[
 71,
159 
],
[
 72,
164 
] 
];
data.addColumn('number','height');
data.addColumn('number','weight');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartScatterChartID10f7d52b78f89() {
var data = gvisDataScatterChartID10f7d52b78f89();
var options = {};
options["allowHtml"] = true;
options["vAxis"] = {title:'weight (lbs)'};
options["hAxis"] = {title:'height (in)'};

    chartScatterChartID10f7d52b78f89 = new google.visualization.ChartWrapper({
    dataTable: data,       
    chartType: 'ScatterChart',
    containerId: 'ScatterChartID10f7d52b78f89',
    options: options
    });
    chartScatterChartID10f7d52b78f89.draw();
    

}

  function openEditorScatterChartID10f7d52b78f89() {
  var editor = new google.visualization.ChartEditor();
  google.visualization.events.addListener(editor, 'ok',
  function() { 
  chartScatterChartID10f7d52b78f89 = editor.getChartWrapper();  
  chartScatterChartID10f7d52b78f89.draw(document.getElementById('ScatterChartID10f7d52b78f89')); 
  }); 
  editor.openDialog(chartScatterChartID10f7d52b78f89);
  }
    
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "charteditor";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartScatterChartID10f7d52b78f89);
})();
function displayChartScatterChartID10f7d52b78f89() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartScatterChartID10f7d52b78f89"></script>
 
<!-- divChart -->
<input type='button' onclick='openEditorScatterChartID10f7d52b78f89()' value='edit'/>  
<div id="ScatterChartID10f7d52b78f89"
  style="width: 600px; height: 500px;">
</div>


## Intensity Map


```r
df = data.frame(country = c("US", "GB", "BR"), val1 = c(1, 3, 4), val2 = c(23, 
    12, 32))
head(df)
```

```
##   country val1 val2
## 1      US    1   23
## 2      GB    3   12
## 3      BR    4   32
```



```r

Intensity1 <- gvisIntensityMap(df, locationvar = "country", numvar = c("val1", 
    "val2"))
plot(Intensity1)
```

<!-- IntensityMap generated in R 3.0.1 by googleVis 0.4.5 package -->
<!-- Tue Sep  3 09:45:05 2013 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataIntensityMapID10f7d113095cc () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "US",
1,
23 
],
[
 "GB",
3,
12 
],
[
 "BR",
4,
32 
] 
];
data.addColumn('string','country');
data.addColumn('number','val1');
data.addColumn('number','val2');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartIntensityMapID10f7d113095cc() {
var data = gvisDataIntensityMapID10f7d113095cc();
var options = {};
options["width"] =    600;

    var chart = new google.visualization.IntensityMap(
    document.getElementById('IntensityMapID10f7d113095cc')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "intensitymap";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartIntensityMapID10f7d113095cc);
})();
function displayChartIntensityMapID10f7d113095cc() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartIntensityMapID10f7d113095cc"></script>
 
<!-- divChart -->
  
<div id="IntensityMapID10f7d113095cc"
  style="width: 600px; height: 500px;">
</div>



## Combo chart

```r
## Add the mean
CityPopularity$Mean=mean(CityPopularity$Popularity)
CC <- gvisComboChart(CityPopularity, xvar='City',
          yvar=c('Mean', 'Popularity'),
          options=list(seriesType='bars',
                       width=450, height=300,
                       title='City Popularity',
                       series='{0: {type:\"line\"}}'))
plot(CC)
```

<!-- ComboChart generated in R 3.0.1 by googleVis 0.4.5 package -->
<!-- Tue Sep  3 09:45:05 2013 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataComboChartID10f7dcba8ce5 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "New York",
450,
200 
],
[
 "Boston",
450,
300 
],
[
 "Miami",
450,
400 
],
[
 "Chicago",
450,
500 
],
[
 "Los Angeles",
450,
600 
],
[
 "Houston",
450,
700 
] 
];
data.addColumn('string','City');
data.addColumn('number','Mean');
data.addColumn('number','Popularity');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartComboChartID10f7dcba8ce5() {
var data = gvisDataComboChartID10f7dcba8ce5();
var options = {};
options["allowHtml"] = true;
options["seriesType"] = "bars";
options["width"] =    450;
options["height"] =    300;
options["title"] = "City Popularity";
options["series"] = {0: {type:"line"}};

    var chart = new google.visualization.ComboChart(
    document.getElementById('ComboChartID10f7dcba8ce5')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartComboChartID10f7dcba8ce5);
})();
function displayChartComboChartID10f7dcba8ce5() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartComboChartID10f7dcba8ce5"></script>
 
<!-- divChart -->
  
<div id="ComboChartID10f7dcba8ce5"
  style="width: 450px; height: 300px;">
</div>



```r
## Set options back to original options
options(op)
```


Session info
-------------------------

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
## [1] googleVis_0.4.5 knitr_1.4.1    
## 
## loaded via a namespace (and not attached):
## [1] digest_0.6.3   evaluate_0.4.7 formatR_0.9    RJSONIO_1.0-3 
## [5] stringr_0.6.2  tools_3.0.1
```

