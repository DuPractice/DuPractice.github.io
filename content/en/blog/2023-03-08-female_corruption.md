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

where `$NM_{p,t}$` is the number of male corrupt cases in province p in year t; `$M_{p,t}$` is the number of male state actors in province p in year t; `$NF_{p,t}$` is the number of female corrupt cases in province p in year t; and `$F_p,t$` is the number of female state actor in province p in year t.

{{<figure src="/media/en_blog/2023-03-08-female-corruption/pic3.png" caption="Figure 1. The average standardized sex ratio in corruption cases from 2008 to 2016." width="800">}}

Figure 1 displays the average standardized sex ratio in corruption cases from 2008 to 2016. The increasing trend suggests that male individuals were more likely to be involved in corrupt activities than female individuals during this period. In addition to the mean sex ratio, the plot also shows that the standard deviation of the sex ratio increased over time, which indicates a higher variation of corrupt individuals across provinces.

## Why the Sex Ratio of Corruption Increases?

According to the **risk aversion theory**, women are less likely to engage in corruption than men because women are risk averse. To test this hypothsis, I employ the anti-corruption campaign after Xi's period as the exogeneous shock. Although both Hu Jintao and Xi Jinping took measures to combat corruption, the political environment under Xi is less tolerant to the corruption.

To estimate the effect of Xi came into power I run the following regression:

$$S_{p,t} = Xi_{t} + log(population_{p,t}) + log(gdp_{p,t}) + \gamma_{t} + \eta_{p}+\epsilon_{p,t} $$


`$S_{p,t}$` is the dependent variable, which denotes the standardized sex ratio in corruption cases in province p in year t. `$Xi_{t}$` is the main independent variable, which is 1 when Xi came into power in 2013. Besides, I control the effect of provincial population and GDP and include the time and province fixed effects. The standard error is clustered on the provincial level.
{{<figure src="/media/en_blog/2023-03-08-female-corruption/pic1.png" caption="Figure 2. Effects of Xi’s Period on Sex Ratio of Corruption Cases." width="800">}}

Figure 2 zooms into the coefficient of each year. It displays that after Xi came into power in 2013, there is a statistically significant positive relationship on sex ratio in corruption cases. That means the gender gap in corruption keeps expanding after 2013.  

To test the **marginalization mechanism** I run the following regression:

$$S_{p,t} = Occupation_{p,t} + log(population_{p,t}) + log(gdp_{p,t}) + \gamma_{t} + \eta_{p}+\epsilon_{p,t} $$

I use the occupation as a proxy as the marginalization of the workplace because in the context of China, the provincial statistics yearbook shows that the male-to-female sex ratio is highest in local government, a male-dominated workplace, and lowest among public institution employees, a more gender-balanced workplace. According to the marginalization mechanism, women may be less corrupt because they lack the power to abuse it for personal gain. Building on this idea, we can predict that the gender difference in corruption cases will be greater among local government employees than among public institution employee..

`$S_{p,t}$` is the dependent variable, which denotes the standardized sex ratio in corruption cases in province p in year t. `$Occupation_{p,t}$` is the main independent variable, which I manually coded the state actors into three groups: government officials, urban non-private units (e.g., enterprises), and public institutions (e.g., hospitals and schools). `$Occupation_{p,t}$` is 1 when the workplace is the local government, and 2 and 3 the public institution and the state-owned enterprises. Besides, I control the effect of provincial population and GDP and include the time and province fixed effect. The standard error is clustered on the provincial level.

{{<figure src="/media/en_blog/2023-03-08-female-corruption/pic2.png" caption="Figure 3. The coefficient of occupation (government officials as the reference group)" width="800">}}

Using sex ratio of corruptions in local governments as the reference group, Figure 3 shows the coefficients of working in public institutions and enterprises.  This result means that sex ratio in corruption cases among local government employees is larger than its counterpart among public institutions, and state-owned enterprises. In other words, the sex ratio in corruption cases in marginalized workplaces is larger than it in a less marginalized one, which is consistent with the marginalization mechanism.

## Conclusion

I uses court judgment data from “China Judgments Online” to answer two research questions: whether women in China commit fewer corruption activities than men; and second, why there is a gender gap in corruption. I find that from 2008 to 2016, more male state actors were convicted than their female counterparts. The male-to-female sex ratio of corruption cases during Xi’s period increased nearly three times that in Hu’s period. In addition, using occupation as a proxy of power access, this paper finds sex ratio of corruption cases is the highest among government agents, then enterprises and public institutions. I argue that risk aversion and marginalization mechanisms could assist our understanding of these patterns.

These findings imply that only increasing females’ share in units cannot alleviate corruption in China. Previous results show that women in a less marginalized workplace, where the male-to-female sex ratio is more balanced, have no salient difference in corruption from the male employees. Thus, promoting female political participation could make females less marginalized in the workplace and as powerful as males to engage in corruption. A more promising way to reduce corruption is to make corruption a higher-risk behavior, such as strengthening law enforcement, increasing penalties for corrupt behavior, and increasing transparency in the governance, enterprises, and institutions. 

However, the interpretation of my findings should be careful. My findings are based on limited data on corrupt individuals, which may make my estimations biased. There are three potential threats that data put on my findings. First, the court judgments are incomplete, and they are not representative data on corruption cases. That limitation may make my analysis selective. Second, although court judgments provide observations on corrupt individuals, the problem is that there is no observation on non-corrupt individuals. This limitation makes the analysis cannot locate on the individual level. Instead, I aggregate the observations on the provincial level, which wastes individual information. Finally, there are many missing values in individual observations. And by so far, I have failed to refute the assumption that the unobserved individuals will not bias the estimation.



[^1]: Chaudhuri, A., Iversen, V., Jensenius, F. R., & Maitra, P. (2022). Time in Office and the Changing Gender Gap in Dishonesty: Evidence from Local Politics in India. American Journal of Political Science, ajps.12733. https://doi.org/10.1111/ajps.12733
[^2]: Croson, R., & Gneezy, U. (2009). Gender Differences in Preferences. Journal of Economic Literature, 47(2), 448–474. https://doi.org/10.1257/jel.47.2.448
[^3]: Bauhr, M., & Charron, N. (2021). Will Women Executives Reduce Corruption? Marginalization and Network Inclusion. Comparative Political Studies, 54(7), 1292–1322. https://doi.org/10.1177/0010414020970218




