---
id: 136
title: 'XPath Evaluation in Java : Xalan XPath API vs Apache XmlBean'
date: 2010-09-22T17:12:41+00:00
permalink: /xpath-evaluation-in-java-xalan-xpath-api-vs-apache-xmlbean-2010-09.html
dsq_thread_id:
  - "280242176"
pvc_views:
  - "8864"
categories:
  - 'Tips, Tricks &amp; Hacks'
tags:
  - java
  - XML
  - XPath
---
## How to evaluate Xpath value for an XML in Java?

Well there are couple of popular ways to evaluate XPath in Java. If you are using JDK 1.4 version than Xalan&#8217;s XPathAPI class is one of the most popular ways to evaluate XPath. Using XPathAPI is simple, use the following static method from XPathAPI class:

<p style="padding-left: 30px;">
  XPathAPI.selectNodeList(Document d,  String XPath)
</p>

which returns a NodelList.

Another way of XPath evaluation is using Apache XmlBean project. Though Apache XmlBean is used for XML Binding, it can safely be used for XPath evaluation as well.  A simple exmaple of evaluating XPath using XmlBean is as below:
  
<span></p> 

<p style="padding-left: 30px;">
  XmlObject obj = XmlObject.Factory.<em>parse</em>(InputStream);<br /> <span>XmlObject x[] = obj.selectPath(xPath</span><span>);</span>
</p>

<p>
  Another example of using XmlBean to evaluate XPath using cursor is :
</p>

<p style="padding-left: 30px;">
  XmlObject obj = XmlObject.Factory.<em>parse</em>(InputStream);<br /> <span>XmlCursor xcur = obj.newCursor();<br /> <span>xcur.toFirstChild();<br /> xcur.selectPath(</span><span style="color: #2a00ff;"><span style="color: #2a00ff;">xPath</span></span><span>); <br /> <strong><span style="color: #7f0055;"><span style="color: #7f0055;">if</span></span></strong><span>(xcur.hasNextSelection()){<br />             xcur.toNextSelection();<br />             String s = xcur.getTextValue();<br />            System.</span><em><span style="color: #0000c0;"><span style="color: #0000c0;">out</span></span></em><span >.println(s);<br /> }<br /> xcur.dispose();</span></span></span>
</p>

<p>
   
</p>

<p>
  </span>
</p>

<h2>
  XPathAPI vs XmlBean
</h2>

<div>
  Well this is not a generic comparison as one of them, XmlBean, definitely does a lot more than evaluating XPath and we have just found a way (probably) of using it to evaluate XPath. This comparison is limited to evaluating XPath.
</div>

<p>
  So which one of the methods should one use if all we want to do is evaluate XPath. I tried to do some performance benchmarking using a simple example with no complexities involed. For 25000 transactions, where each transaction included both parsing and XPath evaluation, the results are:
</p>

<ul>
  <li>
    Both APIs take almost the same amount of time in parse() so we can neglect the parse time as it&#8217;s not the XPathAPI that is doing the parsing for it. XmlBean parsing however cannot be externalized.
  </li>
  <li>
    The XPath evaluation time: The XPath evaluation time for XmlBean is drastically lower than that of XPathUtil. It varis from being 1/6th to 1/3rd of the time taken by XPathUtil.
  </li>
</ul>

<p>
  The test however took simple XML Paths to evaluate that returns single & multiple nodes.
</p>

<p>
  While considering an API to use for an application, there are many more factors to consider. If you already have XmlBean in your application, use it for XPath evaluation.
</p>
