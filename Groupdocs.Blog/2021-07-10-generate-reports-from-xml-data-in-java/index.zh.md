---
title: "在 Java 中从 XML 数据生成报告"
date: Sat, 10 Jul 2021 10:01:00 +0000
draft: false
url: /zh/2021/07/10/generate-reports-from-xml-data-in-java/
author: 'Shoaib Khan'
summary: "**XML** 是一个 e**X**tensive **M**arkup **L**anguage，它是自描述的、W3C 推荐的，旨在存储和传输数据。在收到 XML 格式的数据后，作为开发人员，您可以将其转换为任何其他更好的人类可读格式，如 PDF 或 MS Word 文档。本文将指导您使用简单的模板将 XML 数据转换为 Java 中的 PDF 和 MS Word 报告。"
tags: ['Convert XML to DOCX in Java', 'Convert XML to PDF in Java', 'Generate PDF Report from XML', 'Generate Reports in Java', 'XML to DOCX in Java', 'XML to PDF in Java']
categories: ['GroupDocs.Assembly Product Family']
---

**XML** 是一个 e**X**tensive **M**arkup **L**anguage，它是自描述的、W3C 推荐的，旨在存储和传输数据。在收到 XML 格式的数据后，作为开发人员，您可以将其转换为任何其他更好的人类可读格式，如 PDF 或 MS Word 文档。本文将指导您使用简单的模板将 XML 数据转换为 Java 中的 PDF 和 MS Word 报告。

下面讨论以下主题：

* [用于生成报告的 Java API][1]
* [使用 Java 从 XML 数据生成 PDF 报告][2]
* [使用 Java 从 XML 数据生成 MS Word DOC/DOCX 报告][3]

## 报告生成 Java API - XML 到 PDF 和 WORD {#generate-report-java-api}

[GroupDocs.Assembly][4] 提供 Java API 以使用 **DOCX** 或 **TXT** 模板从 **XML** 数据自动生成报告。它进一步支持**JSON、CSV、**和其他数据源，将数据转换为不同文件格式的可呈现报告。

### 下载或配置

您可以从 [下载部分][5] 下载 **JAR** 文件，或者仅获取 **基于 maven 的** Java 应用程序的 pox.xml 的存储库和依赖项配置。

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
        <artifactId>groupdocs-assembly</artifactId>
        <version>21.4</version> 
</dependency>
```

## 在 Java 中从 XML 数据生成 PDF 报告 {#xml-to-pdf-report-in-java}

让我们快速跳转到将引导您将 XML 数据转换为格式化的 PDF 报告的步骤。

* 加载 XML 数据源
* 根据您的 XML 数据定义模板
* 为报表生成方法提供 XML 数据源和模板。



{{< figure align=center src="images/xml-to-pdf-word-report-in-java.jpg" alt="Java 中的 XML 到 PDF 报告">}}


### XML 数据

对于 PDF 报告生成，使用以下 XML 示例数据。它包含经理及其各自客户的详细信息。

```
<Managers>
	<Manager>
		<Name>John Smith</Name>
		<Contract>
			<Client>
				<Name>A Company</Name>
			</Client>
			<Price>1200000</Price>
		</Contract>
		<Contract>
		...
		</Contract>
		...
	</Manager>
	<Manager>
		<Name>Tony Anderson</Name>
		...
	</Manager>
	...
</Managers>
```

＃＃＃ 模板

以 TXT 或 DOCX 格式定义以下模板。这允许迭代经理及其各自的客户。之后，使用下面提到的代码生成报告。

```
<<foreach \[in managers\]>>Manager: <<\[Name\]>>
Contracts:
<<foreach \[in Contract\]>>- <<\[Client.Name\]>> ($<<\[Price\]>>)
<</foreach>>
<</foreach>>
```

### Java 步骤从 XML 生成 PDF 报告

以下步骤和代码允许根据定义的模板从 XML 数据自动生成 PDF 报告。

* 定义 XML 数据文件、文本模板文件和 PDF 输出报告文件。
* 用 XML 数据文件实例化 [XMLDataSoure][6]。
* 使用已定义的 XML 数据源创建 [DataSourceInfo][7]。
* 调用[assembleDocument][8]方法生成PDF报告。

以下代码实现了上述步骤，并从 Java 中的 XML 数据源生成 PDF。

```
// 使用 Java 中的 TXT 模板从 XML 数据生成 PDF 报告
// 定义数据源、模板和输出报告文件。
String xmlDataSource = "dataPath/Managers.xml";
String templateFilePath = "templatePath/template.txt";
String reportFilePath = "reportsPath/PDFreportFromXML.pdf";

