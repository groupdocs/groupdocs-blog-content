---
title: 'Convert AutoCAD DWG Drawings to PDF in Java'
date: Tue, 08 Feb 2022 16:48:40 +0000
draft: false
url: /2022/02/08/convert-cad-drawings-to-pdf-in-java/
aliases:
    - /2020/10/31/convert-cad-drawings-to-pdf-in-java/
author: 'Shoaib Khan'
summary: '**CAD** stands for Computer-Aided Design. It is used to create 2D and 3D architectural designs, computer animations, special effects in movies, technical drawings, and much more. **PDF** is one of the most well-known file formats that is famous due to its portability. Here comes the need to convert CAD files to PDF format when such technical drawings are to be transferred to a normal user who is not equipped with the technical software that supports CAD drawings. This article will help programmers to add the feature to **convert** different **CAD formats** like **DWG, DGN, or DWF into PDF in Java** applications.'
tags: ['convert cad to pdf in java', 'convert dgn to pdf in java', 'convert dwf to pdf', 'convert dwg to pdf', 'convert dwg to pdf in java', 'dwg to pdf', 'DWG to PDF in Java']
categories: ['GroupDocs.Conversion Product Family']
---

**CAD** stands for Computer-Aided Design. It is used to create 2D and 3D architectural designs, computer animations, special effects in movies, technical drawings, and much more. **PDF** is one of the most well-known file formats that is famous due to its portability. Here comes the need to convert CAD files to PDF format when such technical drawings are to be transferred to a normal user who is not equipped with the technical software that supports CAD drawings. This article guides programmers on how to **convert** different **CAD formats** like **DWG to PDF in Java**.



{{< figure align=center src="images/convert-cad-drawings-to-pdf-using-java.png" alt="Convert CAD Drawings to PDF in Java">}}


The following topics are covered below:

*   [CAD Drawings Conversion Java Library](#cad-conversion-java-lib)
*   [Converting DWG to PDF](#dwg-to-pdf)

## CAD Drawings Conversion Java Library {#cad-conversion-java-lib}



{{< figure align=center src="images/groupdocs-conversion-java.png" alt="Convert Documents and Images using Java">}}


[GroupDocs.Conversion for Java](https://products.groupdocs.com/conversion/java) is the document and image conversion library for Java-based applications. It supports various file formats for conversion from one format to another, which include Word-processing documents, spreadsheets, presentations, images, portable documents, web pages, photoshop formats, Microsoft Project files, emails, Vector graphics by Microsoft Visio, CAD drawings, Page descriptive languages, etc.

In the examples below, I will use this API for the **conversion of CAD drawings to PDF in Java**. It will be better if you download the library and prepare the development environment beforehand. You may get the API from the [downloads](https://downloads.groupdocs.com/conversion/java) section or by the following configuration in your maven-based Java applications.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>21.10.1</version> 
</dependency>
```

## Convert DWG to PDF in Java {#dwg-to-pdf}

Let's move to quickly convert the drawing. These steps allow you to easily convert the AutoCAD DWG drawings to a PDF file in Java with a lot of customization options.

*   Set the **loading options** using the [CadLoadOptions](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.load/CadLoadOptions) class.
*   Specify **layouts** using [setLayoutNames()](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.load/CadLoadOptions#setLayoutNames(java.lang.String%5B%5D)) method.
*   **Load** the DWG drawing using the [Conveter](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.load/CadLoadOptions) class.
*   Specify **conversion options** like **width**, **height**, and **format**.
*   **Convert** to PDF using the appropriate [convert()](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)) method.

Here is the complete Java code that demonstrates the above steps and converts a DWG file into PDF format.

{{< gist GroupDocsGists f1e0ef5d80ba4f8bb44aa96085fb932b "ConvertCadToPDF.java" >}}

With a little change in code, you can also convert DGN and DWF files accordingly. For a file format that does not support layouts, we will not use the **setLayoutNames** method.

## Conclusion

To conclude, we learned to convert the CAD files into PDF format. Specifically, we converted the AutoCAD DWG drawings to PDF format using the Java API. You can now try building your online CAD to PDF converter Java application using [GroupDocs.Conversion](https://products.groupdocs.com/conversion/). In case of any confusion, you may contact the **Free Support Team**, which always feels good to help you on the [forum](https://forum.groupdocs.com/).

## See Also

*   [View CAD Documents using Java](https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/)
*   [How to Rearrange PDF Pages in Java](https://blog.groupdocs.com/2022/03/10/move-pdf-pages-in-java/)
*   [Watermark PDF Files in Java](https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/)
*   [Password Protection of PDF Files in Java](https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/)
*   [Different Ways to Split PDF Files in Java](https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/)
*   [Convert CAD Drawings to PDF in C#](https://blog.groupdocs.com/2020/11/08/convert-cad-drawings-to-pdf-in-csharp/)




