---
title: "从 Java 中的 JSON 数据生成报告"
date: Wed, 10 Feb 2021 18:40:00 +0000
draft: false
url: /zh/2021/02/10/generate-pdf-report-from-json-data-in-java/
author: 'Shoaib Khan'
summary: 'JSON is a formatted and readable data interchange format to transmit data with attributes. However, the large data in JSON format is not very presentable and easily understandable. We mostly need to convert the large JSON data into a presentable format. This article will guide you to **convert JSON data into PDF report in Java** using a simple template.

[继续阅读...][1]'
tags: ['Convert JSON to PDF in Java', 'Generate PDF report from JSON', 'Generate PDF Report in Java', 'JSON to PDF using Template in Java']
categories: ['GroupDocs.Assembly Product Family']
---

JSON 是一种格式化且可读的数据交换格式，用于传输带有属性的数据。但是，JSON 格式的大数据不是很形象，也不是很容易理解。我们主要需要将大型 JSON 数据转换为可呈现的格式。本文将指导您使用一个简单的模板**将 JSON 数据转换为 Java 中的 PDF 和 MS Word 报告**。

## 报告生成 Java API

我将使用 [GroupDocs.Assembly for Java][2] API 从提供的 **JSON** 数据和 **DOCX** 和 **TXT** 格式的模板生成报告。它还支持从**CSV、XML** 数据源自动生成多种格式的报告。

### 下载或配置

您可以从 [下载部分][3] 下载 **JAR** 文件，或者只获取 **基于 maven 的** Java 应用程序的 pox.xml 的存储库和依赖项配置。

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
        <version>21.1</version> 
</dependency>
```

## 从 Java 中的 JSON 数据生成 PDF 报告

让我们快速跳转到将引导您将 JSON 数据转换为格式化的 PDF 报告的步骤。

* 获取JSON数据源
* 根据JSON数据定义模板
* 提供 JSON 数据源和模板到简单的 java 代码生成报告。



{{< figure align=center src="images/json-to-pdf-report-in-java.jpg" alt="Java 中的 JSON 到 PDF 报告">}}


### JSON 数据

对于 PDF 报告生成，我将使用经理及其各自客户和详细信息的以下示例 JSON 数据。

```
\[
	{
		"Name":"John Smith","Contract":\[
		{"Client":{"Name":"A Company"},"Price":1200000},
		{"Client":{"Name":"B Ltd."},"Price":750000},
		{"Client":{"Name":"C & D"},"Price":350000}\]
	},
	{
		"Name":"Tony Anderson","Contract":\[
		{"Client":{"Name":"E Corp."},"Price":650000},
		{"Client":{"Name":"F & Partners"},"Price":550000}\]
	},
	{
		"Name":"July James","Contract":\[
		{"Client":{"Name":"G & Co."},"Price":350000},
		{"Client":{"Name":"H Group"},"Price":250000},
		{"Client":{"Name":"I & Sons"},"Price":100000},
		{"Client":{"Name":"J Ent."},"Price":100000}\]
	}
\]
```

＃＃＃ 模板

以 TXT 或 DOCX 格式定义以下模板。这将允许迭代经理及其各自的客户及其详细信息。之后，您可以跳转到生成报告的代码。

```
<<foreach [in managers]>>Manager: <<[Name]>>
Contracts:
<<foreach [in Contract]>>- <<[Client.Name]>> ($<<[Price]>>)
<</foreach>>
<</foreach>>
```

### Java 步骤从 JSON 生成 PDF 报告

以下步骤和 Java 代码允许根据定义的模板将 JSON 数据自动转换为 PDF 报告。

* 定义 JSON 数据文件、.txt 模板文件和 PDF 输出报告文件路径。
* 使用 JSON 数据文件实例化 [JsonDataSoure][4]。
* 使用定义的 JsonDataSource 创建 [DataSourceInfo][5]。
* 调用 [DocumentAssembler][6] 类的 _**assembleDocument**_ 方法，根据提供的 JSON 数据和定义的模板生成 PDF 报告。

```
// 使用 Java 中的 TXT 模板和 GroupDocs.Assembly API 从 JSON 数据生成 PDF 报告
// 定义数据源、模板和输出报告文件。
String jsonFilePath = "dataPath/ManagerData.json";
String templateFilePath = "templatePath/template.txt";
String reportFilePath = "reportsPath/reportFromJSON.pdf";				
// 实例化 JSON 数据源
JsonDataSource datasource= new JsonDataSource(jsonFilePath);			  
DataSourceInfo dataSourceInfo = new DataSourceInfo(datasource,"managers");
// 生成报告
DocumentAssembler assembler = new DocumentAssembler();
assembler.assembleDocument(templateFilePath,reportFilePath,dataSourceInfo);
```

## 从 Java 中的 JSON 数据生成 MS Word 报告

同样，像上面的 PDF 报告生成一样，您可以通过以下方式轻松创建 DOCX 报告：

* 以 DOCX 格式定义相同的模板。
* 设置输出报表文档格式为DOCX。
* 其余代码将保持不变，以从 JSON 数据生成 MS Word DOCX 报告。

```
// 使用 Java 中的 DOCX 模板和 GroupDocs.Assembly API 从 JSON 数据生成 Word 报告
// 定义数据源、模板和输出报告文件。
String jsonFilePath = "dataPath/ManagerData.json";
String templateFilePath = "templatePath/template.docx";
String reportFilePath = "reportsPath/reportFromJSON.docx";			
// 实例化 JSON 数据源
JsonDataSource datasource= new JsonDataSource(jsonFilePath);			  
DataSourceInfo dataSourceInfo = new DataSourceInfo(datasource,"managers");
// 生成报告
DocumentAssembler assembler = new DocumentAssembler();
assembler.assembleDocument(templateFilePath,reportFilePath,dataSourceInfo);
```

有关更多详细信息、选项和示例，您可以浏览 [documentation][7] 和 [GitHub][8] 存储库。如果有进一步的疑问和歧义，请联系 [论坛][9] 上的免费支持。

## 结论

我希望您能够轻松构建自己的基于 Java 的应用程序，通过将 JSON 数据转换为 PDF 格式来生成报告。同样，您可以使用 CSV 和 XML 等其他数据源生成其他格式的报告，例如 DOCX。

## 也可以看看

* [在 C# 中从 JSON 数据生成报告][10]







[1]: https://blog.groupdocs.com/2021/02/10/generate-pdf-report-from-json-data-in-java
[2]: https://products.groupdocs.com/assembly/java
[3]: https://downloads.groupdocs.com/assembly/java
[4]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/JsonDataSource
[5]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DataSourceInfo
[6]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DocumentAssembler
[7]: https://docs.groupdocs.com/assembly/java/
[8]: https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-Java
[9]: https://forum.groupdocs.com/c/assembly
[10]: https://blog.groupdocs.com/2021/03/20/generate-reports-from-json-data-in-csharp/


