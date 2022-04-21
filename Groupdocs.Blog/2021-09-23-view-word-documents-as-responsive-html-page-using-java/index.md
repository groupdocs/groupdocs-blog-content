---
title: 'View Word Documents as Responsive HTML Page using Java'
date: Thu, 23 Sep 2021 10:31:47 +0000
draft: false
url: /2021/09/23/view-word-documents-as-responsive-html-page-using-java/
author: 'Shoaib Khan'
summary: 'Responsive HTML web pages are the ones that look good on different devices by adjusting themselves according to the different screen sizes. This article will guide you about **how to programmatically convert word documents as responsive HTML pages** within the **Java** applications using GroupDocs.Viewer.

The following topics will be covered in this article:

*   Java API for Word and Responsive HTML viewer
*   View Word Documents as Responsive HTML in Java'
tags: ['convert docx to html', 'Convert Word to HTML', 'Convert Word to Responsive HTML', 'view word as html responsive', 'Word to HTML in Java']
categories: ['GroupDocs.Viewer Product Family']
---

Responsive HTML web pages are the ones that look good on different devices by adjusting themselves according to the different screen sizes. This article will guide you about **how to programmatically convert word documents as responsive HTML pages** within the **Java** applications using [GroupDocs.Viewer][1].



{{< figure align=center src="images/word-to-responsive-html-layout-using-java-1024x614.jpg" alt="Word to Responsive HTML Layout using Java">}}


The following topics will be covered below:

*   [Java API for Word and Responsive HTML viewer][2]
*   [View Word Documents as Responsive HTML in Java][3]

## Java API - Convert & View Word Docs as Responsive HTML {#responsive-html-view-java-api}

GroupDocs.Viewer provides the Java API to render the Word documents as responsive HTML pages within Java applications. This Java API allows to render, display, and manipulate a [large number of different document formats][4]. It further allows building **HTML Viewer** with external as well as embedded resources, an **Image Viewer** by rendering as JPG and PNG, and also the **PDF Viewer** that could be best for printing or sharing with others.

### Download or Configure

You may download the **JAR** file from the [downloads section][5], or just get the latest repository and dependency configurations for the pox.xml of your **maven-based** Java applications.

```
<repository>
	<id>GroupDocsArtifactRepository</id>
	<name>GroupDocs Artifact Repository</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-viewer</artifactId>
        <version>21.4</version> 
</dependency>
```

## Convert Word Documents to View as Responsive HTML using Java {#word-to-html-responsive}

You can render your MS Word DOC, DOCX documents, to responsive HTML pages to look good on all the different screen sizes. The following steps show how to convert a Word document (DOC/DOCX) to responsive HTML in Java.

*   Load the Word document (DOC/DOCX) using the [Viewer][6] class.
*   Set either the embedded or external resources for the html output using [HtmlViewOptions][7].
*   Enable the responsive rendering using [setRenderResponsive][8] method.
*   To generate the responsive webpages of the loaded Word document, use the [view][9] method of the Viewer class

The following source code renders the Word document as responsive HTML with embedded resources in Java.

{{< gist GroupDocsGists a74b1e67139b125f6f1be4709abca7cf "ConvertWordToHtmlResponsive.java" >}}

## Get a Free API License

You can [get a free temporary license][10] to use the API without the evaluation limitations.

## Conclusion

To conclude, you discussed how to render the Word documents as responsive HTML pages within Java applications using GroupDocs.Viewer for Java API. Additionally, you can generate these HTML pages with either embedded or external resources. You must think about starting building your own document viewer application in Java like the one already [built by GroupDocs][11].

For more about the API, you can visit [documentation][12] and the [GitHub][13] repository. In case of further queries and ambiguities, contact the free support on the [forum][14].

## See Also

*   [View CAD Documents using Java][15]
*   [Render Word documents as Minified HTML in Java][16]
*   [Rearrange Pages in Word documents using Java][17]
*   [View Word Documents as HTML Responsive Page using C#][18]







[1]: https://products.groupdocs.com/viewer/
[2]: #responsive-html-view-java-api
[3]: #word-to-html-responsive
[4]: https://docs.groupdocs.com/viewer/java/supported-document-formats/
[5]: https://downloads.groupdocs.com/viewer
[6]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[7]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions
[8]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions#setRenderResponsive(boolean)
[9]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://products.groupdocs.app/viewer/total
[12]: https://docs.groupdocs.com/viewer/java/
[13]: https://github.com/groupdocs-viewer
[14]: https://forum.groupdocs.com/c/assembly
[15]: https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/
[16]: https://blog.groupdocs.com/2022/03/04/render-word-documents-as-minified-html-in-java/
[17]: https://blog.groupdocs.com/2022/03/01/move-word-pages-using-java/
[18]: https://blog.groupdocs.com/2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/

