---
title: "使用 Java 的文档中的删除线文本"
date: Mon, 06 Dec 2021 07:19:00 +0000
draft: false
url: /zh/2021/12/06/删除线-text-in-documents-using-java/
author: 'Shoaib Khan'
summary: "可能您有一些不再有效的内容。让我们划掉它。划掉是其中一种方法，用于突出显示文档中的无效内容。为了在应用程序中自动删除，本文展示了如何在 Java 文档中删除文本。"
tags: ['Cross out Text', 'Cross out Text in Java', 'Strike through Text in Java', 'Strikeout Text', 'Strikethrough Text']
categories: ['GroupDocs.Annotation Product Family']
---



{{< figure align=center src="images/strikethrough-text-using-java.jpg" alt="使用 Java 的 StrikeThrough 文本">}}


可能您有一些不再有效的内容。让我们划掉它。划掉是其中一种方法，用于突出显示文档中的无效内容。为了在应用程序中自动删除，本文展示了**如何在 Java 文档中删除文本**。

本文讨论了以下主题。

* [用于删除线注释的 Java API][1]
* [如何删除文档中的文本][2]

## 删除线文本的 Java API {#strikethrough-text-java-api}

[GroupDocs.Annotation][3] 展示了支持可应用于多个文档和图像的各种注释的 Java API。我们将在本文的示例中使用它来划掉文档中选定的文本。

您可以从 [下载部分][4] 下载 **JAR** 文件，或者在您的 Java 应用程序中使用最新的存储库和依赖项 [Maven][5] 配置。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-annotation</artifactId>
        <version>21.7.2</version> 
</dependency>
```

## 如何使用 Java 删除文档中的文本 {#how-to-strikethrough-text-using-java}

让我们划掉不再有效的文档区域。以下步骤允许您在 Java 文档中删除文本。

* 使用 [Annotator][6] 类加载源文档（PDF、Word 等）。
* 使用 [StrikeoutAnnotation][7] 类创建和定义删除线注释。
    * 设置删除线的颜色。
    * 设置不透明度，文档页码。
    * 定义坐标和其他属性。
* 使用 [add()][8] 方法将准备好的删除注释添加到注释器。
* 最后，使用 [save()][9] 方法保存带注释的文档。

同样，您可以注释 Word 文档、电子表格、演示文稿、PDF 文档、网页、电子邮件和许多其他文档。

以下 Java 代码示例删除了 PDF 文档中的选定文本。

```
/*
 * Strikethrough Text in Word, PDF, Spreadsheets, Presentations using Java
 */
Annotator annotator = new Annotator("path/document.pdf");
StrikeoutAnnotation strikeout = new StrikeoutAnnotation();
strikeout.setFontColor(0xFF0000);
strikeout.setOpacity(0.7);
strikeout.setPageNumber(0);

// 添加三振出局点数
List<Point> points = new ArrayList<Point>();
points.add(new Point(180, 730));
points.add(new Point(300, 730));
points.add(new Point(180, 700));
points.add(new Point(300, 700));
strikeout.setPoints(points);

annotator.add(strikeout);
annotator.save("path/strikethrough-text.pdf");
```

## 获取免费 API 许可证

您可以通过 [获得临时许可证][11] 免费使用 [GroupDocs.Annotation for Java][10]。

## 结论

最后，我们讨论了以编程方式向 Java 应用程序中的文档添加交叉注释。此外，您可以删除 PDF 文件、电子表格、演示文稿和 Word 文档中的文本。同样，您也可以根据需要使用其他注释。

从其 [文档][12] 中了解有关 **GroupDocs.Annotation for Java** 的更多信息。尝试为 [支持的文档格式][13] 构建您自己的注释器。如有疑问，请随时通过 [论坛][14] 联系我们。

## 也可以看看

* [使用 Java 在 PDF 文件中添加或删除注释][15]
* [用 Java 突出显示 PDF 内容][16]
* [使用 C# 的文档中的删除线文本][17]




[1]: #strikethrough-text-java-api
[2]: #how-to-strikethrough-text-using-java
[3]: https://products.groupdocs.com/annotation/
[4]: https://downloads.groupdocs.com/viewer
[5]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs
[6]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator
[7]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/StrikeoutAnnotation
[8]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#add(com.groupdocs.annotation.models.annotationmodels.AnnotationBase)
[9]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save()
[10]: https://products.groupdocs.com/annotation/java/
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://docs.groupdocs.com/annotation/java/
[13]: https://docs.groupdocs.com/annotation/java/supported-document-formats/
[14]: https://forum.groupdocs.com/
[15]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/
[16]: https://blog.groupdocs.com/2021/10/07/highlight-pdf-using-annotations-in-java/
[17]: https://blog.groupdocs.com/2021/12/18/strikethrough-text-in-documents-using-csharp/


