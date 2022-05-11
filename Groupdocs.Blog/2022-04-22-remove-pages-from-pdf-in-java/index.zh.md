---
title: "在 Java 中从 PDF 中删除页面 |偶数、奇数、列表和范围"
seoTitle: "在 Java 中从 PDF 中删除页面 |偶数、奇数、列表和范围"
date: Fri, 22 Apr 2022 11:00:00 +0000
draft: false
description: "使用 Java 从 PDF 文件中删除任何一组页面。从应用程序中的 PDF 文件中删除页面列表、任何给定范围、偶数页或奇数页。"
url: /zh/2022/04/22/remove-pages-from-pdf-in-java/
author: 'Shoaib Khan'
summary: "更新旧文档时；要求从最新版本的文档中删除过时、过时甚至高度机密的页面。在本文中，我们将学习**如何以编程方式从 Java 中的 PDF 文档中删除此类页面**。此外，我们将讨论删除 PDF 文档的页面列表、页面范围、偶数页和奇数页的不同方法。"
tags: ['delete pages', 'delete pages in java', 'remove pages', 'remove pages in java', 'delete pages from pdf in java']
categories: ['GroupDocs.Merger Product Family']
---

更新旧文档时；要求从最新版本的文档中删除过时、过时甚至高度机密的页面。在本文中，我们将学习**如何以编程方式从 Java 中的 PDF 文档中删除此类页面**。此外，我们将讨论删除 PDF 文档的页面列表、页面范围、偶数页和奇数页的不同方法。

下面讨论以下主题：

- [PDF 页面删除 Java API](#pdf-page-removal-java-api)
- [删除页面列表](#remove-pdf-pages-list-in-java)
- [删除页面范围](#remove-pdf-pages-range-in-java)
- [删除范围内的奇数页或偶数页](#remove-even-odd-pdf-pages-in-java)

## 从 PDF 中删除页面的 Java API {#pdf-page-removal-java-api}

GroupDocs.Merger 提供了允许以编程方式从 PDF 文档中删除页面的 Java API。此外，它还允许更改页面方向、移动页面位置、拆分文档、提取和旋转文档页面。我将使用这个 [GroupDocs.Merger for Java][1] 来删除 Java 中 PDF 文件的各个页面。有关 API 的详细信息和其他功能，您可以访问其[文档][2]。

### 下载并配置

从 [下载部分][3] 获取库。对于基于 Maven 的 Java 应用程序，只需添加以下 pom.xml 配置。在此之后，您可以尝试本文的示例以及 [GitHub][4] 上提供的更多示例。有关详细信息，您可以访问 [API 参考][5]。

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

## 在 Java 中从 PDF 中删除选定的页面 {#remove-pdf-pages-list-in-java}

要删除任何一组页面，您只需提供加载的 PDF 文档中的页码列表。以下步骤允许从 Java 中的 PDF 文档中删除提供的选择性页面列表。

- 使用要删除的**页码**初始化 [RemoveOptions][6] 类。
- 使用源文档路径或流实例化 [Merger][7] 对象。
- 调用 removePages() 方法删除列出的页面。
- 调用适当的 save() 方法来保存生成的文档。

以下 Java 代码示例从 PDF 文档中删除选定的第 2 页和第 4 页。

```
// 在 Java 中从 PDF 中删除选择性页面
RemoveOptions removeOptions = new RemoveOptions(new int[] { 2, 4 });

Merger merger = new Merger("path/document-pdf");
merger.removePages(removeOptions);
merger.save("path/selected-pages-removed.pdf");
```

## 在 Java 中从 PDF 中删除页面范围 {#remove-pdf-pages-range-in-java}

同样，您可以删除 PDF 文档中的任何页面范围。以下步骤允许从 Java 中的 PDF 文件中删除任意范围的页面。

- 初始化 [RemoveOptions][6]。
- 通过设置**开始**和**结束**页码提供**页范围**。
- 使用源文档路径或流实例化 [Merger][7] 对象。
- 使用范围调用 removePages() 方法。
- 调用适当的 save() 方法来保存生成的文档。

以下 Java 示例代码从 PDF 文档中删除了提供的范围（即 3 到 5）内的所有页面。

```
// 从 Java 中的 PDF 中删除选定范围的页面
RemoveOptions removeOptions = new RemoveOptions(3, 5);

Merger merger = new Merger("path/document-pdf");
merger.removePages(removeOptions);
merger.save("path/pages-range-removed.pdf");
```

## 用Java从PDF中删除偶数页或奇数页 {#remove-even-odd-pdf-pages-in-java}

您还可以删除文档的任何偶数/奇数页。以下步骤显示了如何在 Java 中删除给定范围内的 PDF 文件的偶数页或奇数页。

- 使用页面范围初始化 [RemoveOptions][6] 类。
- 将模式设置为**偶**或**奇**。
- 使用源文档路径或流实例化 [Merger][7] 对象。
- 使用删除选项调用 removePages() 方法。
- 调用适当的 save() 方法来保存生成的文档。

以下 Java 代码片段从整个 PDF 文档中删除所有奇数页。

```
// 从Java中给定范围内的PDF中删除所有奇数页
RemoveOptions removeOptions = new RemoveOptions(1,6, RangeMode.OddPages);

Merger merger = new Merger("path/document-pdf");
merger.removePages(removeOptions);
merger.save("path/odd-pages-removed.pdf");
```

以下 Java 代码示例从 PDF 文档中删除了所提供范围（即 1-5）内的所有偶数页。

```
// 从Java中给定范围内的PDF中删除所有偶数页
RemoveOptions removeOptions = new RemoveOptions(1,5, RangeMode.EvenPages);

Merger merger = new Merger("path/document-pdf");
merger.removePages(removeOptions);
merger.save("path/even-pages-removed.pdf");
```

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][8] 以便在没有评估限制的情况下使用 API。

## 结论

总而言之，我们学会了在 Java 应用程序中从 PDF 文档中删除不同的页面集。具体来说，我们已经看到了如何通过提供页码和页面范围来删除页面。此外，我们还了解了如何从 Java 中的任何 PDF 文档中删除奇数页或偶数页。您可以尝试构建自己的应用程序以消除 PDF 文件中的任何页面集。

有关 API 的更多详细信息，请访问文档。如有疑问，请通过 [论坛][14] 联系我们。

## 也可以看看
- [Java 中的水印 PDF 文件][9]
- [用 Java 重新排列 PDF 页面][10]
- [Java 中的 PDF 中的单词搜索和替换文本][11]
- [在Java中将PDF转换为灰度][12]
- [Java中PDF文件的密码保护][13]

[1]: https://products.groupdocs.com/merger/java
[2]: https://docs.groupdocs.com/merger/java/
[3]: https://downloads.groupdocs.com/merger/java
[4]: https://github.com/groupdocs-merger/GroupDocs.Merger-for-Java
[5]: https://apireference.groupdocs.com/merger/java
[6]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/RemoveOptions
[7]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[8]: https://purchase.groupdocs.com/temporary-license
[9]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/
[10]: https://blog.groupdocs.com/2022/03/10/move-pdf-pages-in-java/
[11]: https://blog.groupdocs.com/2022/03/08/find-and-replace-text-in-pdf-in-java/
[12]: https://blog.groupdocs.com/2022/03/02/convert-pdf-to-grayscale-jpg-png-images-in-java/
[13]: https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/
[14]: https://forum.groupdocs.com/
