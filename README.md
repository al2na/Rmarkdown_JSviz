markdown with JavaScript visualization libraries
===============

This is a short tutorial on knitr/markdown and JS visualization libraries [**googleVis**](http://code.google.com/p/google-motion-charts-with-r/) and [**rCharts**](http://ramnathv.github.io/rCharts/). With this packages you can create web pages with interactive visualizations with minimal or no knowledge of HTML or JavaScript.

You need to have the following packages and their dependencies installed:

* **knitr**
* **googleVis**
* **rCharts**

The tutorial is organized in four parts. First two parts introduce basics about knitr and markdown. The last parts are about using googleVis and rCharts packages in markdown documents. You can download the .Rmd files and run knit2html() on them or if you are using RStudio you can click "knit HTML" button on the upper left corner.

1. [markdown_knitr.Rmd](https://github.com/al2na/Rmarkdown_JSviz/blob/master/markdown_knitr.Rmd) shows basics of **markdown** and **knitr** integration. These tools helps you create an HTML page using R. The output is [here](https://rawgithub.com/al2na/Rmarkdown_JSviz/master/markdown_knitr.html)

2. [controlling_knitr.Rmd](https://github.com/al2na/Rmarkdown_JSviz/blob/master/controlling_knitr.Rmd) shows how code chunk output can be controlled by knitr options.
The output is [here](https://rawgithub.com/al2na/Rmarkdown_JSviz/master/controlling_knitr.html)

3. [googleVis.Rmd](https://github.com/al2na/Rmarkdown_JSviz/blob/master/googleVis.Rmd) shows how to use googleVis package in a markdown document.You can incorporate plots from Google Visualization API. The output is [here](https://rawgithub.com/al2na/Rmarkdown_JSviz/master/googleVis.html)

4. [rCharts.Rmd](https://github.com/al2na/Rmarkdown_JSviz/blob/master/rCharts.Rmd) shows how to use rCharts package in a markdown document. Using rCharts, you can incorporate various JS visualizations on your HTML document. The output is [here](https://rawgithub.com/al2na/Rmarkdown_JSviz/master/rCharts.html)


