---
title: "使用 Java 在 PDF 文件中添加或删除注释"
date: Sun, 18 Apr 2021 05:20:00 +0000
draft: false
url: /zh/2021/04/18/annotate-pdf-files-using-java/
author: 'Shoaib Khan'
summary: 'There was a time when we used to discuss document content and feedback in long email threads with multiple attachments and different file versions. Now we can simply use annotations to markup the document with messages and replies and send it. In this article, you will learn how to programmatically annotate PDF documents in Java with your application.

以下是本文简要讨论的主题：

* Java API 用于处理 PDF 中的注释
* 在 Java 中为 PDF 添加注释
    * 箭头注释到 PDF
    * PDF的矩形注释
    * 椭圆或椭圆注释到 PDF
    * 到 PDF 的距离注释
* 在 Java 中从 PDF 中删除注释

[继续阅读...][1]'
tags: ['add annotations in PDF using Java', 'Annotate PDF in Java', 'Remove annotations from PDF in Java']
categories: ['GroupDocs.Annotation Product Family']
---

曾经有一段时间，我们曾经在包含多个附件和不同文件版本的长电子邮件线程中讨论文档内容和反馈。现在我们可以简单地使用注释来标记带有消息和回复的文档并发送它。在本文中，您将学习如何使用您的应用程序以编程方式在 Java 中注释 PDF 文档。此外，我们将了解如何使用相同的 Java API 从 PDF 文件中删除注释。

以下是以下简要讨论的主题：

* [使用 PDF 中的注释的 Java API][2]
* [用Java为PDF添加注释][3]
    * [PDF中的箭头注释][4]
    * [PDF中的矩形注释][5]
    * [PDF 中的椭圆或椭圆注释][6]
    * [PDF中的距离标注][7]
* [用Java从PDF中删除注释][8]

## PDF 注释器 Java API {#pdf-annotation-java-api}

为了在 Java 应用程序中处理文档和图像的注释，GroupDocs 提供了 [GroupDocs.Annotation for Java][9]。使用 API，您可以从**文字处理**文档、**电子表格**、**演示文稿**、**图像**、**电子邮件消息**、Visio * 中添加、删除和提取注释*绘图**、一些 **AutoCAD** 和 **数字成像格式**，如 **DICOM**。此外，API 允许注释 PDF 文件。您可以查看文档以了解 [支持的注释文档格式][10] 的长列表。

### 下载并配置

[从下载中获取注释库][11]，或者在基于 Maven 的 Java 应用程序中添加以下 pom.xml 配置，以尝试本文的示例以及 [GitHub][12] 上提供的更多示例。有关详细信息，您可以访问 [API 参考][13]。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-annotation</artifactId>
        <version>20.2</version> 
