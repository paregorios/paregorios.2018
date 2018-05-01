<!--
.. title: Zotero Item Keys (Again)
.. slug: zotero_item_keys
.. date: 2018-05-01 05:13:26 UTC-05:00
.. tags: bibliography, zotero
.. category: 
.. link: 
.. description: 
.. type: text
-->

[Back in 2012, I posted about _Zotero_ item keys](/posts/2012/02/give-me-zotero-item-keys/) and my attempts to get at them for purposes of linking and reuse. There are better ways, hence this update. <!-- TEASER_END -->

Option 1: Export to [<abbr title="Comma-Separated Values">CSV</abbr>](https://www.loc.gov/preservation/digital/formats/fdd/fdd000323.shtml). The item key is in the first column:

```csv
"Key","Item Type","Publication Year","Author","Title"
"MK49RMWU","encyclopediaArticle","2016","","Κρήτη","Βικιπαίδεια"
```

Option 2: Install [the _Zutilo_ plugin for _Zotero Standalone_](https://github.com/willsALMANJ/Zutilo). It adds several features to the _Zotero_ client, including the ability to get the _Zotero_ <a href="https://en.wikipedia.org/wiki/Uniform_Resource_Identifier"><abbr title="Uniform Resource Identifiers">URIs</abbr></a> for one or more records via a context menu item. The last element in the _Zotero_ URI is the item key:

<img src="/images/2018/05/zutilo.png" alt="Screen capture showing the Zotero Standalone client interface with the context menu activated for an individual record. The 'Zutilo' submenu is activated and the 'Copy Zotero URIs' menu item is selected."/>
