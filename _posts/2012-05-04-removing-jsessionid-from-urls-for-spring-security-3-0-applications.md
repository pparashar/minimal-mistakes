---
id: 490
title: Removing JSESSIONID from URLs for Spring Security 3.0+ applications
date: 2012-05-04T11:28:29+00:00
permalink: /removing-jsessionid-from-urls-for-spring-security-3-0-applications-2012-05.html
pvc_views:
  - "17859"
dsq_thread_id:
  - "675193184"
categories:
  - Asides
  - Java
  - 'Tips, Tricks &amp; Hacks'
tags:
  - Spring
---
jsessionid in URLs look annoying, more so in search results. Disabling them from URL is just a configuration in your spring-security.xml file for Spring version 3.0 + : use the disable-url-rewriting=&#8221;true&#8221; in the security namespace for http tag. the http tag becomes:

<pre class="brush: xml; gutter: false; first-line: 1; highlight: [1]">&lt;security:http auto-config="false" <strong>disable-url-rewriting="true"</strong>&gt;</pre>

If you are not using http cofiguration and using FilterChainProxy, [this article](http://randomcoder.org/articles/jsessionid-considered-harmful "removing jsessionid for Spring application") can help.
