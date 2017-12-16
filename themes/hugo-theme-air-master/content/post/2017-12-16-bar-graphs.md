---
title: Bar Graphs
author: ~
date: '2017-12-16'
slug: bar-graphs
categories: []
tags: []
comments: yes
draft: no
image: ''
menu: ''
share: yes
---

##Extracting the Data--------------------

library(Lahman)
library(sqldf)
library(ggplot2)

query<-"SELECT name,HR FROM Teams WHERE yearID=1980 ORDER BY HR "
result<-sqldf(query)

result$name<-factor(result$name,levels=result$name)

##Visualizing the Data--------------------

ggplot()+
  geom_bar(data=result,aes(x=name,y=HR),stat='identity')+
  coord_flip()+
  ggtitle("1980 Team Homerun Totals")+
  xlab("Team Name")+
  ylab("Homeruns")