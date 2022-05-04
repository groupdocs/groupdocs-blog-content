---
title: "View CAD Documents using C#"
seoTitle: "View CAD files in C# using .NET API | Convert DWG DXF DGN DWF"
description: "Build your CAD files viewer in C# to view drawings. Convert DWG, DGN to render as HTML, JPG, PNG, or PDF using document viewer .NET API by GroupDocs."
date: Tue, 27 Apr 2021 20:23:00 +0000
draft: false
url: /2021/04/27/view-cad-documents-using-csharp/
aliases:
    - /2021/04/27/view-cad-documents-using-charp/
author: 'Shoaib Khan'
summary: '**CAD** (**C**omputer-**A**ided **D**esign) drawings are normally used to create architectural plans and models using CAD software programs. Some of the well-known AutoCAD file formats are **DWG, DXF, DGN, DWF**. We discussed [viewing the CAD drawings using Java][1] in a separate article. Today, in this article, we will discuss how to programmatically view CAD files using C# within .NET applications.

The following topics are covered briefly in this article:

*   .NET API to render CAD files.
*   Convert CAD files to render as HTML, JPG, PNG, or PDF.
*   Get layouts and layers of DWG.
*   Render CAD layers of DWG drawings.
*   Render CAD layouts of DWG drawings.

[Continue Reading ...][2]'
tags: ['CAD Viewer in CSharp', 'Convert DWG to HTML in CSharp', 'Convert DWG to JPG in CSharp', 'DWG Viewer using CSharp']
categories: ['GroupDocs.Viewer Product Family']
---

**CAD** (_Computer-Aided Design_) drawings are normally used to create architectural plans and models using CAD software programs. Some of the well-known AutoCAD file formats are **DWG, DXF, DGN, DWF**. We discussed [viewing the CAD drawings using Java][3] in a separate article. Today, in this article, we will discuss how to programmatically view CAD files using C# within .NET applications.

The following topics are covered below in brief:

*   [.NET API to render CAD files][4].
*   [Convert CAD files to render as HTML, JPG, PNG, or PDF][5].
*   [Get layouts and layers of DWG][6].
*   [Render CAD layers of DWG drawings][7].
*   [Render CAD layouts of DWG drawings][8].

## .NET CAD Viewer API – DWG, DXF, DWF, DGN {#dotnet-api-to-render-cad-files}

In this article, I will be using [GroupDocs.Viewer for .NET][9] that allows programmatically rendering the CAD files like DWG to PDF, JPG, PNG, and HTML within .NET applications. In addition to DWG, the API supports DWF, DGN, DWT, DXF, IFC, STL, Plotter documents, and [many more][10].

Other than the CAD file formats, API provides are the same rendering features for word-processing documents, spreadsheets, presentations, web pages, images, vectors, eBooks, Visio drawings, many source code files of different programming languages.

Download the **DLLs** or **MSI** installer from the [downloads section][11] or install the API in your .NET application via [NuGet][12].

```
PM> Install-Package GroupDocs.Viewer
```

## Convert CAD Drawings to View as HTML, PNG, JPG, or PDF in C# {#convert-cad-to-html-jpg-jpg-pdf-in-csharp}

In this article, I am only using the DWG format for the conversion and rendering to other formats with examples. Let's start with the conversion of the DWG design file to render it as HTML with embedded as well as external resource options using C#.

### Convert DWG to HTML with Embedded Resources in C#

The following are the steps of how to convert the DWG file to render as HTML.

*   Load the DWG file using [Viewer][13] class.
*   Create [HtmlViewOptions][14] using _[forEmbeddedResources][15]_ method.
*   Render .dwg to HTML using _[View][16]_ method.

The following source code converts the DWG file and renders it as HTML with embedded resources using C#.

{{< gist GroupDocsGists f6f22f03f2b4f9c984932a11e77a1b23 "ConvertDwgToHTML.cs" >}}

### Convert DWG to HTML with External Resources in C#

The following are the steps for converting the DWG file and render it as HTML file(s) with external resources.

*   Load the DWG file using the [Viewer][17] class.
*   Create [HtmlViewOptions][18] using _[forExternalResources][19]_ method.
*   Render .dwg as HTML using _[View][20]_ method.

The following source code renders the DWG file as HTML with external resources in C#.

{{< gist GroupDocsGists f6f22f03f2b4f9c984932a11e77a1b23 "ConvertDwgtoHtmlExtRes.cs" >}}

### Convert DWG to PDF, JPG, and PNG in C#

Just like the conversion to HTML format, DWG files can be rendered as PDF, PNG, and JPG format using the respective [ViewOptions][21] as follows:

