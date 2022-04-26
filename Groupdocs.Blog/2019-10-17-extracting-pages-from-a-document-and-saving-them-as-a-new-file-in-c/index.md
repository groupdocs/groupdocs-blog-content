---
title: 'Extracting pages from a document and saving them as a new file in C#'
date: Thu, 17 Oct 2019 08:44:03 +0000
draft: false
url: /2019/10/17/extracting-pages-from-a-document-and-saving-them-as-a-new-file-in-c/
author: 'Atir Tahir'
summary: ''
tags: ['create new pdf', 'extract documents', 'split documents']
categories: ['GroupDocs.Merger for .NET', 'GroupDocs.Merger Product Family']
---

The first and foremost question in your mind could be, is it about PDF documents only? And the answer is, No. In this blog post we will see how simple yet helpful it is to extract pages from different kinds of documents (e.g. Word, Excel, Presentation, PDF, HTML, RTF) and save them as a new file using GroupDocs.Merger for .NET. Learn more about the [supported](https://docs.groupdocs.com/display/mergernet/Supported+Document+Types) file formats. Hence, the resultant document will possess only extracted pages.

**Is there any software installation needed?**  
GroupDocs.Merger for .NET is a back-end API that can be integrated in any existing or new .NET application (e.g. ASP.NET, Windows form, Console). It doesn't matter if MS Office or any PDF reader is installed on your computer or not. API doesn't rely on any third party tool or software.

**How simple is it?**  
The following code sample demonstrates how to extract document pages by _specifying exact page numbers_:  
{{< gist GroupDocsGists 4ed9531e8c9047ac0d39d2c38dd63a5d "extractbyexactpagenumbers.cs" >}}

The following code sample demonstrates how to extract document pages by _specifying page numbers range_:  
{{< gist GroupDocsGists 5d7e2aeca06cb84d94c49595e72738ca "extractbypagenumberrange.cs" >}}

Below is the source PDF with 13 pages. Suppose we want to extract two pages only (1, 3) and create new PDF.

*   

{{< figure align=center src="images/1.jpg" alt="">}}

    

Output PDF will look like this:

*   

{{< figure align=center src="images/2.jpg" alt="">}}

    

You can get API from the download [section.](https://downloads.groupdocs.com/merger/net) If you face any issue, post it on [forum](https://forum.groupdocs.com/c/merger).




