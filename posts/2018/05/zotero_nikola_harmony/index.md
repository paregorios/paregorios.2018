<!--
.. title: Zotero-Nikola Harmony (One Simple Trick)
.. slug: zotero_nikola_harmony
.. date: 2018-05-08 07:43:15 UTC-05:00
.. tags: zotero, nikola, metadata, html, microblogging, rdf, prism, javascript
.. category: 
.. link: 
.. description: How I made Zotero recognize blog posts created with Nikola as blog posts instead of web pages.
.. type: text
-->

<abbr title="Too long; didn't read">TL;DR</abbr>: Modify the post-related templates in your active theme to add the following to the ```<head>``` element in each post:

```html
<meta property="zotero:itemType" content="blogPost">
```
Also, make sure to define the ```zotero``` namespace prefix for this property in the ```prefix``` attribute on the ```<html>``` element. The proper value is ```http://www.zotero.org/namespaces/export# ```.<!-- TEASER_END -->

## Explanation and Example

The surest way I've found to make [the <span class="bibtitle">Firefox</span> plugin for <span class="bibtitle">Zotero Standalone</span>](https://www.zotero.org/download/) recognize my blog posts as blog posts (rather than just as generic web pages) is to insert a ```<meta>``` element in the <abbr title="HyperText Markup Language">HTML</abbr> ```<head>``` for each post. The ```<meta>``` element must make use of a ```property``` attribute containing the name of the <span class="bibtitle">Zotero</span> field we want to specify (in this case, ```itemType```). You won't find ```@property``` in <a title="HTML 5.2: W3C Recommendation, 14 December 2017" href="https://www.w3.org/TR/html/">the HTML5 specification</a>; it's defined by <a href="https://www.w3.org/TR/html-rdfa/" title="HTML+RDFa 1.1 - Second Edition: Support for RDFa in HTML4 and HTML5: W3C Recommendation 17 March 2015">RDFa</a>. You also need a ```content``` attribute on the ```<meta>``` element to carry the value <span class="bibtitle">Zotero</span> expects, <abbr title="id est: Latin for 'that is'">i.e.</abbr>, ```blogPost```. Thus:

```html
<!DOCTYPE html>
<html prefix="og: http://ogp.me/ns# 
  article: http://ogp.me/ns/article# 
  zotero: http://www.zotero.org/namespaces/export# " 
  lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>Zotero Item Keys (Again) | paregorios.org</title>
    <link href="../../../../assets/css/bootstrap.min.css" rel="stylesheet" type="text/css">
    <link href="../../../../assets/css/baguetteBox.min.css" rel="stylesheet" type="text/css">
    <link href="../../../../assets/css/rst.css" rel="stylesheet" type="text/css">
    <link href="../../../../assets/css/code.css" rel="stylesheet" type="text/css">
    <link href="../../../../assets/css/theme.css" rel="stylesheet" type="text/css">
    <link href="../../../../assets/css/custom.css" rel="stylesheet" type="text/css">
    <meta name="theme-color" content="#5670d4">
    <meta name="generator" content="Nikola (getnikola.com)">
    <link rel="alternate" type="application/rss+xml" title="RSS" href="../../../../rss.xml">
    <link rel="canonical" href="https://paregorios.org/posts/2018/05/zotero_item_keys/">
    <!--[if lt IE 9]><script src="../../../../assets/js/html5.js"></script><![endif]-->
    <meta name="author" content="Tom Elliott">
    <link rel="prev" href="../../04/bervus/" title="A Roman Tombstone from Heidelberg" type="text/html">
    <meta property="og:site_name" content="paregorios.org">
    <meta property="og:title" content="Zotero Item Keys (Again)">
    <meta property="og:url" content="https://paregorios.org/posts/2018/05/zotero_item_keys/">
    <meta property="og:description" content="Back in 2012, I posted about Zotero item keys and my attempts ...">
    <meta property="og:type" content="article">
    <meta property="article:published_time" content="2018-05-01T05:13:26-05:00">
    <meta property="article:tag" content="bibliography">
    <meta property="article:tag" content="zotero">
    <meta property="zotero:itemType" content="blogPost">
  </head>
```

## How to implement in <span class="bibtitle">Nikola</span>

