---
title: 'Enable Pagination in WordProcessing Module'
date: Tue, 18 Jun 2019 09:18:06 +0000
draft: false
url: /2019/06/18/enable-pagination-in-wordprocessing-module/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Editor for .NET', 'GroupDocs.Editor Product Family']
---

Yes, this is right. Paginal mode is now implemented in GroupDocs.Editor for .NET [19.5](https://docs.groupdocs.com/display/editornet/GroupDocs.Editor+for+.NET+19.5+Release+Notes). How this mode will effect WordProcessing documents? As you know that previously, there was only _float_ mode. When WordProcessing documents were converted to the page-less HTML, page division was absent. But in this release _WordProcessing_ options class contains new _paged_ (also called _paginal_) mode. When _paged_ is enabled, it produces HTML markup, optimized and adjusted for per-page edit and it creates ease to enable paged editing in any of WYSIWYG-editors.

By default this mode is disabled. In order to enable it you need to set a boolean flag to _true_ in the _WordProcessingToHtmlOptions_ options:  
{{< gist GroupDocsGists a9d9c25c97bbac20665de0cfce771d86 "enablepagination.cs" >}}

Now, when document is edited in the WYSIWYG-editor and is passed back to the GroupDocs.Editor API for converting from HTML to the output format, you also have to set boolean flag to _true_ (by default it is disabled) in the _WordProcessingSaveOptions_:  
{{< gist GroupDocsGists e4d0ed4867a7c9424caf5eede1d85c31 "enablepaginationinsaveoptions.cs" >}}

Aside this, various text effects are implemented in WordProcessing documents:

*   Shadow
*   3D Effect
*   Outline
*   Glow
*   Engrave
*   Emboss

This feature doesn't require any action, it is always enabled and can be observed, when the document with such text effects is processed.

Metered Credits is introduced in this release as well. As API already supports Metered Licensing. But now a new credits concept is implemented. Each document operation, along with consumed bytes, also consumes one credit. The amount of already used credits can be retrieved through new static method _GetConsumptionCredit_ in the _Metered_ class:  
{{< gist GroupDocsGists cc854fe21166991e43b10eaf0fc715d4 "getconsumptioncredit.cs" >}}

Grab the latest release [here](https://www.nuget.org/packages/GroupDocs.editor). Please communicate with us on [forum](https://forum.groupdocs.com/c/editor) if you face any issue.




