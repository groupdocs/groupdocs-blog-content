---
title: "使用 C# 使用密码锁定和解锁 PDF 文件"
date: Wed, 17 Nov 2021 12:28:00 +0000
draft: false
url: /zh/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/
aliases:
- /2021/11/17/password-protection-to-pdf-files-in-csharp/
- /2019/09/25/add-password-protection-to-word-or-pdf-files-in-csharp/
- /2019/09/25/add-password-protection-to-word-or-pdf-files-in-c/
author: 'Shoaib Khan'
summary: 'Let us learn to secure our documents from unauthorized access. Previously we discussed [adding text and image watermarks to the documents][1] to avoid and illegal use. In this article, we will see **how to add password protection to PDF documents to get them locked using C#**. Additionally, we will **change the existing password** and also learn to **remove the password** to make the PDF unlocked.

本文讨论了以下主题：

* .NET API 用于 PDF 文件的密码保护
* 通过添加密码锁定 PDF 文件
* 在 C# 中更改 PDF 密码
* 如何删除 PDF 密码 - 解锁 PDF'
tags: ['add password to PDF in csharp', 'Change PDF Password in CSharp', 'Lock PDF in CSharp', 'Remove PDF Password in CSharp', 'Unlock PDF in CSharp']
categories: ['GroupDocs.Merger Product Family']
---

让我们学习保护我们的文档免受未经授权的访问。之前我们讨论过[在文档中添加文本和图像水印][2] 以避免任何非法使用。在本文中，我们将看到**如何为 PDF 文档添加密码保护以使用 C# 锁定它们**。此外，我们将**更改现有密码**并学习**删除密码**以使 PDF 解锁。



{{< figure align=center src="images/password-protect-lock-unlock-pdf.jpg" alt="使用密码以编程方式保护 PDF 文件 - 锁定解锁">}}


下面讨论以下主题：

* [.NET API 用于 PDF 文件的密码保护][3]
* [通过添加密码锁定PDF文件][4]
* [在 C# 中更改 PDF 密码][5]
* [如何删除PDF密码-解锁PDF][6]

## .NET API 来锁定和解锁 PDF 文件 {#lock-unlock-pdf-dotnet-api}

要锁定和解锁文档，我们将使用 [GroupDocs.Merger for .NET][7]。此 API 支持为 .NET 应用程序中的文档添加、更改和删除密码安全功能。除了保护和取消保护 PDF 文档之外，API 还提供了更多功能，例如 [文档][8] 中提到的合并和拆分。

您可以从 [下载部分][9] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][10] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Merger
```

## 在 C# 中为 PDF 添加密码 - 锁定 PDF {#lock-pdf-by-password}



{{< figure align=center src="images/locked-PDF.jpg" alt="用密码锁定 PDF">}}


让我们首先通过使用密码锁定文件来为文件添加保护。以下步骤展示了如何使用 C# 为 PDF 文档添加密码安全性。

* 使用 [AddPasswordOptions][11] 类定义密码。
* 使用 [Merger][12] 类加载 PDF 文件。
* 通过使用 [AddPassword][13] 方法添加密码来锁定文件。
* 使用 [Save][14] 方法保存受保护的文件。

以下 C# 代码将密码添加到 PDF 文件以确保安全。

```
/*
 * Add password protection to the PDF document using C#
 */
string filePath = @"path/document.pdf";

AddPasswordOptions addOptions = new AddPasswordOptions("mySECRETpassWORD");

