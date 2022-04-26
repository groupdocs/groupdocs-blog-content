---
title: "在 Java 中提取 ZIP 文件数据"
date: Wed, 08 Sep 2021 13:14:00 +0000
draft: false
url: /zh/2021/09/08/extract-zip-files-data-in-java/
author: 'Shoaib Khan'
summary: "ZIP 档案是最流行和最常用的压缩文件格式之一。使用 ZIP 文件的主要原因是减少总文件大小并将多个文件作为单个存档发送。作为开发人员，您可以从 ZIP 存档中压缩的文件中提取文本、图像甚至元数据。在本文中，我们将讨论**如何在 Java 中提取 ZIP 档案数据**。"
tags: ['Extract Archives in Java', 'Extract from ZIP', 'Extract from ZIP in Java', 'unzip data in Java']
categories: ['GroupDocs.Parser Product Family']
---

ZIP 档案是最流行和最常用的压缩文件格式之一。使用 ZIP 文件的主要原因是减少总文件大小并将多个文件作为单个存档发送。作为开发人员，您可以从 ZIP 存档中压缩的文件中提取文本、图像甚至元数据。在本文中，我们将讨论**如何在 Java 中提取 ZIP 档案数据**。



{{< figure align=center src="images/extract-data-from-zip-files-in-java.jpg" alt="从 Java 中的 ZIP 文件中提取数据">}}


以下主题涵盖以下内容：

* [用于 ZIP 文件数据提取的 Java API。][1]
* [如何使用 Java 提取 ZIP 文件数据。][2]
* [从Java ZIP文件中的文件中提取图像][3]

## 用于提取 ZIP 文件数据的 Java API {#zip-files-data-extraction-java-api}

[GroupDocs.Parser][4] 为开发人员提供了文档解析解决方案，其中还包括Java API。我将在本文的示例中使用此 [Java API 提取 ZIP 文件数据][5]。此外，此 API 允许从一长串 [支持的文档格式][6] 中提取图像、原始文本、结构化和格式化文本以及元数据的数据。这些文档格式包括文字处理文档、PDF、演示文稿、电子表格、电子邮件、数据库、电子书等。

### 下载或配置

您可以从 [下载部分][7] 下载 **JAR** 文件，或者仅获取 **基于 maven 的** Java 应用程序的 pox.xml 的最新存储库和依赖项配置。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
	<groupId>com.groupdocs</groupId>
	<artifactId>groupdocs-parser</artifactId>
	<version>21.2</version> 
</dependency>
```

## 如何在 Java 中提取 ZIP 文件数据 {#how-to-extract-zip-data}

要从存档中包含的任何文件中提取数据，您首先需要获取所有包含的文件。之后，您可以进一步从每个文件中提取任何类型的数据。以下步骤展示了如何提取 ZIP 文件数据并从 Java 中的每个包含的文件中检索文本。

* 使用 **[Parser][8]** 类加载 ZIP 存档。
* 使用 **_[getContainer][9]_** 方法提取附件集合。
* 遍历每个附件的数据的附件。
* 您可以使用 **Parser** 类的相应方法获取其不同类型的数据。

源代码显示了如何使用 Java 提取 ZIP 文件数据。下面的示例从 ZIP 存档中的所有文件中提取整个文本。

```
// 在 Java 中提取 ZIP 档案数据
Parser parser = new Parser("path/archive.zip");
// 从容器中提取附件
Iterable<ContainerItem> attachments = parser.getContainer();

