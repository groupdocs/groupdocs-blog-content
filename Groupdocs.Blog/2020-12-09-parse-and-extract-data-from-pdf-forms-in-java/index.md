---
title: 'Read PDF Form Fields in Java'
date: Wed, 09 Dec 2020 15:43:10 +0000
draft: false
url: /2020/12/09/parse-and-extract-data-from-pdf-forms-in-java/
aliases:
    - /2018/09/13/extract-data-from-pdf-forms-using-groupdocs.parser-for-java-18.9/
author: 'Shoaib Khan'
summary: 'In this article, we will discuss **how to parse PDF document and extract values from PDF forms programmatically in Java**. There are many situations, where we have several filled survey forms or feedbacks in PDF format from a large audience. We can easily extract the filled data values and use them for analysis. Let us now move straight towards reading these PDF forms and extract filled data field values within Java applications.'
tags: ['Extract Text from PDF Forms', 'Extract Text from PDF Forms in Java', 'Parse PDF Forms in Java']
categories: ['GroupDocs.Parser Product Family']
---

In this article, we will discuss **how to parse PDF document and extract values from PDF forms programmatically in Java**. There are many situations, where we have several filled survey forms or feedbacks in PDF format from a large audience. We can easily extract the filled data values and use them for analysis. Let us now move straight towards reading these PDF forms and extract filled data field values within Java applications.



{{< figure align=center src="images/Extract-from-PDF-Form-in-java.jpeg" alt="Parse PDF Form to Extract values in Java">}}


## Java API to Parse and Extract Values from PDF Forms

**GroupDocs** offers a [document parsing and data extraction Java API][1] that supports a lot more than word-processing, presentations, spreadsheets, emails, PDF, markup, ebooks, and archive formats. Along with the extraction of text and images, the API also supports the extraction of metadata from the [supported document formats][2]. One of the salient features of the API is to **parse the fillable PDF documents and extract values from the form fields** with easy Java code.

In the coming examples, I will be using the mentioned API i.e. **[GroupDocs.Parser for Java][3]**, so I would recommend you to prepare your environment to implement the feature. You may download the latest JAR file from the [downloads][4] section or just add the following configurations in your Maven-based Java applications. For details about API, visit [API Reference][5].

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
	<groupId>com.groupdocs</groupId>
	<artifactId>groupdocs-parser</artifactId>
	<version>20.8</version> 
</dependency>
```

## Extract Data from PDF Form Field in Java

The following simple steps for how to extract field values from PDF form.

*   Initialize the **[Parser][6]** object with the target PDF form.
*   Call the **[parseForm][7]** method to get all the data from the PDF form.
*   Traverse the collected data to get the desired field values.

The following code shows how to parse PDF document and get values from the filled PDF form fields in Java.

{{< gist GroupDocsGists b64b2266ab7018b43e07dfa41aaa7cad "ParsePdfForms.java" >}}

```
COMPANY: GroupDocs
EMAIL: everything@groupdocs.com
COUNTRY: Australia
```

## Conclusion

I hope, Java developers are now familiar with the easy, precise, and efficient way to parse the PDF documents to extract text values from the PDF form fields. If you are interested to learn more about the basic and advanced features of the API, you can explore the [documentation][8].

In case of any queries, reach support @ [forum][9].

## See Also

*   [Read PDF Form Fields using C#][10]
*   [Extract Images from Documents using Java][11]







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

