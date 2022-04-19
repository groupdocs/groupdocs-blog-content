---
title: "'Java 中 PowerPoint 演示文稿的密码保护'"
date: Thu, 10 Feb 2022 10:00:00 +0000
draft: false
url: /zh/2022/02/10/lock-unlock-ppt-pptx-files-with-password-in-java/
author: 'Shoaib Khan'
summary: "保护对于机密和私人文件很重要。在本文中，我们将了解**如何使用 Java 中的密码锁定 **PowerPoint 演示文件****。此外，我们将学习通过**删除密码**以及**如何更改PPT和PPTX文件的现有密码**来解锁演示文件。"
tags: ['Add Password to PPT in Java', 'Change PPT Password in Java', 'Lock PPT in Java', 'Remove Password in Java', 'Unlock PPT in Java']
categories: ['GroupDocs.Merger Product Family']
---

保护对于机密和私人文件很重要。在本文中，我们将了解**如何使用 Java 中的密码锁定 PowerPoint 演示文件**。此外，我们将学习通过**删除密码**以及**如何更改PPT和PPTX文件的现有密码**来解锁演示文件。



{{< figure align=center src="images/password-protect-lock-unlock-presentations-in-java.jpg" alt="密码保护演示文稿 - 在 Java 中锁定解锁 PPT-PPTX">}}


下面讨论以下主题：

* [使用密码保护 PowerPoint PPT/PPTX 的 Java API](#lock-unlock-ppt-java-api)
* [通过添加密码锁定 PowerPoint 文件](#lock-ppt-by-password)
* [更改PPT/PPTX密码](#change-ppt-password)
* [如何删除演示文稿密码](#remove-password-to-unlock-ppt)

## 用于锁定和解锁 PowerPoint 文件的 Java API {#lock-unlock-ppt-java-api}

为了处理演示文件的保护，我们将使用[GroupDocs.Merger](https://products.groupdocs.com/merger/)的Java API。 API 为演示文稿和其他文档提供添加、更改和删除密码保护功能。

### 下载并配置

从 [下载](https://downloads.groupdocs.com/merger/) 部分获取库。对于基于 Maven 的 Java 应用程序，只需添加以下 pom.xml 配置。在此之后，您可以尝试本文的示例以及 [GitHub](https://github.com/groupdocs-merger) 上提供的更多示例。详情可访问[API 参考](https://apireference.groupdocs.com/merger/java)。

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

## 在 Java 中为 PowerPoint 文件添加密码 - 锁定 PPT/PPTX {#lock-ppt-by-password}



{{< figure align=center src="images/locked-PPT.jpg" alt="用密码锁定PPT">}}


您可以通过以编程方式向其添加密码来轻松锁定任何演示文件。以下步骤显示如何将密码添加到 Java 中的任何 PowerPoint 演示文稿 (PPT/PPTX) 文件。

* 使用 [AddPasswordOptions](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/AddPasswordOptions) 设置密码。
* 使用 [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) 类加载演示文件。
* 使用 [addPassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#addPassword(com.groupdocs.merger.domain.options.interfaces.IAddPasswordOptions)) 应用密码方法。
* 使用 [save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)) 方法保存受保护的演示文稿。

以下 Java 代码片段通过向 PPT 文件添加密码来锁定演示文稿。

```
/*
 * Password Protect PowerPoint Files in Java
 */
AddPasswordOptions addOptions = new AddPasswordOptions("mySECRETpassWORD");

Merger merger = new Merger("path/presentation.pptx");
merger.addPassword(addOptions);
merger.save("path/protected-presentation.pptx");
```

当您尝试打开从上述代码获得的输出文件时，编辑器或查看器会在打开演示文稿时要求输入密码。



{{< figure align=center src="images/enter-pwd-to-protected-pptx-presentation.png" alt="输入受保护 PPTX 的密码">}}


## 在 Java 中更新 PPT/PPTX 文件的现有密码 {#change-ppt-password}

如果您怀疑您的密码被别人看了一眼。您可以轻松更改它。以下步骤允许您更改 Java 中演示文件的现有密码。

* 使用 **current** 密码准备 [加载选项](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/LoadOptions)。
* 使用 **new** 密码设置 [更新选项](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/UpdatePasswordOptions)。
* 使用 [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) 类加载演示文稿。
* 现在，使用 [updatePassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#updatePassword(com.groupdocs.merger.domain.options.interfaces.IUpdatePasswordOptions)) 方法。
* 最后调用[save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String))方法保存锁定的文件。

这是使用 PowerPoint PPT/PPTX 演示文稿中的新密码更改现有密码的 Java 代码片段。

```
/*
 * Change password of the protected PPT/PPTX files in Java
 */
LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");
UpdatePasswordOptions updateOptions = new UpdatePasswordOptions("TOPSECRET_pa22WORD");

Merger merger = new Merger("path/protected-presentation.pptx", loadOptions);
merger.updatePassword(updateOptions);
merger.save("path/pwd-changed-presentation.pptx");
```

## 在 Java 中删除演示文稿的密码 - 解锁 PPT/PPTX {#remove-password-to-unlock-ppt}



{{< figure align=center src="images/unlocked-PPT.jpg" alt="解锁 PPT - 密码已删除">}}


让我们删除保护，让每个人都可以访问该文件。只需打开文件，然后删除其密码以供公众访问。以下步骤显示了如何通过删除 Java 中的密码来解锁 PPT 文件。

* 使用最新密码准备[加载选项](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger.domain.options/LoadOptions)。
* **使用 [Merger](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger) 类加载** PowerPoint PPT/PPTX 文件。
* **使用 [removePassword()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#removePassword()) 方法删除**密码。
* **保存**使用 [save()](https://apireference.groupdocs.com/merger/java/com.groupdocs.merger/Merger#save(java.lang.String)) 方法解锁的文件。

以下 Java 代码示例从 PowerPoint 演示文稿文件中删除密码以使其保持解锁状态。

```
/*
 * Remove password from PowerPoint presentations in Java
 */
LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");

Merger merger = new Merger("path/protected-presentation.pptx", loadOptions);
merger.removePassword();
merger.save("path/no-pwd-presentation.pptx");
```

## 获取免费 API 许可证

您可以[获得免费的临时许可证](https://purchase.groupdocs.com/temporary-license) 使用该 API，而不受评估限制。

## 结论

让我们总结一下我们今天学到的东西。我们使用了 PowerPoint 演示文稿 (PPTX)，首先，我们为其添加了密码以将其锁定。接下来，我们更改了其现有密码。最后，我们学习了如何在 Java 中删除受保护的 PowerPoint 文件的密码。

要了解有关 Java 的 GroupDocs.Merger 的更多信息，请访问 [文档](https://docs.groupdocs.com/merger)。它将帮助您开发自己的应用程序来锁定和解锁演示文件。如有疑问，请通过 [论坛](https://forum.groupdocs.com/) 联系我们。

## 也可以看看

* [Java 中的水印 PowerPoint 文件](https://blog.groupdocs.com/2021/06/09/watermark-presentation-slides-using-java/)
* [Java 中的水印密码保护文档](https://blog.groupdocs.com/2021/11/26/watermark-password-protected-documents-in-java/)
* [使用 Java 在 Word、Excel、PowerPoint 中插入 OLE 对象](https://blog.groupdocs.com/2020/10/19/insert-ole-objects-in-word-excel-powerpoint-with-java/)
* [将演示文稿转换为 Java 中的图像](https://blog.groupdocs.com/2022/01/18/convert-presentations-to-images-in-java/)
* [在 Java 中将演示文稿转换为 PDF](https://blog.groupdocs.com/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/)





