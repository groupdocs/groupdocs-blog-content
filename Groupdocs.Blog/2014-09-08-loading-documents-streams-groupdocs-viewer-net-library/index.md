---
title: 'Loading Documents from Streams with the GroupDocs.Viewer for .NET Library'
date: Mon, 08 Sep 2014 07:23:04 +0000
draft: false
url: /2014/09/08/loading-documents-streams-groupdocs-viewer-net-library/
author: 'Denis Gvardionov'
summary: ''
tags: ['file stream', 'GroupDocs Viewer', 'memory stream', 'network stream', 'viewer for .net library', 'zArchive']
---

Greetings! ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/04/GD_VWR_NETIcon_114.png) As you may noticed, in most [GroupDocs.Viewer for .NET](http://groupdocs.com/dot-net/document-viewer-library) sample projects, target documents are presented in the form of files. They are usually placed in the "testfiles" folder, which is specified in the **Global.asax**. So you might think that GroupDocs.Viewer can work with files only. But this is not true - GroupDocs.Viewer can also load documents from byte streams ([System.IO.Stream](http://msdn.microsoft.com/en-us/library/system.io.stream.aspx)). Moreover, there are no limitations on the type of stream: whether it's a FileStream, a MemoryStream or a NetworkStream - GroupDocs.Viewer can work with it! So, in this article I'd like to shed light on all aspects of using streams with the GroupDocs.Viewer for .NET library: which types of streams are supported, how to grab files from a DB as streams, how to use streams in ASP.NET WebForms and also in MVC projects. **UPD:** the latest versions of the GroupDocs.Viewer for .NET library has seen a number of significant enhancements to how the viewer handles streams. Recently I've updated the article to reflect these changes. In particular, I rewrote the guides on how to use streams in ASP.NET WebForms and MVC projects, and added new chapters describing how to handle cache, load files from multiple streams, etc, as well as most common mistakes developers face with when adjusting streams in GroupDocs.Viewer. I also added a changelog, showing the updates implemented in each version of the viewer, so that you can quickly tweak the necessary settings. Hope, this will help you set up and run streams with GroupDocs.Viewer in your project hassle-free. [Go to the article >>>](https://docs.groupdocs.com/viewer/net)




