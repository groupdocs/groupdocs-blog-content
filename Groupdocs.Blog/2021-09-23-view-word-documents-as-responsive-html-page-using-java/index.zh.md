---
title: "使用 Java 将 Word 文档作为响应式 HTML 页面查看"
date: Thu, 23 Sep 2021 10:31:47 +0000
draft: false
url: /zh/2021/09/23/view-word-documents-as-responsive-html-page-using-java/
author: 'Shoaib Khan'
summary: 'Responsive HTML web pages are the ones that look good on different devices by adjusting themselves according to the different screen sizes. This article will guide you about **how to programmatically convert word documents as responsive HTML pages** within the **Java** applications using GroupDocs.Viewer.

本文将介绍以下主题：

* 用于 Word 和响应式 HTML 查看器的 Java API
* 在 Java 中将 Word 文档视为响应式 HTML'
tags: ['convert docx to html', 'Convert Word to HTML', 'Convert Word to Responsive HTML', 'view word as html responsive', 'Word to HTML in Java']
categories: ['GroupDocs.Viewer Product Family']
---

响应式 HTML 网页是通过根据不同的屏幕尺寸进行自我调整而在不同设备上看起来不错的网页。本文将指导您了解**如何使用 [GroupDocs.Viewer][1] 在 **Java** 应用程序中以编程方式将 Word 文档转换为响应式 HTML 页面**。



{{< figure align=center src="images/word-to-responsive-html-layout-using-java-1024x614.jpg" alt="使用 Java 的 Word 到响应式 HTML 布局">}}


下面将介绍以下主题：

* [用于 Word 和响应式 HTML 查看器的 Java API][2]
* [在 Java 中将 Word 文档视为响应式 HTML][3]

## Java API - 将 Word 文档转换为响应式 HTML 并将其查看 {#responsive-html-view-java-api}

GroupDocs.Viewer 提供 Java API 以在 Java 应用程序中将 Word 文档呈现为响应式 HTML 页面。这个 Java API 允许渲染、显示和操作[大量不同的文档格式][4]。它还允许构建具有外部和嵌入式资源的**HTML 查看器**，通过呈现为 JPG 和 PNG 的**图像查看器**，以及最适合打印或共享的**PDF 查看器**其他。

### 下载或配置

您可以从 [下载部分][5] 下载 **JAR** 文件，或者仅获取 **基于 maven 的** Java 应用程序的 pox.xml 的最新存储库和依赖项配置。

```
<repository>
	<id>GroupDocsArtifactRepository</id>
	<name>GroupDocs Artifact Repository</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-viewer</artifactId>
        <version>21.4</version> 
</dependency>
```

## 使用 Java 将 Word 文档转换为响应式 HTML 查看 {#word-to-html-responsive}

您可以将您的 MS Word DOC、DOCX 文档渲染为响应式 HTML 页面，以便在所有不同的屏幕尺寸上看起来都很好。以下步骤展示了如何将 Word 文档 (DOC/DOCX) 转换为 Java 中的响应式 HTML。

* 使用 [Viewer][6] 类加载 Word 文档 (DOC/DOCX)。
* 使用 [HtmlViewOptions][7] 为 html 输出设置嵌入或外部资源。
* 使用 [setRenderResponsive][8] 方法启用响应式渲染。
* 生成加载的Word文档的响应式网页，使用Viewer类的[view][9]方法

以下源代码将 Word 文档呈现为响应式 HTML，并在 Java 中嵌入资源。

```
// 将 Word DOC/DOCX 文档转换为 Java 中的 HTML 响应页面
try (Viewer viewer = new Viewer("path/document.docx")) {
    HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources("path/page_{0}.html");
    viewOptions.setRenderResponsive(true);
    viewer.view(viewOptions);
}
```

## 获取免费 API 许可证

您可以[获得免费的临时许可证][10] 使用 API 而不受评估限制。

## 结论

最后，您讨论了如何使用 GroupDocs.Viewer for Java API 在 Java 应用程序中将 Word 文档呈现为响应式 HTML 页面。此外，您可以使用嵌入式或外部资源生成这些 HTML 页面。您必须考虑开始用 Java 构建自己的文档查看器应用程序，就像已经 [由 GroupDocs 构建的][11] 那样。

有关 API 的更多信息，您可以访问 [documentation][12] 和 [GitHub][13] 存储库。如果有进一步的疑问和歧义，请联系 [论坛][14] 上的免费支持。

## 也可以看看

* [使用 Java 查看 CAD 文档][15]
* [在 Java 中将 Word 文档呈现为缩小的 HTML][16]
* [使用 Java 重新排列 Word 文档中的页面][17]
* [使用 C# 将 Word 文档作为 HTML 响应页面查看][18]







[1]: https://products.groupdocs.com/viewer/
[2]: #responsive-html-view-java-api
[3]: #word-to-html-responsive
[4]: https://docs.groupdocs.com/viewer/java/supported-document-formats/
[5]: https://downloads.groupdocs.com/viewer
[6]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[7]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions
[8]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions#setRenderResponsive(boolean)
[9]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://products.groupdocs.app/viewer/total
[12]: https://docs.groupdocs.com/viewer/java/
[13]: https://github.com/groupdocs-viewer
[14]: https://forum.groupdocs.com/c/assembly
[15]: https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/
[16]: https://blog.groupdocs.com/2022/03/04/render-word-documents-as-minified-html-in-java/
[17]: https://blog.groupdocs.com/2022/03/01/move-word-pages-using-java/
[18]: https://blog.groupdocs.com/2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/


