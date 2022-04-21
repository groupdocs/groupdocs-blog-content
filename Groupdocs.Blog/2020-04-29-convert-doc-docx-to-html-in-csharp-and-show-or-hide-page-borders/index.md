---
title: 'Show and Hide Page Borders while Converting Documents to HTML in C#'
date: Wed, 29 Apr 2020 20:18:10 +0000
draft: false
url: /2020/04/29/convert-doc-docx-to-html-in-csharp-and-show-or-hide-page-borders/
author: 'Shoaib Khan'
summary: 'Either you want to convert a document to HTML format to get the content for your website, or you have come across an online document submission website that requires documents to be submitted in HTML format. In either case, you need a **DOC to HTML converter**. However, if you need to convert your **documents to HTML programmatically**, then this article is for you only. This article will cover the following ways to convert documents to HTML in C#:'
tags: ['convert document to html in csharp', 'convert docx to html', 'convert docx to html in csharp', 'convert to html', 'show or hide html page borders']
categories: ['GroupDocs.Conversion Product Family']
---



{{< figure align=center src="images/convert-doc-to-html-with-show-and-hide-borders.png" alt="Convert DOCX to HTML in CSharp">}}


Either you want to convert a document to HTML format to get the content for your website, or you have come across an online document submission website that requires documents to be submitted in HTML format. In either case, you need a **DOC to HTML converter**. However, if you need to convert your **documents to HTML programmatically**, then this article is for you only. This article will cover the following ways to convert documents to HTML in C#:

*   Simplest conversion of documents like DOCX to HTML in C#.
*   Convert to HTML with customized options.
*   Convert using the option to show or hide page borders.

## C# Document Conversion Library

[GroupDocs.Conversion for .NET][1] is an easy to use powerful API with the ability to convert any document from the wide list of [supported document formats][2] into any supported target formats. You may download the API from the [downloads][3] section or install it from [NuGet][4].

## Convert DOCX to HTML in C# - Simple

This is the simplest and very useful conversion. I better say that you can convert any of your documents to the HTML format. Just check your format from the [supported formats list][5] and go-ahead to get it converted.

*   Create the instance of the [Converter][6] class to start with your source document.
*   Instantiate [MarkupConvertOptions][7] object.
*   Call the [Convert][8] method of the Converter class.
*   That's it.

Your document will be converted to HTML and the resultant document will be there in your repository. The following small code sample shows the conversion of a **DOCX file into HTML** using the Converter class in C#.

```
// Converting DOCX to HTML in C#
using (Converter converter = new Converter("document.docx"))
{
    MarkupConvertOptions options = new MarkupConvertOptions();
    converter.Convert("converted.html", options);
}
```

## Convert DOC/DOCX to HTML with Customized Options

GroupDocs.Conversion provides different other options to get the desired conversion result. The customized options include:

*   Fixed Layout
*   Fixed Layout - Show Borders
*   Format
*   Page Number
*   Pages
*   Pages Count
*   Use PDF
*   Watermark
*   Zoom

You may visit the [documentation][9] or [GitHub samples][10] to see each option in detail. I will show some of the customizations while again converting the DOCX to HTML format in below code sample.

```
// Converting DOCX to HTML in C# with advance options.
using (Converter converter = new Converter("document.docx"))
{
    MarkupConvertOptions options = new MarkupConvertOptions
    { // Setting customized options
        PageNumber = 2,
        PagesCount = 1,
        FixedLayout = true
    };
    converter.Convert("converted.html", options);
}
```

## Convert DOC/DOCX to HTML - Show or Hide Page Borders

Last but not least, you can now control the visibility of page borders while converting documents to HTML in C#. The GroupDocs.Conversion for .NET gives this control to the C# programmers. The below example shows that by setting the [FixedLayoutShowBorders][11] property of [MarkupConvertOptions][12] class to true or false, you can show or hide the page borders in the resultant HTML document.

```
// Converting DOCX to HTML in C# with show or hide borders control.
using (Converter converter = new Converter("document.docx"))
{
    MarkupConvertOptions options = new MarkupConvertOptions
    {
        PageNumber = 2,
        FixedLayout = true,
        PagesCount = 1,
        FixedLayoutShowBorders = false
    };
    converter.Convert("converted.html", options);
}
```

Images below showing the original DOCX document and the converted HTML with and without page borders.



{{< figure align=center src="images/word-docx-document-1-759x1024.png" alt="Docx document to convert into HTML" caption="Original DOCX Document">}}




{{< figure align=center src="images/doc-to-html-file-with-borders-and-no-borders-1024x716.jpg" alt="HTML File with page borders and no borders." caption="<em>The above figure shows the HTML files that are converted from DOCX with show borders and do not show borders options.</em>">}}


## Learn more about GroupDocs.Conversion

*   [Documentation][13]
*   [Source code examples][14]
*   [GroupDocs.Conversion - The Document & Image Conversion Solution][15]

**Let's talk more @** [Free Support Forum][16].







[1]: https://products.groupdocs.com/conversion/net
[2]: https://docs.groupdocs.com/display/conversionnet/Supported+Document+Formats
[3]: https://downloads.groupdocs.com/conversion/net
[4]: https://www.nuget.org/packages/groupdocs.conversion
[5]: https://docs.groupdocs.com/display/conversionnet/Supported+Document+Formats
[6]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[7]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/markupconvertoptions
[8]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.converter/convert/methods/4
[9]: https://docs.groupdocs.com/display/conversionnet/Convert+to+HTML+with+advanced+options
[10]: https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET/blob/master/Examples/GroupDocs.Conversion.Examples.CSharp/AdvancedUsage/Converting/ConvertToHtmlWithAdvancedOptions.cs
[11]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/markupconvertoptions/properties/fixedlayoutshowborders
[12]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/markupconvertoptions
[13]: https://docs.groupdocs.com/display/conversionnet/Getting+Started
[14]: https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET
[15]: https://products.groupdocs.com/conversion
[16]: https://forum.groupdocs.com/c/conversion

