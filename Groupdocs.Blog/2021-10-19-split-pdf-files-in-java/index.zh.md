---
title: "在 Java 中拆分 PDF 文件的不同方法"
date: Tue, 19 Oct 2021 14:41:58 +0000
draft: false
url: /zh/2021/10/19/split-pdf-files-in-java/
aliases:
- /2021/10/19/split-pdf-files-in-java-2/
author: 'Shoaib Khan'
summary: "PDF 是支持文本、图形和许多其他元素的最著名的文件格式之一。它受欢迎的原因之一是它的便携性。在某些情况下，您可能需要将大型 PDF 文件拆分为多个文件。为了以编程方式解决这个问题，本文讨论了**如何在 Java 中拆分 PDF 文件**的不同方法。"
tags: ['PDF Separator', 'Separate PDF', 'Split API', 'Split PDF', 'Split PDF Files', 'Split PDF in Java']
categories: ['GroupDocs.Merger Product Family']
---



{{< figure align=center src="images/split-pdf-into-multiple-files-in-java.jpg" alt="在 Java 中将 PDF 拆分为多个文件">}}


[PDF][1] 是支持文本、图形和许多其他元素的最著名的文件格式之一。它受欢迎的原因之一是它的便携性。在某些情况下，您可能需要将大型 PDF 文件拆分为多个文件。为了以编程方式解决这个问题，本文讨论了**如何在 Java 中拆分 PDF 文件**的不同方法。

* [Java API 拆分 PDF 文件][2]
* [将PDF拆分为多页文件][3]
* [将PDF拆分为多个单页文件][4]
* [Java 中按范围从 PDF 文件中提取页面][5]
* [使用Java中的偶数或奇数过滤器从PDF文件中提取页面][6]

## 用于拆分 PDF 文件的 Java API {#split-pdf-java-api}

[GroupDocs.Merger][7] 提供了合并和拆分许多不同文件格式的文件的解决方案。我们将使用它的 [Java API][8] 以不同的方式分割 PDF 文件。从 [下载部分][9] 下载 **JAR** 文件，或者仅在您的 Java 应用程序中使用最新的存储库和依赖项 [Maven][10] 配置。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-merger</artifactId>
        <version>21.9</version> 
</dependency>
```

## 在 Java 中将 PDF 文件拆分为多页文件 {#split-pdf-to-multipage}

以下步骤指导如何将 PDF 文件拆分为多页文件：

* 使用 [Merger][11] 类加载 PDF 文件。
* 定义输出文件格式。
* 使用 [SplitOptions][12] 定义页面间隔。
* 使用 [split()][13] 方法根据定义的间隔拆分加载的 PDF。

以下代码示例展示了如何在 Java 中将 PDF 文件拆分为多页文件。

```
/*
 * Split PDF files into multiple page files in Java
 */
// 加载 PDF 文件
Merger merger = new Merger("path/document.pdf"); 

// 定义输出文件格式
String filePathOut = "path/splitPDF_{0}.{1}";

// 定义拆分间隔和拆分模式
SplitOptions splitOptions = new SplitOptions(filePathOut,  new int[] { 3, 6, 8 }, SplitMode.Interval);

// 根据给定的间隔拆分 PDF
merger.split(splitOptions);
```

## 在 Java 中将 PDF 文件拆分为多个单页文件 {#split-to-single-pages}

以下步骤指导您如何拆分 PDF 以将页面提取为多个单页文件：

* 使用 [Merger][14] 类加载 PDF 文件。
* 定义输出文件格式。
* 使用 [SplitOptions][15] 定义准确的页码。
* 使用 [split()][16] 方法根据定义的页面拆分加载的 PDF。

以下代码示例展示了如何在 Java 中将 PDF 文件拆分为多个单页文件。

```
/*
 * Split PDF file into Single Page files in Java
 */
// 加载 PDF 文件
Merger merger = new Merger("path/document.pdf");

// 定义输出文件格式
String filePathOut = "path/splitPDF_{0}.{1}"; 

// 定义要提取为单页文档的页面
SplitOptions splitOptions = new SplitOptions(filePathOut, new int[] { 3, 6, 8 });

// 根据拆分选项拆分 PDF
merger.split(splitOptions);
```

## 在 Java 中按范围从 PDF 文件中提取页面 {#extract-pages-by-range}

以下步骤指导如何通过根据给定范围拆分从 PDF 中提取页面：

* 使用 [Merger][17] 类加载 PDF 文件。
* 定义输出文件格式。
* 使用 [SplitOptions][18] 提供页面范围。
* 使用 [split()][19] 方法根据定义的范围分割加载的 PDF。

以下代码片段显示了如何通过在 Java 中提供范围来拆分 PDF 和提取页面。

```
/*
 * Split PDF file by Given Range into Single Page files in Java
 */
