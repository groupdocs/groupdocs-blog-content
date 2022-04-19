---
title: "在 Java 中从 CSV 数据生成报告"
date: Wed, 07 Jul 2021 14:26:55 +0000
draft: false
url: /zh/2021/07/07/generate-reports-from-csv-data-in-java/
aliases:
- /2019/10/30/generate-reports-from-csv-xml-in-java/
- /2019/10/30/build-reports-using-csv-data-sources-in-groupdocs-assembly-for-java/
author: 'Shoaib Khan'
summary: "[逗号分隔值][1] (CSV) 是一种文件格式，用于以纯文本形式存储数据，其中值由逗号分隔。 CSV 广泛用于在应用程序之间交换数据。作为开发人员，我们经常需要将大型 CSV 数据转换为可呈现的格式。本文将指导您使用一个简单的模板**将 CSV 数据转换为 Java 中的 PDF 和 MS Word 报告**。"
tags: ['Convert CSV to PDF in Java', 'CSV to PDF using template', 'CSV to Word Report in Java', 'Generate PDF report from CSV', 'Generate PDF Report in Java', 'Generate Reports']
categories: ['GroupDocs.Assembly Product Family']
---

[逗号分隔值][2] (CSV) 是一种文件格式，用于以纯文本形式存储数据，其中值由逗号分隔。 CSV 广泛用于在应用程序之间交换数据。作为开发人员，我们经常需要将大型 CSV 数据转换为可呈现的格式。本文将指导您使用一个简单的模板**将 CSV 数据转换为 Java 中的 PDF 和 MS Word 报告**。

以下主题涵盖以下内容：

* [报告生成 Java API][3]
* [从 CSV 数据生成 PDF 报告][4]
* [从 CSV 数据生成 MS Word 报告][5]

## 报告生成 Java API {#report-generator-java-api}

[GroupDocs.Assembly for Java][6] 是我在本文中使用的报告生成 API，用于从选定的 **CSV** 数据和 **TXT** 格式的模板生成报告。它还支持从多个数据源（如 **JSON、XML** 以及 **MS Word**、**Excel** 和 **PowerPoint** 文件作为数据文件）自动生成报告。

### 下载或配置

您可以从 [下载部分][7] 下载 **JAR** 文件，或者仅获取 **基于 maven 的** Java 应用程序的 pox.xml 的存储库和依赖项配置。

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

## 在 Java 中从 CSV 数据生成 PDF 报告 {#csv-to-pdf-report-java}

让我们从将数据转换为可呈现的 PDF 开始。以下步骤将引导您将 CSV 数据转换为格式化的 PDF 报告。

* 加载 CSV 数据源
* 根据CSV数据定义模板
* 提供 CSV 数据源和模板，以简单的方法生成 PDF 报告。



{{< figure align=center src="images/csv-to-pdf-word-report-in-java.jpg" alt="Java 中的 CSV 到 PDF 报告">}}


### CSV 数据

对于 PDF 报告的生成，我将使用以下不同人的示例 CSV 数据以及他们各自的年龄和出生日期。

```
Name,Age,Birth  
John Doe,32,4/1/1989 16:00  
Jane Doe,29,1/31/1992 7:00  
John Smith,53,3/8/1968 13:00
```

＃＃＃ 模板

以 TXT 或 DOCX 格式定义以下模板。这允许使用他们的详细信息迭代人员列表。之后，您可以跳转到生成报告的代码。

```
<<foreach \[in persons\]>>Name: <<\[Name\]>>, Age: <<\[Age\]>>, Date of Birth: <<\[Birth\]:"dd.MM.yyyy">>
<</foreach>>
Average age: <<\[persons.**average**(p => p.Age)\]>>
```

### Java 步骤从 CSV 生成 PDF 报告

以下步骤解释了根据定义的模板将 CSV 数据自动转换为 PDF 报告。

* 定义 CSV 数据文件、.txt 模板文件和 PDF 输出报告文件路径。
* 用 CSV 数据文件实例化 [CsvDataSoure][8]。
* 使用定义的 CsvDataSource 创建 [DataSourceInfo][9]。
* 调用[DocumentAssembler][11]类的_[assembleDocument][10]_方法获取生成的PDF报告。

以下代码显示了如何将 CSV 数据转换为 Java 中的 PDF 报告。

