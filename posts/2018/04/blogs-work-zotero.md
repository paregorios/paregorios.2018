<!--
.. title: Blogs that work with Zotero
.. slug: blogs-work-zotero
.. date: 2018-04-26 13:31:57 UTC-05:00
.. tags: zotero, nikola, wordpress, metadata, html, microblogging
.. category: 
.. link: 
.. description: The first part of an investigation into getting my blog to play nicely with Zotero.
.. type: text
-->

I noticed that posts on my blog don't capture smoothly into [_Zotero_](https://zotero.org) (i.e., I have to edit the records in _Zotero_ after I capture them). So, I want to fix my theme so this is no longer a problem and then contribute that modified theme back to the [_Nikola_](https://getnikola.com) community.

Step one (this post): look at some blogs and figure out which ones work well with _Zotero_ and figure out why.<!-- TEASER_END -->

## Does _Zotero_ recognize a blog post as a blog post?

If [the _Zotero_ Connector plugin](https://www.zotero.org/download/) in the browser knows it is dealing with a blog post, it will display a blog post icon in the browser toolbar. But on my blog posts, _Zotero_ shows me the more generic "web page" icon:

<img alt="Screen capture showing part of the Firefox browser's toolbar. A mouse pointer icon is displayed, hovering over the Zotero button in the browser toolbar. The Zotero button displays an icon connoting a 'web page': a rectangle with a light blue border and internal shading. A help kite reads 'Save to Zotero (Embedded Metadata).'" src="/images/blog_zotero/zotero_generic.png"/>

When I capture a reference to _Zotero_ from such a post, I do indeed get a record that's typed as a "web page":

<img alt="Screen capture showing the 'info' portion of the Zotero user interface. It contains data translated from a page on the paregorios.org blog. The 'Item Type' field reads 'Web Page'." src="/images/blog_zotero/zotero_record_mine.png"/>

I see this behavior on [Sean Gillies' blog](https://sgillies.net/) too, which also looks to be running the default [Nikola "Bootstrap 3" theme](https://themes.getnikola.com/v8/bootstrap3/).

But on [Ruth Kitchin Tillman's blog](http://ruthtillman.com/blog/), we see that _Zotero_ has figured out it's looking at a blog post:

<img alt="Screen capture showing part of the Firefox browser's toolbar. A mouse pointer icon is displayed, hovering over the _Zotero_ button in the browser toolbar. The Zotero button displays an icon connoting a 'blog post': a rectangle with a grey border, within which a horizontal band of orange and black appears above a few horizontal lines of grey. A help kite reads 'Save to Zotero (Embedded Metadata).'" src="/images/blog_zotero/zotero_post.png"/>

And, as we would expect, the resulting _Zotero_ record is auto-classified as a "blog post":

<img alt="Screen capture showing the 'info' portion of the Zotero user interface. It contains data translated from a page on the ruthtillman.com blog. The 'Item Type' field reads 'Blog Post'." src="/images/blog_zotero/zotero_record_rkt.png"/>

## What's different? 

My first thought, since the _Zotero_ browser plugin says it's using "embedded metadata" in both cases, is to have a look at [the "meta" elements](https://en.wikipedia.org/wiki/Meta_element) in the HTML "head" in each of the posts. Leaving aside technical metadata about character set, view ports and so forth, the following differences can be noted:

 - Both sites are embedding ```meta@property``` terms from [the Open Graph Protocol](http://ogp.me/) namespace (http://ogp.me/ns/#), including its "article" object (http://ogp.me/ns/article#).
   - The only difference I see with Open Graph is that ruthtillman.com uses ```property="article.section"``` whereas paregorios.org uses ```property="article.tag"```.
 - Ruthtillman.com also embeds ```meta@name``` terms conforming to the "Summary" [Twitter Cards](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/overview/abouts-cards.html) convention (creator, description, image, site, title). Paregorios.org doesn't make use of these.
 - Paregorios.org embeds un-namespaced ```meta@name terms``` for "author" and "description," but ruthtillman.com doesn't.

So, unless there's some heuristic encoded into [the _Zotero_ translator](https://www.zotero.org/support/translators) that comes to a different conclusion about these two sets of ```meta``` tags, something else must be at play. Either there's a different kind of metadata that it finds elsewhere in the posts on ruthtillman.com that it interprets as indicative of a blog post, or it notices that it's looking at WordPress output and infers "blog" from that. 

## Now what?

In any case, I guess it's time to go snooping around in [the _Zotero_ code](https://github.com/zotero/translators/blob/master/Embedded%20Metadata.js) to see what we can find.

Stay tuned to [my _Zotero_ tag](/categories/zotero/) for updates ...
