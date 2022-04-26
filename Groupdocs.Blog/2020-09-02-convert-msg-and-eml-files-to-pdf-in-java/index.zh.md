---
title: "在 Java 中将 MSG 和 EML 文件转换为 PDF"
date: Wed, 02 Sep 2020 14:04:02 +0000
draft: false
url: /zh/2020/09/02/convert-msg-and-eml-files-to-pdf-in-java/
author: 'Shoaib Khan'
summary: "电子邮件到 PDF 的转换通常是引用和共享电子邮件内容等要求所必需的。在本文中，我们将了解**如何使用 Java 将 MSG 和 EML 等电子邮件文件转换为 PDF **。以前，在 [早期的博客文章][1] 中，我们已经学会了在 .NET 应用程序中使用 C# 转换 MSG 和 EML 文件。这将有助于在桌面或 Web 应用程序中自动进行电子邮件转换。"
tags: ['convert emails to pdf', 'Convert MSG or EML to PDF in Java', 'eml to pdf in java', 'MSG to PDF in Java']
categories: ['GroupDocs.Conversion Product Family']
---



{{< figure align=center src="images/Convert-Emails-to-PDF-in-Java.png" alt="在 Java 中将电子邮件转换为 PDF">}}


电子邮件到 PDF 的转换通常是引用和共享电子邮件内容等要求所必需的。在本文中，我们将了解**如何使用 Java 将 MSG 和 EML 等电子邮件文件转换为 PDF**。以前，在 [早期的博客文章][2] 中，我们已经学会了在 .NET 应用程序中使用 C# 转换 MSG 和 EML 文件。这将有助于在桌面或 Web 应用程序中自动进行电子邮件转换。

以下是本文涵盖的主题：

* [Java 转换库][3]
* [使用 Java 将 MSG 转换为 PDF][4]
* [使用 Java 将 EML 转换为 PDF][5]

## Java 转换库 {#java-conversion-library}

在本文中，我将使用 [GroupDocs.Conversion for Java][6] API 进行转换。通过使用它，您可以将 MSG 和 EML 等电子邮件文档格式转换为 PDF 和其他格式，而不会丢失电子邮件格式。

您可以从 [下载][7] 部分获取 JAR 文件。对于基于 maven 的应用程序，以下是 pom.xml 配置：

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>20.6</version> 
</dependency>
```

## 使用 Java 将 MSG 转换为 PDF {#convert-msg-to-pdf-in-java}

以下是将 Outlook MSG 文件转换为 PDF 的步骤，只需几行代码。步骤中的嵌入链接将允许进一步探索类和方法。

1. 创建 [Converter][8] 类的实例并将 MSG 文件传递给构造函数。
2. 实例化 [PdfConvertOptions][9] 类。
3. 调用 [convert][10] 方法获取转换后的 PDF 文件。

```
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

public class EmailMessagesConverter 
{
	// Convert MSG message to PDF
	public void convertMsgtoPDF(String filePath) 
	{
		Converter converter = new Converter(filePath + "emailMessage.msg");
		PdfConvertOptions options = new PdfConvertOptions();
		converter.convert(filePath + "msg-Message.pdf", options);
	}
}
```

这是使用 Microsoft Outlook 创建的示例 MSG 文件。下面是PDF文件，它是通过使用上述java代码转换MSG文件获得的。



{{< figure align=center src="images/MSG-message.png" alt="要转换为 PDF 的 MSG 文件" caption="味精文件">}}




{{< figure align=center src="images/converted-msg-to-pdf-in-java.png" alt="从 MSG 转换的 PDF 文件" caption="使用上述 Java 代码从 MSG 格式转换的 PDF 文件。">}}


## 使用 Java 将 EML 转换为 PDF {#convert-eml-to-pdf-in-java}

我们可以以编程方式将我们以 EML 格式存储的电子邮件消息转换为具有类似 Java 代码行的 PDF 格式，非常简单有效。以下步骤将指导实现目标。

1. 初始化提供源 EML 文件路径的 [Converter][11] 对象。
2. 初始化 [PDFConvertOptions][12]。您可以为生成的 PDF 文件设置进一步的自定义。
3. 只需调用 Converter 类的 [convert][13] 方法并将生成的 PDF 文件路径和已设置的 PDFConvertOptions 作为参数传递给它。

```
// 将 EML 消息转换为 PDF
public void convertEmltoPDF(String filePath) 
{
	Converter converter = new Converter(filePath + "emailMessage.eml");
	PdfConvertOptions options = new PdfConvertOptions();
	converter.convert(filePath + "eml-Message.pdf", options);
}
```

下面显示的是源 EML 文件和转换后的 PDF 文件屏幕截图，已使用上述 java 代码转换。



{{< figure align=center src="images/EML-message.png" alt="要转换为 PDF 的 EML 文件" caption="EML 文件">}}




{{< figure align=center src="images/converted-eml-to-pdf-in-java.png" alt="从 EML 转换的 PDF 文件" caption="使用 Java 从 EML 格式转换的 PDF 文件。">}}


## 结论

在本文中，我们学习了如何使用 Java Conversion API 将 MSG 和 EML 文件转换为 PDF。此外，我们可以以编程方式对 PDF 文件应用自定义，以获得所需样式的结果。您可能会从文档中获得有关 Java 的 GroupDocs.Conversion 的更多信息。

## 也可以看看

* [在 C# 中将 EML 或 MSG 文件转换为 PDF][14]







[1]: https://blog.groupdocs.com/2019/12/06/convert-eml-or-msg-file-to-pdf-in-csharp/
[2]: https://blog.groupdocs.com/2019/12/06/convert-eml-or-msg-file-to-pdf-in-csharp/
[3]: https://blog.groupdocs.com/2020/09/02/convert-msg-and-eml-files-to-pdf-in-java/#java-conversion-library
[4]: https://blog.groupdocs.com/2020/09/02/convert-msg-and-eml-files-to-pdf-in-java/#convert-msg-to-pdf-in-java
[5]: https://blog.groupdocs.com/2020/09/02/convert-msg-and-eml-files-to-pdf-in-java/#convert-eml-to-pdf-in-java
[6]: https://products.groupdocs.com/conversion/java
[7]: https://downloads.groupdocs.com/conversion/java
[8]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion/Converter
[9]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/PdfConvertOptions
[10]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[11]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion/Converter
[12]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/PdfConvertOptions
[13]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[14]: https://blog.groupdocs.com/2019/12/06/convert-eml-or-msg-file-to-pdf-in-csharp/


