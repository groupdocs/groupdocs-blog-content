---
title: 'Render Files Contained in ZIP Archive using GroupDocs.Viewer for .NET 19.4'
date: Fri, 03 May 2019 04:09:47 +0000
draft: false
url: /2019/05/03/render-files-contained-in-zip-archive-using-groupdocs.viewer-for-.net-19.4/
author: 'Usman Aziz'
summary: ''
tags: ['CAD viewer', 'document rendering API', 'document viewer', 'document viewer API for .net', 'DWG viewer', 'Office Viewer', 'PDF viewer', 'Rendering Archive']
categories: ['GroupDocs.Viewer Product Family']
---

Hello everyone! We are back with another exciting release announcement. In this post, I am going to give you an overview of what's new as well as what's improved and fixed in the latest release of [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net). In this release, we majorly focused on providing bug fixes and improvements. Along with this, we have introduced the support of **CDR** file format and the feature of rendering files contained in the ZIP archives. For details, you may also have look at the [release notes](https://docs.groupdocs.com/display/viewernet/GroupDocs.Viewer+for+.NET+19.4+Release+Notes).

First, let's have a walk through the new features that we introduced in the latest release.

## Support of CDR File Format

We have added the support of **CDR** file format that is a vector graphics file to store the images and it is used by **CorelDRAW** software.

## Getting and Rendering Files from ZIP Archives

In the [previous blog](https://blog.groupdocs.com/2019/03/30/groupdocs.viewer-for-.net-19.3-is-released/), we demonstrated how you can get the list of files, folders and the subfolders enclosed in a ZIP archive. Now, its time to go one step ahead and render the files contained in the ZIP archives. With the latest release, you can get the files located in the root as well as in a folder of the archive. The following code snippet shows how we can get and then render the files as attachments from an archive.

{{< gist GroupDocsGists bd45b1eb0a74ffab7eaa6a902e1de38a "GetFileInZIPArchive.cs" >}}

Isn't it easier than you expected before reading this blog? Let's not stop here and move forward to what has been fixed and improved in the latest release.

## Important Bug Fixes and Improvements

In addition to the new features we have discussed above, we fixed a number of issues that were found in the previous releases as well as introduced a couple of improvements. The list includes:

*   Exception: Value does not fall within the expected range
*   Some characters are missing when rendering PDF as Html
*   Invalid Printable HTML  for MS Project documents with several pages
*   Missing characters when rendering PDF document as HTML
*   License is not applied in Unit Test project
*   ArchiveDocumentInfoContainer.Folders doesn't return the list of folders
*   Values in the form fields are missing when rendering PDF into HTML
*   First page of ODT documents is not rendering
*   Metered related exception when License is initialized with other GroupDocs products
*   Extended support for ViewerConfig.FontDirectories setting to vector image formats
*   Improved rending attachments from password protected zip archives

Now, it's time to enhance and upgrade your application with the features offered by the latest release of GroupDocs.Viewer for .NET. You may also evaluate the API features by downloading or cloning the complete examples project from [GitHub repository](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET).

As always, we would love to hear your suggestions at our [forum](https://forum.groupdocs.com/). Cheers!




