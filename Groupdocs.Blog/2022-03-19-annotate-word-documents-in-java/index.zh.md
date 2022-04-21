---
title: "'在 Java 中添加或删除注释或标记 Word 文件'"
date: Sat, 19 Mar 2022 15:42:43 +0000
draft: false
url: /zh/2022/03/19/annotate-word-documents-in-java/
author: 'Shoaib Khan'
summary: "注释通常用于提及文档中的错误或讨论其内容。使用注释，您可以避免在电子邮件线程中进行冗长且永无止境的讨论。在本文中，您将学习如何以编程方式添加和删除注释以标记 Java 中的 Word 文档。"
tags: ['Add Annotations in Java', 'Add Annotations in Word using Java', 'Annotate Word in Java', 'Annotations in Java', 'Remove Annotation from Word in Java']
categories: ['GroupDocs.Annotation Product Family']
---

注释通常用于提及文档中的错误或讨论其内容。使用注释，您可以避免在电子邮件线程中进行冗长且永无止境的讨论。在本文中，您将学习如何以编程方式添加和删除注释以标记 Java 中的 Word 文档。

以下是以下简要讨论的主题：

* [用于 Word DOC/DOCX 注释的 Java API](#java-annotation-api)
* [为单词添加注释](#add-annotations-to-word)
    * [箭头注释](#add-arrow-annotation)
    * [矩形注释](#add-area-annotation)
    * [椭圆或椭圆注释](#add-ellipse-annotation)
    * [距离注释](#add-distance-annotation)
* [从 Word 文件中删除注释](#remove-annotations)

## 用于注释和标记 Word 文件的 Java API {#dotnet-annotation-api}

[GroupDocs.Annotation](https://products.groupdocs.com/annotation/) 提供Java API 来处理注解。 API 允许从 Word 文档和许多其他文件格式中添加、删除和提取注释。  [支持的文档格式](https://docs.groupdocs.com/annotation/java/supported-document-formats/) 包括；电子表格、演示文稿、图像、PDF 文件、网页、电子邮件、Visio 绘图。

### 下载或配置

从 [下载部分](https://downloads.groupdocs.com/annotation) 下载 **JAR** 文件，或者仅获取 **基于 maven* 的 pox.xml 的最新存储库和依赖项配置* Java 应用程序。

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

## 在 Java 中为 Word 添加注释 {#add-annotations-to-word}

让我们为 Word 文档添加不同类型的注释。注释有多种类型，因此我们将在这里仅介绍几种。

{{< figure align=center src="images/add-annotations-to-doc-docx-using-groupdocs-dotnet-java-api-1024x624.png" alt="使用 GroupDocs API 向 DOC DOCX 添加注释">}}


## 在 Java 中为 Word 添加箭头注释 {#add-arrow-annotation}

以下是在 Java 中为 Word 文档添加箭头注释的步骤。

* 使用 [Annotator](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator) 类加载文档。
* 使用 [ArrowAnnotation](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ArrowAnnotation) 类初始化箭头注释。
* 调整箭头标注的位置、大小、页码。
* 使用 add() 方法添加创建的箭头注释。
* 使用适当的 save() 方法将带注释的 Word 文档保存到路径中。

以下 Java 代码示例显示了如何向 Word 文档添加箭头注释。

```
// 在 Java 中为 Word 文档添加箭头注释
final Annotator annotator = new Annotator("path/document.docx");
ArrowAnnotation arrow = new ArrowAnnotation();
arrow.setBox(new Rectangle(100, 100, 100, 100));
arrow.setMessage("Arrow annotation");
arrow.setOpacity(0.7);
arrow.setPageNumber(0);
arrow.setPenColor(0x65535);
arrow.setPenStyle(PenStyle.Dot);
arrow.setPenWidth((byte) 3);
annotator.add(arrow);
annotator.save("path/annotatedDoc.docx");
```

{{< figure align=center src="images/arrow-annotation.jpg" alt="在 Java 和 .NET 中以编程方式添加箭头注释">}}

## 在 Java 中向 Word 中插入矩形或区域注释 {#add-area-annotation}

以下是通过一些自定义将矩形或区域注释添加到 DOC/DOCX 文档的步骤。它类似于添加箭头注释，但它使用**AreaAnnotation**。

* 使用 [Annotator](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator) 类加载 Word DOC/DOCX 文档。
* 使用 [AreaAnnotation](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/AreaAnnotation) 类初始化矩形注释。
* 调整矩形的位置、大小和颜色。
* 设置其他属性，如**页码、背景、不透明度、样式、笔宽**、**消息**和**时间**。
* 将创建的矩形注解添加到注解器中。
* 使用 save() 方法将带注释的 Word 文档保存到路径中。

以下 Java 代码示例展示了如何向 Word 文档添加矩形/区域注释。

```
// 在 Java 中的 Word 文档中添加区域或矩形注释

final Annotator annotator = new Annotator("path/document.docx");

AreaAnnotation area = new AreaAnnotation();
area.setBackgroundColor(65535);
area.setBox(new Rectangle(100, 100, 100, 100));
area.setCreatedOn(Calendar.getInstance().getTime());
area.setMessage("This is area annotation");
area.setOpacity(0.7);
area.setPageNumber(0);
area.setPenColor(65535);
area.setPenStyle(PenStyle.Dot);
area.setPenWidth((byte) 3);
area.setReplies(replies);
annotator.add(area);
annotator.save("path/annotatedDoc.docx");
```

{{< figure align=center src="images/rectangle-area-annotation.jpg" alt="在 .NET 和 Java 中以编程方式添加矩形或区域注释">}}

## 在 Java 中为 Word 添加椭圆或椭圆注释 {#add-ellipse-annotation}

以下是在 Java 中为文档添加椭圆/椭圆注释的步骤。

* 使用 [Annotator](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator) 类加载 DOC/DOCX 文档。
* 使用 [EllipseAnnotation](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/EllipseAnnotation) 类初始化椭圆注释。
* 设置初始化椭圆标注的位置和大小。
* 将创建的椭圆注释添加到 Annotator。
* 使用适当的 save() 方法保存带注释的 Word 文件。

以下 Java 代码示例展示了如何向任何 Word 文档添加椭圆/椭圆注释。

```
// 在 Java 中的 Word 文档中添加椭圆或椭圆注释
final Annotator annotator = new Annotator("path/document.docx");

EllipseAnnotation ellipse = new EllipseAnnotation();
ellipse.setBackgroundColor(65535);
ellipse.setBox(new Rectangle(100, 100, 100, 100));
ellipse.setCreatedOn(Calendar.getInstance().getTime());
ellipse.setMessage("This is ellipse annotation");
ellipse.setOpacity(0.7);
ellipse.setPageNumber(0);
ellipse.setPenColor(65535);
ellipse.setPenStyle(PenStyle.Dot);
ellipse.setPenWidth((byte) 3);
ellipse.setReplies(replies);
annotator.add(ellipse);
annotator.save("path/annotatedDoc.docx");
```

{{< figure align=center src="images/ellipses-annotation.jpg" alt="在 C# .NET 和 Java 中以编程方式添加椭圆或椭圆注释">}}

## 在 Java 中向 Word 中插入距离注释 {#add-distance-annotation}

同样，您可以使用距离注释来提及两点之间的距离。以下是在 Java 中为文档添加距离注释的步骤。

* 加载 Word 文档后，使用 [DistanceAnnotation](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/DistanceAnnotation) 类初始化距离标注。
* 设置注释的外观。
* 将距离注释添加到 Annotator 对象。
* 将带注释的文档保存在给定位置或使用正确的 save() 方法，

以下 Java 代码示例展示了如何向 DOC/DOCX 文档添加距离注释。

```
// 在 Java 中为 Word 文档添加距离注释
final Annotator annotator = new Annotator("path/document.docx");

DistanceAnnotation distance = new DistanceAnnotation();
distance.setBox(new Rectangle(200, 150, 200, 30));
distance.setCreatedOn(Calendar.getInstance().getTime());
distance.setMessage("This is distance annotation");
distance.setOpacity(0.7);
distance.setPageNumber(0);
distance.setPenColor(65535);
distance.setPenStyle(PenStyle.Dot);
distance.setPenWidth((byte) 3);
distance.setReplies(replies);
annotator.add(distance);
annotator.save("path/annotatedDoc.docx");
```

{{< figure align=center src="images/distance-annotation.jpg" alt="在 C# .NET 和 Java 中以编程方式添加距离注释">}}

## 从 Java 中的 Word DOC/DOCX 文件中删除注释 {#remove-annotations}

有许多方法可以从 Word 文档中删除注释。您可以通过提供删除特定注释的索引来删除特定注释。此外，您可以一次删除所有注释。用于删除注释的详细信息和 Java 源代码将在另一篇文章中讨论。

以下是从 Word 文件中删除所有注释的步骤。

* 加载文档。
* 初始化[保存选项](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/SaveOptions)。
* 将 [注释类型](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/AnnotationType) 设置为无。
* 保存 Word 文件。它将没有注释。

以下代码显示了如何从 Java 中的 Word 文件中删除注释。

```
// 从Java中的Word文档中删除所有注释
final Annotator annotator = new Annotator("path/annotatedDoc.docx");

SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.None);
annotator.save("path/annotationsRemoved.docx", saveOptions);
```

## 结论

总而言之，您已经学习了如何在 Java 应用程序中向 Word 文档添加注释。具体来说，我们使用 [GroupDocs.Annotation for Java](https://products.groupdocs.com/annotation/java/) 在 Word DOC/DOCX 文件中添加了箭头、椭圆、面积和距离注释。此外，您还了解了如何从任何 Word 文件中删除所有注释。现在，您可以尝试构建自己的文档注释器 Java 应用程序。

从 [文档](https://docs.groupdocs.com/annotation/java/) 和 [GitHub](https://github.com/groupdocs-annotation) 存储库了解有关 API 的更多信息。如需进一步查询，请联系 [论坛](https://forum.groupdocs.com/) 上的支持人员。

## 也可以看看

* [用Java注释PDF文件](https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/)
* [在 Java 中将 Word 文档呈现为缩小的 HTML](https://blog.groupdocs.com/2022/03/04/render-word-documents-as-minified-html-in-java/)
* [在 Java 中从 PDF 或 Word 文档中删除注释](https://blog.groupdocs.com/2022/03/12/remove-annotations-from-pdf-or-word-documents-in-java/)





