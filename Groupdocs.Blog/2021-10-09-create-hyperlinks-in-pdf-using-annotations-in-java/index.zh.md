---
title: "使用 Java 中的注释在 PDF 中创建超链接"
date: Sat, 09 Oct 2021 15:29:53 +0000
draft: false
url: /zh/2021/10/09/create-hyperlinks-in-pdf-using-annotations-in-java/
author: 'Shoaib Khan'
summary: 'Link annotations are used to create any part of the document as hyperlink. In other words, it allows us to associate external data with the specified area of the document. We can add these link annotations to documents within Java applications. In this article, you will learn **how to create hyperlinks in PDF files using Java**.

本文涵盖以下主题：

* Java API 在 PDF 文件中添加超链接
* 如何以编程方式在 PDF 中创建超链接'
tags: ['annotate PDF', 'Annotate PDF in Java', 'Create Hyperlink in PDF', 'Link Annotation', 'Link Annotation in Java', 'Link Annotation in PDF']
categories: ['GroupDocs.Annotation Product Family']
---

链接注释用于将文档的任何部分创建为超链接。换句话说，它允许我们将外部数据与文档的指定区域相关联。我们可以将这些链接注释添加到 Java 应用程序中的文档中。在本文中，您将学习**如何使用 Java 在 PDF 文件中创建超链接**。

以下主题涵盖以下内容：

* [Java API 在 PDF 文件中添加超链接][1]
* [如何以编程方式在 PDF 中创建超链接][2]



{{< figure align=center src="images/add-link-annotation-in-pdf-using-groupdocs.jpg" alt="在 PDF 中创建链接 - 以编程方式">}}


## Java API 在 PDF 中创建超链接 {#hyperlink-java-api}

[GroupDocs.Annotation][3] 提供了 Java API，允许在基于 Java 的应用程序中对文档中的各种注释进行操作和自动化。我们将使用此 API 在 PDF 文件中创建超链接注释。

### 下载或配置

从 [下载部分][4] 下载 **JAR** 文件，或者仅获取 **基于 maven 的** Java 应用程序的 pox.xml 的最新存储库和依赖项配置。

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

## 使用 Java 在 PDF 中创建超链接 {#how-to-create-hyperlinks-annotations}

以下是使用 Java 在 PDF 中的任何位置创建超链接的步骤。

* 使用 [Annotator][5] 类加载 PDF 文档。
* 定义代表超链接区域的 [Points][6] 列表。
* 创建 [LinkAnnotation][7] 对象。
* 定义超链接属性，如 url、页码、点等。
* 使用 [add][8] 方法将定义的超链接添加到加载的 PDF 文档。
* 使用 [save][9] 方法保存带注释的 PDF。

以下 Java 代码显示了如何以编程方式将 PDF 文件的任何部分转换为超链接。

```
// 使用 Java 中的链接注释在 PDF 中创建超链接
Annotator annotator = new Annotator("path/sample.pdf");
List<Point> points = new ArrayList<Point>();
points.add(new Point(120, 300));
points.add(new Point(600, 300));
points.add(new Point(120, 270));
points.add(new Point(600, 270));

LinkAnnotation link = new LinkAnnotation();
link.setCreatedOn(Calendar.getInstance().getTime());
link.setPageNumber(0);
link.setPoints(points);
link.setUrl("https://products.groupdocs.com/annotation");
annotator.add(link);

annotator.save("path/annotation-link.pdf");
annotator.dispose();
```

以下是上述代码的输出。



{{< figure align=center src="images/link-annotation-in-pdf-using-groupdocs.jpg" alt="在 PDF 中创建链接 - 以编程方式">}}


## 获取免费 API 许可证

您可以 [获得免费的临时许可证][10] 以便在没有评估限制的情况下使用 API。

## 结论

总而言之，我们已经讨论了如何以编程方式添加链接注释以使用 Java 在 PDF 文件中创建超链接。通过使用链接注释，您可以将文档的任何部分修改为超链接。许多[不同类型的注释][11] 可通过 API 获得。可以使用相同的 API 以类似的方式添加这些注释。要了解有关 API 的更多信息，请访问 [文档][12]。如有疑问，请通过 [论坛][13] 联系我们。

## 也可以看看

* [使用 C# 的 PDF 中的超链接注释][14]
* [在Java中添加或删除PDF文件的注释][15]
* [使用 Java 中的注释突出显示 PDF][16]
* [在Java中为图像添加水印][17]







[1]: #hyperlink-java-api
[2]: #how-to-create-hyperlinks-annotations
[3]: https://products.groupdocs.com/annotation/java/
[4]: https://downloads.groupdocs.com/redaction
[5]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#Annotator(java.io.InputStream)
[6]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models/Point
[7]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/LinkAnnotation
[8]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#add(com.groupdocs.annotation.models.annotationmodels.AnnotationBase)
[9]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save()
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/package-frame
[12]: https://docs.groupdocs.com/redaction
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2021/10/16/create-hyperlinks-in-pdf-using-annotations-in-csharp/
[15]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/
[16]: https://blog.groupdocs.com/2021/10/07/highlight-pdf-files-using-annotations-in-java/
[17]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/


