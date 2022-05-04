---
title: "Generate Reports from XML Data in Java"
seoTitle: "PDF & Word Reports from XML in Java | XML to PDF and DOCX"
description: "Automate reports generation by converting XML data into PDF & DOC/DOCX via text based templates using Java API by GroupDocs."
date: Sat, 10 Jul 2021 10:01:00 +0000
draft: false
url: /2021/07/10/generate-reports-from-xml-data-in-java/
author: 'Shoaib Khan'
summary: "**XML** is an e**X**tensive **M**arkup **L**anguage that is self-descriptive, W3C Recommended, and designed to store and transport data. After receiving the data in XML format, as a developer, you can convert it into any other better human-readable format like PDF or MS Word document. This article will guide you to convert XML data into PDF and MS Word reports in Java using simple templates."
tags: ['Convert XML to DOCX in Java', 'Convert XML to PDF in Java', 'Generate PDF Report from XML', 'Generate Reports in Java', 'XML to DOCX in Java', 'XML to PDF in Java']
categories: ['GroupDocs.Assembly Product Family']
---

**XML** is an e**X**tensive **M**arkup **L**anguage that is self-descriptive, W3C Recommended, and designed to store and transport data. After receiving the data in XML format, as a developer, you can convert it into any other better human-readable format like PDF or MS Word document. This article will guide you to convert XML data into PDF and MS Word reports in Java using simple templates.

The following topics are discussed below:

*   [Java API for Generating Reports][1]
*   [PDF Report from XML Data using Java][2]
*   [MS Word DOC/DOCX Report from XML Data using Java][3]

## Report Generation Java API - XML to PDF and WORD {#generate-report-java-api}

[GroupDocs.Assembly][4] provides Java API to automate the report generation from the **XML** data using **DOCX** or **TXT** template. It further supports the **JSON, CSV,** and other data sources to convert the data into presentable reports of different file formats.

### Download or Configure

You may download the **JAR** file from the [downloads section][5], or just get the repository and dependency configurations for the pox.xml of your **maven-based** Java applications.

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

## Generate PDF Report from XML Data in Java {#xml-to-pdf-report-in-java}

Let’s quickly jumps to the steps that will lead you to convert XML data into the formatted PDF report.

*   Load the XML data source
*   Define the template according to your XML data
*   Provide XML data source and template to a method for report generation.



{{< figure align=center src="images/xml-to-pdf-word-report-in-java.jpg" alt="XML to PDF Report in Java">}}


### XML Data

For the PDF report generation, the following XML sample data is used. It contains the data of managers and their respective clients with details.

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

### Template

Define the following template in TXT or DOCX format. This allows iteration over Managers and their respective Clients. After that, use the code mentioned below for report generation.

```
<<foreach \[in managers\]>>Manager: <<\[Name\]>>
Contracts:
<<foreach \[in Contract\]>>- <<\[Client.Name\]>> ($<<\[Price\]>>)
<</foreach>>
<</foreach>>
```

### Java Steps to Generate PDF Report from XML

The following steps and the code allows automating the generation of PDF reports from the XML data as per the defined template.

*   Define XML data file, text template file, and PDF output report files.
*   Instantiate [XMLDataSoure][6] with XML data file.
*   Create [DataSourceInfo][7] with defined XML data source.
*   Call the [assembleDocument][8] method to generate the PDF report.

The following code implements the above steps and generates a PDF from the XML data source in Java.

{{< gist GroupDocsGists 836ca189a2cb4d2a7e5283c47a5a70ce "XmlToPdfReport.java" >}}

## Generate MS Word Report from XML data in Java {#xml-to-word-report-in-java}

Likewise, you can create the MS Word DOC/DOCX report from the same XML data in Java. There will be no difference, except to change the output file name.

*   Load the XML data file.
*   Defining the template in TXT or DOCX format.
*   Set the output report document format as DOCX.
*   Provide the XML data file, template, and output file path to DocumentAssembler to convert the XML to DOCX.

The following code converts the XML and generates the DOCX file using the defined template in Java.

{{< gist GroupDocsGists 836ca189a2cb4d2a7e5283c47a5a70ce "XmlToWordReport.java" >}}

## Get a Free API License

You can [get a free temporary license][9] in order to use the API without the evaluation limitations.

## Conclusion

To conclude, you have learned to convert your XML data into PDF format as a report in Java. Additionally, you have seen the report generation in DOC/DOCX format from the same XML using the template. After reading the series, Generate PDF and MS Word Reports from [**JSON**][10], [**CSV**][11], **XML**, you should be comfortable in building your own report builder Java application.

Similarly, you can convert many other data sources to report. For more details, options, and examples, you can visit [documentation][12] and the GitHub repository. In case of further queries, contact us via the [forum][13].

## See Also

*   [Convert JSON Data to PDF or Word Report using Java][14]
*   [Transform CSV Data into PDF or Word Report using Java][15]







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