// 加载 PDF 文件
Merger merger = new Merger("path/document.pdf"); 

// 定义输出文件格式
String filePathOut = "path/splitPDF_{0}.{1}";

// 定义范围以提取为单页文档
SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7);

// 根据拆分选项拆分 PDF
merger.split(splitOptions);
```

## 使用 Java 中的偶数/奇数过滤器从 PDF 文件中提取页面 {#extract-even-or-odd-pages}

以下步骤指导如何通过拆分从 PDF 文件中提取给定范围内的偶数/奇数页：

* 使用 [Merger][20] 类加载 PDF 文件。
* 定义输出文件格式。
* 使用 [SplitOptions][21] 提供页面范围。
* 使用 [RangeMode][22] 应用偶数、奇数或所有页面过滤器。
* 使用 [split()][23] 方法根据定义的过滤器拆分加载的 PDF。

以下代码片段显示了如何使用 Java 提取 PDF 文件定义范围内的所有奇数/偶数页。

```
/*
 * Split PDF file by Given Range & Filter (Even/Odd Pages) into Single Page files in Java
 */
// 加载 PDF 文件
Merger merger = new Merger("path/document.pdf"); 

// 定义输出文件格式
String filePathOut = "path/splitPDF_{0}.{1}";

// 定义范围和过滤器以将给定范围内的所有奇数页提取为单页文档
SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7, (Integer)RangeMode.OddPages);

// 根据拆分选项拆分 PDF
merger.split(splitOptions);
```

## 代码更改摘要

上述场景中唯一不同的是创建 **SplitOptions** 的方式。您可以根据代码中的要求使用以下配置。

* **对于多页文件 - 使用间隔**：\[1,2\]、\[3,4,5\]、\[6,7\]、\[8,9,10\]。

```
new SplitOptions(outputFile,  new int[] { 3, 6, 8 }, SplitMode.Interval)
```

* **单个页面**：\[3\]、\[6\]、\[8\]

```
new SplitOptions(outputFile, new int[] { 3, 6, 8 });
```

* **提取范围内的页面**：\[3\]、\[4\]、\[5\]

```
new SplitOptions(outputFile, 3, 5);
```

* **带过滤器的范围**：\[3\]、\[5\]、\[7\]

```
new SplitOptions(outputFile, 3, 7, (Integer)RangeMode.OddPages);
```

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][24] 以便在没有评估限制的情况下使用 API。

## 结论

总而言之，您已经学习了在 Java 中拆分 PDF 文件的不同方法。首先，我们将 PDF 文件拆分为多页文档以及多个单页文档。然后我们一一提取给定范围内PDF文件的所有页面和偶数/奇数页。现在您应该有信心使用 GroupDocs.Merger API 构建自己的 PDF 拆分器 Java 应用程序。

要了解有关 API 的更多信息，请访问 [文档][25]。如有疑问，请通过 [论坛][26] 联系我们。

## 也可以看看

* [使用Java将多种文件类型合并为一个][27]
* [用Java合并PDF、Word、Excel文档][28]
* [使用C#分割PDF文件的不同方法][29]







[1]: https://docs.fileformat.com/pdf/
[2]: #split-pdf-java-api
[3]: #split-pdf-to-multipage
[4]: #split-to-single-pages
[5]: #extract-pages-by-range
[6]: #extract-even-or-odd-pages
[7]: https://products.groupdocs.com/merger/
[8]: https://products.groupdocs.com/merger/java/
[9]: https://downloads.groupdocs.com/merger
[10]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-merger
[11]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[12]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/SplitOptions
[13]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#split(com.groupdocs.merger.domain.options.interfaces.ISplitOptions)
[14]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[15]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/SplitOptions
[16]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#split(com.groupdocs.merger.domain.options.interfaces.ISplitOptions)
[17]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[18]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/SplitOptions
[19]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#split(com.groupdocs.merger.domain.options.interfaces.ISplitOptions)
[20]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[21]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/SplitOptions
[22]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/RangeMode
[23]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#split(com.groupdocs.merger.domain.options.interfaces.ISplitOptions)
[24]: https://purchase.groupdocs.com/temporary-license
[25]: https://docs.groupdocs.com/merger
[26]: https://forum.groupdocs.com/
[27]: https://blog.groupdocs.com/2021/06/13/merge-multiple-file-types-using-java/
[28]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/
[29]: https://blog.groupdocs.com/2021/10/11/split-pdf-files-in-csharp/


