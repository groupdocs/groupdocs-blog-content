---
title: "'如何在 Java 中对 Word 文档进行密码保护和删除保护'"
date: Wed, 02 Feb 2022 08:45:00 +0000
draft: false
url: /zh/2022/02/02/lock-unlock-word-documents-with-password-in-java/
author: 'Shoaib Khan'
summary: "早些时候，我们通过应用密码来限制对 [PDF 文档](https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/) 的访问。在本文中，我们将看到**如何在 Java 中使用密码保护 Word 文档**。此外，我们还将学习**更改 DOC 和 DOCX 文件的现有密码**，最后，**如何在 Java 应用程序中解除密码保护以解锁** Word 文档。"
tags: ['Add Password in Java', 'Change Password in Java', 'Lock Files in Java', 'Lock Word Files in Java', 'Password Protect Word Documents', 'Remove Password in Java']
categories: ['GroupDocs.Merger Product Family']
---

早些时候，我们通过应用密码来限制对 [PDF 文档](https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/) 的访问。在本文中，我们将看到**如何在 Java 中使用密码保护 Word 文档**。此外，我们还将学习**更改 DOC 和 DOCX 文件的现有密码**，最后，**如何在 Java 应用程序中解除密码保护以解锁** Word 文档。

{{< figure align=center src="images/lock-unlock-word-documents-in-java.jpg" alt="Java中的密码保护Word文档">}}


以下主题涵盖以下内容：

* [用于锁定/解锁 Word 文档的 Java API](#java-api-lock-unlock-documents)
* [为 Word 文档添加密码](#password-protect-document)
* [修改Word文档密码](#change-password)
* [如何从 Word 文档中删除密码](#remove-password-to-unlock)

## 用于锁定/解锁 Word 文档的 Java API {#java-api-lock-unlock-documents}

[GroupDocs.Merger](https://products.groupdocs.com/merger/) 展示了允许在 Java 应用程序中锁定和解锁 Word 文档的 Java API。我们将使用 [GroupDocs.Merger for Java](https://products.groupdocs.com/merger/java/) 将密码添加到 Word 文件中，更改密码，并从 Java 中的 Word 文件中删除密码保护。

您可以从 [下载部分](https://downloads.groupdocs.com/merger) 下载 **JAR** 文件或使用最新的存储库和依赖项 [Maven](https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs) 配置。

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

有关 API 和其他支持的文档格式的更多详细信息，您可以访问 [文档](https://docs.groupdocs.com/merger/java/) 和 [GitHub 存储库](https://github.com/groupdocs-merger) 获取源代码示例。

## Java中的密码保护Word文档 {#password-protect-document}



{{< figure align=center src="images/locked-DOC.jpg" alt="以编程方式锁定的 Word 文档">}}


让我们首先为 MS Word DOCX 文件添加密码以确保安全。以下步骤显示了如何在 Java 中为 Word 文档添加密码。

* 使用 [AddPasswordOptions](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/AddPasswordOptions) 类定义密码。
* 使用 [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) 类加载 DOCX 文件。
* 使用 [addPassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#addPassword(com.groupdocs.merger.domain.options.interfaces.IAddPasswordOptions)) 方法使其受密码保护。
* 使用适当的 [save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)) 方法保存受保护的文件。

以下 Java 代码片段将密码添加到 MS Word DOCX 文件。

```
/*
 * Java中的密码保护Word文档
 */
AddPasswordOptions addOptions = new AddPasswordOptions("mySECRETpassWORD");

Merger merger = new Merger("path/document.docx");
merger.addPassword(addOptions);
merger.save("path/protected-document.docx");
```

现在，每当您尝试打开受密码保护的文档时，文档查看器和编辑器都会要求输入密码以打开文件。

{{< figure align=center src="images/enter-pwd-to-open-protected-word-doc.jpg" alt="输入密码以打开受保护的 Word 文档">}}


## 在 Java 中更改 Word 文档的现有密码 {#change-password}

让我们用一个新密码来更改密码。以下步骤更改 Java 中 Word 文件的现有密码。

* 使用当前密码设置[加载选项](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/LoadOptions)。
* 现在使用 [密码更新选项](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/UpdatePasswordOptions) 定义新密码。
* 使用 [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) 类和定义的加载选项加载受保护的 Word 文档。
* 使用 [updatePassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#updatePassword(com.groupdocs.merger.domain.options.interfaces.IUpdatePasswordOptions)) 方法申请新密码。
* 使用 [save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)) 方法再次保存受密码保护的文件。

以下代码片段使用 Java 更改 Word 文档的当前密码。

```
/*
 * 在 Java 中更改受保护的 DOC/DOCX 文档的密码
 */
LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");
UpdatePasswordOptions updateOptions = new UpdatePasswordOptions("TOPSECRET_pa22WORD");

Merger merger = new Merger("path/protected-document.docx", loadOptions);
merger.updatePassword(updateOptions);
merger.save("path/pwd-changed-document.docx");
```

## 从 Java 中的 Word 文档中删除密码 {#remove-password-to-unlock}

如果文档不再保密并且不需要文件保护，您可以简单地删除密码。以下步骤显示了如何在 Java 中删除受保护 Word 文件的密码。

* 使用 [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) 类和现有密码加载受保护的 Word 文档。
* 使用 [removePassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#removePassword()) 方法删除其密码。
* 使用 [save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)) 方法保存解锁的 DOCX 文件。

以下是删除 Word 文件密码以使其解锁/不受保护的 Java 代码示例。

```
/*
 * 从 Java 中的 Word 文档中删除密码
 */
LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");

Merger merger = new Merger("path/protected-document.docx", loadOptions);
merger.removePassword();
merger.save("path/no-pwd-document.docx");
```

## 获取免费 API 许可证

您可以[获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 使用该 API，而不受评估限制。

## 结论

让我们总结一下我们上面讨论的内容。使用一个简单的 Word 文档，我们使用 Java 示例使用密码锁定它。接下来，我们学会了更改现有密码。最后，我们删除了 Word 文件的密码，使其在任何 Java 应用程序中都可以解锁。

要了解有关 **GroupDocs.Merger for Java** 的更多信息，请访问其 [文档](https://docs.groupdocs.com/merger) 以开始为各种受 [支持的文档格式](https://docs.groupdocs.com/merger/net/supported-document-formats/) 构建您自己的文档保护器或密码删除器应用程序。 如有疑问，请通过[论坛](https://forum.groupdocs.com/)联系我们。

## 也可以看看

* [Java 中的 PDF 文件数](https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/)
* [Java 中拆分 PDF 文件的不同方法](https://blog.groupdocs.com/2021/10/19/split-pdf-files-in-java/)
* [使用 Java 查找和替换文档中的单词](https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/)
* [使用 Java 将多种文件类型合并为一种](https://blog.groupdocs.com/2021/06/13/merge-multiple-file-types-using-java/)





