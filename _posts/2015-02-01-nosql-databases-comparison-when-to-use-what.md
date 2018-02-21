---
id: 782
title: How to choose a NoSQL Database?
date: 2015-02-01T07:56:13+00:00
permalink: /nosql-databases-comparison-when-to-use-what-2015-02.html
tumblr_post_id:
  - "109753493168"
pvc_views:
  - "10071"
dsq_thread_id:
  - "3474610694"
medium_post:
  - 'O:11:"Medium_Post":11:{s:16:"author_image_url";s:69:"https://cdn-images-1.medium.com/fit/c/200/200/0*w9R9GHEgUrfaFwnJ.jpeg";s:10:"author_url";s:27:"https://medium.com/@sucoder";s:11:"byline_name";N;s:12:"byline_email";N;s:10:"cross_link";s:3:"yes";s:2:"id";s:12:"f414a774eca7";s:21:"follower_notification";s:3:"yes";s:7:"license";s:19:"all-rights-reserved";s:14:"publication_id";s:2:"-1";s:6:"status";s:6:"public";s:3:"url";s:71:"https://medium.com/@sucoder/how-to-choose-a-nosql-database-f414a774eca7";}'
categories:
  - Featured
  - 'Scalability &amp; HA'
tags:
  - Comparison
  - Databases
  - NoSQL
  - Scalability
---
[Cross-posted on <a href="http://www.nextbigwhat.com/how-to-choose-nosql-database-297/" target="_blank">NextBigWhat.com</a>]

NoSQL databases are now part of web-scale architecture. The question is when to use what? Below, I try to compare the NoSQL data stores that I have worked with. Hopefully, it would be useful for programmers exploring and deciding the technology for their web-scale application.

### When to use NoSQL