</dependency>
```

## 在 Java 中为 PDF 添加注释 {#add-annotations-to-pdf-in-java}

让我们快速跳转到 PDF 文档中添加一些不同类型的注释。由于有许多不同类型的注释，我们可能不会在本文中涵盖所有内容。我将仅提及它们，您可以[单独了解每个注释][14]。

* 面积/矩形标注
* 箭
* 距离
* 椭圆
* 强调
* 关联
* 观点
* 折线

* 替换
* 资源编辑
* 三振出局
* 文本域
*文本编辑
* 下划线
* 水印

让我们开始在 PDF 文档中添加其中的一些内容。

## 使用 Java 将箭头注释添加到 PDF {#add-arrow-annotation-to-pdf-in-java}

以下是向 PDF 文档添加箭头注释的步骤。



{{< figure align=center src="images/arrow-annotation.jpg" alt="箭头注释">}}


* 使用 [Annotator][15] 类加载 PDF 文档。
* 使用 [ArrowAnnotation][16] 类初始化箭头注释。
* 使用 ArrowAnnotation 的 [setBox][17] 方法设置箭头的位置和大小。
* 将创建的箭头注释添加到 Annotator 对象。
* 通过使用 [save][18] 方法提供路径来保存带注释的 PDF。

以下代码示例展示了如何使用 Java 向 PDF 文档添加箭头注释。

```
// 使用 Java 向 PDF 添加箭头注释
final Annotator annotator = new Annotator("document.pdf");
ArrowAnnotation arrow = new ArrowAnnotation();
arrow.setBox(new Rectangle(100, 100, 100, 100)); // (x, y, width, height)
annotator.add(arrow);
annotator.save("path/annotated-with-arrow.pdf");
```

## 使用 Java 将矩形或区域注释插入 PDF {#rectangle-area-annotation-to-pdf-in-java}

您可以在将任何注释添加到文档时对其进行自定义。以下是向 PDF 文档添加矩形或区域注释的步骤，只需少量自定义即可。它类似于添加箭头注释，但使用 **AreaAnnotation** 类代替 **ArrowAnnotation**。

* 使用 [Annotator][19] 类加载 PDF 文档。
* 使用 [AreaAnnotation][20] 类初始化矩形标注。
* 使用AreaAnnotation的[setBox][21]方法设置矩形的位置和大小。
* 设置其他属性，如 **color**、**background**、**opacity**、**style**、**pen width**，甚至是 **messages** 和 **time** .
* 将创建的矩形注解添加到 Annotator 对象中。
* 通过使用 [save][22] 方法提供路径来保存带注释的 PDF。



{{< figure align=center src="images/rectangle-area-annotation.jpg" alt="矩形或区域注释">}}


以下代码示例展示了如何使用 Java 向 PDF 文档添加矩形/区域注释。

```
// 使用 Java 向 PDF 添加区域注释或矩形注释
final Annotator annotator = new Annotator("document.pdf");
AreaAnnotation area = new AreaAnnotation();
area.setBox(new Rectangle(50, 100, 500, 100));
area.setCreatedOn(Calendar.getInstance().getTime());
area.setMessage("Annotate documents and images.");
area.setOpacity(0.7);
area.setPenColor(-13076963);
area.setPenStyle(PenStyle.Dash);
area.setPenWidth((byte) 3);
// 添加到文档
annotator.add(area);
annotator.save("path/annotated-with-rectangle.pdf");
```

## 使用 Java 向 PDF 添加椭圆或椭圆注释 {#oval-ellipse-annotation-to-pdf-in-java}

以下是向 PDF 文档添加椭圆注释或椭圆注释的步骤。



{{< figure align=center src="images/ellipses-annotation.jpg" alt="椭圆或椭圆注释">}}


* 使用 [Annotator][23] 类加载 PDF 文档。
* 使用 [EllipseAnnotation][24] 类初始化椭圆注释。
* 使用 EllipseAnnotation 的 [setBox][25] 方法设置椭圆的位置和大小。
* 将创建的椭圆注释添加到 Annotator 对象中。
* 通过使用 [save][26] 方法提供路径来保存带注释的 PDF。

以下代码示例展示了如何使用 Java 向 PDF 文档添加椭圆或椭圆注释。

```
// 使用 Java 在 PDF 中添加椭圆或椭圆注释
final Annotator annotator = new Annotator("document.pdf");
// 椭圆或椭圆注释
EllipseAnnotation ellipse = new EllipseAnnotation();
ellipse.setBox(new Rectangle(275, 505, 300, 80));
// 添加到文档
annotator.add(area);
annotator.save("path/annotated-with-ellipse.pdf");
```

## 使用 Java 将距离注释插入 PDF {#distance-annotation-to-pdf-in-java}



{{< figure align=center src="images/distance-annotation.jpg" alt="距离标注">}}


您还可以添加距离注释以显示两点之间的距离。以下是在 PDF 文档中添加距离注释的步骤。

* 使用 [Annotator][27] 类加载 PDF 文档。
* 使用 [DistanceAnnotation][28] 类初始化距离标注。
* 使用DistanceAnnotation的[setBox][29]方法设置标注的大小和位置。
* 将创建的距离注释添加到 Annotator 对象。
* 通过使用 [save][30] 方法提供路径来保存带注释的 PDF。

以下代码示例展示了如何使用 Java 向 PDF 文档添加距离注释。

```
// 使用 Java 进行距离标注
final Annotator annotator = new Annotator("document.pdf");
// 距离标注
DistanceAnnotation distance = new DistanceAnnotation();
distance.setBox(new Rectangle(775, 235, 0, 150));
// 添加到文档
annotator.add(area);
annotator.save("path/annotated-with-distance.pdf");
```

## 完整代码

总而言之，这里是 Java 代码，其输出显示了所有添加的 **annotations** 和 **messages** 以及 **replies** 使用提到的 Java 代码。



{{< figure align=center src="images/added-annotations-to-pdf.jpg" alt="为 PDF 添加注释">}}


下面的代码将箭头、矩形、椭圆、距离注释、消息和回复添加到 PDF 文件。

```
// 使用 Java 向 PDF 添加多个注释
// 使用 Java 向 PDF 添加箭头、面积、椭圆（椭圆）、距离注释以及消息和回复
final Annotator annotator = new Annotator(Constants.INPUT);
// 设置回复
Reply reply1 = new Reply();
reply1.setComment("Please look in to these issues.");
reply1.setRepliedOn(Calendar.getInstance().getTime());

Reply reply2 = new Reply();
reply2.setComment("Change Description");
reply2.setRepliedOn(Calendar.getInstance().getTime());

Reply reply3 = new Reply();
reply2.setComment("On-Premises APIs");
reply2.setRepliedOn(Calendar.getInstance().getTime());

Reply reply4 = new Reply();
reply2.setComment("Add images as well.");
reply2.setRepliedOn(Calendar.getInstance().getTime());

