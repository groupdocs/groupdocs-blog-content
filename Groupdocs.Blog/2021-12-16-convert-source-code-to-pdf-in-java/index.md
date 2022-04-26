---
title: 'Convert Source Code to PDF in Java'
date: Thu, 16 Dec 2021 16:44:27 +0000
draft: false
url: /2021/12/16/convert-source-code-to-pdf-in-java/
author: 'Shoaib Khan'
summary: 'If you want to share your code snippets, you can convert them into PDF format. In this article, we will discuss **how to convert Java, Python, C++, PHP source code to PDF** format within Java application. Additionally, we will also learn to password-protect the converted PDF files.

The following topics are discussed in this article:

*   Source Code Conversion Java API
*   Java to PDF using Java
*   Python to PDF using Java
*   PHP to PDF - Protect the PDF file'
tags: ['Convert Source Code to PDF in Java', 'Java to PDF', 'PHP to PDF', 'Python Code to PDF', 'Source Code to PDF']
categories: ['GroupDocs.Viewer Product Family']
---

If you want to share your code snippets, you can convert them into PDF format. In order to do this, we will discuss **how to convert Java, PHP, Python, **C#, C++** source code to PDF** format within Java application. Additionally, we will also learn to password-protect the converted PDF files.



{{< figure align=center src="images/convert-source-code-to-pdf-in-java.jpg" alt="Convert Source Code to PDF">}}


The following topics are discussed below:

*   [Source Code Conversion Java API][1]
*   [Java to PDF using Java][2]
*   [Python to PDF using Java][3]
*   [PHP to PDF - Protect the PDF file][4]

## Source Code Converter Java API {#source-code-converter-java-api}

[GroupDocs.Viewer][5] provides Java API to [render files into different formats][6] like PDF, HTML, and image formats. I will use this API to convert source code files of different languages into PDF format.

You can download the **JAR** file from the [downloads section][7] or use the latest repository and dependency [Maven][8] configurations within your Java applications.

```
<repository>
	<id>GroupDocsArtifactRepository</id>
	<name>GroupDocs Artifact Repository</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-viewer</artifactId>
        <version>21.11</version> 
</dependency>
```

## Convert Java Code to PDF {#java-to-pdf}

Let's quickly come to the objective and see the results. The following steps allow you to convert the Java source code file to PDF.

*   Load the Java file using the [Viewer][9] class.
*   Define the output file and options using the [PdfViewOptions][10] class.
*   Convert the loaded Java file to PDF using the appropriate [view()][11] method.

The following Java code snippet converts the complete Java source code file to PDF format.

{{< gist GroupDocsGists 07263be03154d33914f5671e6254513f "JavaToPdf.java" >}}

Here is the converted PDF of the Java file using the above Java code. If you want to add security to the resultant PDF file, jump to the section below where the [PHP file gets converted][12].



{{< figure align=center src="images/java-to-pdf.jpg" alt="Java source file converted to PDF">}}


## Convert Python Code to PDF using Java {#python-to-pdf}

Do you really think, there will be a separate code for converting the Python code to PDF and it will be somewhat different from converting a Java file? No, it's the same, just hand over the right .py file. The following steps allow you to convert the Python code to PDF.

*   Load the Python file using the [Viewer][13] class.
*   Set the output file path and options using the [PdfViewOptions][14] class.
*   Convert the loaded .py file to PDF using the suitable [view()][15] method.

The following Java code snippet converts the complete Python source code file into PDF format.

{{< gist GroupDocsGists 07263be03154d33914f5671e6254513f "PythonToPdf.java" >}}

## Convert PHP to PDF using Java {#php-to-pdf}

Similarly, you can also convert the PHP files. One more thing to add here; while converting your source code files, you can add security to the PDF files. Let's protect the PHP code when it is converted to PDF format. The following steps show how to convert the PHP file to PDF.

*   Load the PHP file using the [Viewer][16] class.
*   Define the security using [Security][17] class.
*   Set the passwords for opening and editing the resultant PDF file.
*   Define the output file and its options using the [PdfViewOptions][18] class.
*   Call the [view()][19] method to render the loaded PHP file to the protected PDF.

The following Java code example converts the PHP source code file to a password-protected PDF file.

{{< gist GroupDocsGists 07263be03154d33914f5671e6254513f "PhpToPdfProtected.java" >}}

Similarly, you can use this code for other source codes of [supported programming languages][20] like C#, C/C++, GROOVY, Ruby, and more.

## Get a Free API License

You can [get a free temporary license][21] to use the API without the evaluation limitations.

## Conclusion

To conclude, we learned to convert source code files of different programming languages to PDF format using Java. We converted the Java, Python, and PHP files into PDF format. Additionally, we learned how to password-protect the resultant PDF file. Using this API, you can start building your own source code viewer Java application.

To learn more about **GroupDocs.Viewer**, visit the [documentation][22]. For queries, contact us via the [forum][23].

## See Also

*   [Convert Images to PDF in Java][24]
*   [Convert Excel Sheets to PDF in Java][25]
*   [View Word Documents as Responsive HTML Page using Java][26]







[1]: #source-code-converter-java-api
[2]: #java-to-pdf
[3]: #python-to-pdf
[4]: #php-to-pdf
[5]: https://products.groupdocs.com/viewer/
[6]: https://docs.groupdocs.com/viewer/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/viewer
[8]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs
[9]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[10]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PdfViewOptions
[11]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[12]: #php-to-pdf
[13]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[14]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PdfViewOptions
[15]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[16]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[17]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/Security
[18]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PdfViewOptions
[19]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[20]: https://docs.groupdocs.com/viewer/java/supported-document-formats/
[21]: https://purchase.groupdocs.com/temporary-license
[22]: https://docs.groupdocs.com/viewer
[23]: https://forum.groupdocs.com/
[24]: https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/
[25]: https://blog.groupdocs.com/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/
[26]: https://blog.groupdocs.com/2021/09/23/view-word-documents-as-responsive-html-page-using-java/

