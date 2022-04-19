---
title: 'STL File Viewer using C#'
date: Tue, 28 Dec 2021 11:00:00 +0000
draft: false
url: /2021/12/28/stl-file-viewer-using-csharp/
author: 'Shoaib Khan'
summary: 'STL (STereoLithography) file format is used for 3D CAD drawings and 3D printing. There are several requirements when the developers are required to programmatically render STL files into various other formats. One of the reasons for conversion is better portability. In this article, you will learn how to render the STL files into PDF format using C#. Additionally, we will convert the STL files to HTML, JPG, and PNG format within .NET application using examples.

The following topics are discussed in this article:

*   STL Viewer .NET API
*   View STL as PDF
*   View STL as HTML, JPG, PNG'
tags: ['STL as HTML', 'STL as JPG', 'STL as PNG', 'STL Viewer', 'STL Viewer using C#', 'View STL', 'View STL as PDF']
categories: ['GroupDocs.Viewer Product Family']
---

STL (**ST**ereo**L**ithography) file format is used for 3D CAD drawings and 3D printing. There are several requirements when the developers are required to programmatically render STL files into various other formats. One of the reasons for conversion is better portability. In this article, you will learn **how to render the STL files into PDF format using C#**. Additionally, we will convert the **STL files to HTML, JPG, and PNG format** within .NET application using examples.

The following topics are discussed below:

*   [STL Viewer .NET API][1]
*   [View STL as PDF][2]
*   [View STL as HTML, JPG, PNG][3]

## .NET API to View STL Files {#stl-viewer-dotnet-api}

[GroupDocs.Viewer][4] showcases [document viewer .NET API][5] that allows rendering the documents into PDF, HTML, and images within the .NET application. In this article, we will use it in examples to convert the STL files into different other file formats.

You can download the DLLs or MSI installer from the [downloads section][6] or install the API in your .NET application via [NuGet][7].

```
PM> Install-Package GroupDocs.Viewer
```

## View STL File as PDF using C# {#stl-to-pdf}

It is often required to convert the stereolithography STL format to PDF format due to its high portability. The following steps show how to convert the STL files into PDF format using C#.

*   Load the STL file using the [Viewer][8] class.
*   Prepare the PDF rendering options using the [PdfViewOptions][9] class.
*   Use the [View()][10] method to render STL file as PDF.

The following C# code example renders the STL files into PDF format.

{{< gist GroupDocsGists 07d6814f87a48e2a208698b1dfeaab52 "ViewStlAsPdf.cs" >}}

## View STL File as HTML, JPG, or PNG using C# {#convert-stl-using-csharp}

Similarly, you can convert the STL files into other formats according to the requirement. The following steps help you to render the STL files into various other formats using C#.

*   Load the **STL** file using the [Viewer][11] class.
*   Prepare the rendering options according to the conversion format:
    *   **HTML** rendering needs the [](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions)[HtmlViewOptions][12] class. (You can use either embedded or external resources)
    *   **JPG** rendering uses the [JpgViewOptions][13] class.
    *   **PNG** rendering requires the [PngViewOptions][14] class.
*   Use the [View()][15] method to render STL file as HTML, JPG, or PNG.

Below are the C# examples that separately render STL files into each format using the respective format options.

### STL to HTML using C# {#stl-to-html}

The following C# code converts the STL file into HTML with embedded resources. Similarly, you can convert to HTML with external resources.

{{< gist GroupDocsGists 07d6814f87a48e2a208698b1dfeaab52 "ViewStlAsHtml.cs" >}}

### STL to JPG using C# {#stl-to-jpg}

The following C# code converts the STL file into JPG image format.

{{< gist GroupDocsGists 07d6814f87a48e2a208698b1dfeaab52 "ViewStlAsJpg.cs" >}}

### STL to PNG using C# {#stl-to-png}

The following C# code converts the STL file into PNG image format.

{{< gist GroupDocsGists 07d6814f87a48e2a208698b1dfeaab52 "ViewStlAsPng.cs" >}}

## Get a Free API License

You can use the APIs for free by [getting a temporary license][16].

## Conclusion

To conclude, we learned how to render the STL files into other formats. Specifically, we converted the STL files into PDF, HTML, JPG, and PNG formats using the C# example. You can build your own STL viewer application like [Groupdocs.Viewer Online App][17].

To learn more about [GroupDocs.Viewer for .NET][18], visit its [documentation][19]. For queries, contact us via the [forum][20].

## See Also

*   [Source Code to PDF in C#][21]
*   [View CAD Documents using C#][22]
*   [Word Documents as HTML Responsive Page using C#][23]







[1]: #stl-viewer-dotnet-api
[2]: #stl-to-pdf
[3]: #convert-stl-using-csharp
[4]: https://products.groupdocs.com/viewer/
[5]: https://products.groupdocs.com/viewer/net/
[6]: https://downloads.groupdocs.com/viewer/net
[7]: https://www.nuget.org/packages/groupdocs.viewer
[8]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[9]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
[10]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
[11]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[12]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
[13]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/jpgviewoptions
[14]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pngviewoptions
[15]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
[16]: https://purchase.groupdocs.com/temporary-license
[17]: https://products.groupdocs.app/viewer
[18]: https://products.groupdocs.com/viewer/net/
[19]: https://docs.groupdocs.com/viewer/
[20]: https://forum.groupdocs.com/
[21]: https://blog.groupdocs.com/2021/12/03/convert-source-code-to-pdf-in-csharp/
[22]: https://blog.groupdocs.com/2021/04/27/view-cad-documents-using-csharp/
[23]: https://blog.groupdocs.com/2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/

