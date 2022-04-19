---
title: "'从 Java 中的 PDF 或 Word 文档中删除注释'"
date: Sat, 12 Mar 2022 16:43:18 +0000
draft: false
url: /zh/2022/03/12/remove-annotations-from-pdf-or-word-documents-in-java/
author: 'Shoaib Khan'
summary: "注释通常用于指出文档中的观察结果。这些也可用于在讨论时提供反馈。之前，我们讨论过 [Java 方法为 PDF 文档添加不同的注释](https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/)。本文讨论**如何从 Java 中的 PDF 和 Word DOC/DOCX 文件等文档中删除注释**。"
tags: ['Remove Annotation from PDF in Java', 'Remove Annotation in Java', 'Remove Annotations', 'Remove Annotations from Word in Java', 'Uncategorized']
categories: ['GroupDocs.Annotation Product Family']
---

注释通常用于指出文档中的观察结果。这些也可用于在讨论时提供反馈。之前，我们讨论过 [Java 方法为 PDF 文档添加不同的注释](https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/)。本文讨论**如何从 Java 中的 PDF 和 Word DOC/DOCX 文件等文档中删除注释**。

下面讨论以下主题：

* [注解 Java API](#java-annotation-api)
* [删除所有注释](#remove-all-annotations)
* [按 ID 删除注释](#remove-annotation-by-id)
* [通过注解对象消除注解](#remove-annotations-by-obj)

## 用于注解的 Java API {#java-annotation-api}

GroupDocs 具有允许处理各种文档和图像中的注释的 Java API。 它允许从 PDF、Word 和许多其他类型的文档中添加、删除和提取注释。您可以访问文档以获取[支持的注释文档格式](https://docs.groupdocs.com/annotation/java/supported-document-formats/)的完整列表。

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

## 从 Java 中的 PDF 和 Word 文档中删除所有注释 {#remove-all-annotations}

有一些方法可以从文档中删除注释。可以一次删除所有注释。您可以通过提供 ID 来移除特定的注解，或者通过提供注解对象来移除特定的注解。有关其他选项，请访问 [文档](https://docs.groupdocs.com/annotation/java/remove-annotation-from-document/)。

以下是从 Java 中的 PDF 和 Word DOC/DOCX 文档中删除所有注释的步骤。

* **使用 [Annotator](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation/Annotator) 加载**文档。
* 初始化[保存选项](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/SaveOptions) 类。
* **将 [注释类型](https://apireference.groupdocs.com/annotation/java/com.groupdocs.annotation.options.export/AnnotationType) 设置为**无**。
* **使用 **save()** 方法保存**没有注释的文件。

以下 Java 代码显示了如何从 PDF 或 Word 文件中删除注释。

```
// 使用 Java 从 PDF 文档中删除所有注释
final Annotator annotator = new Annotator("document.pdf");
SaveOptions saveOptions = new SaveOptions();
saveOptions.setAnnotationTypes(AnnotationType.None);
// 保存 PDF，其中不再添加注释。
annotator.save("path/annotations-removed.pdf", saveOptions);
annotator.dispose();
```

## 在 Java 中按 ID 删除注释 {#remove-annotation-by-id}

同样，您可以提供注释 ID 以消除文档中不需要的注释。它只是准备和提供 ID 列表以消除列出的注释。以下 Java 代码显示如何通过提供 ID 从 PDF 或 Word 文档中删除注释。

```
// 使用 Java 从 PDF 文档中删除选定的注释
final Annotator annotator = new Annotator("document.pdf");
java.util.List<Integer> removalList = new java.util.ArrayList<>();
removalList.add(0);
removalList.add(1);
annotator.remove(removalList);

// 保存带有已删除注释的 PDF。
annotator.save("path/annotations-removed.pdf", new SaveOptions());
annotator.dispose();
```

## 在 Java 中通过注解对象移除注解 {#remove-annotations-by-obj}

您还可以通过证明 **Annotation** 对象来摆脱特定的注释。为了删除注释，以下 Java 代码使用注释对象从 PDF 或 Word 文档中删除注释。

```
// 使用 Java 从 PDF 文档中删除选定的注释
final Annotator annotator = new Annotator("document.pdf");
java.util.List<AnnotationBase> annotations = annotator.get();
annotator.remove(annotations.get(0));

// 保存带有已删除注释的 PDF。
annotator.save("path/annotations-removed.pdf", new SaveOptions());
annotator.dispose();
```

## 结论

总而言之，您学会了从 Java 应用程序中的文档中删除注释。最初，我们从 PDF 和 Word 文档中删除了所有注释。后来我们通过提供 ID 和证明注释对象来消除注释。尝试使用 **[GroupDocs.Annotation for Java](https://products.groupdocs.com/annotation/java/)** 构建您自己的文档注释移除器 Java 应用程序。从 [文档](https://docs.groupdocs.com/annotation/java/) 和 [GitHub](https://github.com/groupdocs-annotation) 存储库了解有关 API 的更多信息。如需进一步查询，请联系 [论坛](https://forum.groupdocs.com/) 上的支持人员。

## 也可以看看

* [使用 Java 注释 PDF 文件](https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/)
* [用 Java 注释 Word 文件](https://blog.groupdocs.com/2022/03/19/annotate-word-documents-in-java/)
* [在 Java 中使用注释突出显示 PDF](https://blog.groupdocs.com/2021/10/07/highlight-pdf-using-annotations-in-java/)
* [使用 Java 中的注释在 PDF 中创建超链接](https://blog.groupdocs.com/2021/10/09/create-hyperlinks-in-pdf-using-annotations-in-java/)





