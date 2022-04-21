---
title: 'Implement Link Annotation in PDF Documents'
date: Fri, 10 May 2019 10:08:37 +0000
draft: false
url: /2019/05/10/implement-link-annotation-in-pdf-documents/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Annotation for .NET', 'GroupDocs.Annotation Product Family']
---

You might be wondering if there would be more annotation types. The wait is over, we've introduced Link Annotation in GroupDocs.Annotation for .NET 19.4. With the passage of time we'll introduce more annotations. Currently, Link Annotation is supported for PDF, Slides and Word documents only. Let's see the minimal set of fields required for Link Annotation.

{{< gist GroupDocsGists bf827c413af77936033197bc72a2b72c "linkannotationsupport.cs" >}}

There is one improvement and few bug fixes introduced as well. Previously,  
_GetPdfFile_ method was not processing password protected documents. Now, if you need to process password protected documents you should pass an extra parameter for _GetPdfFile_ method.

{{< gist GroupDocsGists 3cdd2aad071de7677ddd4a4cbbe36477 "getpdfmethod.cs" >}}

Following are the major bug fixes:

*   Annotations were not removing from Cell documents
*   Password protected documents were not converted to PDF
*   GetPdfFile method was returning broken file
*   ImportAnnotations method was not closing source stream for Tiff files

[Download](https://www.nuget.org/packages/GroupDocs.annotation) and implement various types of annotations programatically in documents. See documentation of link and various other annotation types in [developer guide](https://docs.groupdocs.com/display/annotationnet/Developer+Guide) section.




