---
title: 'GroupDocs.Viewer 2.0 - New Features and Improvements in the Document Viewer for .NET Library (Part B)'
date: Thu, 22 May 2014 16:36:20 +0000
draft: false
url: /2014/05/22/new-features-and-improvements-in-the-document-viewer-for-net-library-part-b/
author: 'Denis Gvardionov'
summary: ''
tags: ['document viewer for .net', 'GroupDocs Viewer', 'viewer for .net library', 'zArchive']
---

Greetings!![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/03/GD_VWR_NETIcon_114.png) This is **Part B** of my post looking at the new features and enhancements to the GroupDocs document viewer for .NET version 2.0. For those of you who missed my previous post, please find it [here](https://blog.groupdocs.com/enhancements-and-new-features-in-the-document-viewer-for-net-library-part-a). This time I'm going to continue describing the core updates that the library has seen in the second major release. So, here we go:

### Enhanced Text Search OptionsGroupDocs.Viewer 2.0 includes a lot of helpful text search improvements. And importantly, all the features described below are compatible with both the image-based and HTML-based rendering modes.

#### Adjusting the Color of Search HitsWhen you search a word or a phrase in a document using GroupDocs.Viewer’s search toolbar, the matched text is highlighted with two colors. The first color, _CurrentSearchColor_, is applied to the first matched result. The second color, _OtherSearchColor_, is applied to all other matched results located after the first one. By default, _CurrentSearchColor_ is light green, and _OtherSearchColor_ is dark green. In GroupDocs.Viewer 2.0 you can specify these colors yourself. In order to do this, invoke the _SearchHighlightColor_ method, which contains two string parameters - the first one is mandatory and specifies _OtherSearchColor_, while the second one is optional and specifies _CurrentSearchColor_. If you omit the second parameter, then the default light green color is used for both of the parameters. For example:```
…ViewerClientCode(). ….SearchHighlightColor("blue") //only OtherSearchColor is specified
…ViewerClientCode(). … .SearchHighlightColor("blue", "red")//both OtherSearchColor and CurrentSearchColor are specified

```

#### Search for Any of Several WordsWhat happens when you insert several words (two, for example) into the search field and hit **Enter**? There are two ways to deal with this. On the one hand, it can be treated as if you want to find an exact phrase. On the other hand, it can be treated as if you want to find both an exact combination AND all distinct words located separately. GroupDocs.Viewer 2.0 supports both of these approaches. By default, when you enter several words, GroupDocs.Viewer tries to find only the exact combination of these words - that is how previous versions of GroupDocs.Viewer worked. Now, if you want to switch to the second scenario, just use the new _SearchForSeparateWords_ method, which takes two parameters and sets the value of its first parameter, _searchForSeparateWords_, to **true**. In this case, when several words are entered, GroupDocs.Viewer will find and highlight all of them, whether they are combined or separate. This might make you ask: what if the _SearchForSeparateWords_ mode is enabled and you want to search only for the exact phrase, without having to change the source code back on the server-side? Continue reading…

#### Treat Phrases in Double Quotes as Exact Phrases when Searching for Separate WordsLet’s take a look at the _SearchForSeparateWords_ method more closely:```
public ClientHelper SearchForSeparateWords(bool searchForSeparateWords = true, bool treatPhrasesInDoubleQuotesAsExactPhrases = false)

```This method has two parameters, the second of which allows you to find and highlight only exact phrases even if the _SearchForSeparateWords_ mode is enabled. To do this just call this method with both parameters set to **true**:```
…ViewerClientCode(). …..SearchForSeparateWords(true, true)

```By default, the second parameter is set to **false**, so you need to change it to **true** explicitly. When you do this, you can find exact phrases by wrapping words in double quotes. For example, if you enter **word1 word2** into the search field, GroupDocs.Viewer finds and highlights all **word1**, all **word2** and all combinations of the two. But if you enter **"word1 word2"** (in double quotes), GroupDocs.Viewer finds and highlights only this exact phrase (if any in the document).

### Rearranging PagesPage reordering is a brand new feature that was added in version 2.0 of the GroupDocs document viewer. This feature allows you to change the page order of the displayed document client-side, from a web-browser. This can be done in the GroupDocs.Viewer interface via the thumbnails panel, where page previews are displayed. A user just needs to drag the thumbnail of a page he wants to move and drop it to a new location. Pages in the document will be reordered accordingly. Also, GroupDocs.Viewer fixes the new order of the pages, so that next time the user loads the document, he/she will see the rearranged document. Page reordering doesn’t impact the original document on the server, but the user can download the rearranged version of the original document to the client-side. The only way to download it is to enable an option for downloading a PDF instead of the original file (please see how to configure conversion to PDF on download in my [previous post](https://blog.groupdocs.com/enhancements-and-new-features-in-the-document-viewer-for-net-library-part-a)). By default document rearranging feature is disabled. To turn it on, you should invoke the _SupportPageReordering_ method:```
…ViewerClientCode(). ….SupportPageReordering(true)

```Also, please note that page reordering is supported only with the image-based rendering mode.

### Centering PagesGroupDocs.Viewer allows you to increase and decrease a document's zoom level using the toolbar buttons **Zoom In**, **Zoom Out** and **Zoom Level**. In previous versions of the GroupDocs.Viewer for .NET library, and by default in version 2.0, when you decrease a zooming level and pages become small, they rearrange in such a way that they are located one next to the other, like tiles. For example, when a 50% zoom out level is reached, two pages are shown side by side, horizontally. GroupDocs.Viewer 2.0 has a new mode, designed to prevent this type of tile-like rearrangement. With this mode pages are always placed in one row, regardless of the zoom factor. In order to enable this mode, pass the **true** parameter to the _ShowOnePageInRow_ method:```
…ViewerClientCode(). ….ShowOnePageInRow(true)

```

### LocalizationGroupDocs.Viewer 2.0 includes localizations for four languages for interface elements like text labels and tooltips, including: “en-US” (American English, the default), “es-ES” (Spanish), “pt-PT” (Portuguese) and "nb-NO" (Norwegian). To set up the needed locale, use the _ClientHelper_ class' _Locale_ method. It has two overloads:```
public ClientHelper Locale(string locale);
public ClientHelper Locale(SupportedLocales locale);

```These overloads are equivalent: you can use either of them. If you use several _Locale_ methods in one _Viewer_ control, the last one is applied. For example:```
…ViewerClientCode(). ….Locale(SupportedLocales.ptPT).Locale("en-US")

```In this line of code we invoke both overloads: in the first line we apply the Portuguese locale, and in second, English. The last locale will be applied, so after compilation and execution, end-users will see the English locale.

### Other Features and Improvements1\. The _DocViewerId_ method was removed from the _ClientHelper_ class - there is no need for it anymore. 2. The _Groupdocs.Web.UI.Viewer_ class now has two new methods: _EnableDownloadRequestHandling_ and _EnablePrintRequestHandling_. All of these have one **Boolean** parameter. They are like enabling and disabling downloading and printing (this was described earlier), but, in contrast to showing or hiding buttons in the GroupDocs.Viewer UI, these methods are more global - they allow developers to enable or disable downloading and printing across a website, all pages and instances of the GroupDocs.Viewer web-control. These options are more powerful than those that the web-control has. For example, if downloading is enabled in GroupDocs.Viewer's web-control but disabled in the _Viewer_ class, then users will not be able to download anything at all. 3. PDF to HTML conversion performance has been improved significantly thanks to using a newer version of Knockout.js (ver.3.0.0), which reduces the size of the sprites.png file. 4. Plenty of other minor features have been added to GroupDocs.Viewer 2.0. You can find a complete list of improvements, as well as download the new version of the viewer on [this page](http://groupdocs.com/Community/files/8/.net-libraries/groupdocs_viewer_for_.net/entry1177.aspx). For more details on the GroupDocs.Viewer for .NET library itself, please see the [product's homepage](http://groupdocs.com/dot-net/document-viewer-library).




