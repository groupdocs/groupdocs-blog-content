---
title: "'在 Java 中将 Word 文档呈现为缩小的 HTML'"
date: Fri, 04 Mar 2022 12:12:56 +0000
draft: false
url: /zh/2022/03/04/render-word-documents-as-minified-html-in-java/
author: 'Shoaib Khan'
summary: "HTML 缩小通过有效的加载时间和带宽使用提高了 Web 应用程序的性能。 HTML 和 CSS 中不必要的代码部分、无关紧要的空格、注释、分号、颜色值在缩小过程中得到优化。让我们自动化该过程以消除不需要的代码并提高 Java 应用程序的效率。为了提高性能，本文讨论了**如何在 Java 中将 Word 文档呈现为缩小的 HTML**。"
tags: ['Minify HTML', 'Minify HTML in Java', 'Word to Clean HTML', 'Word to Minified HTML']
categories: ['GroupDocs.Viewer Product Family']
---

HTML 缩小通过有效的加载时间和带宽使用提高了 Web 应用程序的性能。 HTML 和 CSS 中不必要的代码部分、无关紧要的空格、注释、分号、颜色值在缩小过程中得到优化。让我们自动化该过程以消除不需要的代码并提高 Java 应用程序的效率。为了提高性能，本文讨论了**如何在 Java 中将 Word 文档呈现为缩小的 HTML**。



{{< figure align=center src="images/render-word-to-clean-html-in-java.jpg" alt="在 Java 中将 Word 文档呈现为干净的 HTML">}}


## 用于呈现为缩小 HTML 的 Java API {#stl-viewer-dotnet-api}

[GroupDocs.Viewer](https://products.groupdocs.com/viewer/) 展示了一个 [文档查看 API](https://products.groupdocs.com/viewer/java/)，它允许将各种类型的文档呈现到Java 应用程序中的 HTML、PDF 和图像格式。我将在示例中使用此 API 将 Microsoft Word DOCX 文件转换为干净的 HTML 文件。

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

## 在 Java 中将 Word DOC/DOCX 渲染为缩小的 HTML {#stl-to-pdf}

可以使用相应的方法生成具有嵌入式或外部资源的 HTML 文件。以下步骤展示了如何将 Word (DOC/DOCX) 文档呈现为 Java 中的缩小 HTML。

* 使用 [Viewer](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer) 类加载 DOCX 文件。
* 使用 [HtmlViewOptions](https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions) 类准备 HTML 呈现选项。
* 通过将其设置为 true 来启用缩小选项。
* 使用带有创建选项的 **view()** 将 DOCX 文件呈现为缩小的 HTML。

以下 Java 代码示例将 Word DOCX 文件呈现为缩小的 HTML。

```
// 在 Java 中将 Word DOC/DOCX 转换为缩小的 HTML
Viewer viewer = new Viewer("path/document.docx");

HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources("path/page_{0}.html");
viewOptions.setMinify(true);

viewer.view(viewOptions);
```

## 获取免费 API 许可证

您可以通过 [获得临时许可证](https://purchase.groupdocs.com/temporary-license) 免费使用这些 API，而不受评估限制。

## 结论

最后，本文讨论了如何在 Java 中将 DOC/DOCX 文件呈现为缩小的 HTML。您可以开发自己的在线文档转换器和 HTML 缩小器，允许用户将文档转换为缩小的 HTML。此外，您可以从其[文档](https://docs.groupdocs.com/viewer/) 中了解有关 [GroupDocs.Viewer for Java](https://products.groupdocs.com/viewer/net/) 的更多信息。如有疑问，请通过 [论坛](https://forum.groupdocs.com/) 联系我们。

## 也可以看看

* [使用 Java 的 STL 文件查看器](https://blog.groupdocs.com/2022/01/07/stl-file-viewer-using-java/)
* [使用 Java 的 CAD 文档查看器](https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/)
* [Java 中的源代码到 PDF](https://blog.groupdocs.com/2021/12/16/convert-source-code-to-pdf-in-java/)
* [使用 Java 将 Word 文档作为响应式 HTML 页面](https://blog.groupdocs.com/2021/09/23/view-word-documents-as-responsive-html-page-using-java/)





