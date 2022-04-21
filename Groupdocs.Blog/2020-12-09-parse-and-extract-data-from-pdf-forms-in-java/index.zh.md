---
title: "阅读 Java 中的 PDF 表单字段"
date: Wed, 09 Dec 2020 15:43:10 +0000
draft: false
url: /zh/2020/12/09/parse-and-extract-data-from-pdf-forms-in-java/
aliases:
- /2018/09/13/extract-data-from-pdf-forms-using-groupdocs.parser-for-java-18.9/
author: 'Shoaib Khan'
summary: "在本文中，我们将讨论**如何在 Java 中以编程方式解析 PDF 文档并从 PDF 表单中提取值**。在很多情况下，我们会收到大量填写的调查表或 PDF 格式的反馈。我们可以轻松提取填充的数据值并将其用于分析。现在让我们直接阅读这些 PDF 表单并在 Java 应用程序中提取填充的数据字段值。"
tags: ['Extract Text from PDF Forms', 'Extract Text from PDF Forms in Java', 'Parse PDF Forms in Java']
categories: ['GroupDocs.Parser Product Family']
---

在本文中，我们将讨论**如何在 Java 中以编程方式解析 PDF 文档并从 PDF 表单中提取值**。在很多情况下，我们会收到大量填写的调查表或 PDF 格式的反馈。我们可以轻松提取填充的数据值并将其用于分析。现在让我们直接阅读这些 PDF 表单并在 Java 应用程序中提取填充的数据字段值。



{{< figure align=center src="images/Extract-from-PDF-Form-in-java.jpeg" alt="解析 PDF 表单以提取 Java 中的值">}}


## 用于从 PDF 表单解析和提取值的 Java API

**GroupDocs** 提供 [文档解析和数据提取 Java API][1]，它支持的不仅仅是文字处理、演示文稿、电子表格、电子邮件、PDF、标记、电子书和存档格式。除了提取文本和图像外，API 还支持从 [支持的文档格式][2] 中提取元数据。 API 的显着特点之一是使用简单的 Java 代码**解析可填写的 PDF 文档并从表单字段中提取值**。

在接下来的示例中，我将使用提到的 API 即 **[GroupDocs.Parser for Java][3]**，因此我建议您准备好您的环境来实现该功能。您可以从 [下载][4] 部分下载最新的 JAR 文件，或者在基于 Maven 的 Java 应用程序中添加以下配置。有关 API 的详细信息，请访问 [API 参考][5]。

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
	<artifactId>groupdocs-parser</artifactId>
	<version>20.8</version> 
</dependency>
```

## 从 Java 中的 PDF 表单字段中提取数据

以下是如何从 PDF 表单中提取字段值的简单步骤。

* 使用目标 PDF 表单初始化 **[Parser][6]** 对象。
* 调用**[parseForm][7]**方法获取PDF表单中的所有数据。
* 遍历收集到的数据，得到想要的字段值。

以下代码显示了如何解析 PDF 文档并从 Java 中填充的 PDF 表单字段中获取值。

```
// 使用 GroupDocs.Parser 的 Java API 解析填充的 PDF 表单以提取字段值
Parser parser = new Parser("filePath/PDFForm.pdf"); 
// 从 PDF 表单中提取数据
DocumentData data = parser.parseForm();
// 迭代提取的 PDF 表单数据
for (int i = 0; i < data.getCount(); i++) {
    System.out.print(data.get(i).getName() + ": ");
    PageTextArea area = (data.get(i).getPageArea() instanceof PageTextArea)
            ? (PageTextArea) data.get(i).getPageArea()
            : null;
    System.out.println(area == null ? "Not a template field" : area.getText());
}
```

```
COMPANY: GroupDocs
EMAIL: everything@groupdocs.com
COUNTRY: Australia
```

## 结论

我希望，Java 开发人员现在熟悉解析 PDF 文档以从 PDF 表单字段中提取文本值的简单、精确和有效的方法。如果您有兴趣了解更多有关 API 的基本和高级功能的信息，可以浏览 [文档][8]。

如有任何疑问，请联系@ [论坛][9] 支持。

## 也可以看看

* [使用 C# 读取 PDF 表单域][10]
* [使用Java从文档中提取图像][11]







[1]: https://products.groupdocs.com/parser/java
[2]: https://docs.groupdocs.com/parser/java/supported-document-formats/
[3]: https://products.groupdocs.com/parser/java
[4]: https://downloads.groupdocs.com/parser/java
[5]: https://apireference.groupdocs.com/parser/java
[6]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser
[7]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#parseForm()
[8]: https://docs.groupdocs.com/parser/java/
[9]: https://forum.groupdocs.com/c/parser
[10]: https://blog.groupdocs.com/2020/12/23/parse-and-extract-data-from-pdf-forms-in-csharp/
[11]: https://blog.groupdocs.com/2020/10/27/extract-images-from-pdf-word-excel-ppt-using-java/


