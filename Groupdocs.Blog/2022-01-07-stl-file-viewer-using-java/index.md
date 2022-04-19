---
title: 'STL File Viewer using Java'
date: Fri, 07 Jan 2022 10:49:14 +0000
draft: false
url: /2022/01/07/stl-file-viewer-using-java/
author: 'Shoaib Khan'
summary: 'STL (**ST**ereo**L**ithography) file format is vastly used for 3D CAD drawings and printing. On the other hand, there are many other formats that are more portable than STL. Here comes the requirement to render the STL format into other formats. In this article, we will discuss **how to render the STL files into PDF format using Java**. In addition to this, we will convert the **STL files to HTML, JPG, and PNG formats** within Java application using examples.'
tags: ['STL as HTML', 'STL as JPG', 'STL as PNG', 'STL Viewer', 'STL Viewer using Java', 'View STL', 'View STL as PDF']
categories: ['GroupDocs.Viewer Product Family']
---

STL (**ST**ereo**L**ithography) file format is vastly used for 3D CAD drawings and printing. On the other hand, many other formats are more portable than STL. Here comes the requirement to render the STL format into other formats. In this article, we will discuss **how to render the STL files into PDF format using Java**. In addition to this, we will convert the **STL files to HTML, JPG, and PNG formats** within Java application using examples.

The following topics are discussed below:

*   [STL Viewer Java API](#stl-viewer-java-api)
*   [View STL as PDF](#stl-to-pdf)
*   [View STL as HTML, JPG, PNG](#convert-stl-using-csharp)

## Java API to View STL Files {#stl-viewer-java-api}

[GroupDocs.Viewer](https://products.groupdocs.com/viewer/) showcases [document viewer Java API](https://products.groupdocs.com/viewer/net/) that allows rendering the documents into PDF, HTML, and images within the Java application. In this article, we will use this API in examples to convert the STL files into different other file formats.

You can download the **JAR** file from the [downloads section](https://downloads.groupdocs.com/viewer/java) or use the latest repository and dependency [Maven](https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs) configurations within your Java applications.

```
<repository>
	<id>GroupDocsArtifactRepository</id>
	<name>GroupDocs Artifact Repository</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-viewer</artifactId>
        <version>21.11.1</version> 
</dependency>
```

## View STL File as PDF using Java {#stl-to-pdf}

The high portability of PDF format often leads to the conversion of other formats to PDF. The following steps guide how to convert the STL files into PDF format in Java.

*   Load the STL file using the [Viewer](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer) class.
*   Prepare the PDF rendering options using the [PdfViewOptions](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PdfViewOptions) class.
*   Render the STL file as PDF using the [view()](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)) method.

The following Java code example renders the STL files into PDF format.

{{< gist GroupDocsGists f82b9836c8c4781963cb6565badc911d "ViewStlAsPdf.java" >}}

## View STL File as HTML, JPG, or PNG using Java {#convert-stl-using-csharp}

Quite similarly, you can also convert the STL files into various other formats. The following steps help you to render the STL files into HTML, JPG, and PNG formats using Java.

*   Load the **STL** file using the [Viewer](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer) class.
*   Prepare the rendering options according to the intended output format:
    *   **HTML** rendering needs the [](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions)[HtmlViewOptions](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions) class. (You can use either embedded or external resources)
    *   **JPG** rendering uses the [JpgViewOptions](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/JpgViewOptions) class.
    *   **PNG** rendering requires the [PngViewOptions](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PngViewOptions) class.
*   Render the STL file as HTML, JPG, or PNG using the [view()](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)) method.

Below are the Java source code examples that independently render STL files into each format using the above-mentioned respective format options.

### STL to HTML using Java {#stl-to-html}

The following Java code converts the STL file into HTML format with embedded resources. Similarly, you can convert to HTML with external resources.

{{< gist GroupDocsGists f82b9836c8c4781963cb6565badc911d "ViewStlAsHtml.java" >}}

### STL to JPG using Java {#stl-to-jpg}

The following Java code renders the STL file into JPG image format.

{{< gist GroupDocsGists f82b9836c8c4781963cb6565badc911d "ViewStlAsJpg.java" >}}

### STL to PNG using Java {#stl-to-png}

The following Java code converts the STL file into PNG image format.

{{< gist GroupDocsGists f82b9836c8c4781963cb6565badc911d "ViewStlAsPng.java" >}}

## Get a Free API License

You can use the APIs for free by [getting a temporary license](https://purchase.groupdocs.com/temporary-license).

## Conclusion

To sum up, we learned to render the STL files into PDF, HTML, JPG, and PNG formats using the Java examples. Now, you can try developing your own STL viewing application like the [Online App of Groupdocs.Viewer](https://products.groupdocs.app/viewer).

To learn more about [GroupDocs.Viewer for Java](https://products.groupdocs.com/viewer/java/), visit its [documentation](https://docs.groupdocs.com/viewer/). For queries, contact us via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Source Code Files to PDF in Java](https://blog.groupdocs.com/2021/12/16/convert-source-code-to-pdf-in-java/)
*   [View CAD Files using Java](https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/)
*   [Word Documents as HTML Responsive Page using Java](https://blog.groupdocs.com/2021/09/23/view-word-documents-as-responsive-html-page-using-java/)




