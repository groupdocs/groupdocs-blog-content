---
title: 'Convert PowerPoint PPT, PPTX and OpenOffice Presentations to PDF in C#'
date: Thu, 05 Mar 2020 21:59:00 +0000
draft: false
url: /2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/
aliases:
    - /2020/03/05/convert-pptx-to-pdf-in-csharp/
    - /2020/03/05/convert-ppt-to-pdf-in-csharp/
    - /2020/03/05/convert-pptx-ppt-to-pdf-in-csharp/
author: 'Shoaib Khan'
summary: '[PDF][1] is no doubt the [Portable Document Format][2], which is one of the most commonly used file formats. [PPT][3] and [PPTX][4] formats of Microsoft PowerPoint share the popularity in business documents. Due to the popularity of both the document formats and the fixed layout nature of PDF format, there comes the requirement to **convert PPT/PPTX to PDF** format.'
tags: ['Convert PPT to PDF in CSharp', 'Convert PPTX to PDF in CSharp', 'CSharp PPT to PDF', 'CSharp PPTX to PDF']
categories: ['GroupDocs.Conversion Product Family']
---

[PDF][5] is no doubt the [Portable Document Format][6], which is one of the most commonly used file formats. [PPT][7] and [PPTX][8] formats of Microsoft PowerPoint share the popularity in business documents. Due to the popularity of both the document formats and the fixed layout nature of PDF format, there comes the requirement to **convert PPT/PPTX to PDF** format.



{{< figure align=center src="images/Convert-PPT-to-PDF-csharp.png" alt="PPTX to PDF in C#">}}


Considering the .NET developers today, this article will be providing the solution to the above-mentioned file format conversion. GroupDocs supports the conversion of [50+ document formats][9], hence providing On-Premise APIs (.NET & Java), Cloud APIs, and online [Conversion Apps][10]. After this article, you will get familiar with different ways to convert Microsoft and OpenOffice presentations using [GroupDocs.Conversion for .NET][11].

The following topics are discussed below:

*   [How to Convert Complete Presentation to PDF][12]
*   [Convert Specific PPT slides to PDF][13]
*   [Convert Sequential Subset of Slides to PDF][14]
*   [Possible Conversions of PowerPoint PPT/PPTX format][15]
*   [Convert Presentation with Advanced Options][16]
*   [Apply Watermark while Conversion to PDF][17]

## Convert PPT to PDF in C# {#ppt-to-pdf}

[GroupDocs.Conversion][18] has made this so easy; the popular and demanding conversion of presentation files. Just with the below-mentioned two lines of CSharp code, you can quickly convert any type of presentation like PPTX or PPT to PDF.

*   Create a new instance of [Converter][19] Class with the source document.
*   Instantiate [PdfConvertOptions][20] object.
*   Call [Convert()][21] method of Converter class.

The following code sample converts the complete PowerPoint PPTX to PDF in C#.

{{< gist GroupDocsGists 3b2358dd1dcdf2281bd21c0f01ceef0c "ConvertPptToPDF.cs" >}}

## Convert Specific Slides of PPT to PDF in C# {#specific-slides}

We could have a requirement to convert only the selected slides instead of converting the whole presentation. GroupDocs.Conversion allows converting the specific slides of a presentation to the resultant PDF document. Below are the steps and C# source code that shows, how to achieve this.

*   **Load** the presentation using [Converter][22] class.
*   Prepare [ConversionOptions][23] for PDF.
*   **List the selected slide numbers** to convert.
*   **Convert** to PDF using [Convert()][24] method.

The following source code converts slides number 1, and 3 of a presentation to PDF.

{{< gist GroupDocsGists 3b2358dd1dcdf2281bd21c0f01ceef0c "ConvertSpecifiedSlidesToPDF.cs" >}}

## Convert Consecutive Slides of PPTX to PDF using C# {#successive-slides}

With the little modification in the requirement, below is the little change in the code. Certain consecutive slides of the presentation can be selected to get these converted into PDF format. Just set the starting page number and number of successive pages ahead.

*   **Load** the presentation file using [Converter][25] class.
*   Set the **starting page number** and the **count of sequentials slides** ahead using [PDF Conversion Options][26].
*   **Save** the selected slides in PDF format using [Convert()][27] method.

The following code snippet converts the slide numbers 2, 3, and 4 to PDF format in C#.

{{< gist GroupDocsGists 3b2358dd1dcdf2281bd21c0f01ceef0c "ConvertConsecutiveSlidesToPDF.cs" >}}

## Possible Conversions of PPT/PPTX {#possible-conversions}

This is not only the PDF that could be the target document format while conversion. You can refer to the [documentation for all the possible conversions][28]. More important for developers, we can retrieve all the possible conversion formats of PPT/PPTX presentations by simply calling the GetPossibleConversions() method of the Converter class.

