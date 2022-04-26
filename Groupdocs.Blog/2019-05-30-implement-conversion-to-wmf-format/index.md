---
title: 'Implement Conversion to WMF Format'
date: Thu, 30 May 2019 08:43:05 +0000
draft: false
url: /2019/05/30/implement-conversion-to-wmf-format/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Conversion for .NET', 'GroupDocs.Conversion Product Family']
---

WMF is a Windows MetaFile that can contain both vector and bitmap image information. We added support of WMF file format along-with few others in GroupDocs.Conversion for .NET 19.5. You can now convert any [supported](https://docs.groupdocs.com/display/conversionnet/Supported+Document+Formats) file format to WMF. Along-with WMF, convert supported documents to EMF.

**Convert to EMF**

{{< gist GroupDocsGists 689443a490974e334f8e855e32964e9a "converttoemf.cs" >}}

**Convert to WMF**

{{< gist GroupDocsGists 8b9f548c66090f2aa273e9b34c573857 "converttowmf.cs" >}}

Moreover, you can now pay royalties for the use of the API. Yes, **metered licensing** is now enabled.

{{< gist GroupDocsGists 8deb92b132287b904e0cb9cdbaadd11f "meteredlicenseconvesion.cs" >}}

New file formats you can convert from:

*   DIB
*   XLT
*   POT

In this release, we also removed obsolete property _JpegQuality_ from _ImageSaveOptions_.

We'd recommend you to download [latest](https://www.nuget.org/packages/GroupDocs.Conversion) version of the API and share your feedback.




