---
title: 'Cache Page Previews in GroupDocs.Annotation for Java'
date: Fri, 31 May 2019 10:19:32 +0000
draft: false
url: /2019/05/31/cache-page-previews-in-groupdocs.annotation-for-java/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Annotation for Java', 'GroupDocs.Annotation Product Family']
---

**EnableCaching** feature stores image representation of a document in a directory at the local drive. In case of repetitive processing/opening of a document, it uses cached data. This thing helps to avoid the processing of the same document again and again. You might be waiting for this feature. The wait is over now. GroupDocs.Annotation for Java 19.5 permits you to enable cache mode and cache page previews. Let's take a overview of its code.

{{< gist GroupDocsGists 090a62520ee05417b155ff2138338ef0 "enablecacheannotation.java" >}}

We also added possibility to display distance annotation caption for following file formats:

*   Slides
*   Cells
*   Diagrams

Following older formats for Slides, Cells and Words are now supported:

*   .ppt
*   .xls
*   .doc

Along with new features, this release also covers some improvements and bug fixes. As an improvement we refactored _PdfToPngSaver_ and _AnnotationHandler_ classes.

Moreover, we added additional parameters to _ImageOptions_ for more flexible retrieval of pages.  

*   Parameter for getting pages without annotation
*   Retrieve the range of pages
*   Retrieve only specific count of pages

Given below are some of the major bug fixes.

*   Line width not set in Slides
*   Issue when opening protected with password documents
*   Exception occurred while remove annotations from .xls file

Download our open-source example project [here](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-Java) and explore API documentation [here](https://docs.groupdocs.com/display/annotationjava/Home).




