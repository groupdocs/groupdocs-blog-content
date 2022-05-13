---
title: "Count Words and Occurrences of Each Word in a Document using Java"
seoTitle: "Count Words and Occurrences of ach Word in a Document using Java"
description: "Count number of words and their occurrences in PDF, Word, Excel, PowerPoint, and Email documents in Java using document parsing API."
date: Fri, 13 May 2022 16:33:57 +0000
draft: false
url: /2022/05/13/count-words-and-occurrences-in-java
author: "Shoaib Khan"
summary: "Writing is not just a simple task for everyone. It is recommended not to repeat the same words and phrases again and again. In today's world of optimization, you often need to count and then limit the repetition of words and phrases. This article discusses, how to programmatically count words in documents and the occurrences of each word in Java."
tags: ['GroupDocs.Parser for .NET', "count words", "count words in documents", "count words in java"]
categories: ['GroupDocs.Parser Product Family']
---

Writing is not just a simple task for everyone. It is recommended not to repeat the same words and phrases again and again. In today's world of optimization, you often need to count and then limit the repetition of words and phrases. This article discusses, how to programmatically count words in documents and the occurrences of each word in Java.

## Java API to Count Words & Occurrences

[GroupDocs.Parser][1] showcases the document parsing solution for developers. I will use its Java API i.e. [GroupDocs.Parser for Java][2] for the extraction of text from documents, and counting occurrences. The API also allows the images, and metadata extraction for a large list of [supported document formats][3] like word-processing documents, presentations, spreadsheets, emails, databases, eBooks, and many others.

## Download and Configure

Get the library from the [downloads section][4]. For your Maven-based Java application, just add the following pom.xml configuration. After this, you can run the examples of this article, and many more examples available on [GitHub][5]. For the details, you may visit the [API Reference][6].

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
	<groupId>com.groupdocs</groupId>
	<artifactId>groupdocs-parser</artifactId>
	<version>22.3</version> 
</dependency>
```

## Count Words in Document using Java {#count-words}

Firstly, it is important to accurately parse and extract the whole content of the document before counting the words. After the extraction of the text, we can easily split its content into a collection of words and phrases. The following steps show how to count the words within the document using Java.

- Load the document using the [Parser][7] class.
- Fetch the text of the loaded document using [TextReader][8].
- Split the text into words using delimiters.
- Perform word count.

The following Java source code counts the number of words in a document.

{{< gist GroupDocsGists e7bc4dd7923f1b0586b4343d07ddf89f "CountWordInDocuments.java" >}}

## Count Words Occurrences in Java {#count-words-occurrences}

Likewise, we can count how many times a particular or any unique word or a phrase appeared in the document. By using this feature, you can avoid the repetition of any word within the article. The following steps count the occurrence of each word within the document using Java.

- Load the document using the [Parser][7] class.
- Retrieve the text of the loaded document using [TextReader][8].
- Read and split the whole text into words collection.
- Traverse the words collection to count the appearance of each words.

The following Java code snippet counts the occurrence of each unique word within the document.

{{< gist GroupDocsGists e7bc4dd7923f1b0586b4343d07ddf89f "CountWordOccurrences.java" >}}

The following is the output of the above code:

```
lorem: 6
ipsum: 2
eleifend: 2
integer: 1
augue: 3
aliquet: 1
ligula: 1
dolor: 1
venenatis: 2
viverra: 1
amet: 2
urna: 1
senectus: 2
lectus: 2
volutpat: 1
massa: 1
blandit: 1
dapibus: 1
habitant: 2
pharetra: 2
...
```

## Get a Free API License

You can [get a free temporary license][10] in order to use the API without the evaluation limitations.

## Conclusion

To conclude, you learned how to count words in a document using Java. Additionally, we discussed how we can get the word occurrence count for each word used in the document. Try developing your online word counter Java application. For more details and learning about the API, visit the [documentation][11]. For queries, contact us via the [forum][12].

## See Also

- [Extract ZIP Files Data in Java][13]
- [Extract Images from EPUB, FB2, CHM eBooks in Java][14]
- [Read PDF Form Fields in Java][15]

[1]: https://products.groupdocs.com/parser/
[2]: https://products.groupdocs.com/parser/java/
[3]: https://docs.groupdocs.com/parser/java/supported-document-formats/
[4]: https://downloads.groupdocs.com/parser
[5]: https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java
[6]: https://apireference.groupdocs.com/parser/java
[7]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser
[8]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser.data/TextReader
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://docs.groupdocs.com/parser/
[12]: https://forum.groupdocs.com/
[13]: https://blog.groupdocs.com/2021/09/08/extract-zip-files-data-in-java/
[14]: https://blog.groupdocs.com/2021/03/15/extract-images-from-ebooks-in-java/
[15]: https://blog.groupdocs.com/2020/12/09/parse-and-extract-data-from-pdf-forms-in-java/