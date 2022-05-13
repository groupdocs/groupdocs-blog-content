---
title: 'Support of .NET Standard 2.0 in GroupDocs.Viewer for .NET 19.10'
date: Thu, 07 Nov 2019 05:39:08 +0000
draft: false
url: /2019/11/07/support-of-net-standard-and-net-core-in-groupdocs-viewer-for-net/
author: 'Usman Aziz'
summary: ''
tags: ['dotNET Standard 2.0', 'API', 'document viewer API for .net', 'dotnet', 'GroupDocs.Viewer for .NET Releases']
categories: ['GroupDocs.Viewer Product Family']
---



{{< figure align=center src="images/groupdocs-viewer-net.png" alt="">}}


Hello everyone! We have released v19.10 of [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net) and I have a piece of breaking news especially for those who requested the support of [.NET Core](https://en.wikipedia.org/wiki/.NET_Core). The latest release of the API includes _6_ new features, _2_ improvements, and _11_ bug fixes. So let's have a look at some major updates we have brought for you.

## Support of .NET Standard 2.0

As promised, we have added the support of [.NET Standard 2.0](https://docs.microsoft.com/en-us/dotnet/standard/net-standard) in v19.10. So now, the API supports the .NET implementations that target .NET Standard 2.0 inlcuding .NET Framework and .NET Core. Thus, you can use GroupDocs.Viewer for .NET API in your cross-platform applications. At the moment, there exist a few limitations when using the API in a non-Windows environment. You can see the details of the limitations and the possible recommendations [here](https://docs.groupdocs.com/display/viewernet/.NET+Standard+2.0+API+Limitations).

## Adjusting Page Size when Rendering Emails as HTML

Previously, the feature of setting page size for email messages was available only for image-based rendering. However, we have extended it for HTML-based rendering as well. Now, you can control the page size of the resultant HTML pages as shown in the following code sample:

{{< gist GroupDocsGists 01d5d49139e26660cd01b834ad27d591 "AdjustPageSizeWhenRenderingEmailAsHTML.cs" >}}

## Support of .gzip and .sxc Formats

In the latest release. we have extended the list of our supported file formats and added the support of [Gnu Zipped Files](https://wiki.fileformat.com/compression/gz/) (.gzip) and StarOffice Calc Spreadsheets (.sxc).

## Bug Fixes

The following bugs that were reported in earlier versions have been fixed.

*   Tiff files are rendered incorrectly.
*   Incorrect image URLs when rendering email as HTML.
*   Blur image in when rendering slides as HTML.
*   Rendering Word document is taking a long time.
*   External resources failed to load when rendering Email messages.
*   Styles are lost when rendering XLSX into HTML.
*   The print preview of the rendered HTML is zoomed in.
*   Exception when rendering Word document as HTML.
*   Rendering Diagram document provides improper output colors.
*   "A null reference or invalid value was found" exception when rendering DWG as HTML.
*   DWG rendered empty.

## Other Improvements

*   Improved rendering of Markdown Documentation File (\*.md) file format.
*   Fit content by width when rendering mail messages into PDF/JPG/PNG.

Have a look at the [release notes](https://docs.groupdocs.com/display/viewernet/GroupDocs.Viewer+for+.NET+19.10+Release+Notes) for more details about the API changes in v19.10. We have also updated the source code examples on the [GitHub repository](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET) for the latest release and added the sample project for .NET Core. In case you would have any questions or queries, do let us know on our [forum](https://forum.groupdocs.com/c/viewer).





