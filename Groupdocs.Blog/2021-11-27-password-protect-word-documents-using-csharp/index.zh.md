---
title: "如何使用 C# 对 Word 文档进行密码保护和删除保护"
date: Sat, 27 Nov 2021 04:30:16 +0000
draft: false
url: /zh/2021/11/27/password-protect-word-documents-using-csharp/
author: 'Shoaib Khan'
summary: "让我们讨论如何通过设置密码保护来限制对 Word 文档的访问。我们已经学会了锁定和解锁 PDF 和 PowerPoint 文件。在本文中，我们将看到**如何使用 C# 对 Word 文档进行密码保护**。此外，我们将学习**删除密码以解锁 Word 文档**，最后，**如何在 .NET 应用程序中更改 DOC 和 DOCX 文件的现有密码**。"
tags: ['add password in csharp', 'Change Doc Password in C#', 'Lock Files in CSharp', 'Lock Word Files in CSharp', 'Remove Password in CSharp', 'Unlock Files in CSharp']
categories: ['GroupDocs.Merger Product Family']
---

让我们讨论如何通过设置密码保护来限制对 Word 文档的访问。我们已经学会了[锁定和解锁 PDF][1] 和 [PowerPoint][2] 文件。在本文中，我们将看到**如何使用 C# 对 Word 文档进行密码保护**。此外，我们将学习**删除密码以解锁 Word 文档**，最后，**如何在 .NET 应用程序中更改 DOC 和 DOCX 文件的现有密码**。



{{< figure align=center src="images/lock-unlock-word-documents-in-dotnet.jpg" alt="使用 C# 密码保护 Word 文档">}}


下面讨论以下主题：

* [.NET API 密码保护 Word 文档][3]
* [为Word文档添加密码][4]
* [修改Word文档密码][5]
* [如何从Word文档中删除密码][6]

## .NET API 用于密码保护 Word 文档 {#dotnet-api-lock-unlock-documents}

[GroupDocs.Merger][7] 提供了 .NET API，允许在 .NET 应用程序中锁定和解锁 Word 文档。我们将使用 [GroupDocs.Merger for .NET][8] 添加、更改和删除密码保护。除了保护和取消保护 Word 文档之外，使用 API 可以对 Word 文档进行更多操作。 [文档][9] 可用于解释详细功能、支持的文件格式等。

您可以从 [下载部分][10] 下载 **DLLs** 或 **MSI** 安装程序，或通过 [NuGet][11] 在您的 .NET 应用程序中安装 API。

```
PM> Install-Package GroupDocs.Merger
```

## C# 中的密码保护 Word 文档 {#password-protect-document}

{{< figure align=center src="images/locked-doc.jpg" alt="以编程方式锁定的 Word 文档">}}


让我们讨论如何为word文档添加密码并使其受密码保护。以下步骤显示如何使用 C# 使用密码锁定 Word 文档 (DOC/DOCX)。

* 使用 [AddPasswordOptions][12] 设置密码选项。
* **使用 [Merger][13] 类加载**文档。
* **添加**密码以使用 [AddPassword][14] 方法锁定加载的 Word 文档。
* **使用 [Save][15] 方法保存**受密码保护的文件。

以下代码片段显示了如何使用 C# 对 Word 文档进行密码保护。

```
/*
 * Password Protect Word Documents using C#
 */
string filePath = @"path/document.docx";

AddPasswordOptions addOptions = new AddPasswordOptions("mySECRETpassWORD");

using (Merger merger = new Merger(filePath))
{
    merger.AddPassword(addOptions);
    merger.Save(@"path/protected-document.docx");
}
```

现在，当您尝试打开受密码保护的文档时，文档查看器和编辑器将要求输入密码以打开文件。



{{< figure align=center src="images/enter-pwd-to-open-protected-word-doc.jpg" alt="输入密码以打开受保护的 Word 文档">}}


## 在 C# 中更改 Word 文档的现有密码 {#change-password}

您的旧密码可能太常见以至于被猜到了。让我们改变它，下次更加小心。以下步骤指导如何使用 C# 更改 Word 文档的现有密码。

