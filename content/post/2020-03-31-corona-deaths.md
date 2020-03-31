---
URL: /2020/03/31/corona-COVID-19-death-tolls-worst-day-so-far/
title: Daily Death Tolls During the Corona Pandemic—The Worst Days So Far
author: Cédric
date: "2020-03-31"
image: img/banner/corona-giacomo-carra.jpg
layout: post
description: "The massive bushfires in Australia are in the news worldwide. The incredible extent of burnt land and plume of smoke is hard to imagine so I have compared the areas to countries in Europe and worldwide."
tags:
    - DataViz
    - COVID-19
    - ggplot2
    - SWDchallenge
    - animation
    - heatmap
showtoc: false
---
<font size="-1">Header image by [Giacomo Carra via Unsplash](https://unsplash.com/photos/gf6UDwpl0ac)</font>

**Coronavirus SARS-CoV-2, COVID-19 or simply Corona&mdash;what started as an epidemic in Wuhan, China has become a global pandemic, leading to hundreds of thousands of infections and thousands of deaths so far, national lockdowns and quarantines of cities, [#stayhome](https://twitter.com/hashtag/stayhome) and [#flattenthecurve](https://twitter.com/hashtag/flattenthecurve) hashtags and obviously a global shortage of toilet paper.**

When the corona pandemic started, I felt scared, curious and tired at the same time. *Scared as a husband and father* by the impact this virus outbreak might have on our life, in 2020 and way beyond. *Curious as a scientist* who focused his PhD thesis on the spread and persistence of directly transmitted diseases in the context of contact rates and movement. And *tired as a data visualization specialist* when I saw a lot of visualizations that were created by persons that neither had the knowledge nor the interest to produce accurate visualizations. Back then I decided against creating corona-related data visualizations for several reasons (see below). However, I have the feeling that the initial spread of misleading visualizations that either trigger panic or whataboutism is mainly over and we now have a lot of data to base our visualizations on.

##### Latest update: March 31, 2020

| ![latest-animation](/img/corona-animation/0330_corona_begin_series.gif) ![latest-plot](/img/corona-animation/0330_corona_sum_latest.png) |
|:--:|
| *Latest numbers of daily death tolls worldwide and per country, sorted by first case (animation) and total deaths (static visualization).* |

### The idea

Inspired by my colleague [Alexandre Courtiol](https://twitter.com/alexcourtiol), who looked at [the worst day on a country-level by visualizing the deaths due to COVID-19 adjusted for baseline mortality and population size](https://github.com/courtiol/excess_mortality_COVID19), I decided to highlight where each country falls along the wave. While his plot reveals some interesting patterns, I aimed for a timeline to reveal the temporal trends. Particularly, I wanted to show where along the curve each country falls&mdash;are we already over the (first) wave or can we expect more and more deaths in the next days? So I decided to take a different approach by calculating the number of daily deaths relative to the worst day on both the global and the country level.

| ![animation-corona-original](/img/corona-animation/corona_sum.gif) | ![static-plot-corona-original](/img/corona-animation/corona_begin_latest.png) |
|:--:|:--:|
| *The first version as of 29th of March that I submitted as contibution to the [#SWDchallenge](https://community.storytellingwithdata.com/challenges/ed4eaf73-f659-4f41-b7ec-58396809a907/95f2ba49-12ee-4ea0-951c-ce4ba394ff7b).* | *A static version of the situation as of 29th of March with countries sorted by first reported death due to COVID-19.* |

### How to read the visualization

As explained above, I calculated for each day the number of death cases relative to the "worst  day", namely the day with the most deaths so far. Imagine a naïve population that was not facing the virus before. At some point, there might be people dying but likely only a few (with regard to COVID-19&mdash;in general, this highly depends on the severity of infection caused by the pathogen, often referred to as *case fatality ratio* or simply *case fatality*). Consequently, the proportion of deaths on the first day compared to the worst day has to be 100% (since the first day has to be, by definition, the worst day so far). On the next day, there might be more deaths than on the day before, a known pattern we see in reality and in simulations of early epidemics. Exponential growth, an always increasing curve we aim to flatten by reducing contact between infected and susceptible (non-infected but able to catch the infection). So on day two, two times as many people might die which makes day 2 the worst day with a proportion of 100%. At the same time, the proportion of deaths on day 1 decreases from 100% to 50%. This way it enables to see if we are still facing (exponential) growth or if we, at least for now, over the peak if deaths.


### Things to keep in mind when visualizing COVID-19 data

In the recent weeks, there is a lot of discussion on several things to account for when analyzing data and designing visualizations on the topic of the corona pandemic.

First of all, the final visualization should be as precise and transparent as possible. (Of course, this should be the case for all visualizations!) This means that the final product should be designed with care by adding the source of data, how the data was aggregated and analyzed, and what the visualization shows. Further, this implies a careful choice of text, especially the title, and the colors which should both neither be hysteric nor play down the current situation. For example, the [use of bloodish colors](https://blog.datawrapper.de/coronaviruscharts/) to make it crystal-clear that this virus is dangerous might spark panic in some people. If this is an intended choice, this is [professional malpractice and must be called out by us as data visualization specialists](https://twitter.com/AlbertoCairo/status/1241374480351576064).

##### Make design choices carefully

In the early days of the global pandemic, the intention of a particular graphic was often not clear to the reader. Also, I hardly could tell if the designer has the knowledge to analyze and visualize the data in a meaningful way (no, [you are not an expert in pathogen spread when you're investigating market sales!](https://twitter.com/CT_Bergstrom/status/1241522140559503360)) or contacted any experts while preparing the piece. To cite Alberto Cairo, knight chair in visual journalism at the University of Miami: ["Numbers without domain knowledge are dangerous"](https://twitter.com/AlbertoCairo/status/1241371617680293888) and ["the rule should be to ignore **any** 'analysis' from people who haven't consulted with epidemiologists/biostatisticians"](https://twitter.com/AlbertoCairo/status/1241386040570626048). For example, the use of epidemiological terms such as R_0

##### Be explicit about uncertainty

The data we hear and see in the news and our social media streams come with a lot of uncertainty. It is very important to understand that detected or confirmed cases do not necessarily reflect the reality but underestimate the real number of cases&mdash;and to communicate this fact explicitly in the visualization. The number of detected infections with the coronavirus are highly dependent on the number of tests that were performed&mdash;and that [differs a lot among countries](https://ourworldindata.org/covid-testing)! A more robust measure might be deaths due to the coronavirus but keep in mind that the way to report these numbers differs between countries. Furthermore, [no two countries are alike when it comes to access to healthcare and medical resources and even the age structure of the population](https://edition.cnn.com/2020/03/26/health/number-of-cases-testing-data-intl/index.html) which in turn influences the number of reported cases.

Since we are still in the early days of the coronavirus pandemic, correlations with any variable such as temperature or cultural differences need to be treated with caution. Do not release any of such analyses or visualizations if you are not sure what you are doing and did your best to account for any biases. There are experts for this and they are already searching for correlations with the right tools and knowledge.

##### Do I need to adjust for population?

There is a ongoing discussion of ["showing the raw numbers" versus "adjust data for population"](https://twitter.com/jburnmurdoch/status/1242904596856614912). As John Burn-Murdoch&mdash;data visualization designer at the Financial Times and creator of [these fantastic and very informative visualizations on the current situation of the corona spread](https://www.ft.com/coronavirus-latest)&mdash;states: ["Generally, and especially early in outbreak (first few weeks), higher per-capita numbers just mean smaller country, not anything different about how that country’s dealing with covid"](https://twitter.com/jburnmurdoch/status/1242904703144464390). Of course, *population density* matters since the coronavirus is transmitted by direct or close contact. However, *population size* does not necessarily reflect the density in a country. So if accounting for population, this should be optimally done on a regional level sufficient to capture the area of spread instead of borders drawn by influential humans. In the end, it also depends on the story you want to tell if and how you adjust the data. There are also other ways to adjust the data such as those which two ways [Alexandre](https://github.com/courtiol/excess_mortality_COVID19) and I have chosen.

##### Should I use a logarithmic axis?

Furthermore, the use of logarithmic axes is another ongoing discussion. Since the initial growth is likely exponential in case of directly transmitted diseases&mdash;and this is what we see with the coronavirus as well&mdash;a logarithmic scale ["is the natural way to track the spread"](https://twitter.com/jburnmurdoch/status/1237748598051409921). While I would not name it the *natural* way, it is true that such a transformation helps to understand the dynamics and makes (some) comparisons more easy. But again, the choice depends on the picture you want to draw: when turning the y axis into a logarithmic one as John did, ["readers now only have to draw a straight line in their head to see if two countries are one the same path"](https://twitter.com/jburnmurdoch/status/1237749654281912321). While with this transformation it might be easier to compare countries there might be disadvantages: the reader needs to realize and understand the logarithmic axis and small differences might be underestimated which are in reality much higher than some might think.


### Benefits and caveats of the visualization

By calculating the proportion of deaths per country, I avoid some of the issues with current visualizations on the COVID-19 topic:  

1. I use the **number of deaths** which is, compared to confirmed infections, a more reliable measure. Countries also have been reported to classify "death due to COVID-19" in different ways which again makes a comparison between countries difficult. However, by just looking at the numbers per country, every comparison is made with the same standards which do not differ within countries.

1. There was **no need to perform any logarithmic transformation** to reveal the pattern since, again, we compare the absolute numbers per country not between countries.

1. By **scaling death tolls by country**, the visualization accounts for different population sizes and states of the epidemic which enables us to compare them more easily.  

1. The evolving patterns mimics the way we have experienced and are experiencing the pandemic. I found it very interesting to look at the **change in a dynamic way** since values that look very high today might be low in a few days depending on the trend. This way the animations mimics us humans and how we see the situation without making any claims about how the numbers will change in the next days. You can also *ride the wave* and wait for the new colors to be not pink anymore.


### How to create the visualization?

The data is available via [datahub.io](https://datahub.io/core/covid-19).
You can find the codes for my submission to the [SWDchallenge](https://community.storytellingwithdata.com/challenges/ed4eaf73-f659-4f41-b7ec-58396809a907/95f2ba49-12ee-4ea0-951c-ce4ba394ff7b) showing the death tolls until the 29th of March in my corresponding [GitHub repository](https://github.com/Z3tt/SWDchallenge). The code for the latest visualization are uploaded to this [GitHub repository](https://github.com/Z3tt/Corona-Daily-Deaths-Animation).