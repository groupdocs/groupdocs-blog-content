---
title: "'使用 Java 的 STL 文件查看器'"
date: Fri, 07 Jan 2022 10:49:14 +0000
draft: false
url: /zh/2022/01/07/stl-file-viewer-using-java/
author: 'Shoaib Khan'
summary: 'STL (**ST**ereo**L**ithography) file format is vastly used for 3D CAD drawings and printing. On the other hand, there are many other formats that are more portable than STL. Here comes the requirement to render the STL format into other formats. In this article, we will discuss **how to render the STL files into PDF format using Java**. In addition to this, we will convert the **STL files to HTML, JPG, and PNG formats** within Java application using examples.

本文讨论了以下主题：

* STL 查看器 Java API
* 以 PDF 格式查看 STL
* 以 HTML、JPG、PNG 格式查看 STL'
tags: ['STL as HTML', 'STL as JPG', 'STL as PNG', 'STL Viewer', 'STL Viewer using Java', 'View STL', 'View STL as PDF']
categories: ['GroupDocs.Viewer Product Family']
---

STL (**ST**ereo**L**ithography) 文件格式广泛用于 3D CAD 绘图和打印。另一方面，许多其他格式比 STL 更便携。这是将 STL 格式呈现为其他格式的要求。在本文中，我们将讨论**如何使用 Java 将 STL 文件呈现为 PDF 格式**。除此之外，我们将使用示例在 Java 应用程序中将 **STL 文件转换为 HTML、JPG 和 PNG 格式**。

下面讨论以下主题：

* [STL 查看器 Java API](#stl-viewer-java-api)
* [以 PDF 格式查看 STL](#stl-to-pdf)
* [以 HTML、JPG、PNG 格式查看 STL](#convert-stl-using-csharp)

## 用于查看 STL 文件的 Java API {#stl-viewer-java-api}

[GroupDocs.Viewer](https://products.groupdocs.com/viewer/) 展示了 [document viewer Java API](https://products.groupdocs.com/viewer/net/)，允许将文档呈现为 PDF， HTML 和 Java 应用程序中的图像。在本文中，我们将在示例中使用此 API 将 STL 文件转换为其他不同的文件格式。

您可以从 [下载部分](https://downloads.groupdocs.com/viewer/java) 下载 **JAR** 文件，或使用最新的存储库和依赖项 [Maven](https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs) 配置。

```
<repository>
	<id>GroupDocsArtifactRepository</id>
	<name>GroupDocs Artifact Repository</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-viewer</artifactId>
        <version>21.11.1</version> 
</dependency>
```

## 使用 Java 以 PDF 格式查看 STL 文件 {#stl-to-pdf}

PDF格式的高可移植性往往导致其他格式转换为PDF。以下步骤指导如何将 STL 文件转换为 Java 中的 PDF 格式。

* 使用 [Viewer](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer) 类加载 STL 文件。
* 使用 [PdfViewOptions](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PdfViewOptions) 类准备 PDF 呈现选项。
* 使用 [view()](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)) 将 STL 文件呈现为 PDF方法。

以下 Java 代码示例将 STL 文件呈现为 PDF 格式。

```
// 在 Java 中将 STL 文件渲染为 PDF
try (Viewer viewer = new Viewer("path/input.stl")) {
    PdfViewOptions options = new PdfViewOptions("path/stl-output.pdf");
    viewer.view(options);
}
```

## 使用 Java 以 HTML、JPG 或 PNG 格式查看 STL 文件 {#convert-stl-using-csharp}

同样，您也可以将 STL 文件转换为各种其他格式。以下步骤可帮助您使用 Java 将 STL 文件呈现为 HTML、JPG 和 PNG 格式。

* 使用 [Viewer](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer) 类加载 **STL** 文件。
* 根据预期的输出格式准备渲染选项：
    * **HTML** 渲染需要 [](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions)[HtmlViewOptions](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions) 类。 （您可以使用嵌入式或外部资源) 
    * **JPG** 渲染使用 [JpgViewOptions](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/JpgViewOptions) 类。
    * **PNG** 渲染需要 [PngViewOptions](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PngViewOptions) 类。
* 使用 [view()](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)) 方法。

以下是使用上述相应格式选项将 STL 文件独立呈现为每种格式的 Java 源代码示例。

### STL 到 HTML 使用 Java {#stl-to-html}

以下 Java 代码将 STL 文件转换为带有嵌入资源的 HTML 格式。同样，您可以使用外部资源转换为 HTML。

```
// 使用 Java 将 STL 文件渲染为带有嵌入式资源的 HTML
try (Viewer viewer = new Viewer("path/input.stl")) {
    HtmlViewOptions options = HtmlViewOptions.forEmbeddedResources("path/stl-output.html");
    viewer.view(options);
}
```

### STL 到 JPG 使用 Java {#stl-to-jpg}

以下 Java 代码将 STL 文件呈现为 JPG 图像格式。

```
// 在 Java 中将 STL 文件渲染为 JPG
try (Viewer viewer = new Viewer("path/input.stl")) {
    JpgViewOptions options = new JpgViewOptions("path/stl-output.jpg");
    viewer.view(options);
}
```

### STL 到 PNG 使用 Java {#stl-to-png}

以下 Java 代码将 STL 文件转换为 PNG 图像格式。

```
// 在 Java 中将 STL 文件渲染为 PNG
try (Viewer viewer = new Viewer("path/input.stl")) {
    PngViewOptions options = new PngViewOptions("path/stl-output.png");
    viewer.view(options);
}
```

## 获取免费 API 许可证

您可以通过 [获得临时许可证](https://purchase.groupdocs.com/temporary-license) 免费使用这些 API。

## 结论

综上所述，我们学习了使用 Java 示例将 STL 文件渲染为 PDF、HTML、JPG 和 PNG 格式。现在，您可以尝试开发自己的 STL 查看应用程序，如 [Groupdocs.Viewer 的在线应用程序](https://products.groupdocs.app/viewer)。

要了解有关 [GroupDocs.Viewer for Java](https://products.groupdocs.com/viewer/java/) 的更多信息，请访问其 [文档](https://docs.groupdocs.com/viewer/)。如有疑问，请通过 [论坛](https://forum.groupdocs.com/) 联系我们。

## 也可以看看

* [Java 中的源代码文件到 PDF](https://blog.groupdocs.com/2021/12/16/convert-source-code-to-pdf-in-java/)
* [使用 Java 查看 CAD 文件](https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/)
* [使用 Java 将 Word 文档作为 HTML 响应页面](https://blog.groupdocs.com/2021/09/23/view-word-documents-as-responsive-html-page-using-java/)