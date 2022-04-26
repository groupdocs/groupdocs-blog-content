---
title: 'Important Bug Fixes in GroupDocs.Viewer for .NET 19.11'
date: Wed, 11 Dec 2019 16:42:47 +0000
draft: false
url: /2019/12/11/bug-fixes-for-pdf-dwg-odg-in-groupdocs-viewer-for-net-api/
author: 'Usman Aziz'
summary: ''
tags: ['autocad viewer', 'CAD viewer', 'document viewer', 'dwg or dfx viewer', 'Excel viewer', 'html5 document viewer', 'visio viewer', 'vsdx viewer', 'web document viewer', 'Word Viewer']
categories: ['GroupDocs.Viewer for .NET Releases', 'GroupDocs.Viewer Product Family']
---



{{< figure align=center src="images/groupdocs-viewer-net.png" alt="asp.net document viewer API">}}


We have rolled out another update for [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net) featuring some important bug fixes as well as an improvement related to the MSI package. This release hasn't brought any new feature, still, it has addressed some important issues related to PDF, DWG and ODG file formats. Furthermore, a few compatibility issues which appeared under .NET Standard 2.0 have been resolved. So let's have a brief overview of the bug fixes and improvements we have introduced in **v19.11**.

## Issue: Rendering DWG to image (PNG/JPG) or PDF resulted in an empty output

This issue appeared for some specific DWG files when the contents of the source files were missing in the output and it resulted in blank/empty images or PDF documents.

## Issue: The code hangs when rendering PDF document to HTML

One of our customers faced an issue where the API was taking too long to render a particular PDF document into HTML. We have resolved this issue and improved the performance of the API when rendering such PDF documents.

## Issue: Console output is printed when rendering ODG images

In the previous versions, the unnecessary messages were printed in the console window while rendering the ODG images. Although it wasn't affecting API's functionality or the output, it might have created confusion for the developers. We have fixed this issue to prevent unexpected messages to be printed in the console window.

## Issue: Compatibility issues under .NET Standard 2.0

In the [previous release](https://blog.groupdocs.com/2019/11/07/support-of-net-standard-and-net-core-in-groupdocs-viewer-for-net/), we added the support of .NET Standard 2.0 for cross-platform development using GroupDocs.Viewer for .NET. This enhancement raised some internal compatibility issues, however, we have fixed these issues in v19.11.

## Improvement: New ProjectGuid and UpgradeCode for MSI package

We have updated the unique identifier that is used by OS to identify the application installed with an MSI package. This update would require you to manually uninstall the previous version of GropuDocs.Viewer for .NET before installing v19.11 using the MSI package.

Since the updates are always important, we would recommend you to upgrade to v19.11 in your applications. In case you would face any issue or have any confusion, feel free to share with us via our [forum](https://forum.groupdocs.com/c/viewer).




