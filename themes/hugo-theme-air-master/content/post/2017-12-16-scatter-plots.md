---
title: Scatter Plots
author: ~
date: '2017-12-16'
slug: scatter-plots
categories: []
tags: []
comments: yes
draft: no
image: ''
menu: ''
share: yes
---

library(Lahman)
library(sqldf)
library(ggplot2)

##Extracting the Data--------------------------------

query<-"SELECT playerID,sum(HR),sum(SO)
FROM Batting 
GROUP BY playerID
HAVING sum(HR)>400"
sqldf(query)

query<-"SELECT playerID,sum(HR) AS CareerHR,sum(SO) AS CareerSO
FROM Batting
GROUP BY playerID
HAVING sum(HR)>400"
result<-sqldf(query)

##Plotting the Data-------------------------------

ggplot()+
  geom_point(data=result,aes(x=CareerSO,y=CareerHR),size=3)+
  ggtitle("Career Strikeouts and Homeruns - The Best")+
  xlab("Career Strikeouts")+
  ylab("Career Homeruns")