// 迭代 ZIP 实体的集合
for (ContainerItem item : attachments) {
    // Print the FILE INFO
    System.out.println("-----------------------------------");
    System.out.println("Name: " + item.getName());
    System.out.println("File Size: " + item.getSize() + " Bytes");
    System.out.println("-----------------------------------");

    try {
        Parser attachmentParser = item.openParser();
        TextReader reader = attachmentParser.getText();
        System.out.println(reader == null ? "No text" : reader.readToEnd());
    } 
    catch (UnsupportedDocumentFormatException ex) {
        System.out.println("Isn't supported.");
    }
}
```

上述源代码的输出显示了 ZIP 文件中的 PDF 文件之一的检索文本。

```
 -----------------------------------
 Name: sample.pdf
 File Size: 33370 Bytes
 -----------------------------------

 Heading

 This is the first paragraph of the sample document that contains some sample
 text, bulleted list, numbered list and more.

    •  Bullet Item 1
    •  Bullet Item 2
    •  Bullet Item 3
 
 This is the second paragraph of the sample document and after this, there is a
 numbered list: 

    1. Numbered Item 1
    2. Numbered Item 2
    3. Numbered Item 3 
```

## 从 Java 中的 ZIP 文件中的文件中提取图像 {#extract-images-from-zip-data}

不仅限于文本，您还可以类似地提取图像信息。以下步骤显示如何提取 ZIP 文件数据并从每个随附文件中检索图像信息。

* 使用 **[Parser][10]** 类加载 ZIP 存档。
* 使用 **_[getContainer][11]_** 方法提取附件集合。
*遍历附件以获取每个附件中的图像集合。
* 现在使用 **[PageImageArea][12]** 类遍历图像以获取每个图像的信息。

以下源代码显示了如何从 Java 中的 ZIP 文件中包含的文件中提取图像数据。

```
// 从 Java 中的 ZIP 存档中的文件中提取图像信息
Parser parser = new Parser("path/archive.zip");
// 从容器中提取附件
Iterable<ContainerItem> attachments = parser.getContainer();

// 迭代 ZIP 实体的集合
for (ContainerItem item : attachments) {
    try {
        Parser attachmentParser = item.openParser();
        Iterable<PageImageArea> images = attachmentParser.getImages();
        if (images != null) {
            int imageCount = 1;
            for (PageImageArea image : images) {
                // Print a page index, rectangle and image type:
                System.out.println(String.format("Image# %d \nPage: %d\nFile Type: %s", imageCount, image.getPage().getIndex()+1, image.getFileType()));
                imageCount++;
            }
        }
    } 
    catch (UnsupportedDocumentFormatException ex) {
        System.out.println("Isn't supported.");
    }
}
```

```
Image# 1 
Page: 1
File Type: JPEG Image (.jpeg) 
```

## 获取免费 API 许可证

您可以[获得免费的临时许可证][13] 使用 API 而不受评估限制。

## 结论

简而言之，您已经学会了如何在 Java 应用程序中提取 ZIP 归档数据。此外，您还可以使用 GroupDocs.Parser for Java 从 ZIP 文件中提取图像。开始为压缩文件构建数据提取 Java 应用程序。要了解有关 API 的更多信息，请访问 [文档][14]。如有疑问，请通过 [论坛][15] 联系我们。

## 也可以看看

* [用C#提取ZIP文件数据][16]
* [使用Java从文档中获取图像][17]
* [用 Java 从 EPUB、FB2、CHM 电子书中提取图像][18]







[1]: #zip-files-data-extraction-java-api
[2]: #how-to-extract-zip-data
[3]: #extract-images-from-zip-data
[4]: https://products.groupdocs.com/parser/
[5]: https://products.groupdocs.com/parser/java/
[6]: https://docs.groupdocs.com/parser/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/parser
[8]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser
[9]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getContainer()
[10]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser
[11]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#getContainer()
[12]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/PageImageArea
[13]: https://purchase.groupdocs.com/temporary-license
[14]: https://docs.groupdocs.com/parser/
[15]: https://forum.groupdocs.com/
[16]: https://blog.groupdocs.com/2021/08/25/extract-zip-files-data-in-csharp/
[17]: https://blog.groupdocs.com/2020/10/27/extract-images-from-pdf-word-excel-ppt-using-java/
[18]: https://blog.groupdocs.com/2021/03/15/extract-images-from-ebooks-in-java/


