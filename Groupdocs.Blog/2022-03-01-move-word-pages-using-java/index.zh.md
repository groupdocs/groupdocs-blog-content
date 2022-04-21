---
title: "'如何使用 Java 在 Word 中重新排列页面'"
date: Tue, 01 Mar 2022 06:28:00 +0000
draft: false
url: /zh/2022/03/01/move-word-pages-using-java/
author: 'Shoaib Khan'
summary: "文字处理文档是用于起草文档的最常见的文件格式之一。在处理多个大文件时，在不丢失格式的情况下移动页面绝非易事。为了重新排列页面，本文讨论了**如何在 Java 中以编程方式移动 Word 文档 (DOC/DOCX) 中的页面**。"
tags: ['Move Pages in DOC/DOCX', 'Move Pages in Java', 'Rearrange Document', 'Rearrange Document Pages in Java', 'Rearrange Pages in Java', 'Rearrange pages in Word']
categories: ['GroupDocs.Merger Product Family']
---



{{< figure align=center src="images/rearrange-word-pages-in-java.jpg" alt="在 Java 中重新排列 Word 页面">}}


文字处理文档是用于起草文档的最常见的文件格式之一。在处理多个大文件时，在不丢失格式的情况下移动页面绝非易事。为了重新排列页面，本文讨论了**如何在 Java 中以编程方式移动 Word 文档 (DOC/DOCX) 中的页面**。

## 用于移动 Word 文档页面的 Java API

**[GroupDocs.Merger](https://products.groupdocs.com/merger/)** 提供[Java API 处理文档及其页面](https://products.groupdocs.com/merger/java/)。它允许在 Java 应用程序中移动、删除、拆分文档和提取页面、更改页面方向以及旋转文档页面。我将使用这个 API 来移动 DOC/DOCX 文件的页面。有关 API 的详细信息和其他功能，您可以访问[文档](https://docs.groupdocs.com/merger/)。

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

## 使用 Java 在 Word 文档中移动页面

只需命令一个页面移动到新位置，它就会。以下是在 Java 中重新排列 Word 文档页面的步骤。

* 使用 [MoveOptions](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/MoveOptions) 类设置目标页面的页码及其新位置。
* 使用 [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) 类加载 DOC/DOCX 文件。
* 使用**movePage()** 方法移动设置的页面。
* 使用 **save()** 方法保存重新排列的文档。

以下 Java 源代码重新排列 Word 文档的页面。准确地说，它会将 DOCX 文档的第 7 页移至第 2 位。

```
// 用 Java 重新排列文字处理文档 (DOC/DOCX) 的页面
int pageNumber = 7;
int newPageNumber = 2;
MoveOptions moveOptions = new MoveOptions(pageNumber, newPageNumber);

Merger merger = new Merger("path\document.docx");

merger.movePage(moveOptions);
merger.save("path\rearranged-document.docx");
```

## 获取免费 API 许可证

您可以 [获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 以便在没有评估限制的情况下使用 API。

## 结论

综上所述，我们学习了如何在 Java 中更改 Word 文档的页面顺序。我们看到了更改 DOCX 文件中页面位置的源代码示例。您可以构建自己的在线应用程序以在线重新排列 Word 页面。有关 API 的更多详细信息，请访问 [文档](https://docs.groupdocs.com/merger/java/)。如有疑问，请通过 [论坛](https://forum.groupdocs.com/) 联系我们。

## 也可以看看

* [将 Word 文档呈现为缩小的 HTML](https://blog.groupdocs.com/2022/03/04/render-word-documents-as-minified-html-in-java/)
* [Word 文档中的 Word 搜索和替换文本](https://blog.groupdocs.com/2022/02/04/find-and-replace-text-in-word-documents-using-java/)
* [如何对 Word 文档进行密码保护和删除保护](https://blog.groupdocs.com/2022/02/02/lock-unlock-word-documents-with-password-in-java/)
* [以响应式 HTML 页面查看 Word 文档](https://blog.groupdocs.com/2021/09/23/view-word-documents-as-responsive-html-page-using-java/)
* [在 Word、Excel、PowerPoint 中插入 OLE 对象](https://blog.groupdocs.com/2020/10/19/insert-ole-objects-in-word-excel-powerpoint-with-java/)