```
// 使用 Java 中的 TXT 模板和 GroupDocs.Assembly API 从 CSV 数据生成 PDF 报告
// 定义数据源、模板和输出报告文件。
String csvDataSource = "dataPath/Person.csv";
String templateFilePath = "templatePath/template.txt";
String reportFilePath = "reportsPath/reportFromCSV.pdf";

// 加载 CSV 数据源
CsvDataLoadOptions options = new CsvDataLoadOptions(true);
CsvDataSource datasource= new CsvDataSource(csvDataSource,options);
DataSourceInfo dataSourceInfo = new DataSourceInfo(datasource,"persons");

// 生成报告
DocumentAssembler assembler = new DocumentAssembler();
assembler.assembleDocument(templateFilePath, reportFilePath, dataSourceInfo);
```

## 从 Java 中的 CSV 数据生成 MS Word 报告 {#csv-to-docx-report-java}

它与上面的 PDF 报告生成非常相似，您可以轻松地从 CSV 数据创建 MS Word DOC/DOCX 报告：

* 从文件中加载 CSV 数据。
* 以 TXT 或 DOCX 格式定义模板。
* 设置输出报表文档格式为 DOC/DOCX。
* 其余代码将保持不变，以从 CSV 数据生成 MS Word DOCX 报告。

以下代码显示了如何将 CSV 数据转换为 Java 中的 DOCX 报告。

```
// 使用 Java 中的 TXT 模板和 GroupDocs.Assembly API 从 CSV 数据生成 Word 报告
// 定义数据源、模板和输出报告文件。
String csvDataSource = "dataPath/Person.csv";
String templateFilePath = "templatePath/template.txt";
String reportFilePath = "reportsPath/reportFromCSV.docx";

// 加载 CSV 数据源
CsvDataLoadOptions options = new CsvDataLoadOptions(true);
CsvDataSource datasource= new CsvDataSource(csvDataSource,options);
DataSourceInfo dataSourceInfo = new DataSourceInfo(datasource,"persons");

// 生成报告
DocumentAssembler assembler = new DocumentAssembler();
assembler.assembleDocument(templateFilePath, reportFilePath, dataSourceInfo);
```

## 获取免费 API 许可证

您可以 [获得免费的临时许可证][12] 以便在没有评估限制的情况下使用 API。

## 结论

总而言之，您已经学会了用 Java 将 CSV 数据转换为 PDF 和 MS Word 报告。我希望您现在可以轻松构建自己的基于 Java 的应用程序，通过将 CSV 数据转换为 PDF 格式来生成报告。同样，您可以使用 JSON 和 XML 等数据源生成报告。

有关 API 的更多信息，您可以访问 [documentation][13] 和 [GitHub][14] 存储库。如果有进一步的疑问和歧义，请联系 [论坛][15] 上的免费支持。

## 也可以看看

* [使用 Java 从 JSON 数据生成报告][16]
* [使用 C# 从 CSV 数据创建报告][17]
* [使用 C# 从 JSON 数据生成报告][18]







[1]: https://docs.fileformat.com/spreadsheet/csv/
[2]: https://docs.fileformat.com/spreadsheet/csv/
[3]: #report-generator-java-api
[4]: #csv-to-pdf-report-java
[5]: #csv-to-docx-report-java
[6]: https://products.groupdocs.com/assembly/java
[7]: https://downloads.groupdocs.com/assembly/java
[8]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/CsvDataSource
[9]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DataSourceInfo
[10]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DocumentAssembler#assembleDocument-java.lang.String-java.lang.String-com.groupdocs.assembly.DataSourceInfo...-
[11]: https://apireference.groupdocs.com/assembly/java/com.groupdocs.assembly/DocumentAssembler
[12]: https://purchase.groupdocs.com/temporary-license
[13]: https://docs.groupdocs.com/assembly/java/
[14]: https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-Java
[15]: https://forum.groupdocs.com/c/assembly
[16]: https://blog.groupdocs.com/2021/02/10/generate-pdf-report-from-json-data-in-java/
[17]: https://blog.groupdocs.com/2021/08/15/generate-reports-from-csv-data-in-csharp/
[18]: https://blog.groupdocs.com/2021/03/20/generate-reports-from-json-data-in-csharp/


