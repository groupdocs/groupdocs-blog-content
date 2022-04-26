---
title: 'Export Annotations to TIFF Files'
date: Sat, 29 Jun 2019 07:47:27 +0000
draft: false
url: /2019/06/29/export-annotations-to-tiff-files/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Annotation for .NET', 'GroupDocs.Annotation Product Family']
---

This may be a big news for those who annotate TIFF documents, most of the time. Previously, there was issue with this format. API was throwing exception "Cannot open image file". But now you can:

*   Import annotations from TIFF file
*   Delete annotations from it
*   Export annotations into it

Moreover, in trial mode you were not able to get document info. This issue is now resolved in GroupDocs.Annotation for .NET [19.6](https://docs.groupdocs.com/display/annotationnet/GroupDocs.Annotation+for+.NET+19.6+Release+Notes).

Lets see new features introduced:

**More Slide Formats**  
API now supports following new Slide formats:

*   PPTM
*   POTX
*   POTM
*   PPSM

**Credit Based Billing**  
We integrated credit based billing system in GroupDocs.Annotation for .NET 19.6. Each document operation, along with consumed bytes, also consumes one credit. The amount of already used credits can be retrieved through method GetConsumptionCredit in the Metered class: {{< gist GroupDocsGists 2f9cad3b25a73caeabd92ca53735c8c2 "GetAlreadyUsedCredit.cs" >}}

API version 19.6 is now available for [download](https://www.nuget.org/packages/GroupDocs.annotation). Integrate it in your existing or new applications.




