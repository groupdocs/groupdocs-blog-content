---
title: 'Count Words and Occurrences of Each Word in a Document using C#'
date: Wed, 16 Oct 2019 16:33:57 +0000
draft: false
url: /2019/10/16/count-words-and-occurrences-of-each-word-in-documents-using-csharp/
aliases:
    - /2019/10/16/count-words-and-occurrences-of-each-word-in-a-document-using-c/
author: 'Usman Aziz'
summary: ''
tags: []
categories: ['GroupDocs.Parser for .NET', 'GroupDocs.Parser Product Family']
---

Repetition of data can diminish the worth of the content. Working as a writer, you must follow [DRY](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) (don't repeat yourself) principle. The statistics such as **word count** or the number of occurrences of each word can let you analyze the content but it's hard to do it manually for multiple documents. So in this article, I'll demonstrate how to **programmatically count words** and the **number of** **occurrences** of  each word in **PDF**, **Word**, **Excel**, **PowerPoint**, **Ebook**, **Markup**, and **Email document** formats using **C#**. For extracting text from documents, I'll be using [**GroupDocs.Parser for .NET**](https://products.groupdocs.com/parser/net) which is a powerful **document parsing API**.

## Steps to count words and their occurrences in C#

**1.** Create a new project.

**2.** Install _GroupDocs.Parser for .NET_ using NuGet Package Manager.

**3.** Add the following namespaces.

{{< gist GroupDocsGists 694d31da56994b95bad031c2e737868d "GroupDocsParserNamespaces.cs" >}}

**4.** Create an instance of the _[Parser](https://apireference.groupdocs.com/net/parser/groupdocs.parser/parser)_ class and load the document.

{{< gist GroupDocsGists 694d31da56994b95bad031c2e737868d "LoadDocumentForParsing.cs" >}}

**5.** Extract the text from the document into a _[TextReader](https://docs.microsoft.com/en-us/dotnet/api/system.io.textreader?view=netframework-4.8)_ object using _[Parser.GetText()](https://apireference.groupdocs.com/net/parser/groupdocs.parser/parser/methods/gettext)_ method.

{{< gist GroupDocsGists 694d31da56994b95bad031c2e737868d "GetText.cs" >}}

**6.** Split up the text into words, save them into a string array and perform word count.

{{< gist GroupDocsGists 694d31da56994b95bad031c2e737868d "SplitTextAndCountWords.cs" >}}

**7\.** Order the words by their occurrence count and display the results.

{{< gist GroupDocsGists 694d31da56994b95bad031c2e737868d "PrintWordCount.cs" >}}

## Complete Code

{{< gist GroupDocsGists 694d31da56994b95bad031c2e737868d "CountWordInDocuments.cs" >}}

## Results



{{< figure align=center src="images/Word-Count.png" alt="">}}


Read more about _GroupDocs.Parser for .NET_ API [here](https://docs.groupdocs.com/display/parsernet/Home). Leave your questions or queries on our [forum](https://forum.groupdocs.com/c/parser).