*   **HTML** rendering using [HtmlViewOptions][22].
*   **JPG** rendering using [JpgViewOptions][23].
*   **PNG** rendering using [PngViewOptions][24].
*   **PDF** rendering using [PdfViewOptions][25].

## Get Layouts and Layers of DWG in C# {#get-layout-and-layers-of-dwg-in-csharp}

The CAD files can contain multiple layouts and layers, you can get these layouts and layers using the following steps.

*   Load the DWG file using the [Viewer][26] class.
*   Create the [ViewInfoOptions][27] for HTML view rendering.
*   Using Viewer, get the [CadViewInfo][28] that has layouts.
*   Get the layouts from CadViewInfo and iterate over them.
*   Similarly, get the layers from CadViewInfo and iterate over them.

The following code shows how to get the layouts and layers of ا DWG file using C#.

{{< gist GroupDocsGists f6f22f03f2b4f9c984932a11e77a1b23 "GetDwgLayoutsAndLayers.cs" >}}

## Render CAD Layers of DWG file in C# {#render-layers-of-dwg-in-csharp}

If you do not want to render all the layers but only some specific layer of the DWG, it can be done by setting layer names.

*   Load the DWG drawing using the [Viewer][29] class.
*   Create view options.
*   **Add CAD layers to the View Options**
*   Render DWG to HTML using _[View][30]_ method.

The following code renders the layers of a CAD file of DWG format in C#.

{{< gist GroupDocsGists f6f22f03f2b4f9c984932a11e77a1b23 "RenderCadLayers.cs" >}}

## Render CAD Layouts of DWG file in C# {#render-layouts-of-dwg-in-csharp}

By default, we only get the model presentation when we render a CAD file. We can set properties to render all the non-empty layouts along with the model.

*   Load the DWG drawing using the [Viewer][31] class.
*   Create view options.
*   **Set the Render Layouts property to true.**
*   Render DWG to HTML using _[View][32]_ method.

The following code renders all the non-empty layouts along with the model of a CAD drawing with DWG format in C#.

{{< gist GroupDocsGists f6f22f03f2b4f9c984932a11e77a1b23 "RenderCadLayouts.cs" >}}

## Get a Free API License {#Get-a-Free-API-License}

You can [get a free temporary license][33] in order to use the API without evaluation limitations.

## Conclusion

To conclude, I hope you have learned how to view CAD files in C# within the .NET applications. Further, you have seen, how to get and show models, layouts, and layers of CAD files within your application. You must be confident to build your own CAD Viewer using C#. You can [experience the Online applications to view any of your files][34]. These are built using GroupDocs.Viewer.

You can learn more about GroupDocs.Viewer for .NET using the [documentation][35]. In case you would have any queries, feel free to let us know via our [forum][36].

## See Also

*   [View CAD Documents using Java][37]
*   [Convert CAD Drawings to PDF in C#][38]
*   [Render Word documents as Clean HTML using C#][39]







[1]: https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/
[2]: https://blog.groupdocs.com/2021/04/27/view-cad-documents-using-charp/
[3]: https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/
[4]: #dotnet-api-to-render-cad-files
[5]: #convert-cad-to-html-jpg-jpg-pdf-in-csharp
[6]: #get-layout-and-layers-of-dwg-in-csharp
[7]: #render-layers-of-dwg-in-csharp
[8]: #render-layouts-of-dwg-in-csharp
[9]: https://products.groupdocs.com/conversion/net
[10]: https://docs.groupdocs.com/viewer/net/supported-document-formats/
[11]: https://downloads.groupdocs.com/viewer/net
[12]: https://www.nuget.org/packages/groupdocs.viewer
[13]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[14]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
[15]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions/methods/forembeddedresources/index
[16]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view/index
[17]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[18]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
[19]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions/methods/forexternalresources/index
[20]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view/index
[21]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/viewoptions
[22]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
[23]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/jpgviewoptions
[24]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pngviewoptions
[25]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
[26]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[27]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/viewinfooptions
[28]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.results/CadViewInfo
[29]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[30]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view/index
[31]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[32]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view/index
[33]: https://purchase.groupdocs.com/temporary-license
[34]: https://products.groupdocs.app/viewer/family
[35]: https://docs.groupdocs.com/viewer/net/
[36]: https://forum.groupdocs.com/
[37]: https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/
[38]: https://blog.groupdocs.com/2020/11/08/convert-cad-drawings-to-pdf-in-csharp/
[39]: https://blog.groupdocs.com/2022/02/25/render-word-documents-as-clean-html-using-csharp/

