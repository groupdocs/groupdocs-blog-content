---
title: "在 Java 中将源代码转换为 PDF"
date: Thu, 16 Dec 2021 16:44:27 +0000
draft: false
url: /zh/2021/12/16/convert-source-code-to-pdf-in-java/
author: 'Shoaib Khan'
summary: 'If you want to share your code snippets, you can convert them into PDF format. In this article, we will discuss **how to convert Java, Python, C++, PHP source code to PDF** format within Java application. Additionally, we will also learn to password-protect the converted PDF files.

本文讨论了以下主题：

* 源代码转换 Java API
* Java 到 PDF 使用 Java
* Python到PDF使用Java
* PHP to PDF - 保护 PDF 文件'
tags: ['Convert Source Code to PDF in Java', 'Java to PDF', 'PHP to PDF', 'Python Code to PDF', 'Source Code to PDF']
categories: ['GroupDocs.Viewer Product Family']
---

如果您想分享您的代码片段，您可以将它们转换为 PDF 格式。为此，我们将讨论**如何在 Java 应用程序中将 Java、PHP、Python、**C#、C++** 源代码转换为 PDF** 格式。此外，我们还将学习使用密码保护转换后的 PDF 文件。



{{< figure align=center src="images/convert-source-code-to-pdf-in-java.jpg" alt="将源代码转换为 PDF">}}


下面讨论以下主题：

* [源代码转换Java API][1]
* [Java 到 PDF 使用 Java][2]
* [Python 到 PDF 使用 Java][3]
* [PHP 转 PDF - 保护 PDF 文件][4]

## 源代码转换器 Java API {#source-code-converter-java-api}

[GroupDocs.Viewer][5] 提供 Java API 来[将文件呈现为不同的格式][6]，例如 PDF、HTML 和图像格式。我将使用此 API 将不同语言的源代码文件转换为 PDF 格式。

您可以从 [下载部分][7] 下载 **JAR** 文件，或者在您的 Java 应用程序中使用最新的存储库和依赖项 [Maven][8] 配置。

```
<repository>
	<id>GroupDocsArtifactRepository</id>
	<name>GroupDocs Artifact Repository</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-viewer</artifactId>
        <version>21.11</version> 
</dependency>
```

## 将 Java 代码转换为 PDF {#java-to-pdf}

让我们快速达到目标并查看结果。以下步骤允许您将 Java 源代码文件转换为 PDF。

* 使用 [Viewer][9] 类加载 Java 文件。
* 使用 [PdfViewOptions][10] 类定义输出文件和选项。
* 使用适当的 [view()][11] 方法将加载的 Java 文件转换为 PDF。

以下 Java 代码片段将完整的 Java 源代码文件转换为 PDF 格式。

```
/*
 * Renders a Java file into PDF using Java
 */
try (Viewer viewer = new Viewer("path/HelloWorld.java")) 
{
    PdfViewOptions viewOptions = new PdfViewOptions("path/HelloWorld.pdf");
    viewer.view(viewOptions);
}
```

这是使用上述 Java 代码转换的 Java 文件的 PDF。如果您想为生成的 PDF 文件添加安全性，请跳转到下面的 [PHP 文件被转换][12] 部分。



{{< figure align=center src="images/java-to-pdf.jpg" alt="Java 源文件转换为 PDF">}}


## 使用 Java 将 Python 代码转换为 PDF {#python-to-pdf}

你真的认为，会有一个单独的代码将 Python 代码转换为 PDF，它与转换 Java 文件会有些不同吗？不，是一样的，只是交出正确的.py文件。以下步骤允许您将 Python 代码转换为 PDF。

* 使用 [Viewer][13] 类加载 Python 文件。
* 使用 [PdfViewOptions][14] 类设置输出文件路径和选项。
* 使用合适的 [view()][15] 方法将加载的 .py 文件转换为 PDF。

以下 Java 代码片段将完整的 Python 源代码文件转换为 PDF 格式。

```
/*
 * Convert Python source file into PDF using Java
 */
try (Viewer viewer = new Viewer("path/source.py")) 
{
    PdfViewOptions viewOptions = new PdfViewOptions("path/python-source.pdf");
    viewer.view(viewOptions);
}
```

## 使用 Java 将 PHP 转换为 PDF {#php-to-pdf}

同样，您也可以转换 PHP 文件。这里还要补充一件事；在转换源代码文件时，您可以为 PDF 文件添加安全性。让我们在转换为 PDF 格式时保护 PHP 代码。以下步骤显示如何将 PHP 文件转换为 PDF。

* 使用 [Viewer][16] 类加载 PHP 文件。
* 使用 [Security][17] 类定义安全性。
* 设置打开和编辑生成的 PDF 文件的密码。
* 使用 [PdfViewOptions][18] 类定义输出文件及其选项。
* 调用 [view()][19] 方法将加载的 PHP 文件渲染为受保护的 PDF。

以下 Java 代码示例将 PHP 源代码文件转换为受密码保护的 PDF 文件。

```
/*
 * Convert Php source file into PDF using Java
 */
try (Viewer viewer = new Viewer("path/source.php")) 
{
    Security security = new Security();
    security.setDocumentOpenPassword("OpEnD0c");
    security.setPermissionsPassword("Ple@se");
    security.setPermissions(Permissions.ALLOW_ALL ^ Permissions.DENY_PRINTING);

    PdfViewOptions viewOptions = new PdfViewOptions("path/php-source.pdf");
    viewOptions.setSecurity(security);
    
    viewer.view(viewOptions);
}
```

同样，您可以将此代码用于 [支持的编程语言][20] 的其他源代码，例如 C#、C/C++、GROOVY、Ruby 等。

## 获取免费 API 许可证

您可以[获得免费的临时许可证][21] 使用 API 而不受评估限制。

## 结论

总而言之，我们学会了使用 Java 将不同编程语言的源代码文件转换为 PDF 格式。我们将 Java、Python 和 PHP 文件转换为 PDF 格式。此外，我们还学习了如何使用密码保护生成的 PDF 文件。使用此 API，您可以开始构建自己的源代码查看器 Java 应用程序。

要了解有关 **GroupDocs.Viewer** 的更多信息，请访问 [文档][22]。如有疑问，请通过 [论坛][23] 联系我们。

## 也可以看看

* [用Java将图像转换为PDF][24]
* [用Java将Excel表格转换为PDF][25]
* [使用 Java 将 Word 文档作为响应式 HTML 页面查看][26]







[1]: #source-code-converter-java-api
[2]: #java-to-pdf
[3]: #python-to-pdf
[4]: #php-to-pdf
[5]: https://products.groupdocs.com/viewer/
[6]: https://docs.groupdocs.com/viewer/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/viewer
[8]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs
[9]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[10]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PdfViewOptions
[11]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[12]: #php-to-pdf
[13]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[14]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PdfViewOptions
[15]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[16]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[17]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/Security
[18]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PdfViewOptions
[19]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[20]: https://docs.groupdocs.com/viewer/java/supported-document-formats/
[21]: https://purchase.groupdocs.com/temporary-license
[22]: https://docs.groupdocs.com/viewer
[23]: https://forum.groupdocs.com/
[24]: https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/
[25]: https://blog.groupdocs.com/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/
[26]: https://blog.groupdocs.com/2021/09/23/view-word-documents-as-responsive-html-page-using-java/


