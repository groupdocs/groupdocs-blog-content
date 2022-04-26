---
title: 'Extract Data from Invoices or Receipts in C#'
date: Thu, 24 Oct 2019 16:17:53 +0000
draft: false
url: /2019/10/24/extract-data-from-invoices-or-receipts-in-csharp/
author: 'Usman Aziz'
summary: ''
tags: []
categories: ['GroupDocs.Parser Product Family']
---

**Invoices** and **receipts** are the documents that are used to record the transactions in a particular format when buying or selling of the services or goods is involved. Things have gone digital and with the popularity of online shopping, digital invoices are widely used. Processing a number of digital invoices and extracting the information manually is a complex as well as time taking process. Thus, you need a faster yet efficient way for such a case. So in this article, I am going to show you how to **extract data** from a **PDF invoice** or **receipt** **programmatically** in **C#** using [**GroupDocs.Parser for .NET**](https://products.groupdocs.com/parser/net) **API**.

## Workflow for Extracting Data from a PDF Invoice

The following is the workflow of how to extract the data from a PDF invoice using GroupDocs.Parser for .NET.

*   Create table parameters for extracting data from the tables.
*   Create template items for extracting data from fields.
*   Parse the invoice according to the given template.
*   Extract the data.

## The Invoice

The following is the screenshot of a sample PDF invoice that I'll use for extracting the data. You can download this invoice from our [GitHub repository](https://github.com/groupdocs-parser).



{{< figure align=center src="images/invoice.jpg" alt="">}}


## The Code

*   Create the template for the given invoice ([read more](https://docs.groupdocs.com/display/parsernet/Working+With+Templates) about templates).

{{< gist GroupDocsGists c9cde916cd2a125b834c8f2c13dacc82 "CreateTemplateForInvoice.cs" >}}

*   Parse the invoice and extract data.

{{< gist GroupDocsGists c9cde916cd2a125b834c8f2c13dacc82 "ExtractDataFromInvoice.cs" >}}

## The Output



{{< figure align=center src="images/Output-1.png" alt="">}}


To explore more about _GroupDocs.Parser for .NET_ API, visit the [documentation](https://docs.groupdocs.com/display/parsernet/Introducing+GroupDocs.Parser+for+.NET). Reach us at our [forum](https://forum.groupdocs.com/c/parser) in case of any questions or queries.

## See Also

*   [Extract invoice data from PDF using templates in Java](https://blog.groupdocs.com/2021/01/22/extract-data-from-invoices-or-receipts-in-java/)




