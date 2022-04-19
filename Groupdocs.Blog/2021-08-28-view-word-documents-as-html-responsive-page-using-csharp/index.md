---
title: 'View Word Documents as HTML Responsive Page using C#'
date: Sat, 28 Aug 2021 12:35:45 +0000
draft: false
url: /2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/
author: 'Shoaib Khan'
summary: "HTML Responsive web pages are meant to look good on different devices. These pages automatically adjust according to different screen sizes. This article will guide you to automate the conversion and view your Word documents as responsive HTML pages within your .NET applications using C#."
tags: ['convert docx to html in csharp', 'docx to html responsive', 'view word as html responsive', 'Word to HTML in CSharp']
categories: ['GroupDocs.Viewer Product Family']
---

HTML Responsive web pages are meant to look good on different devices. These pages automatically adjust according to different screen sizes. This article will guide you to automate the conversion and view your Word documents as responsive HTML pages within your .NET applications using C#.



{{< figure align=center src="images/word-to-responsive-html-layout-using-dotnet-1024x614.jpg" alt="Word to Responsive HTML Layout using C# .NET API">}}


The following topics will be covered below:

*   [.NET API for Word and Responsive HTML viewer][1]
*   [View Word Documents as Responsive HTML using C#][2]

## .NET API for Word and Responsive HTML Viewer {#html-viewer-dotnet-api}

I will be using [GroupDocs.Viewer for .NET][3] to render the Word documents as responsive HTML pages in the examples below. The API is a powerful [document viewer .NET API that supports rendering a large number of documents][4]. It allows building **HTML Viewer** with embedded and external resources, an **Image Viewer** by rendering as JPG and PNG, and **PDF Viewer** that is best for printing or sharing with others.

You can download the **DLLs** or **MSI** installer from the [downloads section][5] or install the API by adding its package to your .NET application via [NuGet][6].

```
PM> Install-Package GroupDocs.Viewer
```

## Convert Word Documents to View as Responsive HTML using C# {#word-to-html-responsive}

If you have MS Word DOC, DOCX documents, and want to render these documents into responsive HTML pages to look good on all the different screen sizes, here are the steps and C# code for you.

The following steps show how to convert the Word document (DOC/DOCX) to responsive HTML using .NET API.

*   Load the Word document (DOC/DOCX) using [Viewer][7] class.
*   Set the [HtmlViewOptions][8] for either embedded or external resources for the html output.
*   Set the [RenderResponsive][9] to true.
*   Call the [View][10] method of Viewer class to generate the responsive webpages of the loaded Word document.

The following just a four-liner source code renders the Word document as responsive HTML with embedded resources using C#.

{{< gist GroupDocsGists a74b1e67139b125f6f1be4709abca7cf "ConvertWordToHtmlResponsive.cs" >}}

## Get a Free API License

You can [get a free temporary license][11] in order to use the API without the evaluation limitations.

## Conclusion

To sum up, you have learned how to render the Word documents as responsive HTML pages using C#. Further, you can generate the HTML pages with embedded and external resources. You must be confident to start building your own document viewer .NET application like the one [built by GroupDocs][12].

For more about the API, you can visit [documentation][13] and the [GitHub][14] repository. In case of further queries and ambiguities, contact the free support on the [forum][15].

## See Also

*   [How to view Word documents as responsive HTML using Java][16]
*   [View CAD documents using C#][17]
*   [Play and pause animated images in web pages using C#][18]
*   [Render Word documents as Minified HTML using C#][19]







[1]: #html-viewer-dotnet-api
[2]: #word-to-html-responsive
[3]: https://products.groupdocs.com/viewer/net/
[4]: https://docs.groupdocs.com/viewer/net/supported-document-formats/
[5]: https://downloads.groupdocs.com/viewer
[6]: https://www.nuget.org/packages/groupdocs.viewer
[7]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[8]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
[9]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions/properties/renderresponsive
[10]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view/index
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://products.groupdocs.app/viewer/total
[13]: https://docs.groupdocs.com/viewer/net/
[14]: https://github.com/groupdocs-viewer
[15]: https://forum.groupdocs.com/c/assembly
[16]: https://blog.groupdocs.com/2021/09/23/view-word-documents-as-responsive-html-page-using-java/
[17]: https://blog.groupdocs.com/2021/04/27/view-cad-documents-using-charp/
[18]: https://blog.groupdocs.com/2021/02/28/play-pause-animated-gif-and-apng-in-web-pages-using-csharp/
[19]: https://blog.groupdocs.com/2022/02/25/render-word-documents-as-clean-html-using-csharp/

