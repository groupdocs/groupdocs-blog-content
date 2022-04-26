---
title: 'GroupDocs.Viewer 2.0 - New Features &amp; Improvements to the Java Version of the Document Viewer'
date: Tue, 27 May 2014 13:59:00 +0000
draft: false
url: /2014/05/27/groupdocs-viewer-2-0-new-features-in-the-java-version-of-the-document-viewer/
author: 'Ihor Mykhalevych'
summary: ''
tags: ['GroupDocs Viewer', 'viewer for java library', 'zArchive']
---

[![GroupDocs.Viewer for Java library](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/05/GD_VWR_JavaIcon_114.png "GroupDocs.Viewer for Java library")](http://groupdocs.com/java/document-viewer-library) Last week, we released an update to the GroupDocs.Viewer library for the .NET platform. Now it is time to share what version 2.0 of [GroupDocs.Viewer](http://groupdocs.com/java/document-viewer-library "GroupDocs.Viewer for Java") has to offer to the Java world. You can find a full list of new features, improvements and fixes on the [GroupDocs.Viewer download page](http://groupdocs.com/Community/files/9/java-libraries/groupdocs_viewer_for_java/entry1204.aspx). The most notable improvements, I'm going to discover in this article.

### Native HTML5-Based Document RenderingThe brightest gem presented in this version is the **HTML**\-based rendering mode - an addition to the image-based one that was the only choice in previous versions of the document viewer. Under the new mode, all text is placed on the page using pure HTML and CSS, while graphics are drawn using [SVG format](http://en.wikipedia.org/wiki/Scalable_Vector_Graphics). This feature makes pages more "lightweight" and allows end-users to search for text within the document using the native browser search functionality. **Please note:** by default, the rendering mode is image-based, so you have to switch it explicitly. This can be done via the _useHtmlBasedEngine_ parameter in the JavaScript plugin - just specify **true** to enable HTML mode. Also, when you turn on the HTML-based mode, make sure to set the _com.groupdocs.viewer.config.ServiceConfiguration_ constructor's _useCache_ argument to **true**.

### Enhanced Thumbnails Panel UsabilityGroupDocs.Viewer for Java 2.0 has a new layout option for the thumbnails panel. The panel can now either slide over the document pages, or you can place it on the same level as the pages, so that it doesn't overlap the document's content. The layout options can be switched with the _useInnerThumbnails_ Boolean parameter, where the **true** value places thumbnails to the left side of the viewport.

### Improved Text Search EnginePrevious versions of the viewer could only search on exact phrases. That is also the default in the new version. A newly added option allows users to search for every separate word entered to the search form. To activate this, just specify **true** for the _searchForSeparateWords _parameter.

### Enhancements for the Upload API

#### Token ID - a New Unique and Secure File IdentifierThis is a Java-specific feature of the new version of the document viewer. Before this update, the upload API was quite primitive - it only provided an ID of the uploaded file on the output side. The identification functionality was encapsulated into the _TokenId_ class. Now, the _ViewerHandler _method:```
public Object uploadFile(InputStream inputStream, String fileName, Integer timeToLive)
```returns the file token ID, which, as before, can be used to view the uploaded file. But with its new ID, the viewing process got few important improvements:

#### Uploaded File Time Usage RestrictionThe first improvement is the ability to restrict access to uploaded files using the _TokenId_ time limit. Each uploaded file's ID now has the _timeToLive _parameter, which can be checked with the```
public boolean isExpired()
```method of the _TokenId _class. For example, before displaying a document, you can check:```
TokenId tki = new TokenId(tokenId);
if(tki.isExpired()) {
    // access denied
}
```

#### Token ID Renewal APIThe redundancy of file upload and space usage issue was resolved with the token ID renewal API. Now, the old token can be refreshed using the```
public Object renewTokenId(String tokenId)
```method of the _ViewerHandler _class.

### Other ImprovementsIn addition to the above, the new version of the Java document viewer library features the following:

*   Faster page rendering on first load - due to additional cache.
*   Lower memory usage - due to tuned-up algorithms.
*   Improved integration - the API is now better structured.

For a complete list of new features, improvements and bug fixes, as well as to download the new version of the GroupDocs.Viewer for Java library, please visit [this page](http://groupdocs.com/Community/files/9/java-libraries/groupdocs_viewer_for_java/entry1204.aspx). Also, here are a couple of samples that might help you discover all the new features faster:

*   [Java Dropwizard Framework Sample](https://github.com/groupdocs-viewer/)
*   [Java Spring Framework Sample](https://github.com/groupdocs-viewer/)




