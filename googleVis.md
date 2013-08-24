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

<!-- PieChart generated in R 3.0.0 by googleVis 0.4.3 package -->
<!-- Sat Aug 24 23:06:07 2013 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataPieChartID2a6f5f730594 () {
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
function drawChartPieChartID2a6f5f730594() {
  var data = gvisDataPieChartID2a6f5f730594();
  var options = {};
options["allowHtml"] = true;
options["width"] =    400;
options["height"] =    200;

     var chart = new google.visualization.PieChart(
       document.getElementById('PieChartID2a6f5f730594')
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
  callbacks.push(drawChartPieChartID2a6f5f730594);
})();
function displayChartPieChartID2a6f5f730594() {
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
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartPieChartID2a6f5f730594"></script>
 
<!-- divChart -->
  
<div id="PieChartID2a6f5f730594"
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


<!-- GeoChart generated in R 3.0.0 by googleVis 0.4.3 package -->
<!-- Sat Aug 24 23:06:08 2013 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataGeoChartID2a6f78736880 () {
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
function gvisDataTableID2a6f60d1e947 () {
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
function drawChartGeoChartID2a6f78736880() {
  var data = gvisDataGeoChartID2a6f78736880();
  var options = {};
options["width"] =    350;
options["height"] =    300;

     var chart = new google.visualization.GeoChart(
       document.getElementById('GeoChartID2a6f78736880')
     );
     chart.draw(data,options);
    

}
  


// jsDrawChart
function drawChartTableID2a6f60d1e947() {
  var data = gvisDataTableID2a6f60d1e947();
  var options = {};
options["allowHtml"] = true;
options["height"] =    300;
options["width"] =    200;

     var chart = new google.visualization.Table(
       document.getElementById('TableID2a6f60d1e947')
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
  callbacks.push(drawChartGeoChartID2a6f78736880);
})();
function displayChartGeoChartID2a6f78736880() {
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
  callbacks.push(drawChartTableID2a6f60d1e947);
})();
function displayChartTableID2a6f60d1e947() {
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
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartGeoChartID2a6f78736880"></script>


<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartTableID2a6f60d1e947"></script>
 
<table border="0">
<tr>
<td>

<!-- divChart -->
  
<div id="GeoChartID2a6f78736880"
  style="width: 350px; height: 300px;">
</div>

</td>
<td>

<!-- divChart -->
  
<div id="TableID2a6f60d1e947"
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

<!-- ScatterChart generated in R 3.0.0 by googleVis 0.4.3 package -->
<!-- Sat Aug 24 23:06:08 2013 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataScatterChartID2a6f328cfa87 () {
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
function drawChartScatterChartID2a6f328cfa87() {
  var data = gvisDataScatterChartID2a6f328cfa87();
  var options = {};
options["allowHtml"] = true;
options["vAxis"] = {title:'weight (lbs)'};
options["hAxis"] = {title:'height (in)'};

    chartScatterChartID2a6f328cfa87 = new google.visualization.ChartWrapper({
         dataTable: data,       
         chartType: 'ScatterChart',
         containerId: 'ScatterChartID2a6f328cfa87',
         options: options
    });
    chartScatterChartID2a6f328cfa87.draw();
    

}

  function openEditorScatterChartID2a6f328cfa87() {
      var editor = new google.visualization.ChartEditor();
      google.visualization.events.addListener(editor, 'ok',
        function() { 
          chartScatterChartID2a6f328cfa87 = editor.getChartWrapper();  
          chartScatterChartID2a6f328cfa87.draw(document.getElementById('ScatterChartID2a6f328cfa87')); 
      }); 
      editor.openDialog(chartScatterChartID2a6f328cfa87);
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
  callbacks.push(drawChartScatterChartID2a6f328cfa87);
})();
function displayChartScatterChartID2a6f328cfa87() {
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
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartScatterChartID2a6f328cfa87"></script>
 
<!-- divChart -->
<input type='button' onclick='openEditorScatterChartID2a6f328cfa87()' value='edit'/>  
<div id="ScatterChartID2a6f328cfa87"
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

<!-- IntensityMap generated in R 3.0.0 by googleVis 0.4.3 package -->
<!-- Sat Aug 24 23:06:08 2013 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataIntensityMapID2a6f4593cefe () {
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
function drawChartIntensityMapID2a6f4593cefe() {
  var data = gvisDataIntensityMapID2a6f4593cefe();
  var options = {};
options["width"] =    600;

     var chart = new google.visualization.IntensityMap(
       document.getElementById('IntensityMapID2a6f4593cefe')
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
  callbacks.push(drawChartIntensityMapID2a6f4593cefe);
})();
function displayChartIntensityMapID2a6f4593cefe() {
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
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartIntensityMapID2a6f4593cefe"></script>
 
<!-- divChart -->
  
<div id="IntensityMapID2a6f4593cefe"
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

<!-- ComboChart generated in R 3.0.0 by googleVis 0.4.3 package -->
<!-- Sat Aug 24 23:06:08 2013 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataComboChartID2a6f6afaa961 () {
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
function drawChartComboChartID2a6f6afaa961() {
  var data = gvisDataComboChartID2a6f6afaa961();
  var options = {};
options["allowHtml"] = true;
options["seriesType"] = "bars";
options["width"] =    450;
options["height"] =    300;
options["title"] = "City Popularity";
options["series"] = {0: {type:"line"}};

     var chart = new google.visualization.ComboChart(
       document.getElementById('ComboChartID2a6f6afaa961')
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
  callbacks.push(drawChartComboChartID2a6f6afaa961);
})();
function displayChartComboChartID2a6f6afaa961() {
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
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartComboChartID2a6f6afaa961"></script>
 
<!-- divChart -->
  
<div id="ComboChartID2a6f6afaa961"
  style="width: 450px; height: 300px;">
</div>



```r
## Set options back to original options
options(op)
```

