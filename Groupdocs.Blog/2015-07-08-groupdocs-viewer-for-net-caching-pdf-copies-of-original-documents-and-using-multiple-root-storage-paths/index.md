---
title: 'GroupDocs.Viewer for .NET version 2.13.0 - caching PDF copies of original documents &amp; using multiple root storage paths'
date: Wed, 08 Jul 2015 14:43:48 +0000
draft: false
url: /2015/07/08/groupdocs-viewer-for-net-caching-pdf-copies-of-original-documents-and-using-multiple-root-storage-paths/
author: 'Stanislav Tatarin'
summary: ''
tags: ['dotNET library', 'release notes', 'zArchive']
categories: ['GroupDocs.Viewer Product Family']
---

[![GroupDocs.Viewer for .NET](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/04/GD_VWR_NETIcon_114.png)](http://groupdocs.com/dot-net/document-viewer-library)Last week we’ve [announced](https://blog.groupdocs.com/) a release of the GroupDocs.Viewer for .NET library version [2.13.0](http://groupdocs.com/Community/files/8/.net-libraries/groupdocs_viewer_for_.net/entry7302.aspx) and its two new features – an option for caching PDF copies of original files and the ability to use the viewer with an unlimited number of different independent root storage paths. Today we’d like to write about these features in more detail to help you quickly set up and get the most out of them. Let’s start with the caching enhancement. As you may already know, [GroupDocs .Viewer for .NET](http://groupdocs.com/dot-net/document-viewer-library) allows you to configure caching for displayed documents. When enabled, the viewer doesn’t have to convert original documents stored on the server to HTML-compatible content each time the documents are requested. Instead, documents are converted only during the first view request and then added to the cache. For all subsequent requests of the same documents, they are loaded from the cache, which significantly reduces load time. This caching feature, however, was unavailable for PDF copies of original documents. So, when using features like **.UsePdfPrinting(true)** and **.DownloadPdfFileIfPossible(true)**, the viewer had to convert original documents to the PDF format repeatedly for each new request. This was the case until the version 2.13.0. In the latest release of the GroupDocs.Viewer for .NET, you can now configure caching for PDF copies as well. What is important, the viewer is able to identify whether any changes to the displayed documents has been made (e.g. added watermarks, rotated or re-ordered pages, etc.) and if yes, refreshes the cache with the updated PDF copies, so that you can be sure that end users always get access only to the latest versions of the documents. This new caching feature can also be used ahead-of-time. In other words, you can configure GroupDocs.Viewer to add PDF copies of original files to cache even before they were actually requested by end users. For doing so, just use a new method – **GeneratePdfVersion** – within the **DocumentCache** class. The **GeneratePdfVersion** method obtains only one mandatory parameter – document’s name, then converts the document to the PDF format and saves it inside the cache folder. The method also has optional parameters which allow you to burn watermarks into PDF copies of original files. Please be cautious when configuring watermarks for different versions of a document. If you pre-generate a PDF copy of a document with watermarks and then specify the same document in the widget without the watermarks (or with some other watermarks), a discrepancy will occur, since watermarks specified for the "standard" document will vary from those specified for the PDF-version of the document.

### Using Multiple Independent Root Storage PathsAnother remarkable improvement we’ve implemented in this version is the ability to use the viewer with an unlimited number of different independent root storage paths. Here is how this works. The default root storage path, which is configured via the **Viewer.SetRootStoragePath** method, remains obligatory. However, you can now set up additional paths using the **InstanceID** identifier. For example:

*   `Groupdocs.Web.UI.Viewer.SetRootStoragePath(Server.MapPath("~/App_Data/"));` - the default mandatory initialization.
*   `Groupdocs.Web.UI.Viewer.SetRootStoragePath(Server.MapPath("~/OtherFiles/"), null, "myInstanceIdN1");` - an additional root storage path (the OtherFiles folder), linked to the **myInstanceIdN1** identifier.

Now, to load documents from the second root storage path (the OtherFiles folder), simply set the **.ViewerInstanceId("myInstanceIdN1")** method in the **ClientHelper**. This way you can configure as many independent root storage paths, as you need. That’s it! If you have any questions about these or other GroupDocs.Viewer for .NET features, please feel free to ask for help on our [Support Forum](http://groupdocs.com/Community/Forums/Default.aspx).





