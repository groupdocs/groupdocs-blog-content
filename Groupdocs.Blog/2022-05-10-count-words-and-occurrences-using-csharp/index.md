---
title: "Count Words and Occurrences of Each Word in a Document using C#"
seoTitle: "Count Words and Occurrences of Each Word in a Document using C# .NET"
description: "Count number of words and their occurrences in PDF, Word, Excel, PowerPoint, and Email documents in C# using .NET document parsing API."
date: Tue, 10 May 2022 16:33:57 +0000
draft: false
url: /2022/05/10/count-words-and-occurrences-using-csharp
aliases:
    - /2019/10/16/count-words-and-occurrences-of-each-word-in-a-document-using-c/
    - /2019/10/16/count-words-and-occurrences-of-each-word-in-documents-using-csharp/
author: "Shoaib Khan"
summary: "This article demonstrates how to programmatically count words and the word occurrence count of each word in PDF, Word, Excel, PowerPoint, Ebook, Markup, and Email document formats using C#."
tags: ['GroupDocs.Parser for .NET']
categories: ['GroupDocs.Parser Product Family']
---

Repetition of data can diminish the worth of the content. Working as a writer, you must follow [DRY][1] (don't repeat yourself) principle. The statistics such as word count or the number of occurrences of each word can let you analyze the content but it's hard to do it manually for multiple documents. So this article demonstrates how to **programmatically count words** and the word occurrence count of each word in PDF, Word, Excel, PowerPoint, eBook, Markup, and Email document formats using C#.

## .NET API to Count Words & Occurrences

[GroupDocs.Parser][2] provides the document parsing solution for developers. For the extraction of text from documents, and counting occurrences, we will use its [GroupDocs.Parser for .NET][3]. The API further allows the extraction of images, and metadata from a long list of [supported document][4] formats like word-processing documents, presentations, spreadsheets, emails, databases, eBooks, and many others.

You can download the DLLs or MSI installer from the [downloads section][5] or install the API by adding its package to your .NET application via [NuGet][6].

```
PM> Install-Package GroupDocs.Parser
```

## Count Words using C# {#count-words}

For the counting of words, the main thing is to parse and extract the whole content of the document. After the extraction of the text, we can split its content into a collection of sentences and words. The following step allows counting the words within the document using C#.

- Load the document using the [Parser][7] class.
- Fetch the text of the loaded document into [TextReader][8].
- [Get][9] the text of the document from the TextReader as a string.
- Split the text into words and save them into a string array.
- Perform word count.

The following C# source code counts the number of words in a document.

{{< gist GroupDocsGists 694d31da56994b95bad031c2e737868d "CountWordInDocuments.cs" >}}

## Count Words Occurrence in C# {#count-words-occurrences}

Similarly, we can count how many times a particular word or a phrase has been used in the document. By using this feature, you can avoid the excessive repetition of any word within an article. The following steps count the occurrence of each word used in a document.

- Load the document using the [Parser][7] class.
- Retrieve the text of the loaded document into [TextReader][8].
- Read and split the whole text into the word collection.
- Traverse the word collection to count words.

The following C# code snippet counts the occurrence of each unique word within the document.

{{< gist GroupDocsGists 694d31da56994b95bad031c2e737868d "CountWordOccurrences.cs" >}}

The following is the output of the above code:

{{< figure align=center src="images/Word-Count.png" alt="Word Occurrence Count">}}

## Get a Free API License

You can [get a free temporary license][10] in order to use the API without the evaluation limitations.

## Conclusion

To sum up, you learned how to count words in a document using C#. Additionally, we discussed how we can get the word occurrence count for each word in the document. Try developing your online word counter .NET application. For more details and learning about the API, visit the [documentation][11]. For queries, contact us via the [forum][12].

## See Also

- [Extract ZIP Files Data in C#][13]
- [Parse Documents to Extract Images using C#][14]
- [Extract Images from EPUB, FB2, CHM eBooks in C#][15]
- [Read PDF Form Fields using C#][16]

[1]: [https://en.wikipedia.org/wiki/Don%27t_repeat_yourself]
[2]: https://products.groupdocs.com/parser/
[3]: https://products.groupdocs.com/parser/net/
[4]: https://docs.groupdocs.com/parser/net/supported-document-formats/
[5]: https://downloads.groupdocs.com/parser
[6]: https://www.nuget.org/packages/groupdocs.parser
[7]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser
[8]: https://docs.microsoft.com/en-us/dotnet/api/system.io.textreader
[9]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/gettext
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://docs.groupdocs.com/parser/
[12]: https://forum.groupdocs.com/
[13]: https://blog.groupdocs.com/2021/08/25/extract-zip-files-data-in-csharp/
[14]: https://blog.groupdocs.com/2020/10/28/extract-images-from-pdf-word-excel-ppt-using-csharp/
[15]: https://blog.groupdocs.com/2021/02/26/extract-images-from-ebooks-in-csharp/
[16]: https://blog.groupdocs.com/2020/12/23/parse-and-extract-data-from-pdf-forms-in-csharp/