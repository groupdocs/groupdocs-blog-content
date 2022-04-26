---
title: "在 Java 中拆分或合并 PDF、Word、Excel 文档"
date: Wed, 20 May 2020 08:22:00 +0000
draft: false
url: /zh/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/
aliases:
- /2020/02/20/split-or-merge-pdf-word-excel-documents-in-dotnet-or-java/
- /2020/02/20/split-or-merge-pdf-word-excel-documents-in-csharp-or-java/
- /2020/02/20/split-or-merge-pdf-word-excel-documents-in-c-or-java/
author: 'Shoaib Khan'
summary: "担心在多个平台合并或拆分各种类型的文档？您可能会想到很多陈述： * 如何在 Java 中将 PDF 文档合并在一起？ * 想要拆分word文档，或者合并excel电子表格。 * 如果我需要合并 PPT/PPTX 演示文稿怎么办。 * 更多问题，列表可能不会结束。"
tags: ['Merge Documents in Java', 'Merge PDF in Java', 'Merge Word in Java', 'Split Documents in Java', 'Split PDF in Java', 'Split PPT in Java']
categories: ['GroupDocs.Merger Product Family']
---

担心在多个平台合并或拆分各种类型的文档？你的脑海里可能有很多陈述：

* 如何在 Java 中合并 PDF 文档？
* 想要拆分word文档，或者合并excel电子表格。
* 如果我需要合并 PPT/PPTX 演示文稿怎么办。
* 更多问题，列表可能不会结束。



{{< figure align=center src="images/merge-split-documents-in-java-1.png" alt="在 Java 中拆分或合并 PDF、Word、Excel 文档">}}




{{< figure align=center src="images/groupdocs-merger-java-90x90-no-reply.png" alt="GroupDocs.Merger for Java">}}


GroupDocs 为所有此类需求提供了[文档合并解决方案][1]。它的 [Java API][2] 允许您在各种受支持的文档格式中**合并文档**和操纵 Java 中的文档结构。它还允许操作文档页面、页面转换、从文档中提取信息、生成预览等等。

在本文中，我们将了解以下主题：

* [如何在 Java 中合并 PDF 文件][3]。
* [合并 Word 文档、Excel 电子表格和 PowerPoint 演示文稿][4]。
* [合并某些文档页面][5]。
* [将任何文档拆分为多个文档][6]。

下面解释的代码示例和步骤使用 [GroupDocs.Merger for Java][7]，因此您可以 [下载][8] 或将其集成到您的基于 maven 的应用程序中并使用 pom.xml 配置。

## 在 Java 中合并 PDF 文件 {#merge-pdf-files-in-java}

我们只需几行代码就可以组合两个或多个 PDF 文件。下面是来自 [examples][9] 的代码片段，它是不言自明的，无需进一步说明，因此展示了如何在 Java 中合并多个 PDF 文档。如果您已经决定要合并的文档，步骤非常简单：

* 用第一个文档实例化 [Merger][10] 对象，其他文档要与之合并。
* 调用[join][11] 方法，传递文档进行合并。
* 调用 join 方法来合并更多文档。
* 调用[save][12]方法保存最终输出。
* 就是这样。

```
// Set paths for the documents to join together in a single file.
String filePath1 = "document-1.pdf";
String filePath2 = "document-2.pdf";
String filePath3 = "document-3.pdf";
// Merger multiple PDF documents into a single PDF file.
Merger merger = new Merger(filePath1 );
merger.join(filePath2 ); // Joining 2nd Document
merger.join(filePath3 ); // Joining 3rd Document
// Save the merged document.
String filePathOutput = "mergedDocument.pdf";
merger.save(filePathOutput);
```

## 在 Java 中合并 Excel、Word、PowerPoint 文档 {#merge-excel-ppt-and-word-docs-in-java}

您可以组合多个 Word 文档、Excel 电子表格、PowerPoint 演示文稿，事实上，几乎任何**相同格式**的文档。上述加入 PDF 文档的代码可用于合并各种文档。在文章的底部，我会提到可以与相同代码合并的文件格式列表。这里举个例子，我展示了如何类似地，只需几行 Java 代码就可以将两个以上的 Word 文档组合成一个 Word 文件。

```
// Merger multiple Word documents into a single DOCX file.
Merger merger = new Merger("document1.docx" );
merger.join("document2.docx" ); // Joining 2nd Document
merger.join("document3.docx" ); // Joining 3rd Document
// Save the merged document.
merger.save("mergedDocument.pdf");
```

## 在 Java 中合并文档页面 {#merge-document-pages-in-java}

多个文档可以通过选择性页面合并，也可以通过指定所需的页面范围来合并。您的代码将与上述类似，只是在使用 [JoinOptions][13] 类设置合并选项时稍作更改。

下面是显示如何通过指定某些页面来合并文档的源代码片段。

