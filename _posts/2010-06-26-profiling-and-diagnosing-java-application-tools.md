---
id: 78
title: 'Profiling and Diagnosing Java Application: Tools'
date: 2010-06-26T07:34:56+00:00
permalink: /profiling-and-diagnosing-java-application-tools-2010-06.html
jd_tweet_this:
  - 'yes'
wp_jd_bitly:
  - http://bit.ly/9VirxA
wp_jd_target:
  - http://www.prashantparashar.com/profiling-and-diagnosing-java-application-tools-2010-06.html
jd_wp_twitter:
  - ' Blog post: Profiling and Diagnosing Java Application: Tools http://bit.ly/9VirxA  #in'
  - ' Blog post: Profiling and Diagnosing Java Application: Tools http://bit.ly/9VirxA  #in'
dsq_thread_id:
  - "277386750"
pvc_views:
  - "7776"
categories:
  - Technology Insider
tags:
  - java
  - performance-tuning
---
[<img class="alignleft size-full wp-image-105" style="margin: 5px" src="http://www.prashantparashar.com/wp-content/uploads/2010/06/java.png" alt="java" width="93" height="114" />](http://www.prashantparashar.com/wp-content/uploads/2010/06/java.png)More often than not at some point of development, and hopefully before production :-), the applications needs to be tuned for performance. For a java/j2ee application the one of the first tasks of performance tuning should include profiling application for memory and CPU usage. There are multiple tools and multiple ways to do the profiling of java applications, however, a non-intrusive approach is always the preferred way of profiling- so that the application does not need to be modified itself. I am listing down some basic tools and ways to perform profiling on Java applications:

#### 1. JMAP (Java Memory Map)

The most basic and useful tool is JMAP utility that is provided by Sun Java JDK itself. It provides memory usage, heap statistics, histogram of the objects in memory and their sizes. The command is simple and no brainer, for example, for histogram for a process can be fetched as:

jmap –histo processid

The above command would provide the details of all the objects available on the heap with their sizes. This is useful to diagnose high memory usage issues.

Another popular use is to use jmap command with no option or –dump option. This dumps the entire memory graph of the JVM which can further be analyzed using JHAT utility.

More information on jmap is available <a href="http://java.sun.com/j2se/1.5.0/docs/tooldocs/share/jmap.html" target="_blank">here</a>.

#### 2. JHAT (Java Heap Analysis Tool)

This utility is used to analyze the heap dump produced by the JVM. The heap dump from a JVM can be generated using the jmap or hprof utility. **Heap dump on outg of memory can also be generated by JVM automatically if the JVM is started using the following parameter:**

-XX:+HeapDumpOnOutOfMemoryError

It is in fact almost always advisable to use the above option if the Out Of Memory error is encountered even once in an application.

jhat provides powerful options to analyze the heap dumps. The command is:

jhat [ options ] <heap-dump-file>

More information on the command is available <a href="http://java.sun.com/javase/6/docs/technotes/tools/share/jhat.html" target="_blank">here</a>.

#### 3. JConsole

JConsole is an extremely useful tool, that comes with JDK 5 and above, to analyze runtime statistics of the JVM. This could be used to  analyze both local and remote JVM statistics. The JConsole shows statistics in the form of useful charts as well as data tables. The “jconsole” command is available in jdk/bin directory and does not require any other option.

#### Monitoring/Profiling a Remote Application using JDK Tools

This is a typical scenario when you need to monitor a Java application running on remote machine. The application can be monitored using the following steps:

##### 1. Application Startup Options

Start the java application with following additional options:

-Dcom.sun.management.jmxremote.port=9003
  
-Dcom.sun.management.jmxremote.ssl=false
  
-Dcom.sun.management.jmxremote.authenticate=false
  
-XX:+HeapDumpOnOutOfMemoryError

This would start the application such that it starts listening on port 9003. The other parameters ssl and authenticate must be set to true for secure/production grade systems.

2. Start the jconsole on another machine and enter IP address and port of the remote machine (IP:port , in case of jdk6)

3. This would start the data collection on JConsole and vital statistics such as Threads, Memory, Heap, Garbage Collection can be monitored to identify application issues.

4. In case of out of memory, the JVM would dump the heap which could be analyzed using jhat.

More later…
