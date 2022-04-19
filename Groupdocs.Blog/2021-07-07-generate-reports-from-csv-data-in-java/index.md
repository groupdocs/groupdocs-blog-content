---
title: 'Generate Reports from CSV Data in Java'
date: Wed, 07 Jul 2021 14:26:55 +0000
draft: false
url: /2021/07/07/generate-reports-from-csv-data-in-java/
aliases:
    - /2019/10/30/generate-reports-from-csv-xml-in-java/
    - /2019/10/30/build-reports-using-csv-data-sources-in-groupdocs-assembly-for-java/
author: 'Shoaib Khan'
summary: 'The [Comma Separated Values][1] (CSV) is a file format for storing the data in the form of plain text where the values are separated by commas. CSV is widely used for exchanging data among applications. As a developer, we often need to convert the large CSV data into a presentable format. This article will guide you to **convert CSV data into PDF and MS Word reports in Java** using a simple template.'
tags: ['Convert CSV to PDF in Java', 'CSV to PDF using template', 'CSV to Word Report in Java', 'Generate PDF report from CSV', 'Generate PDF Report in Java', 'Generate Reports']
categories: ['GroupDocs.Assembly Product Family']
---

The [Comma Separated Values][2] (CSV) is a file format for storing the data in the form of plain text where the values are separated by commas. CSV is widely used for exchanging data among applications. As a developer, we often need to convert the large CSV data into a presentable format. This article will guide you to **convert CSV data into PDF and MS Word reports in Java** using a simple template.

The following topics are covered below:

*   [Report Generation Java API][3]
*   [Generate PDF Report from CSV Data][4]
*   [Generate MS Word Report from CSV data][5]

## Report Generation Java API {#report-generator-java-api}

[GroupDocs.Assembly for Java][6] is the report generation API that I have used in this article to generate reports from the selected **CSV** data and a template in **TXT** format. It also supports report generation automation from multiple data sources like **JSON, XML**, and also from **MS Word**, **Excel**, and **PowerPoint** files as data files.

### Download or Configure

You may download the **JAR** file from the [downloads section][7], or just get the repository and dependency configurations for the pox.xml of your **maven-based** Java applications.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-assembly</artifactId>
        <version>21.4</version> 
</dependency>
```

## Generate PDF Report from CSV Data in Java {#csv-to-pdf-report-java}

Let’s start with the transformation of data into presentable PDF. The following steps will lead you to convert CSV data into a formatted PDF report.

*   Load CSV data source
*   Define template according to the CSV data
*   Provide CSV data source and template to simple method to generate PDF report.



{{< figure align=center src="images/csv-to-pdf-word-report-in-java.jpg" alt="CSV to PDF Report in Java">}}


### CSV Data

For the PDF report generation, I will be using the following sample CSV data of different persons along with their respective ages and date of birth.

```
Name,Age,Birth  
John Doe,32,4/1/1989 16:00  
Jane Doe,29,1/31/1992 7:00  
John Smith,53,3/8/1968 13:00
```

### Template

Define the following template in TXT or DOCX format. This allows iterating the list of persons with their details. After that, you can jump to the code for report generation.

```
<<foreach \[in persons\]>>Name: <<\[Name\]>>, Age: <<\[Age\]>>, Date of Birth: <<\[Birth\]:"dd.MM.yyyy">>
<</foreach>>
Average age: <<\[persons.**average**(p => p.Age)\]>>
```

### Java Steps to Generate PDF Report from CSV

The following steps explain the automatic conversion of CSV data into a PDF report according to the defined template.

*   Define CSV data file, .txt template file, and PDF output report file paths.
*   Instantiate [CsvDataSoure][8] with CSV data file.
*   Create [DataSourceInfo][9] with the defined CsvDataSource.
*   Call the _[assembleDocument][10]_ method of the [DocumentAssembler][11] class to get the generated PDF report.

The following code shows how to convert CSV data to PDF report in Java.

{{< gist GroupDocsGists 386745c6e850606db29ec44796406f20 "GeneratePdfReportFromCSV.java" >}}

## Generate MS Word Report from CSV data in Java {#csv-to-docx-report-java}

It is very similar to the above PDF report generation, you can easily create the MS Word DOC/DOCX report from the CSV data:

*   Load the CSV data from file.
*   Defining the template in TXT or DOCX format.
*   Set the output report document format as DOC/DOCX.
*   The rest of the code will remain the same to generate MS Word DOCX report from the CSV data.

The following code shows how to convert CSV data to DOCX report in Java.

{{< gist GroupDocsGists 386745c6e850606db29ec44796406f20 "GenerateWordReportFromCSVWithTemplate.java" >}}

## Get a Free API License

You can [get a free temporary license][12] in order to use the API without the evaluation limitations.

## Conclusion

To sum up, you have learned to convert the CSV data into PDF and MS Word reports in Java. I hope you are now comfortable building your own Java-based application to generate reports by converting CSV data to PDF format. Similarly, you can generate reports using data sources like JSON and XML.

For more about the API, you can visit [documentation][13] and the [GitHub][14] repository. In case of further queries and ambiguities, contact the free support on the [forum][15].

## See Also

*   [Generate Reports from JSON Data using Java][16]
*   [Create Reports from CSV Data using C#][17]
*   [Generate Reports from JSON Data using C#][18]







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