```
// Set the start and end page number in JoinOptions class.
JoinOptions joinOptions = new JoinOptions(1, 2);
// Merge two files with selective pages using join method.
Merger merger = new Merger("document-1.docx");
merger.join("document-2.docx" , joinOptions);
merger.save("merged-Document.docx");
```

## 在 Java 中将文档拆分为多个文档 {#split-documents-in-java}

就像我们在上面合并文档一样，我们也可以通过不同的方式快速拆分 Word 文档、Excel 电子表格、演示文稿、PDF 文件和许多其他文档。

* 按确切的页码拆分
* 将一个文档拆分为多个多页文档
* 按页面范围拆分
* 按偶数页和奇数页拆分

### 按确切页码拆分

我们可以通过在 Java 中提供确切的页数来拆分文档。以下代码将 PDF 文件拆分为 3 个文档，每个文档都有提到的单页。

* 使用输出文件和模式初始化 [SplitOptions][14] 对象以进行拆分。
* 使用要拆分的源文件或流实例化 [Merger][15] 对象。
* 调用 [split][16] 方法拆分提供的文档并保存。

```
String filePath = "document.pdf";
String filePathOut = "document\_{0}.{1}";
// Split the document into multiple single page documents.
SplitOptions splitOptions = new SplitOptions(filePathOut, new int\[\] { 3, 6, 8 });
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

### 将文档拆分为多页文档

如果您有一个 6 页的文档，下面提到的上述代码中的小修改将按照以下方式将您的文档拆分为 3 个单独的文档：

<figure class="wp-block-table is-style-stripes"><table><tbody><tr><td>**文件名称</td><td><strong>页码**</strong></td></tr><tr><td>文档_1</td><td> 1, 2</td></tr><tr><td>文档_2</td><td> 3、4、5</td></tr><tr><td>文档_3</td><td> 6</td></tr></tbody></table></figure>

```
SplitOptions splitOptions = new SplitOptions(filePathOut,  SplitMode.Interval, new int\[\] { 3, 6 },);
```

### 按开始和结束页面范围拆分

如果您只想通过提供页面范围来拆分任何文档，以下是如何将 Powerpoint 演示文稿拆分为 3 个单页演示文稿。

```
String filePath = "presentation.ppt";
String filePathOut = "presentation\_{0}.{1}";
// Split the presentation into multiple single page presentations.
SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 5);
Merger merger = new Merger(filePath);
merger.split(splitOptions)
```

### 按偶数或奇数页范围分割

您可以将偶数页和奇数页范围设置为拆分。遵循 SplitOptions 将允许将提供的文档拆分为多个一页文档，用于 3 到 8 范围内的奇数页。

```
SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 8, RangeMode.OddPages);
```

## 支持的文档格式

正如所承诺的，这里是可以与上述示例合并或拆分的文档格式列表。您可以随时访问 [docs][17] 查看更新后的列表。

<figure class="wp-block-table is-style-stripes"><table><tbody><tr><td>**文件类型</td><td><strong>文件格式**</strong></td></tr><tr><td>字处理</td><td>DOC、DOCX、DOCM、DOT、DOTX、DOTM、ODT、OTT、RTF、TXT</td></tr><tr><td>电子表格</td><td>XLS、XLSX、XLSM、XLSB、XLT、XLTX、XLTM、ODS、CSV、TSV</td></tr><tr><td>演示文稿</td><td>PPT、PPTX、PPS、PPSX、ODP、OTP</td></tr><tr><td>图纸</td><td>VSDX、VSDM、VSSX、VSSM、VSTX、VSTM、VDX、VSX、VTX</td></tr><tr><td>网络</td><td>HTML, MHT</td></tr><tr><td>页面描述语言</td><td>TEX、XPS</td></tr><tr><td>电子书及其他</td><td>PDF、EPUB、一个</td></tr></tbody></table></figure>

很高兴在这里见到您，如果您有任何困难或困惑或想提出一些好的建议，您可以在 [论坛][18] 上自由联系我们。







[1]: https://products.groupdocs.com/merger
[2]: https://products.groupdocs.com/merger/java
[3]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/#merge-pdf-files-in-java
[4]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/#merge-excel-ppt-and-word-docs-in-java
[5]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/#merge-document-pages-in-java
[6]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/#split-documents-in-java
[7]: https://products.groupdocs.com/merger/java
[8]: https://downloads.groupdocs.com/merger/java
[9]: https://github.com/groupdocs-merger/GroupDocs.Merger-for-Java
[10]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger/Merger
[11]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger/Merger#join(java.lang.String)
[12]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger/Merger#save(java.lang.String)
[13]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/JoinOptions
[14]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger.domain.options/SplitOptions
[15]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger/Merger
[16]: https://apireference.groupdocs.com/java/merger/com.groupdocs.merger/Merger#split(com.groupdocs.merger.domain.options.interfaces.IPageSplitOptions)
[17]: https://docs.groupdocs.com/merger/java
[18]: https://forum.groupdocs.com/c/merger


