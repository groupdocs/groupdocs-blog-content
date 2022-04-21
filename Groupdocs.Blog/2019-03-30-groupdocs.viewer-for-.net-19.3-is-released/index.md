---
title: 'GroupDocs.Viewer for .NET 19.3 is Released!'
date: Sat, 30 Mar 2019 10:22:35 +0000
draft: false
url: /2019/03/30/groupdocs.viewer-for-.net-19.3-is-released/
author: 'Usman Aziz'
summary: ''
tags: ['document viewer', 'document viewer API for .net', 'Office Formats Viewer', 'online document viewer', 'PDF viewer', 'Viewer API']
categories: ['GroupDocs.Viewer for .NET Releases', 'GroupDocs.Viewer Product Family']
---

[![Document Viewer API](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-viewer-net.png)](https://www.groupdocs.com/products/viewer/net)

We are happy to announce the release of version 19.3 of [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net). In this release, we have added several new features that target the PDF documents, archives and the source code files of Visual Basic and C#. Along with 2 bug fixes, we have made a couple of improvements for rendering of ZIP archives and vCard documents. For detailed information about the latest release, please have a look at the [release notes](https://docs.groupdocs.com/display/viewernet/GroupDocs.Viewer+for+.NET+19.3+Release+Notes).

## What's New in this Release?

### **Setting Passwords and Permissions for PDF Documents**

PDF format allows setting the Owner password and the User password to restrict access to the document. The Owner password is used to change the permissions of the document whereas the User password is required when opening a PDF document. Along with the passwords, PDF format supports setting permissions such as allow or deny printing, modification and data extraction. In this release, we have added the support of setting the Owner password, User password, and the file permissions while rendering the document into PDF.

The following is a simple way to create and use the PDF file's security options using GroupDocs.Viewer for .NET:

{{< gist GroupDocsGists 055b16a3478b58ad3d823fe6e9873da4 "RenderingAsPDFWithSecuritySettings.cs" >}}

### **Working with Folders within the Archives**

In the previous version, we introduced the support of rendering archive documents. The rendering of archive documents shows a list of the items (files and folders) located in the root of the archive. In the latest release, we have made it possible to get the list of the folders within the archive and render the content from those folders. The following sections demonstrate how to work with the folders located in an archive document.

### Getting List of Folders within an Archive

The following code snippet shows how to get the list of folders within an archive:

{{< gist GroupDocsGists 055b16a3478b58ad3d823fe6e9873da4 "GetListOfFoldersInArchive.cs" >}}

### Getting List of Folders in a Specific Folder

There might be the case when you have sub-folders within a folder located in the root of the archive. In that case, to get the list of sub-folders you can simply specify the folder name in _ArchiveOptions.FolderName_ property of _HtmlOptions/ImageOptions_ class.

{{< gist GroupDocsGists 055b16a3478b58ad3d823fe6e9873da4 "GetListOfFoldersWithinFolderOfArchive.cs" >}}

### Rendering Specified Folder within Archive

To render the content of a folder, simply specify the folder name in  
_ArchiveOptions.FolderName_ property and call _GetPages_ function as shown in the following code snippet.

{{< gist GroupDocsGists 055b16a3478b58ad3d823fe6e9873da4 "RenderSpecifiedFolderInArchive.cs" >}}

### **Support of Visual Basic (.vb) and C# (.cs) Files**

Using the latest release, you will be able to view the source code files of Visual Basic and C#. The rendering of these source code files is available in both, the HTML-based and image-based rendering.

## Haven't Used GroupDocs.Viewer Before?

In case you haven't yet tried our API but are interested in using it, the following resources will be helpful for you to get started.

*   [Download](https://downloads.groupdocs.com/viewer/net) – Download GroupDocs.Viewer for .NET
*   [Documentation](https://docs.groupdocs.com/viewer/net) – Product Documentation
*   [API References](https://apireference.groupdocs.com/net/viewer/) - Details of publicly available classes, methods, properties, constants & interfaces of the API
*   [Examples / Plugins](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET) – Source Code Examples on GitHub  
    
*   [Sample Front End Apps](https://github.com/groupdocs-viewer/) – Open Source Document Viewer Applications
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPVahuYtHx0uscArNA595GK) – YouTube Videos
*   [Technical Support Forum](https://forum.groupdocs.com/c/viewer) – Technical Support Forum for GroupDocs.Viewer for .NET

## Stay Tuned for Updates!

If you don't want to miss out any news or announcements on GroupDocs products, stay tuned to our blog and keep visiting frequently.




