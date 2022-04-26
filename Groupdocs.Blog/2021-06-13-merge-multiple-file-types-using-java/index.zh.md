---
title: "使用 Java 将多种文件类型合并为一种"
date: Sun, 13 Jun 2021 05:49:00 +0000
draft: false
url: /zh/2021/06/13/merge-multiple-file-types-using-java/
author: 'Shoaib Khan'
summary: "当您打算将不同文档的分散数据收集到一个文件中时，通常需要合并不同的文档。在本文中，您将学习自动化文档合并过程。这将展示如何使用 Java 以编程方式将相同或不同文件类型的多个文档合并到一个文件中。在另一篇文章中，我们讨论了[使用 C# 合并多个不同格式的文件][1]。"
tags: ['Merge Documents in Java', 'Merge Files in Java', 'Merge multiple file types in Java', 'Merge two or more file in Java']
categories: ['GroupDocs.Merger Product Family']
---

当您打算将不同文档的分散数据收集到一个文件中时，通常需要合并不同的文档。在本文中，您将学习自动化文档合并过程。这将展示如何使用 Java 以编程方式将相同或不同文件类型的多个文档合并到一个文件中。在另一篇文章中，我们讨论了[使用 C# 合并多个不同格式的文件][2]。



{{< figure align=center src="images/merged-pdf-word-excel-files-to-pdf-in-java.jpg" alt="用 Java 将 PDF Word Excel 演示文稿合并为一个 PDF">}}


以下主题涵盖以下内容：

* [Java API - 合并多个文件][3]
* [将 PDF、Word、Excel 文件合并为一个 PDF][4]
* [将多个文件的选择性页面合并为一个文件][5]

## 用于合并多种文档类型的 Java API {#java-api-to-merge-multiple-file-types}

我将使用 [GroupDocs.Merger for Java][6] 将不同文件格式的文档合并到一个文件中。 Java API 允许将相同或不同格式的各种文档连接到一个文件中。此外，它还允许文档相应地拆分、修剪、交换、移动、删除、旋转或排列页面。此外，它还支持密码及其删除，以管理 [支持的文档格式][7] 的安全性。

API 支持的一些文档类型包括：文字处理文档、电子表格、演示文稿、HTML、PDF、电子书、Visio 绘图、CSV 和 TSV。

### 下载并配置

从下载部分获取文档合并库。对于基于 Maven 的 Java 应用程序，在 pom.xml 中添加以下配置。之后，您可以尝试文档合并本文的 java 示例以及 [GitHub][8] 中的更多示例。有关详细信息，您也可以访问 [API 参考][9]。

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
        <artifactId>groupdocs-merger</artifactId>
        <version>21.3</version> 
</dependency>
```

## 用 Java 将 PDF、Word、Excel 文件合并为一个 PDF {#merge-multiple-files-into-one-pdf-in-java}

只需几行代码，PDF 文档就可以与您的 Word 文档、Excel 电子表格、PowerPoint 演示文稿和其他 PDF 文档相结合。以下是如何将多种文件类型的文档合并为一个文件的步骤。

* 使用 [Merger][10] 类加载初始文档。
* 使用 [join][11] 方法合并第二个文档。
* 使用相同或相似的 **join** 方法继续合并其他文档（如果需要）。
* 使用相关的 [save][12] 方法将最终组合文档保存在路径或流上。

以下源代码展示了如何在 Java 中将 PDF、Word 和 Excel 文档合并为一个 PDF 文件。

```
// 使用 Java 将两种或多种不同类型的文件合并为一个
Merger merger = new Merger("pdf_document.pdf");
{
  merger.join("word_document.docx");
  merger.join("spreadsheet.xlsx");
	
  merger.save("merged-document.pdf");
}
```

同样，可以合并具有相同文件类型的文档。下面说的是加入word文档、PDF文档得到的输出。以及使用上述 Java 代码的电子表格。



{{< figure align=center src="images/merged-pdf-word-excel-to-one-file.jpg" alt="将不同的文件类型合并为一个 PDF C#">}}


## 在 Java 中将多个 PDF、Word、Excel 文件的选择性页面合并为一个 PDF {#merge-selective-pages-of-multiple-files-into-one-pdf-in-java}



{{< figure align=center src="images/merged-selective-pages-of-pdf-word-excel-to-one-file.jpg" alt="将不同文件类型的选择性页面合并为一个 PDF C#">}}


如果您想从一个文档中选择几页，从下一个文档中选择其他一些页面，依此类推。该 API 允许您以不同的方式将多种文件类型的选择性页面合并到一个文件中。

* 使用 [Merger][13] 类加载初始文档。
* 使用 [JoinOptions][14] 类准备合并选项。
* 使用 [join][15] 方法开始合并文档。
* 通过为每个文档设置适当的加入选项来继续加入文档。
* 使用 [save][16] 方法保存最终合并的文档。

以下源代码显示了如何将 Word 文档的第一页和 Java 中提供的范围内的 Excel 电子表格的偶数表与 PDF 文档合并。输出将是一个 PDF 文件。

```
// 使用 Java 将两种或多种不同类型文件的选择性页面合并为一个
Merger merger = new Merger("pdf_document.pdf");
{
  JoinOptions joinOptions = new JoinOptions(new int[]{1});
  merger.join("word_document.docx", joinOptions);

  joinOptions = new JoinOptions(1, 2, RangeMode.EvenPages);
  merger.join("spreadsheet.xlsx", joinOptions);
    
  merger.save("merged-document.pdf");
}
```

## 获取免费 API 许可证 {#Get-a-Free-API-License}

您可以 [获得免费的临时许可证][17] 以便在没有评估限制的情况下使用 API。

## 结论

最后，您学习了如何在应用程序中使用 Java 将两个或多个相似或不同文件类型的文档合并到一个文件中。此外，您还学习了如何将多种文件类型的选择性页面组合到一个文件中。

您可以使用 [文档][18] 了解有关 GroupDocs.Merger 的更多信息。如果您有任何疑问，请通过 [论坛][19] 联系我们。

## 也可以看看

* [Java 中拆分文件或合并文档][20]
* [使用C#将多个不同格式的文件合并为一个][21]







[1]: https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/
[2]: https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/
[3]: #java-api-to-merge-multiple-file-types
[4]: #merge-multiple-files-into-one-pdf-in-java
[5]: #merge-selective-pages-of-multiple-files-into-one-pdf-in-java
[6]: https://products.groupdocs.com/merger/java/
[7]: https://docs.groupdocs.com/merger/java/supported-document-formats/
[8]: https://github.com/groupdocs-merger
[9]: https://apireference.groupdocs.com/merger/java
[10]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[11]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#join(java.io.InputStream)
[12]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[13]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[14]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/JoinOptions
[15]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#join(java.io.InputStream)
[16]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[17]: https://purchase.groupdocs.com/temporary-license
[18]: https://docs.groupdocs.com/merger
[19]: https://forum.groupdocs.com/
[20]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/
[21]: https://blog.groupdocs.com/2021/05/04/merge-multiple-file-types-using-csharp/


