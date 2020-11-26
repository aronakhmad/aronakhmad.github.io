---
title:  "Indonesia's Poverty Simple Overview Visualization using Matplotlib"
subtitle: "Poverty has been becoming one of Indonesia's biggest problem all along. This article will show you the overview of it in visualization using matplotlib Python. You will get the overview of Indonesia's poverty as well as the simple use of matplotlib for data plotting."
author: "Aron Akhmad"
avatar: "img/authors/cat.jpeg"
image: "img/indo_poverty.jpg"
date:   2020-11-19
---

In data analytics, plotting is an important thing as it gives us insights from the data. There are various tools out there available for plotting. However, as python has been becoming the hottest programming language contemporarily — especially among data scientists, so I’m going to show you how to plot your data using the most eminent python library used for data plotting, matplotlib. Actually, at first I just wanted to make an article about Indonesia’s poverty year-by-year in visualization, but since I’ve been posting about python tutorials before, so why don’t I share the code too, right? Teehee.

Matplotlib is a prominent python library used for data plotting and it is among the most used ones. It is known for its reliability, convenience, and simplicity for plotting, though it might be not the prettiest one. You could plot your data just by typing a few lines of code and poof! you’ll get your data visualized. In this article, you will learn simple plotting using matplotlib as well as simple analysis (or maybe graph reading lmao) of the graph. Please note that the code in this article is just an example aimed to give you an overview of the matplotlib use for data plotting. You may adjust the code as you desire depending on how you want your data to be plotted. The next paragraphs will show you an example of data plotting using the data of Indonesia’s poverty overview year-by-year.

**Import Modules**

First things first, you need to import several modules. There are 3 modules used here; pandas, NumPy, and matplotlib. Pandas will be used for importing and utilizing the data file, NumPy will be used for generating array, and matplotlib will be used for data plotting, obviously. Teehee.

<script src="https://gist.github.com/aronakhmad/cbc65bfd9ff9d644511b6d093c571e5e.js?file=import_modules.py"></script>
<br>
**Import Data**

Bring the data that you desire to plot into the code. We’re using pandas to import the data. In this code below, we open an excel file, so you may adjust the code depending on the type of file you open. Note that `xls.parse(0)` meaning we parse the first sheet on the excel file, and again you may adjust the code according to what you desire. `head` up the data to print the first five data on the file to take a quick sight at the data composition.

<script src="https://gist.github.com/aronakhmad/cbc65bfd9ff9d644511b6d093c571e5e.js?file=data_importing.py"></script>
`output:`
<img src="img/indonesia_poverty_analysis_files/data_head.png" width="100%" height="100%"/>
<br>
**Data Plotting**

Now that the data is already set, we’re about to plot the data immediately. In this particular case, we don’t need to clean up the data since the data is perfectly ready to use. In other cases, you may need to clean the data first before ultimately plotting it. The code below will plot the comparison of the total population living under the poverty line in Indonesia. From the output, we can see that the plot portraying a fluctuated graph meaning the number is going up and down for the past 9 years but more into climbdown in Q1 2017 up to Q3 2019. The graph went up again in Q1 2020, and it’s most probably affected by the COVID-19 pandemic.

<script src="https://gist.github.com/aronakhmad/cbc65bfd9ff9d644511b6d093c571e5e.js?file=plotting1.py"></script>
`output:`
<img src="img/indonesia_poverty_analysis_files/indonesia_poverty_analysis_4_1.svg" width="100%" height="100%"/>
<br>
The second plot portrays pretty much the same as the previous one but in percent. Here, I use a vertical bar plot so that we can compare the 3 parameters side-by-side. The graph depicted the same idea as the first graph.

<script src="https://gist.github.com/aronakhmad/cbc65bfd9ff9d644511b6d093c571e5e.js?file=plotting2.py"></script>
`output:`
<img src="img/indonesia_poverty_analysis_files/indonesia_poverty_analysis_5_1.svg" width="100%" height="100%"/>
<br>
Below is the plot of poverty line comparison in urban and village areas. Just so you know, the poverty line was divided into 2; urban and village up until 2017. I use the horizontal bar plot as it will be easier to compare and get insight from the parameters. From the graph, we can conclude that the poverty line threshold is constantly increasing year by year. It is expected as inflation affect the value of the money as well as the groceries’ prices.

<script src="https://gist.github.com/aronakhmad/cbc65bfd9ff9d644511b6d093c571e5e.js?file=plotting3.py"></script>
`output:`
<img src="img/indonesia_poverty_analysis_files/indonesia_poverty_analysis_6_1.svg" width="100%" height="100%"/>
<br>
The last plot is actually the same as the previous one. Since Q2 2017, the BPS (Indonesia’s Central Bureau of Statistics) website only shows one single poverty line threshold, and judging from the value, it was generalized based on the previous urban threshold. So, in this code below we’re going to plot the urban poverty line threshold from Q1 2011 up until Q1 2017, extended with the general poverty line threshold from Q2 2017 up until Q1 2020. The output graph showing that the threshold is always increasing but the step-up percentage fluctuates until Q1 2018 ¬-— meanwhile you can see in Q3 2011 to Q1 2012 and Q3 2017 to Q1 2018 showing an almost flat horizontal graph meaning the climb-up rate is remarkably low. On another side, Q3 2018 to Q1 2020 showing an almost constant straight line meaning the climb-up rate is pretty much stable.

<script src="https://gist.github.com/aronakhmad/cbc65bfd9ff9d644511b6d093c571e5e.js?file=plotting4.py"></script>
`output:`
<img src="img/indonesia_poverty_analysis_files/indonesia_poverty_analysis_7_1.svg" width="100%" height="100%"/>
<br>
So that was a simple graph plotting of Indonesia’s poverty overview year-by-year. It was just the simple one, you can explore more with matplotlib. You can make interactive graphs and other interesting features with it, but I hope this article was useful. Thank you for reading and don’t forget to always be healthy. ✨

