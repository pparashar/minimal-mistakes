---
id: 629
title: 'JQuery Mobile App: Caching Pages in local Storage Seamlessly'
date: 2012-11-29T10:19:30+00:00
permalink: /jquery-mobile-app-caching-pages-in-local-storage-seamlessly-2012-11.html
pvc_views:
  - "13040"
dsq_thread_id:
  - "949216410"
tumblr_post_id:
  - "157403312848"
medium_post:
  - 'O:11:"Medium_Post":11:{s:16:"author_image_url";s:69:"https://cdn-images-1.medium.com/fit/c/200/200/0*w9R9GHEgUrfaFwnJ.jpeg";s:10:"author_url";s:27:"https://medium.com/@sucoder";s:11:"byline_name";N;s:12:"byline_email";N;s:10:"cross_link";s:3:"yes";s:2:"id";s:12:"370aa30dd8f6";s:21:"follower_notification";s:2:"no";s:7:"license";s:19:"all-rights-reserved";s:14:"publication_id";s:2:"-1";s:6:"status";s:6:"public";s:3:"url";s:100:"https://medium.com/@sucoder/jquery-mobile-app-caching-pages-in-local-storage-seamlessly-370aa30dd8f6";}'
categories:
  - Featured
  - Internet Technology
  - Technology Insider
tags:
  - JQuery
  - Mobile Tech
---
<div style="max-width: 310px" class="wp-caption alignright">
  <a href="http://commons.wikipedia.org/wiki/File:Jquery-mobile-logo.png" target="_blank"><img class="zemanta-img-inserted zemanta-img-configured" src="http://www.prashantparashar.com/wp-content/uploads/2017/02/300px-jquery-mobile-logo.png" alt="English: jQuery Mobile logo." width="300" height="82" /></a>
  
  <p class="wp-caption-text">
    jQuery Mobile. (Photo credit: Wikipedia)
  </p>
</div>

While JQuery Mobile provides a way to cache and prefetch pages and store them in DOM, it does not provide a seamless mechanism to persist these pages in local storage. Local Storage a mechanism introduced in HTML5 to store data locally in the browser and remains persisted between browser sessions.

The mechanism below has been tested with Jquery Mobile 1.2 . The process works as below:

  1. Intercept &#8220;_pagebeforechange_&#8221; event to find out if the page is already in DOM or cache. 
      1. If not in DOM or Cache &#8211; do nothing- continue as usual
      2. If in cache but not in DOM, put the data in DOM so that the loadPage automatically finds it.
  2. Now Intercept &#8220;_pageload_&#8221; event to populate the localStorage cache. 
      1. The example only cache the pages (pages with data-role=&#8221;page&#8221;) and with attribute &#8220;_data-local-storage=true_&#8220;

Here&#8217;s the code:

<pre class="brush: javascript; gutter: true; first-line: 1">$(document).bind( "pagebeforechange", function( e, data ) {

	if ( typeof data.toPage === "string" ) {
		var pageId = getPageId(data.toPage);

		if(localStorage.getItem(pageId) == null) {

		} else {
			if($("#" + pageId) == null || $("#" + pageId).length == 0) {
				var html =  localStorage.getItem(pageId);
				var all = $( "&lt;div&gt;&lt;/div&gt;" );
				all.get( 0 ).innerHTML = html;
				page = all.find( ":jqmData(role='page'), :jqmData(role='dialog')" ).first();
				var u = data.toPage;
				if($.mobile.path.isAbsoluteUrl(u)) {
					u = u.substring($.mobile.path.parseUrl(u).domain.length);
				}
				page.attr("data-url", u);
				$('body').append(page);
			}
		}
	}
});		

		$( document ).bind( "pageload", function( event, data ){

			console.log(data.xhr.responseText);

			var pageId = getPageId(data.dataUrl);

			if(data.xhr.responseText != null) {
				var all = $( "&lt;div&gt;&lt;/div&gt;" );
				all.get( 0 ).innerHTML = data.xhr.responseText;
				var page = all.find( ":jqmData(role='page'), :jqmData(role='dialog')" ).first();

				if(page.jqmData("local-cache") === true) {
					localStorage.setItem(pageId, data.xhr.responseText);
				}
			}

		});</pre>

<pre></pre>

<div class="zemanta-pixie" style="margin-top: 10px;height: 15px">
  <a class="zemanta-pixie-a" title="Enhanced by Zemanta" href="http://www.zemanta.com/?px"><img class="zemanta-pixie-img" style="border: none;float: right" src="http://img.zemanta.com/zemified_e.png?x-id=0b68f9ee-1387-4098-b73d-9d14458c4bd2" alt="Enhanced by Zemanta" /></a>
</div>
