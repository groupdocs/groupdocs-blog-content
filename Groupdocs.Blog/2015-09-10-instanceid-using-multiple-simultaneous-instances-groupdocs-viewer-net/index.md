---
title: 'InstanceID: using multiple simultaneous instances in GroupDocs.Viewer for .NET'
date: Thu, 10 Sep 2015 10:05:59 +0000
draft: false
url: /2015/09/10/instanceid-using-multiple-simultaneous-instances-groupdocs-viewer-net/
author: 'Stanislav Tatarin'
summary: ''
tags: ['.net library', 'GroupDocs Viewer', 'zArchive']
---

[![GroupDocs.Viewer for .NET](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/04/GD_VWR_NETIcon_114.png)](http://groupdocs.com/dot-net/document-viewer-library)Two months ago we [presented](https://blog.groupdocs.com/groupdocs-viewer-for-net-caching-pdf-copies-of-original-documents-and-using-multiple-root-storage-paths) a new feature called **InstanceID** in [GroupDocs.Viewer for .NET](http://groupdocs.com/dot-net/document-viewer-library) for the first time. In short, InstanceID allows you to configure several simultaneous instances of GroupDocs.Viewer associated with different independent root storage paths. Since that time, we’ve received a lot of feedback on the feature and this time would like to clarify how you can benefit from InstqanceID and how to configure it correctly in more details. Those of you who are familiar with GroupDocs.Viewer for .NET probably already know that in order to configure the viewer, a **root storage path** must be specified via the _Groupdocs.Web.UI.Viewer.SetRootStoragePath_ method. The files you want to display to end users must be placed within the root storage path or its subfolders. All temporary files along with log files are also stored in dedicated subfolders within the root storage folder. Now, there is a **File Explorer** option available for end users via the viewer’s widget. When enabled, this option allows users to browse through the local file storage, select documents and view them using the viewer. The file storage can be the root storage folder and its subfolders. In other words, when the **File Explorer** option is enabled, end users can potentially browse through the entire **root storage folder** and access all files, including temporary and log files, via the viewer. And here is where the problem arises. There may be cases when end users need to be able to browse through and select documents on their own, but their access rights must be restricted to a specific folder. Or, for example, there may be several different user groups each having access to different files storages. This is where **InstanceID** can be of great help. It allows you to configure multiple simultaneous root storage folders, absolutely independent one from another, and then assign them to different users or user groups. Recently we’ve prepared a detailed guide on how to configure and use **InstanceID** properly and are welcoming everyone who is interested in this feature to [read it here](https://docs.groupdocs.com/viewer/net).




