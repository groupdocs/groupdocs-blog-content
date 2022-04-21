---
title: "使用 Java 查看 CAD 文档"
date: Mon, 05 Apr 2021 20:34:00 +0000
draft: false
url: /zh/2021/04/05/viewing-cad-documents-using-java/
aliases:
- /2019/07/13/viewing-cad-documents/
author: 'Shoaib Khan'
summary: "**C**计算机-**A**ided **D**esign - **CAD** 文件通常用于 2D 和 3D 设计。这些设计由 CAD 软件程序生成，通常用于创建模型和建筑计划。如果您使用过 CAD，您很可能熟悉 AutoCAD 的一些文件格式，例如**DWG、DXF、DGN、DWF**。本文将讨论如何在 Java 应用程序中以编程方式查看 CAD 文件。"
tags: ['CAD Viewer in Java', 'Convert DWG to HTML in Java', 'Convert DWG to JPG in Java', 'convert dwg to pdf in java', 'Convert DWG to PNG in Java', 'DWG Viewer using Java']
categories: ['GroupDocs.Viewer Product Family']
---

**C**计算机-**A**ided **D**esign - **CAD** 文件通常用于 2D 和 3D 设计。这些设计由 CAD 软件程序生成，通常用于创建模型和建筑计划。如果您使用过 CAD，您很可能熟悉 AutoCAD 的一些文件格式，例如**DWG、DXF、DGN、DWF**。本文将讨论如何在 Java 应用程序中以编程方式查看 CAD 文件。

下面简要介绍以下主题：

* [用于渲染 CAD 文件的 Java API。][2]
* [将 CAD 文件转换为 HTML、JPG、PNG 或 Java 中的 PDF。][3]
* [在 Java 中获取 DWG 的布局和图层。][4]
* [在 Java 中渲染 DWG 绘图的 CAD 图层。][5]
* [在 Java 中渲染 DWG 绘图的 CAD 布局。][6]

## 用于渲染 CAD 文件的 Java API - DWG、DXF、DWF、DGN {#java-api-to-render-cad-files}

[GroupDocs.Viewer for Java][7] 是允许将各种文档和图像文件呈现为 HTML、图像或 PDF 格式以在 Java 应用程序中查看这些文件的 API。 API 支持 [100 多种文件格式以编程方式呈现为 HTML、JPG、PNG 或 PDF][8]。

在本文中，我们将坚持使用 CAD 文件。除了已经提到的 **DWG** 和 **DGN** 格式，您还可以进一步查看 AutoCAD 格式，例如 **DWF、DWT、DXF，以及 IFC、STL、IGS、CF2、绘图仪文档（PLT、 Java 应用程序中的 HPG)** 文件。

### 下载并配置

[获取库][9] 从下载中或在基于 Maven 的 Java 应用程序中添加以下 pom.xml 配置以尝试以下示例。有关详细信息，您可以访问 [API 参考][10]。

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
        <version>21.2</version> 
