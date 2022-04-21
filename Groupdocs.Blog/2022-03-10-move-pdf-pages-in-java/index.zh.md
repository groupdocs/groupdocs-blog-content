---
title: "'如何在 Java 中重新排列 PDF 页面'"
date: Thu, 10 Mar 2022 14:49:46 +0000
draft: false
url: /zh/2022/03/10/move-pdf-pages-in-java/
author: 'Shoaib Khan'
summary: "PDF 是最常用的便携式文件格式之一。对于大型文档，在丢失格式的情况下更改页面顺序总是具有挑战性。本文讨论，**如何在 Java 中以编程方式重新排列 PDF 页面**。"
tags: ['Change Page Sequence in Java', 'Move Pages in Java', 'Rearrange Document', 'Rearrange Document Pages in Java', 'Rearrange PDF Pages', 'Rearrange PDF Pages in Java']
categories: ['GroupDocs.Merger Product Family']
---

PDF 是最常用的便携式文件格式之一。对于大型文档，在不丢失格式的情况下更改页面顺序总是具有挑战性的。本文讨论，**如何在 Java 中以编程方式重新排列 PDF 页面**。



{{< figure align=center src="images/rearrange-pdf-pages-in-java.jpg" alt="在 Java 中重新排列 PDF 页面">}}


## 用于重新排列 PDF 页面和合并文档的 Java API

GroupDocs 提供 [GroupDocs.Merger for Java](https://products.groupdocs.com/merger/java/) 来更改文档中页面的顺序。此 API 支持在应用程序中合并多个文档、移除、拆分和提取页面、旋转和更改文档页面的页面方向。有关 API 的详细信息和其他功能，您可以访问[文档](https://docs.groupdocs.com/merger/java/)。

### 下载并配置

从 [下载](https://downloads.groupdocs.com/merger/) 部分获取库。对于基于 Maven 的 Java 应用程序，只需添加以下 pom.xml 配置。在此之后，您可以尝试本文的示例以及 [GitHub](https://github.com/groupdocs-merger) 上提供的更多示例。详情可访问 [API 参考](https://apireference.groupdocs.com/merger/java)。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-merger</artifactId>
        <version>22.2</version> 
</dependency>
```

## 在 Java 中重新排列 PDF 页面

以下是帮助您在 Java 中更改 PDF 文档页面顺序的步骤。

* 在 [MoveOptions](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/MoveOptions) 类中定义页面的现有位置和新位置。
* 使用 [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) 类加载 PDF 文档。
* 使用 **movePage()** 方法根据定义的选项重新排列页面。
* 使用 **save()** 方法保存重新排序的 PDF 文件。

以下 Java 源代码重新排列 PDF 文档的页面。准确地说，它将文档的第 6 页移动到第 1 位。

```
// 用 Java 重新排列 PDF 文档的页面
int pageNumber = 6;
int newPageNumber = 1;
MoveOptions moveOptions = new MoveOptions(pageNumber, newPageNumber);

Merger merger = new Merger("path\document.pdf");

merger.movePage(moveOptions);
merger.save("path\rearranged-document.pdf");
```

这是上述代码的输出。



{{< figure align=center src="images/Screenshot-1024x454.png" alt="">}}


## 获取免费 API 许可证

您可以 [获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 以便在没有评估限制的情况下使用 API。

## 结论

最后，我们学会了通过在应用程序中更改 Java 中 PDF 文件的页面顺序来重新排序文档。我们已经看到了改变页面位置的运行示例。您可以尝试构建一个简单的应用程序，该应用程序可以通过轻松打乱它们的页面来组织 PDF 文件。

有关 API 的更多详细信息，请访问 [文档](https://docs.groupdocs.com/merger/)。如有疑问，请通过 [论坛](https://forum.groupdocs.com/) 联系我们。

## 也可以看看

* [Java中PDF文件的密码保护](https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/)
* [Java 中拆分 PDF 文件的方法](https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/)
* [使用 Java 将多种文件类型合并为一种](https://blog.groupdocs.com/2021/06/13/merge-multiple-file-types-using-java/)





