---
title: "使用 C# 在网页中播放和暂停动画 GIF 和 APNG 图像"
date: Sun, 28 Feb 2021 12:52:00 +0000
draft: false
url: /zh/2021/02/28/play-pause-animated-gif-and-apng-in-web-pages-using-csharp/
author: 'Shoaib Khan'
summary: "**GIF** 和 **APNG** 来自最常见的动画图像格式列表。 GIF 代表 **G**raphics **I**nterchange **F**ormat 和 APNG 文件是 **A**动画 **P**ortable **N**网络 **G**raphics .如果我们比较相同质量的 GIF 和 APNG 文件，会发现 APNG 文件的大小更小。本文将讨论使用 C#** 在 HTML 网页中播放和暂停动画 GIF 和 APNG 文件。"
tags: ['Play and Pause Animated Images', 'Play and Pause APNG in CSharp', 'Play and Pause GIF in CSharp', 'Render APNG to HTML in CSharp', 'Render GIF to HTML in CSharp']
categories: ['GroupDocs.Viewer Product Family']
---

**GIF** 和 **APNG** 来自最常见的动画图像格式列表。 GIF 代表 **G**raphics **I**nterchange **F**ormat 和 APNG 文件是 **A**动画 **P**ortable **N**网络 **G**raphics .如果我们比较相同质量的 GIF 和 APNG 文件，会发现 APNG 文件的大小更小。本文将讨论使用 C#** 在 HTML 网页中播放和暂停动画 GIF 和 APNG 文件。

下面将介绍以下主题：

* [用于动画图像的.NET API][1]
* [使用 C# 在 HTML 中播放和暂停动画 APNG 图像][2]
* [使用 C# 在 HTML 中播放和暂停动画 GIF 图像][3]

## 用于动画图像的 .NET API {#dotnet-api-for-animated-images}

对于动画图像，我将在本文的 C# 示例中使用 [GroupDocs.Viewer for .NET][4] API。除了渲染 GIF 和 APNG 图像外，此 API 还支持渲染文字处理文档、电子表格、PDF、演示文稿、电子邮件、ZIP 档案、Visio 和 CAD 绘图、电子书图像、编程源代码文件和许多其他文档格式。

您可以从 [下载部分][5] 下载 DLL 或 MSI 安装程序，或通过 [NuGet][6] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Viewer
```

## 在 C# 中播放和暂停动画 APNG 图像 {#play-pause-animated-apng-in-csharp}

要将 APNG 图像文件呈现到 HTML 页面，请按照以下步骤操作。 C# 源代码和输出也在下面提供。

* 使用 APNG 图像文件创建一个 [Viewer][7] 类对象。
* 使用 **ForEmbeddedResources** 方法创建 [HTMLViewOptions][8] 对象，并为其提供输出 HTML 文件。
* 调用查看器对象的[View][9] 方法为APNG 动画图像创建视图。

以下是将 APNG 图像呈现为 HTML 网页的 C# 代码。它还为动画 PNG 文件提供播放和暂停选项。

```
// 使用播放和暂停选项将 APNG 渲染为 HTML
using (Viewer viewer = new Viewer("animation.apng"))
{
    HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources("Web-Page-with-APNG.html");
    viewer.View(options);
}
```

这是带有 APNG 文件的输出 HTML 页面的视图。通过这个链接，您还可以[体验APNG动画的播放和暂停][10]，这是使用上面的C#代码创建的。



{{< figure align=center src="images/play-pause-APNG-in-CSharp.gif" alt="在 C# 中暂停 APNG 动画 PNG">}}


## 在 C# 中播放和暂停动画 GIF 图像 {#play-pause-animated-gif-in-csharp}

如果您想将 GIF 图像渲染到 HTML 网页，您可以使用与上面类似的代码来完成。播放和暂停选项也可用于 GIF 动画，因为它适用于 APNG 动画。以下 C# 代码示例使用播放和暂停选项将 GIF 动画文件呈现为 HTML。

```
// 使用播放和暂停选项将 GIF 渲染为 HTML
using (Viewer viewer = new Viewer("animation.gif"))
{
    HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources("Web-Page-with-gif.html");
    viewer.View(options);
}
```

## 结论

我相信您将有信心尝试使用 C# 将动画 GIF 和 APNG 文件渲染到 HTML 网页。您可以构建自己的 .NET 应用程序，该应用程序具有在 C# 中播放和暂停 GIF 和 APNG 动画的功能。

有关 API 和动画图像的更多信息，请访问 [文档][11] 或 [GitHub][12] 上的开源示例。如有任何疑问或困惑，请随时在 [论坛][13] 上联系支持人员。

用 C# 度过美好的动画日。

## 也可以看看

* [使用 C# 和 Java 的 CAD 文档查看器][14]







[1]: #dotnet-api-for-animated-images
[2]: #play-pause-animated-apng-in-csharp
[3]: #play-pause-animated-gif-in-csharp
[4]: https://products.groupdocs.com/viewer/net
[5]: https://downloads.groupdocs.com/viewer/net
[6]: https://www.nuget.org/packages/groupdocs.viewer
[7]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[8]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
[9]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view/index
[10]: https://blog.groupdocs.com/play-pause-apng.html
[11]: https://docs.groupdocs.com/viewer/net
[12]: https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET
[13]: https://forum.groupdocs.com/c/viewer
[14]: https://blog.groupdocs.com/2019/07/13/viewing-cad-documents/


