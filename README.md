R markdown with JavaScript visualization libraries
===============

This is a short tutorial on knitr/markdown and JS visualization libraries [**googleVis**](http://code.google.com/p/google-motion-charts-with-r/) and [**rCharts**](http://ramnathv.github.io/rCharts/). With these packages you can create web pages with interactive visualizations from R. This will require minimal or no knowledge of HTML or JavaScript.

You need to have the following R packages and their dependencies installed:

* **knitr**
* **googleVis**
* **rCharts** (not on CRAN)

The tutorial is organized in four parts. First two parts introduce basics about knitr and markdown. The last parts are about using googleVis and rCharts packages in markdown documents. You can download the .Rmd files and run knit2html() on them, or if you are using RStudio you can click "knit HTML" button on the upper left corner.


#### 1. R and markdown
[markdown_knitr.Rmd](https://github.com/al2na/Rmarkdown_JSviz/blob/master/markdown_knitr.Rmd) shows basics of **markdown** and **knitr** integration. These tools will help you create an HTML document using R. The output is [here](https://rawgithub.com/al2na/Rmarkdown_JSviz/master/markdown_knitr.html). In addition, R markdown basics are described [here](http://www.rstudio.com/ide/docs/authoring/using_markdown).

#### 2. Customizing code output in markdown documents
 [controlling_knitr.Rmd](https://github.com/al2na/Rmarkdown_JSviz/blob/master/controlling_knitr.Rmd) shows how code chunk output can be controlled by knitr options.
The output is [here](http://rawgithub.com/al2na/Rmarkdown_JSviz/master/controlling_knitr.html)

#### 3. Using Google visualization API in markdown documents
 [googleVis.Rmd](https://github.com/al2na/Rmarkdown_JSviz/blob/master/googleVis.Rmd) shows how to use googleVis package in a markdown document.You can incorporate plots from Google Visualization API. The output is [here](http://rawgithub.com/al2na/Rmarkdown_JSviz/master/googleVis.html)

#### 4. Using multiple JS visualization libraries in markdown documents
 [rCharts.Rmd](https://github.com/al2na/Rmarkdown_JSviz/blob/master/rCharts.Rmd) shows how to use rCharts package in a markdown document. Using rCharts, you can incorporate various JS visualizations on your HTML document. The output is [here](http://rawgithub.com/al2na/Rmarkdown_JSviz/master/rCharts.html). 

