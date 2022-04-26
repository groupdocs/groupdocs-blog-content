---
title: 'Extract Data Fields from the Documents using GroupDocs.Parser Product Family'
date: Thu, 27 Jun 2019 17:14:08 +0000
draft: false
url: /2019/06/27/extract-data-fields-from-the-documents-using-groupdocs.parser-product-family/
author: 'Usman Aziz'
summary: ''
tags: ['data extraction', 'Document Parser', 'document parsing API', 'extract data fields', 'extract data tables', 'text extraction API', 'Text Extractor']
categories: ['GroupDocs.Parser for .NET Releases', 'GroupDocs.Parser for Java Releases', 'GroupDocs.Parser Product Family']
---



{{< figure align=center src="images/groupdocs-parser.png" alt="">}}


Hello everyone! I am back with something new and exciting for the developers who use to deal with the automated data extraction from the documents. A few years back, we released GroupDocs.Parser API which aimed to extract the text from various document formats. We kept on adding the features to it and today, it has become a giant API that provides a wide range of features including formatted text extraction, highlighted and structured text extraction, metadata extraction, extraction of images and the list goes on.

In v19.5 of .NET and Java API, we have introduced another much-needed feature of extracting data from the documents. So today, I shall give you an overview of this feature and demonstrate its working using the code samples.

Some document formats, such as PDF, also support adding the data fields into the documents. An example of this is the invoice that is used to record a predefined set of information such as invoice numbers, order number, date, price, etc. Such documents have a predefined format and therefore, we also call them template documents. There might be the case when you want to process all or some of the invoices and extract the desired data from them. In that case, an automated system must be required to do the job with a little effort.

If you are dealing with such a case then no need to worry at all because GroupDocs.Parser now provides this feature. So let's check out how you could use this feature for extracting data from the template documents such as invoices. To demonstrate this feature, I shall take the following PDF invoice as the input document.



{{< figure align=center src="images/invoice.jpg" alt="">}}


For data extraction, **TemplateField** and **TemplateFieldPosition** classes are introduced. The **TemplateFieldPosition** class defines the data field's position on the page in the document. At the moment, we have introduced the following position types:

*   Fixed - The position is set by a rectangle.
*   Regex - The position is found by a regular expression.
*   Related - The position is set relative to the related field.

To extract the data fields from the document, we first create a document template which contains the template fields. The template fields are those fields for which you want to extract the values from the document, such as Invoice Number, Order Number, etc. Once the document template is created, it is used to parse the input document using **DocumentParser.Default.ParseByTemplate** method. Have a look at the following code snippet in which we are extracting data from the data field that contains "Address" in its name.

**C#**

{{< gist GroupDocsGists c580d6a015cf388b7762428f01735aa8 "ExtractDataByFieldName.cs" >}}

**Java**

{{< gist GroupDocsGists c580d6a015cf388b7762428f01735aa8 "ExtractDataByFieldName.java" >}}

Apart from extracting by field names, you can also extract the whole data tables. The procedure is the same, except the one thing that is creating **TableAreaDetectorParameters** and the **TemplateTable** objects. The **TemplateTable** object is created using **TableAreaDetectorParameters** objects that are used to detect the tables in the desired rectangular area. In the end, the **TemplateTable** is passed to the **DocumentTemplate** object. Let's check out how this can be achieved using the code.

**C#**

{{< gist GroupDocsGists c580d6a015cf388b7762428f01735aa8 "ExtractingDataTable.cs" >}}

**Java**

{{< gist GroupDocsGists c580d6a015cf388b7762428f01735aa8 "ExtractingDataTable.java" >}}

Now, you have seen how you can extract the desired data from the document templates. If you want to avail this feature, just download the [latest release](https://downloads.groupdocs.com/parser) and for more details, consult the [Developer's Guide](https://docs.groupdocs.com/display/parserjava/Developer+Guide) of the API. In case you would find anything confusing, just feel free to post it on our [forum](https://forum.groupdocs.com/) and we would love to assist you.




