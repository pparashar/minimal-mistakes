---
title: Scalability Thumb Rules for Programmers (2011)
date: 2011-04-24
categories:
  - Scalability
  - Programming
tags:
  - Scalability
---


1. Avoid Synchronization. Keep it short.
1. Use lock-free data structures and those in java.util.concurrent.atomic
1. Use Non-Blocking I/O java.nio package for high-scalability. Use only for very high throughput applications.
1. Single thread tasks ARE a problem and would not scale on multiple CPUs. Use parallel execution.
1. More memory mean more GC freeze time.
1. SQL DB becomes the bottleneck ultimately. Work around this constraint.
1. Synchronous logging is a seriois issue. Must avoid.
1. No single point of Failure. 
1. Failover mechanism - by load balancers and automatic watchdog/recover scripts.
1. JVM Caches (internal to JVM) should be read only. Use clustered caches instead with replication.
1. Replicate sessions in real time (on the cluster/DB etc.)
1. Keep session objects Serializable. A good practice is to enforce the use of a custom method like the addObjectToSession(String key, Serializable value) method, instead of the default HttpSession.setAttribute (String key, Object value) method when adding session data.
1. Have application level failsafe.
1. Use distributed cache that is scalable. Memcache, Terracota and Jboss cache are good examples.
1. Use NoSQl or Bigtable like distributed databases such as Cassandra, MongoDB, Hypertable, CouchDB or HBase (for Hadoop)