* 使用当前密码准备[LoadOptions][16]。
* 使用新密码定义 [UpdatePasswordOptions][17]。
* **使用 [Merger][18] 类加载** DOC/DOCX 文件。
* **使用 [UpdatePassword][19] 方法更改**密码。
* **使用 [Save][20] 方法保存**具有新密码的受保护文档。

这是更改 DOCX 文件现有密码的 C# 代码片段。

```
/*
 * Change password of the protected DOC/DOCX documents in C#
 */
string filePath = @"path/protected-document.docx";

LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");
UpdatePasswordOptions updateOptions = new UpdatePasswordOptions("TOPSECRET_pa22WORD");

using (Merger merger = new Merger(filePath, loadOptions))
{
    merger.UpdatePassword(updateOptions);
    merger.Save(@"path/pwd-changed-document.docx");
}
```

## 在 C# 中从 Word 文档中删除密码 {#remove-password-to-unlock}



{{< figure align=center src="images/unlocked-DOC.jpg" alt="以编程方式解锁的 Word 文档">}}


现在让我们从不再保密的文件中删除保护。首先，打开Word文档，然后删除密码使其解锁。以下步骤显示如何通过使用 C# 删除密码来解锁 Word 文档。

* 使用文档现有的密码准备[LoadOptions][21]。
* **使用 [Merger][22] 类加载** Word 文档。
* **使用 [RemovePassword][23] 方法删除**其密码。
* **通过调用[Save][24]方法以DOC/DOCX格式保存**解锁文件。

以下代码示例通过使用 C# 删除密码来解锁 DOCX 格式的 Word 文档

```
/*
 * Remove password from Word document using C#
 */
string filePath = @"path/protected-document.docx";

LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");

using (Merger merger = new Merger(filePath, loadOptions))
{
    merger.RemovePassword();
    merger.Save(@"path/no-pwd-document.docx");
}
```

## 结论

让我们总结一下我们今天学到的东西。首先，我们使用一个简单的 Word 文档，使用 C# 对其进行密码保护。接下来，我们学会了更改 Word 文档的现有密码。最后，我们学习了如何从 Word 文件中删除密码以使其在任何 .NET 应用程序中解锁。

要了解有关 **GroupDocs.Merger for .NET** 的更多信息，请访问其 [文档][25] 以开始为各种 [支持的文档格式][26] 构建您自己的文档保护器或密码删除器应用程序。如有疑问，请通过 [论坛][27] 联系我们。

## 获取免费 API 许可证

您可以[获得免费的临时许可证][28] 使用 API 而不受评估限制。

## 也可以看看

* [添加和删除 PDF 文件的密码保护][29]
* [保护和取消保护 PowerPoint 文件][30]
* [将 Word 文档作为 HTML 响应页面查看][31]
* [合并 Word、PDF、Excel、PowerPoint 文件][32]
* [在 Word、Excel、PowerPoint 文件中插入 OLE 对象][33]







[1]: https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/
[2]: https://blog.groupdocs.com/2021/11/25/lock-unlock-ppt-pptx-files-with-password-using-csharp/
[3]: #dotnet-api-lock-unlock-documents
[4]: #password-protect-document
[5]: #change-password
[6]: #remove-password-to-unlock
[7]: https://products.groupdocs.com/merger/
[8]: https://products.groupdocs.com/merger/net/
[9]: https://docs.groupdocs.com/merger/net/
[10]: https://downloads.groupdocs.com/merger
[11]: https://www.nuget.org/packages/groupdocs.merger
[12]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/addpasswordoptions
[13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/addpassword
[15]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[16]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/loadoptions
[17]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/updatepasswordoptions
[18]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[19]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/updatepassword
[20]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[21]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/loadoptions
[22]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[23]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/removepassword
[24]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[25]: https://docs.groupdocs.com/merger
[26]: https://docs.groupdocs.com/merger/net/supported-document-formats/
[27]: https://forum.groupdocs.com/
[28]: https://purchase.groupdocs.com/temporary-license
[29]: https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/
[30]: https://blog.groupdocs.com/2021/11/25/lock-unlock-ppt-pptx-files-with-password-using-csharp/
[31]: https://blog.groupdocs.com/2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/
[32]: https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/
[33]: https://blog.groupdocs.com/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/


