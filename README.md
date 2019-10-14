# dotAstronomy 2019/10/22 Plotting Workshop

[![DOI](https://zenodo.org/badge/214871831.svg)](https://zenodo.org/badge/latestdoi/214871831)


## Welcome

Welcome to the 11th .Astronomy Conference! For the conference website, [click here](https://www.dotastronomy.com/eleven). This GitHub repository is for the [Plotting Workshop on Tuesday, October 22 at 3:30-4:30 pm](util/Plotting_Workshop.ics).


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

This project is licensed under the MIT License - see the [LICENSE](LICENSE.md) file for details


## Contents

<!-- MarkdownTOC -->

- [Notebooks](#notebooks)
	- [Matplotlib General Reference](#matplotlib-general-reference)
	- [](#)
	- [Plotly General Reference](#plotly-general-reference)
- [Introduction](#introduction)
- [Packages Summary](#packages-summary)
- [Resources](#resources)
- [Matplotlib](#matplotlib)
- [Plotly](#plotly)
	- [Plotly Dash](#plotly-dash)

<!-- /MarkdownTOC -->


### Notebooks

#### [Matplotlib General Reference](notebooks/matplotlib/matplotlib_general_reference.ipynb)

[link](https://nbviewer.jupyter.org/github/jrjohansson/scientific-python-lectures/blob/master/Lecture-4-Matplotlib.ipynb)

#### 


#### [Plotly General Reference](notebooks/plotly/plotly_general_reference.ipynb)



# Introduction

Perhaps you've seen `this`, a package built into every version of python since [2004](https://www.python.org/dev/peps/pep-0020/) that  summarizes the guiding principles of Python. There's one line, line 13 to be exact, which I think is especially salient.
> There should be one-- and preferably only one --obvious way to do it.

In this case, *it* is plotting in Python, and for better or worse there are a whole lot more than one way to go about it. In this tutorial we cannot cover the myriad plotting options, so instead we will focus on just two. The first, [Matplotlib](https://matplotlib.org) is the closest Python has to the "obvious" way to do plotting; though as anyone who has used Matplotlib knows, it is often anything but obvious. The second, [Plotly](https://plot.ly), is a newer entrant to the field, but one that I think has the potential to go the distance and become the standard library for interactive plots. 

If you are here to read a long summary of how to plot I am sorry to disappoint. The best way to learn Python is to use Python and we will mostly be looking at example [Jupyter Notebooks](https://jupyter.org). This README serves as both guide for this tutorial and collection of resources for future reference. We start with a brief overview of the plotting landscape



# Packages Summary


For most, [Matplotlib](https://matplotlib.org) is the place to start and end. Matplotlib is the most popular and also one of the most feature-rich 2D plotting libraries for Python. There are many good reasons to use Matplotlib: it can make pretty much any plot, there's extensive documentation, examples and support, and it is the default plotter for package integration (ex [Pandas](https://pandas.pydata.org/index.html) or [Seaborn](https://seaborn.pydata.org)). However, Matplotlib has a number of shortcomings: it is verbose, it is not interactive[^matplotlib_interactive], and it can take a fair bit of wrangling to produce quality plots.

There are numerous plotting libraries which attempt to address Matplotlib's shortcomings. To name but a few:

- [Seaborn](https://seaborn.pydata.org)
> "Seaborn is a Python data visualization library based on matplotlib. It provides a high-level interface for drawing attractive and informative statistical graphics." ([Seaborn](https://seaborn.pydata.org))
	- Note: Seaborn is built on top of Matplotlib and can very easily be used to clean up and augment Matplotlib plots.
- [Bokeh](https://bokeh.pydata.org/en/latest/)
> "Bokeh is an interactive visualization library that targets modern web browsers for presentation. Its goal is to provide elegant, concise construction of versatile graphics, and to extend this capability with high-performance interactivity over very large or streaming datasets. Bokeh can help anyone who would like to quickly and easily create interactive plots, dashboards, and data applications." ([Bokeh](https://bokeh.pydata.org/en/latest/))
- [Plotly](https://plot.ly)
> "Plotly is a collaborative browser-based plotting and analytics platform. You can generate graphs and analyze data from the in-browser Python sandbox (numpy supported) or the Plotly API (download here). Plotly supports interactive graphs with IPython notebooks. Graphs are interactive, can be styled with Python or the GUI, and sharable by link. Scripts, graphs, and data can be shared, collaboratively edited, and stored and run in Plotly." ([Python Wiki](https://wiki.python.org/moin/NumericAndScientific/Plotting))
- etc...

For a long enumeration of other available plotting libraries, see the list maintained at the [Python Wiki](https://wiki.python.org/moin/NumericAndScientific/Plotting). Unfortunately, we will not have time to explore any of these great resources except Plotly. Why Plotly? One, because I like it. Two, because after its major overhaul it is now a powerful and straitforward library. And three, because Plotly produces HTML plots which can be easily integrated into website and other public facing media and can also be integrated with some incredible tools like [Dash](https://dash-gallery.plotly.host/Portal/) (more on that later).


[^matplotlib_interactive]: Check out [MPLD3](http://mpld3.github.io/index.html) for a way to make interactive Matplotlib plots.
> "The mpld3 project brings together Matplotlib, the popular Python-based graphing library, and D3js, the popular JavaScript library for creating interactive data visualizations for the web. The result is a simple API for exporting your matplotlib graphics to HTML code which can be used within the browser, within standard web pages, blogs, or tools such as the IPython notebook." ([MPLD3](http://mpld3.github.io/index.html))

	- Note: this can be used to augment existing matplotlib codes.




## Resources

Both Matplotlib and Plotly are extensively documented and I am not going to waste your time and mine by contributing yet another general summary of either. 

Instead, 


[towardsdatascience](https://towardsdatascience.com/data-visualization/home)




- - -


# Matplotlib


- - -


# Plotly


#### Plotly Dash

[https://github.com/plotly/dash-svm](https://github.com/plotly/dash-svm)

[https://dash-gallery.plotly.host/dash-svm/](https://dash-gallery.plotly.host/dash-svm/)


<br><br><br>
