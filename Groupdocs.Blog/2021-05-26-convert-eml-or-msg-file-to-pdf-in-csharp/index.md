---
title: "Convert EML or MSG file to PDF in C#"
seoTitle: "Convert EML or MSG files to PDF in C# | Emails to PDF Conversion API"
description: "Programmatically convert email messages like EML and MSG to PDF documents in C#. Use the .NET conversion API in your desktop, console, or web applications."
date: Wed, 26 May 2021 12:50:00 +0000
draft: false
url: /2021/05/26/convert-eml-or-msg-file-to-pdf-in-csharp/
aliases:
    - /2019/12/06/convert-eml-or-msg-file-to-pdf-in-csharp/
author: 'Shoaib Khan'
summary: "For sharing and referencing the email content, you may need to convert your email message to PDF format. In this article, you will learn the **conversion of email message files like EML and MSG into PDF using C#**. In one of the other blog posts, we have already discussed the [conversion of emails to PDF using Java][1]. This will help to automate the email conversions within your desktop or web-based applications."
tags: ['document conversion', 'email to pdf', 'eml to pdf in csharp', 'msg to pdf in csharp']
categories: ['GroupDocs.Conversion Product Family']
---

For sharing and referencing the email content, you may need to convert your email message to PDF format. In this article, you will learn the **conversion of email message files like EML and MSG into PDF using C#**. In one of the other blog posts, we have already discussed the [conversion of emails to PDF using Java][3]. This will help to automate the email conversions within your desktop or web-based applications.



{{< figure align=center src="images/convert-emails-to-pdf-in-dotnet.jpg" alt="Convert Email Messages to PDF in C#">}}


The following topics are covered below:

*   [Email Conversion Library for .NET][4]
*   [Conversion of MSG to PDF][5]
*   [Conversion of EML to PDF][6]

## .NET API for Email Conversion {#dotnet-email-conversion-library}

GroupDocs.Conversion for .NET is the API that allows the conversion of email messages to other formats. In this article, we will use that API for converting MSG and EML messages to PDF format using C#. Furthermore, the API allows the back and forth conversion of word-processing documents, spreadsheets, presentations, eBooks, images, and many other file formats within your .NET applications.

You can download the **DLLs** or **MSI** installer from the [downloads section][7] or install the API in your .NET application via [NuGet][8].

```
PM> Install-Package GroupDocs.Conversion
```

## Convert MSG to PDF in C# {#msg-to-pdf-in-csharp}

The following are the steps to convert the Outlook MSG files to PDF format.

1.  Load the MSG file using the [Converter][9] class.
2.  Create PDF conversion options using [PdfConvertOptions][10] class.
3.  Call the [Convert][11] method to convert the MSG file to PDF format.

The following source code converts the MSG file to PDF using C#.

{{< gist GroupDocsGists 43c2651a5028f1b20d354f5ee4c12647 "ConvertMsgToPdf.cs" >}}

Below shown is the Microsoft Outlook MSG file. Furthermore, the PDF file is also shown here which is obtained after conversion from the MSG file using the above code.



{{< figure align=center src="images/MSG-message.png" alt="MSG file to be converted to PDF" caption="MSG file">}}




{{< figure align=center src="images/converted-msg-to-pdf-in-java.png" alt="Converted PDF file from MSG" caption="PDF file converted from MSG format using the above C# code.">}}


## Convert EML to PDF using C# {#eml-to-pdf-in-csharp}

If you want to convert your email messages stored in EML format into PDF format, it can be efficiently done using similar lines of code. The following are the steps to convert EML files to PDF.

1.  Load the EML message file using the [Converter][12] class.
2.  Using [PdfConvertOptions][13] class, create conversion options for the PDF file.
3.  Call the [Convert][14] method to convert the EML files to PDF format. Pass the path of the resultant PDF file and the conversion options as parameters.

{{< gist GroupDocsGists 43c2651a5028f1b20d354f5ee4c12647 "ConvertEmlToPdf.cs" >}}

Below are the EML file and the converted PDF file screenshots, that have been converted using the above code.



{{< figure align=center src="images/EML-message.png" alt="EML file to be converted to PDF" caption="EML file">}}




{{< figure align=center src="images/converted-eml-to-pdf-in-java.png" alt="Converted PDF file from EML" caption="PDF file converted from EML format using C#.">}}


Further, you can change the appearance of the output PDF files as needed. You can visit [documentation][15] for such purposes and for many more features.

## Get a Free API License {#Get-a-Free-API-License}

You can [get a free temporary license][16] in order to use the API without the evaluation limitations.

## Conclusion

To conclude, we learned how to convert the EML and MSG files to PDF using the .NET Conversion API. Additionally, we can programmatically apply customization on PDF files to get the outcome in the desired style.

You may learn more about GroupDocs.Conversion for .NET using [documentation][17]. Many more examples are available at [GitHub][18]. For queries, contact us via the [forum][19].

## See Also

*   [Excel Spreadsheets to PDF in C#][20]
*   [Images to PDF in C#][21]
*   [Presentations to PDF in C#][22]
*   [](https://blog.groupdocs.com/2019/12/06/convert-eml-or-msg-file-to-pdf-in-csharp/)[Emails to PDF in Java][23]







[1]: https://blog.groupdocs.com/2020/09/02/convert-msg-and-eml-files-to-pdf-in-java/
[2]: https://blog.groupdocs.com/2021/05/26/convert-eml-or-msg-file-to-pdf-in-csharp/
[3]: https://blog.groupdocs.com/2020/09/02/convert-msg-and-eml-files-to-pdf-in-java/
[4]: #dotnet-email-conversion-library
[5]: #msg-to-pdf-in-csharp
[6]: #eml-to-pdf-in-csharp
[7]: https://downloads.groupdocs.com/conversion
[8]: https://www.nuget.org/packages/groupdocs.conversion
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[10]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[11]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[12]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[13]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[14]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[15]: https://docs.groupdocs.com/conversion/
[16]: https://purchase.groupdocs.com/temporary-license
[17]: https://docs.groupdocs.com/conversion/
[18]: https://github.com/groupdocs-conversion
[19]: https://forum.groupdocs.com/
[20]: https://blog.groupdocs.com/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/
[21]: https://blog.groupdocs.com/2021/05/19/convert-images-to-pdf-in-csharp/
[22]: https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/
[23]: https://blog.groupdocs.com/2020/09/02/convert-msg-and-eml-files-to-pdf-in-java/

