---
layout: post
title: "Azure Data Lake Analytics"
microblog: false
audio: 
date: 2018-02-12 17:02:58 +0100
guid: /2018/02/12/azure-data-lake.html
---
Found #bug with executing [USQL](https://msdn.microsoft.com/en-us/azure/data-lake-analytics/u-sql/u-sql-language-reference) in a Visual Studio Solution. If you have multiple projects, you need to set the project with the script you want to run as the [Startup project](https://msdn.microsoft.com/en-us/library/a1awth7y.aspx), otherwise VS runs the last USQL script you opened. 

[`VS 2017 V15.5.6`](https://aka.ms/upgradevs2017). 