java.util.List<Reply> replies = new ArrayList<Reply>();
replies.add(reply1);
replies.add(reply2);
replies.add(reply3);
replies.add(reply4);
// 箭头注释==================================
ArrowAnnotation arrow = new ArrowAnnotation();
arrow.setBox(new Rectangle(560, 250, 60, -60));
arrow.setCreatedOn(Calendar.getInstance().getTime());
arrow.setMessage("This image is little upwards.");
arrow.setOpacity(0.7);
arrow.setPenColor(-3407872);
arrow.setPenWidth((byte) 2);
arrow.setReplies(replies.subList(0, 1));
// 区域标注 ====================================
AreaAnnotation area = new AreaAnnotation();
area.setBox(new Rectangle(50, 100, 500, 100));
area.setCreatedOn(Calendar.getInstance().getTime());
area.setMessage("Annotate documents and images.");
area.setOpacity(0.7);
area.setPenColor(-13076963);
area.setPenStyle(PenStyle.Dash);
area.setPenWidth((byte) 3);
area.setReplies(replies.subList(1, 2));
// 椭圆或椭圆注解 =========================
EllipseAnnotation ellipse = new EllipseAnnotation();
ellipse.setBox(new Rectangle(275, 505, 300, 80));
ellipse.setCreatedOn(Calendar.getInstance().getTime());
ellipse.setMessage("Shows all the available Annotation APIs.");
ellipse.setOpacity(0.7);
ellipse.setPenColor(-16034924);
ellipse.setPenStyle(PenStyle.Dot);
ellipse.setPenWidth((byte) 3);
ellipse.setReplies(replies.subList(2, 3));
// 距离标注================================
DistanceAnnotation distance = new DistanceAnnotation();
distance.setBox(new Rectangle(775, 235, 0, 150));
distance.setCreatedOn(Calendar.getInstance().getTime());
distance.setMessage("This is the heading area");
distance.setOpacity(0.7);
distance.setPenColor(-21197);
distance.setPenStyle(PenStyle.Solid);
distance.setPenWidth((byte) 1);
distance.setReplies(replies.subList(3, 4));
// 添加注释==================================
annotator.add(arrow);
annotator.add(area);
annotator.add(ellipse);
annotator.add(distance);
// 保存带注释的 PDF ================================
annotator.save(outputPath);
annotator.dispose();
```

## 在 Java 中从 PDF 中删除注释 {#remove-annotations-from-pdf-in-java}

以下步骤显示了如何在 Java 中从 PDF 文件中删除所有注释。

* 使用 [Annotator][31] 类加载 PDF 文档。
* 使用 [SaveOptions][32] 类初始化保存选项。
* 将注释类型设置为无。
* 通过使用 [save][33] 方法提供路径，保存删除了所有注释的 PDF 文件。

以下 Java 代码从 PDF 文件中删除注释。

```
// 使用 Java 从 PDF 文档中删除所有注释
final Annotator annotator = new Annotator("document.pdf");
SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.None);
// 保存 PDF，其中不再添加注释。
annotator.save("path/annotations-removed.pdf", saveOptions);
annotator.dispose();
```

## 结论

简而言之，您已经学会了如何在 Java 应用程序中向 PDF 添加注释。此外，您还了解了如何从任何 PDF 文件中删除所有注释。现在，您应该有信心构建自己的文档注释器 Java 应用程序了。它可以使用 GroupDocs.Annotation for Java 支持不同类型的注释。

有关更多详细信息、选项和示例，您可以访问 [文档][34] 和 [GitHub][35] 存储库。如需进一步查询，请联系 [论坛][36] 上的支持人员。

## 也可以看看

* [在 Java 中为图像添加水印][37]







[1]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/
[2]: #pdf-annotation-java-api
[3]: #add-annotations-to-pdf-in-java
[4]: #add-arrow-annotation-to-pdf-in-java
[5]: #rectangle-area-annotation-to-pdf-in-java
[6]: #oval-ellipse-annotation-to-pdf-in-java
[7]: #distance-annotation-to-pdf-in-java
[8]: #remove-annotations-from-pdf-in-java
[9]: https://products.groupdocs.com/annotation/java
[10]: https://docs.groupdocs.com/annotation/java/supported-document-formats/
[11]: https://downloads.groupdocs.com/annotation/java
[12]: https://github.com/groupdocs-annotation
[13]: https://apireference.groupdocs.com/annotation/java
[14]: https://docs.groupdocs.com/annotation/java/add-annotation-to-the-document/
[15]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator
[16]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ArrowAnnotation
[17]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ArrowAnnotation#setBox(com.groupdocs.annotation.models.Rectangle)
[18]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save(java.lang.String)
[19]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator
[20]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/AreaAnnotation
[21]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ArrowAnnotation#setBox(com.groupdocs.annotation.models.Rectangle)
[22]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save(java.lang.String)
[23]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator
[24]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/EllipseAnnotation
[25]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ArrowAnnotation#setBox(com.groupdocs.annotation.models.Rectangle)
[26]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save(java.lang.String)
[27]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator
[28]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/DistanceAnnotation
[29]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.models.annotationmodels/ArrowAnnotation#setBox(com.groupdocs.annotation.models.Rectangle)
[30]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save(java.lang.String)
[31]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator
[32]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/SaveOptions
[33]: https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator#save(java.lang.String)
[34]: https://docs.groupdocs.com/annotation/java/
[35]: https://github.com/groupdocs-annotation
[36]: https://forum.groupdocs.com/
[37]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/


