---
id: 530
title: 'Debian/Ubuntu Linux: Change Timezone to IST'
date: 2012-06-20T08:46:39+00:00
permalink: /debianubuntu-linux-change-timezone-to-india-2012-06.html
pvc_views:
  - "11350"
dsq_thread_id:
  - "733391450"
categories:
  - Asides
  - 'Tips, Tricks &amp; Hacks'
tags:
  - Unix
---
Change timezone of Debian/Ubuntu machine to Asia/Kolkata or any other timezone

<pre>mv /etc/localtime /etc/localtime.old
ln -sf /usr/share/zoneinfo/Asia/Kolkata /etc/localtime
</pre>

&nbsp;