using (Merger merger = new Merger(filePath))
{
    merger.AddPassword(addOptions);
    merger.Save(@"path/protected-document.pdf");
}
```

这是上述代码的输出。当您尝试打开 PDF 文件时，编辑器或查看器会要求您输入密码以证明您的权限。



{{< figure align=center src="images/enter-pwd-to-protected-pdf-1024x298.png" alt="输入受保护 PDF 的密码">}}


## 在 C# 中更新 PDF 文件的现有密码 {#change-pdf-password}

哎呀！您的密码可能已泄露。让我们用新的和困难的方法快速地以编程方式改变它。以下步骤允许您在 C# 中的 .NET 应用程序中更改 PDF 文件的当前密码。

* 使用当前密码准备[加载选项][15]。
* 使用新密码准备[更新选项][16]。
* 使用 [Merger][17] 类和加载选项加载 PDF 文档。
* 使用 [UpdatePassword][18] 方法更改现有密码。
* 使用[Save][19]方法保存更改密码的锁定文件。

这是更改 PDF 文档当前密码的代码片段。

```
/*
 * Update password of the protected PDF document using C#
 */
string filePath = @"path/protected-document.pdf";

LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");
UpdatePasswordOptions updateOptions = new UpdatePasswordOptions("TOPSECRET_pa22WORD");

using (Merger merger = new Merger(filePath, loadOptions))
{
    merger.UpdatePassword(updateOptions);
    merger.Save(@"path/pwd-changed-document.pdf");
}
```

## 在 C# 中删除 PDF 文件的密码 - 解锁 PDF {#remove-password-to-unlock-pdf}



{{< figure align=center src="images/unlocked-PDF.jpg" alt="PDF 已解锁 - 已删除密码">}}


现在，我认为您不需要安全性，这就是您要删除密码的原因。让我们先打开文件，然后删除它的密码，这样每个人都可以轻松访问它。以下步骤显示如何通过使用 C# 删除其密码来解锁 PDF 文件。

* 使用文件密码准备[加载选项][20]。
* 使用 [Merger][21] 类和加载选项加载 PDF 文档。
* 使用 [RemovePassword][22] 方法删除现有密码。
* 使用[Save][23]方法保存解锁的文件。

以下 C# 代码片段通过删除现有密码来解锁 PDF 文件，因此任何人都可以在未经授权的情况下访问它。

```
/*
 * Remove password protection of PDF document using C#
 */
string filePath = @"path/protected-document.pdf";

LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");

using (Merger merger = new Merger(filePath, loadOptions))
{
    merger.RemovePassword();
    merger.Save(@"path/no-pwd-document.pdf");
}
```

## 结论

让我们总结一下我们今天学到的东西。我们从简单的 PDF 文档开始，并添加了密码保护。然后我们更改了该 PDF 文件的现有密码。最后，我们学习了如何删除 PDF 文档的密码。现在，您可以使用 .NET API 构建自己的密码保护器或密码删除器应用程序。

要了解有关 .NET 的 GroupDocs.Merger 的更多信息，请访问 [文档][24]。如有疑问，请通过 [论坛][25] 联系我们。

## 获取免费 API 许可证

您可以[获得免费的临时许可证][26] 使用 API 而不受评估限制。

## 也可以看看

* [使用 C# 为 PDF 文件添加水印][27]
* [如何使用C#分割PDF文件][28]
* [在Java中添加或删除PDF文件的密码保护][29]







[1]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[2]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[3]: #lock-unlock-pdf-dotnet-api
[4]: #lock-pdf-by-password
[5]: #change-pdf-password
[6]: #remove-password-to-unlock-pdf
[7]: https://products.groupdocs.com/merger/net/
[8]: https://docs.groupdocs.com/merger/net/
[9]: https://downloads.groupdocs.com/merger
[10]: https://www.nuget.org/packages/groupdocs.merger
[11]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/addpasswordoptions
[12]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/addpassword
[14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[15]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/loadoptions
[16]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/updatepasswordoptions
[17]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[18]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/updatepassword
[19]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[20]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/loadoptions
[21]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[22]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/removepassword
[23]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[24]: https://docs.groupdocs.com/merger
[25]: https://forum.groupdocs.com/
[26]: https://purchase.groupdocs.com/temporary-license
[27]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[28]: https://blog.groupdocs.com/2021/10/11/split-pdf-files-in-csharp/
[29]: https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/


