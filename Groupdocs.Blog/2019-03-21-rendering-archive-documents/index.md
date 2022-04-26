---
title: 'Rendering Archive Documents'
date: Thu, 21 Mar 2019 06:47:39 +0000
draft: false
url: /2019/03/21/rendering-archive-documents/
author: 'Muhammad Umar'
summary: ''
tags: ['Rendering Archive']
categories: ['GroupDocs.Viewer for .NET', 'GroupDocs.Viewer for Java', 'GroupDocs.Viewer Product Family']
---

The Compressed files (e.g .ZIP or TAR) use file compression in order to save the disk space. Also, the compressed archive formats can be used to compress multiple files into a single archive. This post demonstrates the usage of the GroupDocs.Viewer API to render the list of files or folders from an archive file.

## Rendering the List of a Folder from the Archive {#RenderingArchivedocuments-ObtainingthelistoffoldersfromtheArchive}The **GetPages** method of both **ViewerImageHandler** and **ViewerHtmlHandler** renders the items from the root of archives. The following code snippet shows that how simple is to render the list of items from the root of an archive: {{< gist GroupDocsGists 1f508b5dbf05f99834e73f4badb593c2 "RenderCompressedFile.cs" >}} The output of the above code snippet looks as follows: ![](http://blog.groupdocs.com/wp-content/uploads/sites/4/2019/03/sample-e1553083534996.jpeg)

## Rendering Specified Folder into Image, HTML or PDFTo render a specified folder from an archive into image, html or PDF, all **ImageOptions**, **HtmlOptions** and **PdfOptions** classes have the **ArchiveOptions.FolderName** property which is used like:```
ArchiveOptions.FolderName = "FirstLevelFolder";
```When you need to render the list of items or folders contained in a certain folder inside the archive, set the value using '/' path delimiter character like:```
ArchiveOptions.FolderName = "FirstLevelFolder/SecondLevelFolder";
```The following example shows the rendering of a list of items from a folder "SecondLevelFolder" which is contained inside the "FirstLevelFolder" of the archive: {{< gist GroupDocsGists ec8f73ac96057305ee175ffa448490af "RenderSpecifiedFolderFromArchive.cs" >}} If the rendering into PDF file is required, you can write the code as follows: {{< gist GroupDocsGists 37930f2cdad27d3c3b8b247e867bc83b "RenderCertainFolderIntoPDF.cs" >}} The complete ready to run code sample is available on [GitHub](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET/).




