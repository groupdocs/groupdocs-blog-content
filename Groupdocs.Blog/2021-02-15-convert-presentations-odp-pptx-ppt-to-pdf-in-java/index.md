---
title: 'Convert Presentations to PDF in Java'
date: Mon, 15 Feb 2021 17:30:00 +0000
draft: false
url: /2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/
author: 'Shoaib Khan'
summary: 'As PDF is the popular portable document format, so there comes the need to convert documents of other formats to PDF. Today, we will see **different ways to convert PPT, PPTX, or ODP presentations to PDF in Java**. In an earlier post, we have seen [how to convert presentations using C#][1].

[Continue Reading ...][2]'
tags: ['Convert ODP to PDF in Java', 'Convert PPT to PDF in Java', 'Convert PPTX to PDF in Java', 'Convert Presentation to PDF in Java']
categories: ['GroupDocs.Conversion Product Family']
---

As PDF is the popular portable document format, so there comes the need to convert documents of other formats to PDF. Today, we will see **different ways to convert PPT, PPTX, or ODP presentations to PDF in Java**. In an earlier post, we have seen [how to convert presentations using C#][3]. The following scenarios will be covered in this article:

*   [Presentation Conversion Java API][4]
*   [Convert PPT, PPTX, or ODP Presentations to PDF in Java][5]
*   [Convert Specific Slides of Presentation to PDF][6]
*   [Converting Consecutive Slides of Presentation to PDF][7]
*   [Convert Password Protected Presentation to PDF][8]



{{< figure align=center src="images/convert-ppt-to-pdf-in-java.jpg" alt="PPTX to PDF in Java">}}


## Presentation Conversion Java API {#presentation-conversion-java-api}

For the conversion of presentations to PDF format, I will be using [GroupDocs.Conversion for Java][9] in the examples of this article. Along with this feature, the API supports a long [list of file formats to convert into one another in Java][10]. These include converting **eBooks, word-processing documents, spreadsheets, images, web-pages, emails, CAD**, and many other document formats.

### Download or Configure



{{< figure align=center src="images/groupdocs-conversion-java.png" alt="Convert Documents and Images using Java">}}


[Download the JAR][11] from downloads or in the case of the Maven-based Java application, add the following repository and dependency configurations in the pom.xml.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>21.1</version> 
</dependency>
```

## Convert PPT, PPTX, or ODP Presentations to PDF in Java {#convert-presentations-to-pdf-in-java}

Once the library is configured in your project, you now have various options to convert your presentations into portable PDF format. Let start with the simplest and quickest way to convert the whole presentation file.

*   Create [Converter][12] class object with the source document.
*   Instantiate [PdfConvertOptions][13] object.
*   Call **convert** method of Converter class. Pass the output file path and the created PdfConvertOptions.

Here is the 3 liner Java code that converts the PowerPoint PPTX presentation file into PDF.

{{< gist GroupDocsGists bba9bf2911d17f33dc678fb9373e6c0e "ConvertPresentationToPDF.java" >}}

Similarly, you can convert the presentations of Microsoft PowerPoint PPT format or OpenOffice Impress ODP format to PDF with the same examples of this article.

## Convert Specific Slides of Presentation to PDF in Java {#convert-ppt-slides-to-pdf-in-java}

If you want to skip few slides from the presentation, or just want to convert some specific slides to PDF instead of converting the whole presentation, **setPages** is the method you are searching for.

The below code converts the selected pages of the PPTX presentation to PDF in Java.

{{< gist GroupDocsGists bba9bf2911d17f33dc678fb9373e6c0e "ConvertSlidesToPDF.java" >}}

## Convert Consecutive Slides of Presentation to PDF in Java {#convert-ppt-consecutive-slides-to-pdf}

You can also select the specific set of slides in sequence to get them converted into PDF. Just mention the starting slide number, and then the number of slides in the sequence ahead.

*   Start with initialization of [Converter][14] object with the presentation file.
*   Set starting page number.
*   Set number of consecutive pages.
*   Convert slides to PDF using the **convert** method.

Here is the Java code showing the above steps and converting 3 consecutive slides of a PPTX presentation into PDF starting from the 2nd slide.

{{< gist GroupDocsGists bba9bf2911d17f33dc678fb9373e6c0e "ConvertConsecutiveSlidesToPDF.java" >}}

## Convert Password Protected Presentation to PDF in Java {#convert-password-protected-ppt-to-pdf-in-java}

There are many load options while loading any presentation. You can provide the **password** for the protected presentation using **setPassword** method. After loading the presentation with the password, you can convert it just like any other presentation we converted before.

The following code converts a password protected PPTX presentation to PDF in Java after providing the password while loading.

{{< gist GroupDocsGists bba9bf2911d17f33dc678fb9373e6c0e "ConvertPasswordProtectedPresentationToPDF.java" >}}

Further, you can set the following load options:

*   Specify the presentation **format**, however, it is auto-detected.
*   Show or hide the **comments**.
*   Show or hide **hidden slides**.
*   Specify the substitute font for the missing fonts.

## Conclusion

After trying the above examples, you must be confident to programmatically convert presentations and slides to PDF in your Java applications. You can try to build your own application using the above-highlighted features for MS PowerPoint and OpenOffice Impress presentation formats like PPT, PPTX, ODP, etc.

## Need Help?

First, see more about the conversion features of the API from the [documentation][15]. We would be there on the [forum][16] to help you out of any further facing issues.

## See Also

*   [Converting Presentations (PPT, PPTX) to PDF in C#][17]







[1]: https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/
[2]: https://blog.groupdocs.com/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/
[3]: https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/
[4]: #presentation-conversion-java-api
[5]: #convert-presentations-to-pdf-in-java
[6]: #convert-ppt-slides-to-pdf-in-java
[7]: #convert-ppt-consecutive-slides-to-pdf
[8]: #convert-password-protected-ppt-to-pdf-in-java
[9]: https://products.groupdocs.com/conversion/java
[10]: https://docs.groupdocs.com/conversion/java/supported-document-formats/
[11]: https://downloads.groupdocs.com/conversion/java
[12]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[13]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/PdfConvertOptions
[14]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[15]: https://docs.groupdocs.com/conversion/java
[16]: https://forum.groupdocs.com/c/conversion
[17]: https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/

