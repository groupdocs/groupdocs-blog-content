---
title: "使用 C# 使用密码锁定和解锁 PowerPoint 文件"
date: Thu, 25 Nov 2021 15:48:29 +0000
draft: false
url: /zh/2021/11/25/lock-unlock-ppt-pptx-files-with-password-using-csharp/
author: 'Shoaib Khan'
summary: 'Today, we will provide password protection to our presentation files programmatically. In this article, we will see **how to lock **PowerPoint presentation files** with password protection in C#**. Further, we will learn to unlock these by **removing the password** and also **how to change the existing password** of PPT & PPTX presentation files.

本文讨论了以下主题：

* .NET API 使用密码保护 PowerPoint PPT/PPTX
* 通过添加密码锁定 PowerPoint 文件
* 在 C# 中更改 PPT/PPTX 密码
* 如何删除 PowerPoint 演示文稿密码'
tags: ['Add Password to PPT in CSharp', 'Change PPT Password in CSharp', 'Lock PPT in CSharp', 'Remove Password in CSharp', 'Unlock Files in CSharp']
categories: ['GroupDocs.Merger Product Family']
---

今天，我们将以编程方式为我们的演示文件提供密码保护。之前，我们在讨论 [C# 中 PDF 文件的密码保护][1] 时学到了类似的东西。在本文中，我们将看到**如何在 C# 中使用密码保护锁定 **PowerPoint 演示文件****。此外，我们将学习通过**删除密码**以及**如何更改 PPT 和 PPTX 演示文件的现有密码**来解锁这些。



{{< figure align=center src="images/password-protect-lock-unlock-presentations.jpg" alt="密码保护演示文稿 - 锁定解锁 PPT-PPTX">}}


下面讨论以下主题：

* [.NET API 使用密码保护 PowerPoint PPT/PPTX][2]
* [通过添加密码锁定 PowerPoint 文件][3]
* [在 C# 中更改 PPT/PPTX 密码][4]
* [如何删除 PowerPoint 演示文稿密码][5]

## .NET API 锁定和解锁 PowerPoint 文件 {#lock-unlock-ppt-dotnet-api}

为了保护演示文件，我们将使用 [GroupDocs.Merger for .NET][6]。此 API 允许为 .NET 应用程序中的演示文稿和其他文档添加、更改和删除密码安全功能。除了锁定和解锁 PPT 文件之外，API 还提供了更多功能，包括 [文档][7] 中提到的合并和拆分演示文稿。

您可以从 [下载部分][8] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][9] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Merger
```

## 在 C# 中为 PowerPoint 文件添加密码 - 锁定 PPT/PPTX {#lock-ppt-by-password}



{{< figure align=center src="images/locked-PPT.jpg" alt="用密码锁定PPT">}}


我们可以通过添加密码保护以编程方式锁定任何演示文件。以下步骤显示如何使用 C# 向 PowerPoint 演示文稿 (PPT/PPTX) 添加密码。

* 使用 [AddPasswordOptions][10] 定义密码。
* 使用 [Merger][11] 类加载 PowerPoint 文件。
* 通过使用 [AddPassword][12] 方法添加密码来应用保护。
* 使用 [Save][13] 方法保存受保护的演示文件。

以下 C# 代码片段通过添加密码以限制访问来锁定 PPT。

```
/*
 * Add password protection to the presentation files (PPT/PPTX) in C#
 */
string filePath = @"path/presentation.pptx";

AddPasswordOptions addOptions = new AddPasswordOptions("mySECRETpassWORD");

using (Merger merger = new Merger(filePath))
{
    merger.AddPassword(addOptions);
    merger.Save(@"path/protected-presentation.pptx");
}
```

这是上述代码的输出。当您尝试打开文件时，编辑器或查看器将要求输入密码以打开演示文稿。



{{< figure align=center src="images/enter-pwd-to-protected-pptx-presentation.png" alt="输入受保护 PPTX 的密码">}}


## 在 C# 中更新 PPT/PPTX 文件的现有密码 {#change-ppt-password}

好像有人偷看了你的密码。让我们改变它。以下步骤允许您使用 C# 更改现有的演示文件密码。

* 使用当前密码准备[加载选项][14]。
* 使用新密码准备[更新选项][15]。
* 使用 [Merger][16] 类加载演示文稿。
* 使用 [UpdatePassword][17] 方法更改密码。
* 调用[Save][18]方法来保存新密码的锁定文件。

这是更改 PowerPoint PPT/PPTX 演示文稿的现有密码的代码片段。

```
/*
 * Update password of the protected presentation files (PPT/PPTX) in C#
 */
string filePath = @"path/protected-presentation.pptx";

LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");
UpdatePasswordOptions updateOptions = new UpdatePasswordOptions("TOPSECRET_pa22WORD");

using (Merger merger = new Merger(filePath, loadOptions))
{
    merger.UpdatePassword(updateOptions);
    merger.Save(@"path/pwd-changed-presentation.pptx");
}
```

## 在 C# 中删除 PowerPoint 文件密码 - 解锁 PPT/PPTX {#remove-password-to-unlock-ppt}



{{< figure align=center src="images/unlocked-PPT.jpg" alt="解锁 PPT - 密码已删除">}}


现在让我们揭开封面，让每个人都从您的演示文稿中受益。首先，打开文件，然后删除其密码以便于访问。以下步骤显示了如何通过使用 C# 删除其密码来解锁 PPT 文件。

* 使用文件密码准备[加载选项][19]。
* **使用 [Merger][20] 类加载** PowerPoint 演示文稿文档。
* **使用 [RemovePassword][21] 方法删除**密码。
* **保存**使用[保存][22]方法解锁的文件。

以下 C# 代码示例通过删除密码来解锁 PowerPoint 演示文稿文件。

```
/*
 * Remove password protection of presentation files (PPT/PPTX) in C#
 */
string filePath = @"path/protected-presentation.pptx";

LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");

using (Merger merger = new Merger(filePath, loadOptions))
{
    merger.RemovePassword();
    merger.Save(@"path/no-pwd-presentation.pptx");
}
```

## 结论

让我们总结一下我们今天学到的东西。我们使用了一个简单的 PowerPoint 演示文稿 (PPTX)，首先，我们只需添加密码即可将其锁定。接下来，我们更改了演示文件的现有密码。最后，我们学习了如何删除 PowerPoint 演示文稿的密码。

要了解有关 .NET 的 GroupDocs.Merger 的更多信息，请访问 [文档][23] 并开始构建您自己的应用程序来锁定和解锁演示文件。如有疑问，请通过 [论坛][24] 联系我们。

## 获取免费 API 许可证

您可以[获得免费的临时许可证][25] 使用 API 而不受评估限制。

## 也可以看看

* [使用 C# 使用密码锁定和解锁 PDF 文件][26]
* [在 C# 中将 PPT、PPTX 演示文稿转换为 PDF][27]
* [使用C#给PDF文件加水印][28]
* [如何使用C#分割PDF文件][29]




[1]: https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/
[2]: #lock-unlock-ppt-dotnet-api
[3]: #lock-ppt-by-password
[4]: #change-ppt-password
[5]: #remove-password-to-unlock-ppt
[6]: https://products.groupdocs.com/merger/net/
[7]: https://docs.groupdocs.com/merger/net/
[8]: https://downloads.groupdocs.com/merger
[9]: https://www.nuget.org/packages/groupdocs.merger
[10]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/addpasswordoptions
[11]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[12]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/addpassword
[13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/loadoptions
[15]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/updatepasswordoptions
[16]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[17]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/updatepassword
[18]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[19]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/loadoptions
[20]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[21]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/removepassword
[22]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[23]: https://docs.groupdocs.com/merger
[24]: https://forum.groupdocs.com/
[25]: https://purchase.groupdocs.com/temporary-license
[26]: https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/
[27]: https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/
[28]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[29]: https://blog.groupdocs.com/2021/10/11/split-pdf-files-in-csharp/


