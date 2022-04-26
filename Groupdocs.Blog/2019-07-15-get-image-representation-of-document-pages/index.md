---
title: 'Get Image Representation of Document Pages'
date: Mon, 15 Jul 2019 09:15:01 +0000
draft: false
url: /2019/07/15/get-image-representation-of-document-pages/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Comparison for Java', 'GroupDocs.Comparison Product Family']
---

Getting image representation of document pages is one of the most successful feature that is already implemented in .NET version of the API. Keeping your interest in view, we've now implemented this feature for Java developers. GroupDocs.Comparison for Java [19.6](https://docs.groupdocs.com/display/comparisonjava/GroupDocs.Comparison+for+Java+19.6+Release+Notes) allows you to save document comparison results in image format as well.  
**What does it take to implement such a feature?**  
You just have to pass the output folder path to _convertToImages_ method and API will take care of conversion mechanism itself.  
Let's have a look at the implementation:  
{{< gist GroupDocsGists 82fb867c30591bb934a44d0f01969fb9 "getImageRepresentationOfDocumentPages.java" >}}

**Is there a way to set document size when comparing image with different formats?**  
We added a class _OriginalSize_ using that you can set document size when comparing image with different formats, this size will be used when document is converted to the picture. Given below are the methods:  

*   getHeight()
*   getWidth()
*   setHeight(int value)
*   setWidth(int value)

There are also bug fixes and improvements introduced in this release. Let's have a look at the prominent ones.

  
**Bug Fixes﻿**  

*   Font detection exception
*   Word separation exception
*   Html MarkDeletedInsertedContentDeep Bug
*   Deleted items in comparison output is not as expected
*   Incorrect difference info in PDF

**Improvements**  

*   Improve HTML aligner
*   TableFormatSetter for Slides is improved now
*   Html Anchors comparing
*   StyleSheet Comparer for Html

We'd recommend you to [download](https://downloads.groupdocs.com/comparison/java) and integrate this release in your project and enhance your document comparison experience. Do share your feedback or concerns on [forum](https://forum.groupdocs.com/c/comparison).




