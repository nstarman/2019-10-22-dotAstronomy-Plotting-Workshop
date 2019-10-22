# dotAstronomy 2019/10/22 Plotting Workshop

[![DOI](https://zenodo.org/badge/214871831.svg)](https://zenodo.org/badge/latestdoi/214871831)


## Welcome

Welcome to the 11th .Astronomy Conference! For the conference website, [click here](https://www.dotastronomy.com/eleven). This GitHub repository is for the [Plotting Workshop on Tuesday, October 22 at 3:30-4:30 pm](util/Plotting_Workshop.ics).

<br>

## Attribution

Author: **Nathaniel Starkman** - *Graduate Student @ UofT* - [website](http://www.astro.utoronto.ca/~starkman/) -- [github](https://github.com/nstarman)

Scientific Organization Committee:

- Renée Hložek (Co-Chair)
- Bryan Gaensler (Co-Chair)
- Katie Breivik
- Siqi Liu
- Tina Peters
- Mubdi Rahman
- Michael Reid
- Nathaniel Starkman

<font size="2"> 
This repository is licensed under the MIT License - see the [LICENSE](LICENSE.md) file for details. Contained within this repository are examples, notebooks, and documents not written by this author.  This author claims no credit for their work and has made good-faith effort to properly document and attribute all such documents. Their contributions are governed by their own license agreements.
</font>

<br>

## Contents

<!-- MarkdownTOC -->

- [Introduction](#introduction)
- [Packages Summary](#packages-summary)
- [Notebooks](#notebooks)
    - [Starting Points](#starting-points)
        - [Matplotlib General Reference](#matplotlib-general-reference)
        - [Plotly General Reference](#plotly-general-reference)
    - [Interactive Matplotlib](#interactive-matplotlib)
        - [mpld3 Demo](#mpld3-demo)
        - [Making Movies](#making-movies)
        - [Matplotlib Widgets](#matplotlib-widgets)
    - [Power-User Plotting Functions](#power-user-plotting-functions)
        - [Decorators in Plotting](#decorators-in-plotting)
- [Further Resources](#further-resources)
- [Final Thoughts](#final-thoughts)

<!-- /MarkdownTOC -->

<br>

- - -

<br>

<a id="introduction"></a>
# Introduction

Perhaps you've seen `this`, a package built into every version of python since [2004](https://www.python.org/dev/peps/pep-0020/) that  summarizes the guiding principles of Python. There's one line, line 13 to be exact, which I think is especially salient.
> There should be one-- and preferably only one --obvious way to do it.

In this case, *it* is plotting in Python, and for better or worse there are a whole lot more than one way to go about it. In this tutorial we cannot cover the myriad plotting options, so instead we will focus on just two. The first, [Matplotlib](https://matplotlib.org) is the closest Python has to the "obvious" way to do plotting; though as anyone who has used Matplotlib knows, it is often anything but obvious. The second, [Plotly](https://plot.ly), is a newer entrant to the field, but one that I think has the potential to go the distance and become the standard library for interactive plots. 

If you are here to read a long summary of how to plot I am sorry to disappoint. The best way to learn Python is to use Python and we will mostly be looking at example [Jupyter Notebooks](https://jupyter.org). This README serves as both guide for this tutorial and collection of resources for future reference. We start with a brief overview of the plotting landscape. Next we will dive into a Matplotlib (+ mpld3) and Plotly. Last, time permitting, I will introduce the concept of decorator-augmented plotting functions.

<br>

<a id="packages-summary"></a>
# Packages Summary


For most, [Matplotlib](https://matplotlib.org) is the place to start and end. Matplotlib is the most popular and also one of the most feature-rich 2D plotting libraries for Python. There are many good reasons to use Matplotlib: it can make pretty much any plot, there's extensive documentation, examples and support, and it is the default plotter for package integration (ex [Pandas](https://pandas.pydata.org/index.html) or [Seaborn](https://seaborn.pydata.org)). However, Matplotlib has a number of shortcomings: it is verbose, it is not interactive, and it can take a fair bit of wrangling to produce quality plots.

There are numerous plotting libraries which attempt to address Matplotlib's shortcomings. To name but a few:

- [Seaborn](https://seaborn.pydata.org)
	> "Seaborn is a Python data visualization library based on matplotlib. It provides a high-level interface for drawing attractive and informative statistical graphics." ([Seaborn](https://seaborn.pydata.org))
 
	- Note: Seaborn is built on top of Matplotlib and can very easily be used to clean up and augment Matplotlib plots.
    - [Here](https://jakevdp.github.io/PythonDataScienceHandbook/04.14-visualization-with-seaborn.html), [here](https://towardsdatascience.com/data-visualization-a6dccf643fbb) and [here](https://towardsdatascience.com/matplotlib-seaborn-basics-2bd7b66dbee2) are good examples.

- [Bokeh](https://bokeh.pydata.org/en/latest/)
	> "Bokeh is an interactive visualization library that targets modern web browsers for presentation. Its goal is to provide elegant, concise construction of versatile graphics, and to extend this capability with high-performance interactivity over very large or streaming datasets. Bokeh can help anyone who would like to quickly and easily create interactive plots, dashboards, and data applications." ([Bokeh](https://bokeh.pydata.org/en/latest/))

    - [Here](https://towardsdatascience.com/data-visualization-with-bokeh-in-python-part-one-getting-started-a11655a467d4) is a good introduction.

- [MPLD3](http://mpld3.github.io/index.html) for a way to make interactive Matplotlib plots.
	> "The mpld3 project brings together Matplotlib, the popular Python-based graphing library, and D3js, the popular JavaScript library for creating interactive data visualizations for the web. The result is a simple API for exporting your matplotlib graphics to HTML code which can be used within the browser, within standard web pages, blogs, or tools such as the IPython notebook." ([MPLD3](http://mpld3.github.io/index.html))

	- Note: this can be used to augment existing matplotlib codes.

- [Altair](https://altair-viz.github.io/index.html)
	> "a declarative statistical visualization library for Python, based on Vega and Vega-Lite." ([Altair](https://altair-viz.github.io/index.html))
   
- [Vega-lite](https://vega.github.io/vega-lite/)
    > "Vega-Lite is a high-level grammar of interactive graphics. It provides a concise JSON syntax for rapidly generating visualizations to support analysis. Vega-Lite specifications can be compiled to Vega specifications" ([Vega-lite](https://vega.github.io/vega-lite/))

- [Plotly](https://plot.ly)
	> "Plotly is a collaborative browser-based plotting and analytics platform. You can generate graphs and analyze data from the in-browser Python sandbox (numpy supported) or the Plotly API (download here). Plotly supports interactive graphs with IPython notebooks. Graphs are interactive, can be styled with Python or the GUI, and sharable by link. Scripts, graphs, and data can be shared, collaboratively edited, and stored and run in Plotly." ([Python Wiki](https://wiki.python.org/moin/NumericAndScientific/Plotting))

- ggplot
- etc...

For a long enumeration of other available plotting libraries, see the list maintained at the [Python Wiki](https://wiki.python.org/moin/NumericAndScientific/Plotting). Unfortunately, we will not have time to explore these great resources in detail. There are notebooks to assist in setting up *mpld3* and Plotly. *mpld3* can be used for advanced features, or just as an in-situ modifier for Matplotlib.  Plotly is a different plotting libraries with different syntax -- hardly seems worth it. But learning Plotly is just as valuable as Matplotlib for two reasons: one, because after its major overhaul it is now a powerful and rationally constructed library for interactive plots. And two, because Plotly produces HTML plots that can be easily integrated into website and other public facing media and can also be integrated with some incredible tools, like [Dash](https://dash-gallery.plotly.host/Portal/) or [Glue](http://glueviz.org/index.html). Put together, Plotly can easily accomplish things with which Matplotlib struggles, even with the assistance of tools such as *mpld3*.


<br>

<a id="notebooks"></a>
# Notebooks

Whether you are new to plotting in Python, or have years of experience, these notebooks will serve as useful reference. The notebooks are organized into three levels: *Starting Points*, *Interactive Matplotlib*, and *Power-User Plotting Functions*.

<a id="starting-points"></a>
## Starting Points

<a id="matplotlib-general-reference"></a>
###  [Matplotlib General Reference](notebooks/matplotlib_general_reference.ipynb)

This notebook covers the basic features of Matplotlib. It was originally written by J.R. Johansson and collaborators ([link](https://nbviewer.jupyter.org/github/jrjohansson/scientific-python-lectures/blob/master/Lecture-4-Matplotlib.ipynb)
) and has been updated for style and to reflect some changes in Matplotlib. 

This notebook is extensive. There are worked examples showing:

- using the MATLAB-like API
- using the object-oriented API
- saving figures
- setting legends, labels, and titles
- formatting text
- setting colors, linewidths
- setting colors
- setting line and marker styles
- controlling axis appearance: plot range and axis scaling
- placing ticks and customizing tick labels
- axis labelling and positioning, including twin axes
- 2D and 3D plot types
- text annotation
- subplots and gridspec
- colormaps and contours
- the basics of animations
- changing the backend

*Try making some of these plots with your data.*


<a id="plotly-general-reference"></a>
### [Plotly General Reference](notebooks/plotly_general_reference.ipynb)

This notebook covers the basic features of Plotly Version 4 -- a major update making plotly work entirely offline and overhauling the API. It is much improved and if you disliked the Plotly of yesteryear (I did), Version 4 should make you reconsider. This notebook draws heavily from the Plotly documentation which, though improving, is still fairly unorganized. Hopefully this notebook will present a more coherent picture of Plotly's considerable capabilities.

This notebook has worked examples showing:

- plotly_express, from simple plots to animated plots
- the object-oriented API
- making layouts
- adjusting the layout
- adding plots to different axes and figures
- saving figures
- text formatting
- etc.


*Try making some of these plots with your data.*


<a id="interactive-matplotlib"></a>
## Interactive Matplotlib

These notebooks are for users familiar with Matplotlib. Here we will make different aspects of Matplotlib interactive. I would recommend starting with [mpld3](notebooks/mpld3_demo.ipynb).

<a id="mpld3-demo"></a>
### [mpld3 Demo](notebooks/mpld3_demo.ipynb)

This notebook is an amalgamation of a few example notebooks from [mpld3's website](http://mpld3.github.io). *mpld3* is a plugin that modifies the behavior of matplotlib plots in-situ, adding interactivity. This is an excellent first step in interactive plotting since it uses vanilla Matplotlib.

*Try installing mpld3 and making your plots interactive!*


<a id="making-movies"></a>
### [Making Movies](notebooks/matplotlib_movies.ipynb)

This notebook details how to make and save a movie using the powerful `FuncAnimation` and an update method for a figure. Movies are an excellent way to communicate science, especially to the public. Unfortunately, making a movie can be a fairly involved process: depending on your OS the backend can be difficult to set up, and the structure of a movie-plotting function is quite a bit different than for standard Matplotlib. I cover the basics of how to make a movie, and have embedded in a number of example scripts, sourced from [Jake Vanderplas](http://vanderplas.com) and [matplotlib](https://matplotlib.org/examples/animation/).

*Try taking some of your existing code and turning it into a movie. Anything time-dependent is an easy candidate. Alternatively, a complex figure with a number of components can often be better explained by introducing each piece separately and adding annotations. This also makes for a good movie.*


<a id="matplotlib-widgets"></a>
### [Matplotlib Widgets](notebooks/matplotlib_widgets.ipynb)

I'll be honest -- I'm relatively new to the widget scene, though I plan to rapidly correct this plotting oversight. This notebook was sourced from [Will Koehrsen](https://github.com/WillKoehrsen/Data-Analysis/tree/master/widgets) and updated for Plotly Version 4.

*Try taking some of your existing plots, matplotlib or plotly, and adding widget control!*

<br>

<a id="power-user-plotting-functions"></a>
## Power-User Plotting Functions

Matplotlib plots are great but they are not very responsive. What do I mean? check out this notebook to find out.

<a id="decorators-in-plotting"></a>
### [Decorators in Plotting](notebooks/plotting_with_decorators.ipynb)

This notebook lays out the case for a different approach to creating plotting functions. It's a technique I've been working on recently (see [starkplot](https://github.com/nstarman/starkplot) for details) and has proved immensely useful. If you don't know what a decorator is, you'll need to work your way through [this notebook](resources/making_decorators.ipynb).

*Try constructing a plotting decorator and apply it to one/all of your plotting functions. Like mpld3, this is pretty much an instant upgrade to all of your plotting functions.*

*If you like plotly, try making a plotly decorator. It's the same idea, just slightly different execution than a matplotlib-applicable decorator*

*If you are really feeling advanced, try combining this with interactivity -- mpld3 is easiest but a widget is more flexible.*


<br>

<a id="further-resources"></a>
# Further Resources

- An intro to [thinking about data visualization](https://towardsdatascience.com/the-art-and-science-of-data-visualization-6f9d706d673e).

- A Matplotlib [cheat sheet](resources/Python_Matplotlib_Cheat_Sheet.pdf) 

- The [towardsdatascience](https://towardsdatascience.com/data-visualization/home) website.

- Jake Vanderplas's [Python Data Science Handbook](https://github.com/jakevdp/PythonDataScienceHandbook), also on this repository, [here](resources/Python%20Data%20Science%20Handbook/).

- Robert Johansson's [Scientific Python Lectures](https://github.com/jrjohansson/scientific-python-lectures).

- [Rougier' Matplotlib Tutorial](https://github.com/rougier/matplotlib-tutorial), downloaded [here](resources/Rougier%20Tutorial).

- Plotly's Dash: This is an awesome way to extend plotly plots and make truly interactive figures.

    - [https://github.com/plotly/dash-svm](https://github.com/plotly/dash-svm)

    - [https://dash-gallery.plotly.host/dash-svm/](https://dash-gallery.plotly.host/dash-svm/)

- [Glue](http://glueviz.org/index.html): Prof. Alyssa Goodman just gave an awesome talk on Glue and the future of interactive figures. Definitely check this out!

<br>

<a id="final-thoughts"></a>
# Final Thoughts

Thank your for attending this plotting workshop. I hope this repository serves as a useful future reference. Feel free to contact me with plotting questions and suggestions, or even about science.

I have a final thought, related to plotting, I consider worth sharing.

**The Beauty of Log Files**

Reproducibility and code transparency is important. Log files can be a good way to ensure both these things. Conventionally log files are just plain text, in a plain text format. Recently I have made the switch to Markdown log files, still written in plain text format for application interoperability. The advantage of this approach is that I can specify sections in my log files, but more importantly embed figures with Markdown's `![]()` syntax. Making log files, especially with embedded images, has improved my science. If you are interested in this, check out the `logging` Python package or [`astroPHD`](https://github.com/nstarman/astroPHD) -- my repository-in-progress where I have been tinkering with some of these ideas.


<br><br><br>
