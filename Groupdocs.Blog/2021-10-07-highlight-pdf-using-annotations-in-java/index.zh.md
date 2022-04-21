---
title: "使用 Java 中的注释突出显示 PDF"
date: Thu, 07 Oct 2021 10:35:00 +0000
draft: false
url: /zh/2021/10/07/highlight-pdf-using-annotations-in-java/
aliases:
- /2021/10/07/highlight-pdf-files-using-annotations-in-java/
author: 'Shoaib Khan'
summary: "通常需要特意突出显示文档的重要区域。作为开发人员，您可以在应用程序中自动突出显示。在本文中，您将学习**如何使用 Java 突出显示 PDF 文件中的文本和任何区域**。此外，还会有几个高亮的属性可以根据需要进行调整。"
tags: ['annotate PDF', 'Annotate PDF in Java', 'Highlight Annotation', 'Highlight PDF in Java', 'Highlight Text in PDF', 'Text Highlight']
categories: ['GroupDocs.Annotation Product Family']
---

通常需要故意突出显示文档的重要区域。作为开发人员，您可以在应用程序中自动突出显示。在本文中，您将学习**如何使用 Java 突出显示 PDF 文件中的文本和任何区域**。此外，还会有几个高亮的属性可以根据需要进行调整。

以下主题涵盖以下内容：

* [Java API 在 PDF 中突出显示][1]
* [如何以编程方式在 PDF 中突出显示][2]



{{< figure align=center src="images/add-highlight-annotation-in-pdf-using-groupdocs.jpg" alt="突出显示 PDF 中的文本 - 以编程方式">}}


## 在 PDF 中突出显示的 Java API {#highlight-pdf-java-api}

[GroupDocs.Annotation for Java][3] 是一种 API，它允许在基于 Java 的应用程序中轻松操作和自动化文档中的注释。我们将使用此 API 突出显示 PDF 文件中的文本。

### 下载或配置

您可以从 [下载部分][4] 下载 **JAR** 文件，或者仅获取 **基于 maven 的** Java 应用程序的 pox.xml 的最新存储库和依赖项配置。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-annotation</artifactId>
        <version>21.7</version> 
</dependency>
```

## 使用 Java 在 PDF 中突出显示 {#how-to-highlight-pdf}

以下是使用 Java 突出显示 PDF 中的文本或任何区域的步骤。

* 使用 [Annotator][5] 类加载 PDF 文档。
* 定义 [Point][6] 列表以选择高亮区域。
* 创建 [HighlightAnnotation][7] 对象。
* 定义高亮属性，如颜色、不透明度和页码。
* 使用 [add][8] 方法将定义的突出显示添加到加载的 PDF 文档中。
* 使用 [save][9] 方法保存带注释的 PDF。

**注意：** 您可以更改高亮颜色、不透明度和其他属性。

以下 Java 代码显示了如何以编程方式突出显示 PDF 中的文本。

```
// 使用 Java 中的高亮注释高亮 PDF
Annotator annotator = new Annotator("path/sample.pdf");
List<Point> points = new ArrayList<Point>();
points.add(new Point(120, 270));
points.add(new Point(600, 270));
points.add(new Point(120, 300));
points.add(new Point(600, 300));

HighlightAnnotation highlight = new HighlightAnnotation();
highlight.setBackgroundColor(0xFFF000);
highlight.setOpacity(0.5);
highlight.setPageNumber(0);
highlight.setPoints(points);
annotator.add(highlight);

annotator.save("path/annotation-highlight.pdf");
annotator.dispose();
```

这是上述代码的输出。



{{< figure align=center src="images/highlight-annotation-in-pdf-using-groupdocs.jpg" alt="突出显示 PDF 中的文本 - 以编程方式">}}


## 获取免费 API 许可证

您可以 [获得免费的临时许可证][10] 以便在没有评估限制的情况下使用 API。

## 结论

最后，我们讨论了如何使用 Java 以编程方式在 PDF 文件中添加高亮注释。此外，我们可以轻松更改高亮颜色、不透明度和其他属性。许多[不同类型的注释][11] 可通过 API 获得。可以使用相同的 API 以类似的方式添加这些注释。要了解 API，请访问 [文档][12]。如有疑问，请通过 [论坛][13] 联系我们。

## 也可以看看

* [使用 C# 突出显示 PDF 中的注释][14]
* [在Java中添加或删除PDF文件的注释][15]
* [Java 中的水印 PDF 文件][16]
* [在Java中为图像添加水印][17]







[1]: #highlight-pdf-java-api
[2]: #how-to-highlight-pdf
[3]: https://products.groupdocs.com/annotation/java/
[4]: https://downloads.groupdocs.com/redaction
[5]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#Annotator(java.io.InputStream)
[6]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models/Point
[7]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/HighlightAnnotation
[8]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#add(com.groupdocs.annotation.models.annotationmodels.AnnotationBase)
[9]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save()
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/package-frame
[12]: https://docs.groupdocs.com/redaction
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2021/10/12/highlight-pdf-with-annotations-using-csharp/
[15]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/
[16]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/
[17]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/


