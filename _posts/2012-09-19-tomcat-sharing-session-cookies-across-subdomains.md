---
id: 553
title: 'Tomcat &#8211; Sharing of Session Cookies across Subdomains'
date: 2012-09-19T07:09:42+00:00
permalink: /tomcat-sharing-session-cookies-across-subdomains-2012-09.html
pvc_views:
  - "12634"
dsq_thread_id:
  - "849848434"
categories:
  - Asides
  - Technology Insider
  - 'Tips, Tricks &amp; Hacks'
tags:
  - java
  - Tomcat
---
Since I have multiple microsites i.e. subdomains on touchsy.com , I needed a way for users to be logged-in to one subdomain and then access other subdomains without having to login again. I found out that it is fairly easy to achieve it through Tomcat context configuration.

Here is the context configuration:

<pre>&lt;Context sessionCookiePath="/" sessionCookieDomain=".touchsy.com"&gt;</pre>

&nbsp;

A full reference of tomcat configuration can be found here:
  
<a title="Tomcat 7 Configuration" href="http://tomcat.apache.org/tomcat-7.0-doc/config/context.html#Common_Attributes" target="_blank">http://tomcat.apache.org/tomcat-7.0-doc/config/context.html#Common_Attributes</a>
