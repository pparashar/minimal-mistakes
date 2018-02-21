---
id: 787
title: JVM Off-heap Caching Libraries
date: 2015-02-16T07:07:53+00:00
permalink: /jvm-off-heap-caching-libraries-benchmarking-2015-02.html
tumblr_post_id:
  - "111006829563"
pvc_views:
  - "7104"
dsq_thread_id:
  - "3519759146"
categories:
  - Asides
tags:
  - java
  - performance-tuning
---
Here&#8217;s another gem from <a title="Snapdeal Engineering Blog" href="http://engineering.snapdeal.com/" target="_blank">Snapdeal Engineering blog</a> : analysis and comparison of different off-heap caching solutions and performs benchmarking for their use-case. The Blog post describes benchmarking & analysis of **concurrent hashmap (on-heap) vs EhCache vs MapDb vs Hazlecast vs Apache DirectMemory vs  HugeCollections libraries**.

The link -> <a title="Analysis of off heap caching libraries" href="http://engineering.snapdeal.com/2014/08/analysis-of-various-jvm-off-heap.html" target="_blank">http://engineering.snapdeal.com/2014/08/analysis-of-various-jvm-off-heap.html</a> and a snapshot from original post:

[<img class="alignleft size-full wp-image-788" src="http://www.prashantparashar.com/wp-content/uploads/2015/02/off-heap-chart-get.png" alt="Off heap JVM caching" width="613" height="373" srcset="http://www.prashantparashar.com/wp-content/uploads/2015/02/off-heap-chart-get.png 613w, http://www.prashantparashar.com/wp-content/uploads/2015/02/off-heap-chart-get-300x183.png 300w" sizes="(max-width: 613px) 100vw, 613px" />](http://engineering.snapdeal.com/2014/08/analysis-of-various-jvm-off-heap.html)