[The <span class="bibtitle">Nikola</span> static site generator](https://getnikola.com), which I use for <a href="https://paregorios.org" class="bibtitle">paregorios.org</a>, uses <a href="https://en.wikipedia.org/wiki/Web_template_system">a templating system</a> to generate the HTML pages that are then deployed to the server (I author in <a href="https://daringfireball.net/projects/markdown/" class="bibtitle">Markdown</a>; [<span class="bibtitle">Nikola</span> supports a variety of authoring formats](https://getnikola.com/handbook.html#supported-input-formats)). So, I needed to modify the template(s) used for the individual HTML files that go in the "posts" section of the site so that they include the magic <span class="bibtitle">Zotero</span> metadata described above. <a href="https://getnikola.com/handbook.html" class="bibtitle">The Nikola Handbook</a>, as currently written, makes it sound like you have to create your own custom theme (a collection of templates and [<abbr title="Cascading Style Sheets">CSS</abbr>](https://en.wikipedia.org/wiki/Cascading_Style_Sheets) files) if you want to modify template behavior, but that it is not the case. You can selectively override templates from whatever stock or third-party theme you have installed and configured. 

I use [the "bootstrap4" theme that ships with <span class="bibtitle">Nikola</span> 8](https://github.com/getnikola/nikola/tree/master/nikola/data/themes/bootstrap4), rather than the default "bootblog4" (one changes this via the ```THEME``` variable in ```conf.py```), so I went poking around in the code to find out how and where the ```<html>```, ```<head>```, and ```<meta>``` elements get generated. I discovered that -- in the boostrap4 theme -- there are three templates involved: ```post.tmpl```, ```post_helper.tmpl```, and ```base_helper.tmpl```. Nikola makes it easy to get copies of those templates for the purpose of overriding. I entered the following commands and the command line:

```bash
nikola theme -c post.tmpl
nikola theme -c post_helper.tmpl
nikola theme -c base.tmpl
```

<span class="bibtitle">Nikola</span> created a ```templates``` subdirectory for me and copied the three files into it. Any changes I make in those copies are reflected in output the next time I run ```nikola build```.

To get the behavior I wanted I had to do the following:

1. Modify ```templates/base_helper.tmpl``` to define the ```zotero``` namespace prefix,
2. Modify ```templates/post_helper.tmpl``` to write the <span class="bibtitle">Zotero</span>-related ```<meta>``` element I want, and 
3. Modify ```templates/post.tmpl``` to invoke the code I added to ```templates/post_helper.tmpl```.

[Select this link for a diff via github that shows you what I changed](https://github.com/paregorios/paregorios.2018/commit/3c6fd3798fd16d9a550388a93729854d51cfa7fa#diff-0ce77a451d321cc843e940a5a57847ce).

## A Note on the <span class="bibtitle">Zotero</span> Namespace

Exceptionally devoted readers may recall that [my last post on this subject](../../04/what-zotero-wants) prophesied the use of [the PRISM namespace](https://www.idealliance.org/prism-metadata) to achieve Nikola+Zotero harmony. In fact, I tried adding ```<meta property="prism:genre" content="blogentry">``` based on [what I was seeing in the <span class="bibtitle">Zotero</span> translator code](https://github.com/zotero/translators/blob/beb41ffeb07290e8937a0b99d313a868783487ab/RDF.js#L617), but got no joy (i.e., <span class="bibtitle">Zotero</span> was still identifying my blog posts as generic web pages). I had two options: either try to troubleshoot the relatively complex logic used in the <span class="bibtitle">Zotero</span> translator to find out what I was doing wrong or why some other value was getting prioritized over my PRISM metadata, or take a cue from [the big assignment in the <span class="bibtitle">Zotero</span> translator code that prioritizes a <span class="bibtitle">Zotero</span> item type over any other metadata scheme](https://github.com/zotero/translators/blob/beb41ffeb07290e8937a0b99d313a868783487ab/RDF.js#L684). Embracing laziness as a virtue -- and also noticing that in newer versions of PRISM "blogEntry" seems to have been moved from the Genre vocabulary where the <span class="bibtitle">Zotero</span> translator expects it to [the Content Type vocabulary](http://www.prismstandard.org/vocabularies/3.0/contenttype.xml) -- I went with the latter option, got the result I was looking for, committed the changes, redeployed, wrote this blog post, and moved on to other things.



