---
id: 668
title: Track Multiple Domains and Use Multiple Google Analytics Accounts
date: 2012-12-26T13:14:53+00:00
permalink: /track-multiple-domains-and-use-multiple-google-analytics-accounts-2012-12.html
pvc_views:
  - "12530"
dsq_thread_id:
  - "992866943"
categories:
  - Internet Technology
  - Online Marketing
  - 'Tips, Tricks &amp; Hacks'
tags:
  - Analytics
---
Tracking multiple domains on the same google Analytics is not a big deal but is a little tricky. If you haven&#8217;t checked all the boxes, you might not get it up and running. Here are the basic steps to track multiple websites.

  * Have the site up with default profile using basic GA setup.
  * Now make sure in Google Analytics property setting, you have &#8220;Multiple top-level domains of touchsy&#8221; checkbox set to ON. You can find this setting in &#8220;tracking info&#8221;
  * Now add the following code to your website:

<pre>_gaq.push(['_setAccount', 'UA-XXXXXXXX-X']);
  _gaq.push(['_setDomainName', document.domain]);
  _gaq.push(['_setAllowLinker', true]);
  _gaq.push(['_trackPageview']);</pre>

  * Create a new profile in your GA property
  * On the filters, click on &#8220;Create New Filter&#8221;->Custom Filter->Advanced
  * On FieldA->ExtractA, Select Hostname and Add a value **(.*)**  Remember the brackets.
  * On FieldB->ExtractB, Select Request URI and Add value (.*)  Remember the brackets.
  * On Output To->Constructor, select Request URI and put value $A1$B1
  * Field A Required -> No, Field B Required  -> No, Override Output-> yes
  * Save (refer Image)

<div>
  <a href="http://www.prashantparashar.com/wp-content/uploads/2012/12/ga_crossdomain_profile.png"><img class="aligncenter size-full wp-image-669" src="http://www.prashantparashar.com/wp-content/uploads/2012/12/ga_crossdomain_profile.png" alt="" width="732" height="605" srcset="http://www.prashantparashar.com/wp-content/uploads/2012/12/ga_crossdomain_profile.png 732w, http://www.prashantparashar.com/wp-content/uploads/2012/12/ga_crossdomain_profile-300x247.png 300w" sizes="(max-width: 732px) 100vw, 732px" /></a>
</div>

You would now see complete URLs for the visited pages in your GA report.

&nbsp;

## Multiple Google Analytics Accounts on single website

Track a website on multiple google analytics accounts:

1.  Do not include ga.js script multiple times. Include just once.

2. Include the following code on your website

<pre>_gaq.push(['_setAccount', 'UA-XXXXXXXX-X']);
  _gaq.push(['_setDomainName', document.domain]);
  _gaq.push(['_setAllowLinker', true]);
  _gaq.push(['_trackPageview']);

  // Second tracker 
  _gaq.push(['secondAcc._setAccount','UA-YYYYYYYY-Y']);
  _gaq.push(['secondAcc._setDomainName', document.domain]);
  _gaq.push(['secondAcc._setAllowLinker', true]);
  _gaq.push(['secondAcc._trackPageview']);</pre>
