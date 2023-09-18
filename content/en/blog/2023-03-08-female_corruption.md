---
title: "Gendered Corruption: An Analysis of Corruption Cases in China"
date: 2023-03-20T16:00:21-04:00
author: Xinting Du
slug: bookdown-tips
draft: false
toc: true
tags: Python
---


Although it has been acknowledged for a while that promoting women's political participation is a requirement for achieving gender equality, recent discussions have emphasized the potential of women's political participation to reduce corruption and improve governance. International organizations such as the World Bank and the United Nations, as well as countries like Mexico, Uganda, and various European countries, view women as possessing higher levels of honesty and integrity, which are essential traits for effective governance[^1]. 

Why are women officials linked to less corruption? Two interesting mechanisms explain why females are less corrupt at the individual level. The risk aversion mechanism contends that women tend to be more averse to taking risks than men. They, therefore, are less likely to engage in corrupt activities when there is a high probability of being caught[^2]. The marginalization mechanism suggests that due to women's exclusion from positions of power, they are unable to misuse their authority for their own benefit[^3]. In other words, women are not distinct from men in corruption if they are accessible to the power network.

On International Women's Day this year, I happened to read a [paper](https://doi.org/10.1111/gove.12752). By using the Taiwanese district court judgments, this study examines the individuals who were involved in corruption and finds that women are less corrupt because they are too marginalized to reach the power for corruption. With the rise of gender equality in Taiwanese society, women are as corrupt as men.

This study arose my interest in the same question in the China's context. I realized that I could do a parallel study to examine are female officials more or less corrupt than their male counterparts in China? 

By analyzing text data on 19943 court judgments and 34669 defendants in 32 provinces from 2008 to 2016, I want to answer two questions. First, whether women in China commit fewer corruption activities than men; and second, (if there is a gender gap) why there is a gender gap in corruption. 

## Male-to-Female Sex Ratio of Corruption Cases from 2008 to 2016

The key variable of this study is the gender of corrupt individuals. I extracted the gender information of defendants from the first paragraph in the court judgment, which usually contains individual characters of defendants and lawyers. However, there are variations within different court documents. To be more specific, some cases give the actual name of defendants and exhaustive information on gender, education level, and occupation. However, some cases nickname the defendants “Li Somebody”(李某某) and provide no other information. That makes the missing values in the variable, with 27.2\% (9428) of the observations missing.

Based on the gender information, I constructed a measurement on the annual gender gap in corruption cases in each province and standardized it by dividing the sex ratio in the workplace. 

$$S_{p,t} = \frac{NM_{p,t}}{M_{p,t}} \times  \frac{F_{p,t}}{NF_{p,t}}$$

where `$NM_{p,t}$` is the number of male corrupt cases in province p in year t; `$M_{p,t}$` is the number of male state actors in province p in year t; `$NF_{p,t}$` is the number of female corrupt cases in province p in year t; and $F_p,t$ is the number of female state actor in province p in year t.


Figure 1 displays the average standardized sex ratio in corruption cases from 2008 to 2016. The increasing trend suggests that male individuals were more likely to be involved in corrupt activities than female individuals during this period. In addition to the mean sex ratio, the plot also shows that the standard deviation of the sex ratio increased over time, which indicates a higher variation of corrupt individuals across provinces.

## Why the Sex Ratio of Corruption Increases?

According to the **risk aversion theory**, women are less likely to engage in corruption than men because women are risk averse. 
To estimate the effect of Xi came into power I run the following regression:

$$S_{p,t} = Xi_{t} + log(population_{p,t}) + log(gdp_{p,t}) + \gamma_{t} + \eta_{p}+\epsilon_{p,t} $$


`$S_{p,t}$` is the dependent variable, which denotes the standardized sex ratio in corruption cases in province p in year t. `$Xi_{t}$` is the main independent variable, which is 1 when Xi came into power in 2013. Besides, I control the effect of provincial population and GDP and include the time and province fixed effects. The standard error is clustered on the provincial level.

To test the **marginalization mechanism** I run the following regression:

$$S_{p,t} = Occupation_{p,t} + log(population_{p,t}) + log(gdp_{p,t}) + \gamma_{t} + \eta_{p}+\epsilon_{p,t} $$


`$S_{p,t}$` is the dependent variable, which denotes the standardized sex ratio in corruption cases in province p in year t. `$Occupation_{p,t}$` is the main independent variable, which I manually coded the state actors into three groups: government officials, urban non-private units (e.g., enterprises), and public institutions (e.g., hospitals and schools). `$Occupation_{p,t}$` is 1 when the workplace is the public institution, and 2 and 3 the enterprises and the local government. Besides, I control the effect of provincial population and GDP and include the time and province fixed effect. The standard error is clustered on the provincial level.


[^1]: Water





