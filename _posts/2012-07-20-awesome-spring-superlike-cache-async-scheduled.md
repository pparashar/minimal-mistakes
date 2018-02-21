---
id: 545
title: 'Awesome Spring &#8211; Superlike @Cacheable @Async and @Scheduled'
date: 2012-07-20T09:53:48+00:00
permalink: /awesome-spring-superlike-cache-async-scheduled-2012-07.html
pvc_views:
  - "12390"
dsq_thread_id:
  - "772745500"
categories:
  - Java
tags:
  - Spring
---
**How many times in last 10 years I have to write code to cache things locally or in distributed cache? How many times did I write code to make heavy-lifting Java methods asynchronous?**

Probably numerous! Each time with different style for different product!

&nbsp;

In years such a boilerplate code becomes just that- a boilerplate PAIN. You know what to write how to write as it has long outlived the evolution cycle.  (Remember another Singleton code that you might still write every time? Still? )
  
Cometh the Spring. And what you need to do to make a method call asynchronous? Just tag it with an annotation @Async. That&#8217;s it. Yeah, you read it right- that&#8217;s it! That IS F*KNG awesome stuff. No boilerplate needed, and that&#8217;s how it should have been for long!

This gets the basic stuff ready in seconds and gets rid of writing the Executors, Threads and what now.

Here are few more cases of similar awesomeness I love. Just because they let me focus and get rid of boilerplate.

### 1. @Async &#8211; Asynchronous Processing using underlying ExecutorService

What would you do if you want to make a call to a method Asynchronous? Earlier, you would use an ExecutorService and pass an instance of thread and would end-up creating a small-little framework of your own.

Needed no more. You can simply configure the executor service in Spring application context XML and then use @Async annotation directly on a method to make that method call asynchronous.

Add following to application-context.xml:

<pre>&lt;task:executor id="executor" pool-size="10"/&gt;</pre>

And then use @Async annotation on the method:

<pre>@Async
public void doSomeHeavyLifting(String blah){
 liftingNow(); //Some kool heavy work
}</pre>

More on Async can be found in <a href="http://static.springsource.org/spring/docs/3.0.5.RELEASE/reference/scheduling.html" target="_blank">Spring Documentation here</a>.

### 2. @Cacheable &#8211; A Cache abstraction provided by Spring

You almost in all live projects would have the need to cache some data in-memory; some part of which on local JVM while other on a cache layer like EhCache.

Spring now ships with this amazing Cache feature where you can abstract entire Caching easily and plug it with application super-fast. For example, if you want to cache some objects, say products from an ecommerce website, in a local Hashmap cache  (used only for simplicity sake. don&#8217;t dare to cache our entire catalog to Hashmaps!). You just need to configure the cache in context XML and then mark the method with annotation @Cacheable.

Add this to appContext:

<pre>&lt;bean id="cacheManager" class="org.springframework.cache.support.SimpleCacheManager"&gt;
	&lt;property name="caches"&gt;
	&lt;set&gt;
		&lt;bean class="org.springframework.cache.concurrent.ConcurrentMapCacheFactoryBean" p:name="products"/&gt;
	&lt;/set&gt;
	&lt;/property&gt;
&lt;/bean&gt;</pre>

Now just use Cacheable annotation with the cache name &#8220;products&#8221;. Remember the cache name is important when dealing with keys and eviction.

<pre>@Cacheable(value="products", key="#productCode")
public Product getProductByCode(String productCode) {
 Product product = getFromSomewhere(code);
 return product;
}</pre>

The above  method returns the Product object and this value is Cached. Subsequent invocation of this method would return the cached value. Do note that &#8220;key&#8221; provided in Cacheable annotation plays an important role. If we do not use key in the above example, subsequent invocation of this method would return the same value irrespective of the parameter productCode. So choose key wisely, as always :).

Here is detailed <a title="Spring Cache absraction" href="http://static.springsource.org/spring/docs/current/spring-framework-reference/html/cache.html" target="_blank">documentation on Spring Cache</a>.

&nbsp;

### 3. @Scheduled &#8211; Task Scheduler

Even elementary task scheduling requires good amount of code to be written if not using another framework like Quartz. Which is overwork for non-critical scheduling stuff. Fortunately, Spring now comes with Task Scheduler support.

Add scheduler configuration in app context:

<pre>&lt;task:scheduler id="appScheduler" pool-size="5"/&gt;</pre>

And just add @Scheduled annotation on the method that you want to be invoked periodically:

<pre>@Scheduled(fixedDelay=5000)
public void purge() {
    // purge periodically
}</pre>

The above method would be executed every 5 seconds. The annotation takes parameter, fixedDelay, fixedRate or cron. cron can be used to provide more sophisticated scheduling.

&nbsp;

I just loved these annotation in my project and were really helpful in speeding-up development. Helped you similarly? Put your views in comments section below.

&nbsp;

**And yes, one more time &#8211; Spring is Awesome!!!**

&nbsp;
