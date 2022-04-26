---
title: 'XLTX File Format Support in GroupDocs.Merger for .NET'
date: Tue, 26 Feb 2019 15:18:47 +0000
draft: false
url: /2019/02/26/xltx-file-format-support-in-groupdocs.merger-for-.net/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Merger for .NET', 'GroupDocs.Merger Product Family']
---

Document Manipulation and Modification is now programatically implemented in a lot of file formats. Keeping that in view, we are introducing some new file formats with the release of GroupDocs.Merger for .NET 19.2.

Following new file formats are now supported by the API:

*   XLT
*   XLTX
*   XLTM

In excel these file formats are basically saved as a template files.

Beside new features, we also introduced a improvement and few bug fixes.  
ODP presentations loading is optimized.

Previously, **MovePage** method was not working correctly for _EPUB_ and _XPS_ formats. But this issue is long gone now. You can move any page in _XPS_ or _EPUB_ document to some other position and get resultant document with new page order.

See how MovePage and other document manipulation operations are processed [here](https://docs.groupdocs.com/display/mergernet/Developer+Guide). Download [latest](https://www.nuget.org/packages/GroupDocs.merger) release of the API and share your feedback.