</dependency>
```

## 将 CAD 绘图转换为在 Java 中呈现为 HTML、PNG、JPG 或 PDF {#convert-cad-to-html-jpg-jpg-pdf-in-java}

该 API 允许将 CAD 文档呈现为 HTML、JPG、PNG 和 PDF 格式。在本文中，我坚持使用 DWG 格式进行转换并使用示例渲染为其他格式。首先，让我们转换 DWG 设计并将其呈现为带有嵌入式和外部资源选项的 HTML。

### 使用嵌入式资源将 DWG 转换为 HTML

以下是如何将 DWG 文件转换为 HTML 渲染的步骤。

* 使用源 .dwg 文件初始化 [Viewer][11] 类对象。
* 使用 _[forEmbeddedResources][13]_ 方法创建 [HtmlViewOptions][12]。
* 使用 _[view][14]_ 方法将 .dwg 渲染为 HTML。

以下源代码转换 DWG 文件并将其呈现为带有 Java 中嵌入资源的 HTML。

```
// 使用 Java 将 .dwg CAD 绘图渲染为带有嵌入式资源的 HTML
try (Viewer viewer = new Viewer("drawing.dwg")) {
	HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources("page_{0}.html");
	viewer.view(viewOptions);
}
```

### 使用外部资源将 DWG 转换为 HTML

以下是如何将 DWG 文件转换为 HTML 文件并使用外部资源进行渲染的步骤。

* 使用源 .dwg 文件初始化 [Viewer][15] 类对象。
* 使用 [_forExternalResources_][17] 方法创建 [HtmlViewOptions][16]。
* 使用 _[view][18]_ 方法将 .dwg 渲染为 HTML。

以下源代码将 DWG 文件呈现为带有 Java 中的外部资源的 HTML。

```
// 使用 Java 将 .dwg CAD 绘图渲染为带有外部资源的 HTML
try (Viewer viewer = new Viewer("drawing.dwg")) {
	HtmlViewOptions viewOptions = HtmlViewOptions.forExternalResources("page_{0}.html", "page_{0}/resource_{1}", "page_{0}/resources");
	viewer.view(viewOptions);
}
```

### 在 Java 中将 DWG 转换为 PDF、JPG 和 PNG

与转换为 HTML 格式类似，DWG 文件可以使用各自的 ViewOptions 呈现为 PDF、JPG 和 PNG 格式，如下所示：

* [HtmlViewOptions][19] 呈现为 HTML
* [JpgViewOptions][20] 渲染为 JPG
* [PngViewOptions][21] 渲染为 PNG
* [PdfViewOptions][22] 呈现为 PDF

## 在 Java 中获取 DWG 的布局和图层 {#get-layout-and-layers-of-dwg-in-java}

由于 CAD 文件可能包含多个布局和图层，您可以使用以下步骤轻松获取它们的布局和图层。

* 为 HTML 渲染实例化 [ViewInfoOptions][23] 对象。
* 使用 ViewInfoOptions，您可以获得 [CadViewInfo][24]。
* 使用 _[getLayouts][25]_ 方法从 viewInfo 获取布局。
* 使用 _[getLayers][26]_ 方法从 viewInfo 获取图层。

以下代码显示了如何使用 Java 获取 DWG 文件的所有布局和图层。

```
// 在 Java 中获取 DWG CAD 绘图的布局和图层
try (Viewer viewer = new Viewer("drawing.dwg")) {
	ViewInfoOptions viewInfoOptions = ViewInfoOptions.forHtmlView();
	CadViewInfo viewInfo = (CadViewInfo) viewer.getViewInfo(viewInfoOptions);
    
	System.out.println("File type: " + viewInfo.getFileType());
	System.out.println("Pages count: " + viewInfo.getPages().size());
    
	for (Layout layout : viewInfo.getLayouts()) {
		System.out.println(layout);
	}
	for (Layer layer : viewInfo.getLayers()) {
		System.out.println(layer);
	}
}
```

## 在 Java 中渲染 DWG 文件的 CAD 图层 {#render-layers-of-dwg-in-java}

默认情况下，CAD 绘图的所有图层都会如上所示进行渲染。但是，您可以通过使用 Java API 的 [_setLayers_][27] 方法选择所选图层来渲染 DWG 的任何特定图层，如下所示。

* 使用源 .dwg 文件初始化 [Viewer][28] 类对象。
* 实例化 [HtmlViewOptions][29]。
* 使用 CadOptions 的 _[setLayers][30]_ 方法添加要渲染的层。
* 使用 _[view][31]_ 方法将 .dwg 渲染为 HTML。

以下代码以 Java 呈现 DWG 格式的 CAD 文件的图层。

```
// 在 Java 中渲染 .dwg CAD 绘图的图层
try (Viewer viewer = new Viewer("drawing.dwg")) {
	HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
	viewOptions.getCadOptions().setLayers(Arrays.asList(new Layer("Stairs"), new Layer("Walls")));
	viewer.view(viewOptions);
}
```

## 在 Java 中渲染 DWG 文件的 CAD 布局 {#render-layouts-of-dwg-in-java}

我们在渲染 CAD 图纸时，默认只得到模型展示。要渲染模型以及所有非空布局，我们只需将 CadOptions 的 **RenderLayout** 属性设置为 true。

* 使用源 .dwg 文件初始化 [Viewer][32] 类对象。
* 实例化 [HtmlViewOptions][33]。
* 将 CadOptions 的 [RenderLayout][34] 属性设置为 true。
* 使用 _[view][35]_ 方法将 .dwg 渲染为 HTML。

以下代码以 Java 中的 DWG 格式呈现所有非空布局以及 CAD 绘图模型。

```
// 在 Java 中渲染 .dwg CAD 绘图的布局
try (Viewer viewer = new Viewer("drawing.dwg")) {
	HtmlViewOptions viewOptions = HtmlViewOptions.forEmbeddedResources();
	viewOptions.getCadOptions().setRenderLayouts(true);
	viewer.view(viewOptions);
}
```

## 获取免费 API 许可证 {#Get-a-Free-API-License}

您可以 [获得免费的临时许可证][36] 以便在没有评估限制的情况下使用 API。

## 结论

在本文中，您学习了如何在 Java 应用程序中查看 CAD 文件。我希望您有信心使用 Java 构建自己的 CAD 查看器。您可以在应用程序中进一步显示 CAD 文件的模型、布局和图层。您可以使用 [文档][37] 了解有关 Java 的 GroupDocs.Viewer 的更多信息。如果您有任何疑问，请随时通过我们的 [论坛][38] 告诉我们。

## 也可以看看

* [使用 C# 查看 CAD 文档][39]
* [在 Java 中将 CAD 图纸转换为 PDF][40]
* [在 Java 中将 Word 文档呈现为缩小的 HTML][41]







[1]: https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/
[2]: #java-api-to-render-cad-files
[3]: #convert-cad-to-html-jpg-jpg-pdf-in-java
[4]: #get-layout-and-layers-of-dwg-in-java
[5]: #render-layers-of-dwg-in-java
[6]: #render-layouts-of-dwg-in-java
[7]: https://products.groupdocs.com/viewer/java
[8]: https://docs.groupdocs.com/viewer/java/supported-document-formats/
[9]: https://downloads.groupdocs.com/viewer/java
[10]: https://apireference.groupdocs.com/viewer/java
[11]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[12]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions
[13]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions#forEmbeddedResources()
[14]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[15]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[16]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions
[17]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions#forExternalResources()
[18]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[19]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions
[20]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/JpgViewOptions
[21]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PngViewOptions
[22]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/PdfViewOptions
[23]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/ViewInfoOptions
[24]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.results/CadViewInfo
[25]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.results/CadViewInfo#getLayouts()
[26]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.results/CadViewInfo#getLayers()
[27]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/CadOptions#setLayers(java.util.List)
[28]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[29]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions
[30]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/CadOptions#setLayers(java.util.List)
[31]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[32]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer
[33]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/HtmlViewOptions
[34]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.options/CadOptions#setRenderLayouts(boolean)
[35]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer/Viewer#view(com.groupdocs.viewer.options.ViewOptions)
[36]: https://purchase.groupdocs.com/temporary-license
[37]: https://docs.groupdocs.com/viewer/java/
[38]: https://forum.groupdocs.com/
[39]: https://blog.groupdocs.com/2021/04/27/view-cad-documents-using-charp/
[40]: https://blog.groupdocs.com/2020/10/31/convert-cad-drawings-to-pdf-in-java/
[41]: https://blog.groupdocs.com/2022/03/04/render-word-documents-as-minified-html-in-java/


