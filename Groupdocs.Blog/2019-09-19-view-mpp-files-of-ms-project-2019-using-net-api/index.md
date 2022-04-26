---
title: 'View MPP Files Created in MS Project 2019 using GroupDocs.Viewer for .NET 19.9'
date: Thu, 19 Sep 2019 05:02:13 +0000
draft: false
url: /2019/09/19/view-mpp-files-of-ms-project-2019-using-net-api/
author: 'Usman Aziz'
summary: ''
tags: ['MPP Viewer']
categories: ['GroupDocs.Viewer for .NET Releases', 'GroupDocs.Viewer Product Family']
---



{{< figure align=center src="images/groupdocs-viewer-net.png" alt="ASP.NET Document Viewer API">}}


Hello everyone! We have recently released version 19.9 of [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net) with the support of new file formats as well as a number of bug fixes. So in this post, I am going to write about what is new in this release particularly for those who are interested in viewing Microsoft Project files (_.mpp_) using .NET API.

Microsoft Project is a famous project management software that is proved to be helpful for the managers as well as the other stakeholders in making, organizing, tracking and analyzing their project plans. The MS Project uses the [MPP](https://wiki.fileformat.com/project-management/mpp/) file format to store the data or information related to project management. Since MPP is the proprietary file format of Microsoft, you need to have MS Project installed to view _.mpp_ files. However, if you want to view _.mpp_ files in your web or desktop application without installing MS Project or if you are interested in creating your online MPP viewer then you can easily do it using our .NET document viewer API.

GroupDocs.Viewer for .NET supports viewing MPP format and the big news is that we have now extended this support for _.mpp_ files created in MS Project 2019. So now you can view _.mpp_ files without worrying about their versions. Also, there is no pubic API change for this, so you don't need to change anything in the code if you have already embedded this feature in your application. If you are new and want to get more details on it along with the code samples, please visit [Rendering MS Project Documents](https://docs.groupdocs.com/viewer/net).

In addition, we have also added the support of viewing following file formats in v19.9:

*   _OpenXPS (.oxps)_
*   _OpenDocument Flat XML Spreadsheet (.fods)_

Not only this, but you can also avail the following bug fixes after upgrading to the latest release.

*   Incorrect links to resources when rendering into HTML
*   Failed to render password-protected ODP/OTP presentations
*   Styles are embedded when rendering XLSX into HTML with external resources
*   Incorrect page count for EPUB document
*   Page order ignored when rendering MS Project document into PDF
*   JpegQuality option of PdfFileOptions not works when rendering ODP presentation
*   HTML representation of PPTX document takes too much time
*   Misplaced characters when rendering Word document into HTML or image

So if you are interested in getting the above-mentioned features and fixes, just [download](https://downloads.groupdocs.com/viewer/net/new-releases/-groupdocs.viewer-for-.net-19.9/) and integrate GroupDocs.Viewer for .NET 19.9 in your application. If you haven't used the API before, have a look at the [documentation](https://docs.groupdocs.com/display/viewernet/Home) of the API. In order to evaluate API features, download or clone the examples project from [GitHub repository](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET).

As always, do write to us on our [forum](https://forum.groupdocs.com/categories) in case you would have any questions or queries.




