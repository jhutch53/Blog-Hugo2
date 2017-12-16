---
title: Histograms
author: ~
date: '2017-12-16'
slug: histograms
categories: []
tags: []
comments: yes
draft: no
image: ''
menu: ''
share: yes
---

##Extracting the Data-----------------------

library(Lahman)
library(sqldf)
library(ggplot2)

query<-"SELECT weight FROM Master"
result<-sqldf(query)

##Visualizing the Data---------------------

ggplot()+
  geom_histogram(data=result,aes(x=weight),color="blue",fill="white",bins=60)+
  ggtitle("Distribution of Baseball Player Bodyweight")+
  xlab("Weight of player")+
  ylab("Number of players")