// 加载 XML 数据源
XmlDataSource datasource = new XmlDataSource(xmlDataSource);
DataSourceInfo dataSourceInfo = new DataSourceInfo(datasource,"managers");

// 组装文档以生成 PDF
DocumentAssembler assembler = new DocumentAssembler();
assembler.assembleDocument(templateFilePath, reportFilePath,dataSourceInfo);
```

## 从 Java 中的 XML 数据生成 MS Word 报告 {#xml-to-word-report-in-java}

同样，您可以使用 Java 中的相同 XML 数据创建 MS Word DOC/DOCX 报告。除了更改输出文件名外，不会有任何区别。

* 加载 XML 数据文件。
* 以 TXT 或 DOCX 格式定义模板。
* 设置输出报表文档格式为DOCX。
* 向 DocumentAssembler 提供 XML 数据文件、模板和输出文件路径，以将 XML 转换为 DOCX。

以下代码使用 Java 中定义的模板转换 XML 并生成 DOCX 文件。

```
// 使用 Java 中的文本模板从 XML 数据生成 MS Word 报告
// 定义数据源、模板和输出报告文件。
String xmlDataSource = "dataPath/Managers.xml";
String templateFilePath = "templatePath/template.docx";
String reportFilePath = "reportsPath/WordReportFromXML.docx";

//实例化 XML 数据源
XmlDataSource datasource = new XmlDataSource(xmlDataSource);
DataSourceInfo dataSourceInfo = new DataSourceInfo(datasource,"managers");

//组装文件 
DocumentAssembler assembler = new DocumentAssembler();
assembler.assembleDocument(templateFilePath, reportFilePath,dataSourceInfo);
```

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][9] 以便在没有评估限制的情况下使用 API。

## 结论

最后，您已经学会了将 XML 数据转换为 PDF 格式作为 Java 中的报告。此外，您已经看到使用模板从相同的 XML 生成 DOC/DOCX 格式的报告。在阅读了从 [**JSON**][10]、[**CSV**][11]、**XML** 生成 PDF 和 MS Word 报告系列之后，您应该能够轻松构建自己的报告生成器Java 应用程序。

同样，您可以将许多其他数据源转换为报告。有关更多详细信息、选项和示例，您可以访问 [文档][12] 和 GitHub 存储库。如有其他疑问，请通过 [论坛][13] 联系我们。

## 也可以看看

* [使用 Java 将 JSON 数据转换为 PDF 或 Word 报告][14]
* [使用 Java 将 CSV 数据转换为 PDF 或 Word 报告][15]







[1]: #generate-report-java-api
[2]: #xml-to-pdf-report-in-java
[3]: #xml-to-word-report-in-java
[4]: https://products.groupdocs.com/assembly
[5]: https://downloads.groupdocs.com/assembly/java
[6]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/XmlDataSource
[7]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DataSourceInfo
[8]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DocumentAssembler#assembleDocument-java.lang.String-java.lang.String-com.groupdocs.assembly.DataSourceInfo...-
[9]: https://purchase.groupdocs.com/temporary-license
[10]: https://blog.groupdocs.com/2021/02/10/generate-pdf-report-from-json-data-in-java/
[11]: https://blog.groupdocs.com/2021/07/07/generate-reports-from-csv-data-in-java/
[12]: https://docs.groupdocs.com/assembly/java/
[13]: https://forum.groupdocs.com/c/assembly
[14]: https://blog.groupdocs.com/2021/02/10/generate-pdf-report-from-json-data-in-java/
[15]: https://blog.groupdocs.com/2021/07/07/generate-reports-from-csv-data-in-java/