Before deciding on to use NoSQL instead of a SQL technology, you should ask yourself following questions about your use case (includes <a title="ACID database property" href="http://java.dzone.com/articles/beginners-guide-acid-and" target="_blank">ACID</a> test of your application) :

  1. Transactions vs No transactions (Do you need atomicity?)
  
    [Most NoSQL databases don&#8217;t support transactions]
  2. Consistent or eventual consistent (Are you okay with eventual consistency?)
  
    [Most support configurable consistency mode. You should test your scale with the consistency mode your application requires. For example, your performance test holds no good when done on &#8220;eventual consistency&#8221; mode and you decide to use hard consistency for your application.]
  3. Vertical vs horizontal scaling (what&#8217;s your scale? your use case need infinite scale or needs are finite?)
  
    [This sometimes boils down to what stage of business are you in. Don&#8217;t over-engineer of you are an early stage startup and growing < 5x a month. Postpone & focus on biz growth]
  4. Availability (No downtime? Hot failover?)
  
    [Some NoSQL DBs support hot failovers, some not. More below.]
  5. Do you really need a NoSQL DB. Why RDBMS doesn&#8217;t work for you?
  
    [Don&#8217;t use NoSQL just for the heck of it]

So, once you have decided to go for a NoSQL Data store. Next question should be key-value or document-oriented.

### Key-Value vs Document-oriented

**Key-value stores:** If you have clear data structure defined such that all the data would have exactly one key, go for a key-value store. It&#8217;s like you have a big Hashtable, and people mostly use it for Cache stores or clearly key based data. However, things start going a little nasty when you need query the same data on basis of multiple keys!
  
Some key value stores are: <a title="Memcached" href="http://memcached.org/" target="_blank">Memcache</a>, <a title="Redis" href="http://redis.io/" target="_blank">Redis</a>, <a title="Aerospike" href="http://www.aerospike.com/" target="_blank">Aerospike</a>.

Two important things about designing your data model around key-value store are:

  1. You need to know all use cases in advance and you could not change the query-able fields in your data without a redesign.
  2. Remember, if you are going to maintain multiple keys around same data in a key-value store, updates to multiple tables/buckets/collection/whatever are NOT atomic. You need to deal with this yourself.

&nbsp;

**Document-oriented:** If you are just moving away from RDBMS and want to keep your data in as object way and as close to table-like structure as possible, document-structure is the way to go! Particularly useful when you are creating an app and don&#8217;t want to deal with RDBMS table design early-on (in prototyping stage) and your schema could change drastically over time. However note:

  1. Secondary indexes may not perform as well.
  2. Transactions are not available.

Popular document-oriented databases are: <a title="MongoDB" href="http://www.mongodb.org/" target="_blank">MongoDB</a>, <a title="Couchbase" href="http://www.couchbase.com/" target="_blank">Couchbase</a>.

&nbsp;

### In-memory vs disk persistence (Cache or data-store) ?

Another key concern while deciding data stores is whether you are using it as data store of your application or you are using it as a cache over your data store to scale for your traffic needs.

Once you have decided the kind of use-case you have, here are some of the popular NoSQL stores you could use:

### Comparing Key-value NoSQL databases

**Memcache:**

  * In-memory cache
  * No persistence
  * TTL supported
  * client-side clustering only (client stores value at multiple nodes). Horizontally scalable through client.
  * Not good for large-size values/documents

**Redis:**

  * In-memory cache
  * Disk supported &#8211; backup and rebuild from disk
  * TTL supported
  * Super-fast
  * Data structure support in addition to key-value
  * Clustering support  not mature enough yet. Vertically scalable.
  * Horizontal scaling could be tricky.

**Aerospike:**

  * Both in-memory & on-disk
  * Extremely fast (could support >1 Million TPS on a single node)
  * Horizontally scalable. Server side clustering. Sharded & replicated data
  * Automatic failovers
  * Supports Secondary indexes.
  * CAS, TTL support
  * Enterprise class

### When to use what? Memcache vs Redis vs Aerospike

If I am an early stage startup, I would rather prefer to go with Redis and avoid nuances of maintaining a cluster etc. If I have scaled above half a million TPS (transactions per second) where I need to scale horizontally I would go for Aerospike. I would use memcache (memcached) only when I am going really mean and want to even offload maintaining the servers &#8211; in which case I would go for hosted version of Memcached which is <a title="Amazon Elasticache" href="http://aws.amazon.com/elasticache/" target="_blank">Amazon Elasticache</a>.

<a title="Aerospike snapdeal case study" href="http://www.aerospike.com/wp-content/uploads/2014/02/snapdeal_casestudy.pdf" target="_blank">Here&#8217;s a case study of Aerospike</a>.

###  Comparing document-oriented NoSQL databases

**MongoDB:**

  * Fast
  * Mature & stable &#8211; feature rich
  * Supports failovers
  * Horizontally scalable reads &#8211; read from replica/secondary
  * Writes not scalable horizontally unless you use mongo shards
  * Supports advanced querying
  * Supports multiple secondary indexes
  * Shards architecture becomes tricky, not scalable beyond a point where you need secondary indexes. Elementary shard deployment need 9 nodes at minimum.
  * Document-level locks are a problem if you have a very high write-rate

&nbsp;

**Couchbase Server:**

  * Fast
  * Sharded cluster instead of master-slave of mongodb
  * Hot failover support
  * Horizontally scalable
  * Supports secondary indexes through views
  * Learning curve bigger than mongoDB
  * Claims to be faster

&nbsp;

### When to use what? MongoDB vs Couchbase

For most de-facto use cases, I would go for mongo unless my write-rate is extremely high (I would think again only when my writes are > 10% and I am doing more than few thousand transactions a second). Fast prototyping, schema-less design, on-the-fly indexes etc makes it a ideal choice for early stage traffic.

I would consider Couchbase only when I have scaled beyond a point where write-locks are becoming a problem and I do have secondary indexes and I need extremely high availability (* more on couchbase in coming posts).

&nbsp;

Of course, there are many more databases knocking the doors like, VoltDB, FoundationDB, GraphDB etc, would try to cover them on this blog in later posts. C**olumnar databases** &#8211; where Cassandra and Hbase are leading the stack- are used for certain use cases that would probably be part of some future posts. If you have thoughts, comments, do share here and I would try to incorporate in my posts.

&nbsp;

**We are hiring! Want to work on exciting technology at scale? **Email your brief CV to prashant.parashar /at snapdeal

&nbsp;