*   Define the source format using the [Converter][29] class.
*   Get all the possible conversions of the source format using [GetPossibleConversions()][30] method.

The following source code shows how to retrieve all the possible conversions of the PPTX formats using C#.

{{< gist GroupDocsGists 3b2358dd1dcdf2281bd21c0f01ceef0c "PossiblePptConversions.cs" >}}

## Convert PPT to PDF with Advanced Options {#ppt-to-pdf-adv}

There are many more options while converting the presentations. These options are rarely needed, however when required, they prove their importance.  [**PdfConvertOptions**][31] gives control over conversion results while converting to PDF. Along with the common conversion options, it has many additional options that can be seen in detail from the [documentation][32]. Just for an overview, we can customize the PPT conversion with the mentioned options and much more:

*   [Zoom][33]
*   [Margins][34]
*   [GrayScale][35]
*   [Formatting Options][36]
*   [Image Quality][37]
*   [Rotation][38]
*   [Watermark][39]

{{< gist GroupDocsGists 3b2358dd1dcdf2281bd21c0f01ceef0c "PptToPdfAdvanced.cs" >}}

## Add Watermark while converting PPTX or PPT to PDF in C# {#watermarked}

Want to secure your presentation while converting it to PDF format? Leave a watermark on the resultant PDF. The below-mentioned steps and source code shows how to put a watermark when a PPT/PPTX presentation is converted to PDF format.

*   **Load** the PPT file using [Converter][40] class.
*   **Prepare the [text watermark options][41]** and define:
    
    *   Watermark Text & Font
    
    *   Watermark Color
    *   Widht and Height
    *   Rotation Angle
    *   Tranparency
*   **Add the prepared watermark** to [PDF conversion options][42].
*   **Save** the presentation to PDF using [Convert()][43] method.

The following C# code example adds a watermark with rotation angle and transparency while converting the PPT to PDF.

{{< gist GroupDocsGists 3b2358dd1dcdf2281bd21c0f01ceef0c "WatermarkPPT.cs" >}}

## Conclusion

Let's summarize what we discussed. We learned different ways to convert PPT to PDF format in C#. We separately looked at the steps and code example for converting a **specific list of slides**, any **successive subset** of presentation slides, and conversion of **PPT to PDF with a customized watermark** and other options. Learn more about **GroupDocs.Conversion** from the [documentation][44].

## Let's Talk

You can build your own application using the above-highlighted features. We will be delighted if you contact us on the [forum][45] to discuss, solve a problem, or share your feedback. Have a nice development time.

## See Also

*   [Convert PowerPoint and OpenOffice Presentations to PDF in Java][46]







[1]: https://wiki.fileformat.com/view/pdf/
[2]: https://en.wikipedia.org/wiki/PDF
[3]: https://wiki.fileformat.com/presentation/ppt/
[4]: https://wiki.fileformat.com/presentation/pptx/
[5]: https://wiki.fileformat.com/view/pdf/
[6]: https://en.wikipedia.org/wiki/PDF
[7]: https://wiki.fileformat.com/presentation/ppt/
[8]: https://wiki.fileformat.com/presentation/pptx/
[9]: https://docs.groupdocs.com/conversion/net/supported-document-formats/
[10]: https://products.groupdocs.app/conversion/family
[11]: https://products.groupdocs.com/conversion/net
[12]: #ppt-to-pdf
[13]: #specific-slides
[14]: #successive-slides
[15]: #possible-conversions
[16]: #ppt-to-pdf-adv
[17]: #watermarked
[18]: https://products.groupdocs.com/conversion
[19]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion/converter
[20]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions
[21]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion/converter/methods/convert/2
[22]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[23]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[24]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[25]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[26]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[27]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[28]: https://docs.groupdocs.com/conversion/net/supported-document-formats/
[29]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[30]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/getpossibleconversions/index
[31]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions
[32]: https://docs.groupdocs.com/conversion/net/convert-to-pdf-with-advanced-options/#ConverttoPDFwithadvancedoptions-PdfOptions
[33]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfoptions/properties/zoom
[34]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/marginleft
[35]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfoptions/properties/grayscale
[36]: https://docs.groupdocs.com/display/conversionnet/Convert+to+PDF+with+advanced+options#ConverttoPDFwithadvancedoptions-PdfFormattingOptions
[37]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfoptimizationoptions/properties/imagequality
[38]: https://apireference.groupdocs.com/net/conversion/groupdocs.conversion.options.convert/pdfconvertoptions/properties/rotate
[39]: https://apireference.groupdocs.com/conversion/net
[40]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[41]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/watermarktextoptions
[42]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[43]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[44]: https://docs.groupdocs.com/conversion/net/
[45]: https://forum.groupdocs.com/c/conversion
[46]: https://blog.groupdocs.com/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/

