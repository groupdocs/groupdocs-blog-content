---
title: 'Convert Selected or Partial Spreadsheet Rows'
date: Fri, 30 Aug 2019 10:50:52 +0000
draft: false
url: /2019/08/30/convert-selected-or-partial-spreadsheet-rows/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Conversion for .NET', 'GroupDocs.Conversion for Java', 'GroupDocs.Conversion Product Family']
---

You might be looking for a software component or API using that an excel sheet could be converted to PDF/Word or any other [supported format](https://docs.groupdocs.com/display/conversionnet/Supported+Document+Formats) partially.

What is the difference?  
Many of us are just concerned with the output. Process an excel spreadsheet and get the right PDF/output. A simple conversion (Complete spreadsheet to PDF) is ideal _until the source file has limited number of rows_.  

## Partial Conversion - Usability

If you have a spreadsheet with more than 10,000 rows and your data or concerned rows are somewhere between 5,000 to 8,000. Wouldn't you prefer to get PDF of rows 5,000 to 8,000 only?  
This is useful because:

*   Fast and to the point conversion
*   Less resources consumption
*   Easy to define conversion range

Let's have a look at the implementation:  
**C#**  
{{< gist GroupDocsGists 8fcd5ac07b9c59c76ce7f439cd871455 "loadoptions.cs" >}}  
**Java**  
{{< gist GroupDocsGists ba33c892e92dc3332bf77ada945b2cbd "loadoption.java" >}}  
**"G7:I10"** is the cells range (convert from row G7 to I10). Below are the screenshots of source and output files.  
  

*   

{{< figure align=center src="images/excel-2.jpg" alt="">}}

    

*   

{{< figure align=center src="images/output-2.jpg" alt="">}}

    

API allows you to set sheet/page number to convert using **PageNumber** property. For example you have an Excel file with 10 sheets. You can easily convert from G7 to I10 on page 6.

Download GroupDocs.Conversion API and try out this feature. Below are some helpful resources:

*   Download API for [Java](https://downloads.groupdocs.com/conversion/java) or [.NET](https://downloads.groupdocs.com/conversion/net)
*   Documentation ([Java](https://docs.groupdocs.com/conversion/java/), [.NET](https://docs.groupdocs.com/conversion/net))
*   [Sample Code](https://github.com/groupdocs-conversion)




