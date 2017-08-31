---
layout: post
title: Luoo Stats - 落网数据分析
author: Author Heming
---
The post is a simple analysis of the music tags in [luoo.net](luoo.net), which, as the first step of the luoo analysis.

First of all, the data crawler is written in Python, which imports libraries like bs4 and request to obtain and parse data. Then store data in a sql database(not necessary, as data size is only a few Mb).

There are 943 music volumes in Luoo now, and most of them have multiple music tags. The tag plot is drawn by seaborn as shown below:

![Alt](../images/luoo_1.png)




