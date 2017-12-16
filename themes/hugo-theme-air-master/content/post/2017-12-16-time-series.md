---
title: Time Series
author: ~
date: '2017-12-16'
slug: time-series
categories: []
tags: []
comments: yes
draft: no
image: ''
menu: ''
share: yes
---

##Extracting the Data-------------------

library(Lahman)
library(sqldf)
library(ggplot2)

query<-"SELECT yearID,HR FROM Batting WHERE playerID='ruthba01'"
result<-sqldf(query)

##Visualizing the Data------------------

ggplot()+
  geom_point(data=result,aes(x=yearID,y=HR),size=1/2)+
  geom_line(data=result,aes(x=yearID,y=HR))+
  ggtitle("Babe Ruth's Homeruns by Year")+
  xlab("Year")+
  ylab("Number of Homeruns")