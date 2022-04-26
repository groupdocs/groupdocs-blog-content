---
title: "Java中PDF文件的密码保护"
date: Tue, 07 Dec 2021 07:36:00 +0000
draft: false
url: /zh/2021/12/07/password-protect-pdf-files-in-java/
author: 'Shoaib Khan'
summary: 'There are different security levels that you can provide to your confidential documents. You can apply watermarks, encrypt files, or you can make your documents password-protected. In this article, we will see **how to programmatically add password protection to the PDF files within the Java applications**. Further, we will learn to **change the password** and also to **remove the passwords** to unlock PDF files.

本文讨论了以下主题：

* 用于 PDF 文件密码保护的 Java API
*用Java密码保护PDF文件
* 在 Java 中更改 PDF 密码
* 如何删除 PDF 密码 - 解锁 PDF'
tags: ['Add Password to PDF in Java', 'Change PDF Password in Java', 'Lock PDF in Java', 'Password Protect Document', 'Remove Password in Java', 'Unlock PDF in Java']
categories: ['GroupDocs.Merger Product Family']
---

您可以为机密文档提供不同的安全级别。您可以[应用水印][1]、加密文件，也可以[使您的文档受密码保护][2]。在本文中，我们将了解**如何以编程方式为 Java 应用程序中的 PDF 文件添加密码保护**。此外，我们将学习**更改密码**以及**删除密码**以解锁 PDF 文件。



{{< figure align=center src="images/password-protect-lock-unlock-pdf-in-java.jpg" alt="在 Java 中使用密码保护 PDF 文件 - 锁定解锁">}}


下面讨论以下主题：

* [用于PDF文件密码保护的Java API][3]
* [用Java密码保护PDF文件][4]
* [用Java更改PDF密码][5]
* [如何删除PDF密码-解锁PDF][6]

## 用于锁定和解锁 PDF 文件的 Java API {#lock-unlock-pdf-java-api}

[GroupDocs.Merger for Java][7] 是允许锁定和解锁文档的 API。我们将使用它为 Java 应用程序中的 PDF 文档添加、更改和删除密码安全功能。除了保护和取消保护文档之外，API 还提供了更多功能，例如拆分、合并文档以及 [文档][8] 中提到的更多功能。

您可以从 [下载部分][9] 下载 **JAR** 文件，或者在您的 Java 应用程序中使用最新的存储库和依赖项 [Maven][10] 配置。

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-merger</artifactId>
        <version>21.9</version> 
</dependency>
```

## 在 Java 中为 PDF 添加密码 - 锁定 PDF {#lock-pdf-by-password}



{{< figure align=center src="images/locked-PDF.jpg" alt="用密码锁定 PDF">}}


让我们快速跳转到为 PDF 文件添加密码保护以确保安全。以下步骤显示了如何在 Java 中为 PDF 文档添加密码。

* 使用 [AddPasswordOptions][11] 类定义密码。
* 使用 [Merger][12] 类加载 PDF 文件。
* 通过使用 [addPassword()][13] 方法添加密码来保护文件。
* 使用 [save()][14] 方法保存受保护的文件。

以下代码片段将密码添加到 Java 中的 PDF 文件。

```
/*
 * Add password protection to the PDF document in Java
 */
Merger merger = new Merger("path/document.pdf");
AddPasswordOptions addOptions = new AddPasswordOptions("mySECRETpassWORD");

merger.addPassword(addOptions);
merger.save("path/protected-document.pdf");
```

如果您尝试打开受密码保护的 PDF 文件，PDF 查看器将要求输入密码。



{{< figure align=center src="images/enter-pwd-to-protected-pdf-1024x298.png" alt="输入受保护 PDF 的密码">}}


## 用 Java 更新 PDF 文件的现有密码 {#change-pdf-password}

如果你的秘密不再是秘密怎么办？再把它保密。让我们将密码更改为新密码。以下步骤更改 Java 中 PDF 文件的现有密码。

* 使用当前密码设置[加载选项][15]。
* 现在使用新密码设置[更新选项][16]。
* 使用 [Merger][17] 类和加载选项加载 PDF 文档。
* 使用 [updatePassword()][18] 方法更改现有密码。
* 使用 [save()][19] 方法使用更新的密码再次保存受密码保护的文件。

代码片段使用 Java 代码更改 PDF 文档的当前密码。

```
/*
 * Update password of the protected PDF document in Java
 */
LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");
UpdatePasswordOptions updateOptions = new UpdatePasswordOptions("TOPSECRET_pa22WORD");

Merger merger = new Merger("path/protected-document.pdf", loadOptions);
merger.updatePassword(updateOptions);
merger.save("path/pwd-changed-document.pdf");
```

## 从 Java 中的 PDF 文件中删除密码 - 解锁 PDF {#remove-password-to-unlock-pdf}



{{< figure align=center src="images/unlocked-PDF.jpg" alt="PDF 已解锁 - 已删除密码">}}


如果不再需要文件保护，您可以删除密码。以下步骤显示如何在 Java 中删除受保护 PDF 文件的密码。

* 使用现有密码准备[加载选项][20]。
* 使用加载选项使用 [Merger][21] 类加载 PDF 文档。
* 使用 [removePassword()][22] 方法删除其密码。
* 使用 [save()][23] 方法保存解锁的文件。

以下是删除 PDF 文件密码以使其解锁的 Java 代码示例。

```
/*
 * Remove password protection of PDF document in Java
 */
LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");

Merger merger = new Merger("path/protected-document.pdf", loadOptions);
merger.removePassword();
merger.save("path/no-pwd-document.pdf");
```

## 获取免费 API 许可证

您可以[获得免费的临时许可证][24] 使用 API 而不受评估限制。

## 结论

最后，我们讨论了 PDF 文档的密码保护。最初，我们通过添加密码来锁定 PDF 文件。然后，我们更改了它的密码。最后，我们删除了 PDF 文件密码以保持这些文件解锁。现在您可以考虑构建自己的密码保护器和密码删除器 Java 应用程序。

要了解有关 Java 的 GroupDocs.Merger 的更多信息，请访问 [文档][25]。如有疑问，请通过 [论坛][26] 联系我们。

## 也可以看看

* [用Java拆分PDF文件的方法][27]
* [Java 中的水印 PDF 文件][28]
* [使用 C# 对 PDF 文件进行密码保护][29]



[1]: https://blog.groupdocs.com/category/watermark/
[2]: https://blog.groupdocs.com/?s=password
[3]: #lock-unlock-pdf-java-api
[4]: #lock-pdf-by-password
[5]: #change-pdf-password
[6]: #remove-password-to-unlock-pdf
[7]: https://products.groupdocs.com/merger/java/
[8]: https://docs.groupdocs.com/merger/java/
[9]: https://downloads.groupdocs.com/merger
[10]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs
[11]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/AddPasswordOptions
[12]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[13]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#addPassword(com.groupdocs.merger.domain.options.interfaces.IAddPasswordOptions)
[14]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[15]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/LoadOptions
[16]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/UpdatePasswordOptions
[17]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[18]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#updatePassword(com.groupdocs.merger.domain.options.interfaces.IUpdatePasswordOptions)
[19]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[20]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/LoadOptions
[21]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger
[22]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#removePassword()
[23]: https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)
[24]: https://purchase.groupdocs.com/temporary-license
[25]: https://docs.groupdocs.com/merger
[26]: https://forum.groupdocs.com/
[27]: https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/
[28]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/
[29]: https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/