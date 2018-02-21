---
id: 737
title: Remove .svn files recursively on linux
date: 2013-11-09T00:36:09+00:00
permalink: /remove-svn-files-recursively-on-linux-2013-11.html
pvc_views:
  - "7327"
dsq_thread_id:
  - "2174644094"
categories:
  - Asides
  - 'Tips, Tricks &amp; Hacks'
tags:
  - Linux
---
<pre class="brush:bash">find . -type d -name .svn -exec rm -rf {} \;</pre>

&nbsp;
