---
title: 'Find and Replace Words in Word Documents using C#'
seoTitle: "Find and Replace Words in Word Documents using C# | Text Redaction"
description: "Find, replace, or hide text, words, phrases in Word DOC/DOCX files using C#. Redact and perform text, case-sensitive & RegEx search with .NET Redaction API."
date: Tue, 15 Feb 2022 10:41:00 +0000
draft: false
url: /2022/02/15/find-and-replace-text-in-word-using-csharp/
aliases:
    - /2021/08/04/find-and-replace-text-in-documents-using-csharp/
    - /2021/08/04/find-and-replace-text-in-documents-using-csharp-2/
    - /2019/09/20/find-and-replace-text-in-word-documents-using-net-api/
    - /2019/09/20/find-and-replace-text-in-word-excel-powerpoint-pdf-documents-net-api/
author: 'Shoaib Khan'
summary: "There could be many reasons to replace a word or phrase in the document. Whether you want to erase the sensitive content before publically sharing the document or you want to hide/remove all the private information like email IDs or Social Security Numbers, you need to redact the document content. This article guides you on **how to redact Word documents programmatically** in your .NET applications using C#. We will separately discuss how to redact by hiding the text and how to **find and replace the text, words, or phrases** using different techniques."
tags: ['case sensitive find and replace', 'Find &amp; Replace in Word', 'Find and replace text', 'Redact in CSharp', 'Redact Word in CSharp', 'Replace words in CSharp', 'text redaction']
categories: ['GroupDocs.Redaction Product Family']
---

There could be many reasons to replace a word or phrase in the document. Whether you want to erase the sensitive content before publically sharing the document or you want to hide/remove all the private information like email IDs or Social Security Numbers, you need to redact the document content. This article guides you on **how to redact Word documents programmatically** in your .NET applications using C#. We will separately discuss how to redact by hiding the text and how to **find and replace the text, words, or phrases** using different techniques.

The following topics are going to be covered below:

*   [.NET API for Replacing Text](#dotnet-redaction-api)
*   [Find & Replace Words or Phrases](#replace-word-or-phrase)
*   [Case-Sensitive Search and Replace Words or Phrases](#case-sensitive-text-redaction)
*   [Replace Text using Regular Expressions (RegEx)](#replace-text-using-regex)
*   [Hide the Text with Colored Box](#hide-text-with-colored-box)

## .NET Redaction API for Replacing Text {#dotnet-redaction-api}

GroupDocs.Redaction for .NET is the document redaction API that allows finding and then replacing the intended data from documents of various file formats. Along with the text redaction and rasterization, the API provides metadata, annotation, spreadsheet, and images redaction features. The [supported file formats](https://docs.groupdocs.com/redaction/net/supported-document-formats/) of the Word documents, spreadsheets, presentations, images, and PDF documents are available at the documentation.

You can download the **DLLs** or **MSI** installer from the [downloads section](https://downloads.groupdocs.com/redaction) or install the API in your .NET application via [NuGet](https://www.nuget.org/packages/groupdocs.redaction).

```
PM> Install-Package GroupDocs.Redaction
```

There is no need to install MS Office or any other third-party software in this process. Let’s now begin and have a look at different approaches to deal with finding and replacing text in the documents. The following is the screenshot of a Word document that is used in the examples for demonstration. The same methods will work for other document formats without any change in the code.



{{< figure align=center src="images/original-doc.png" alt="">}}


## Find and Replace Words or Phrases in Word document using C# {#replace-word-or-phrase}

The following step explains how to find any word/phrase in a Word document and then replaces all the occurrences with some other text within the C# application.

*   Load the Word document (DOC/DOCX) using [Redactor](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor) class.
*   Find the exact phrase or word, using the [ExactPhraseRedaction](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/exactphraseredaction) class with [ReplacementOptions](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/replacementoptions).
*   Use [Apply](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/apply/index) method of Redactor to apply redaction.
*   Save the changes using the [Save](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/save/index) method.

The following code finds and replaces the word in C#. More precisely, it replaces all the occurrences of "John Doe" with "\[censored\]".

{{< gist GroupDocsGists 21c0de0a57527723026b9e85128b8e17 "ReplaceExactPhrase.cs" >}}

The output of the code is as follows.



{{< figure align=center src="images/Exact-Phrase-Replacement.png" alt="">}}


## Case-Sensitive Search and Replace in Word files using C# {#case-sensitive-text-redaction}

Similarly, you can perform the case-sensitive redaction of a Word document by finding the exact word and replacing it with any other. The following code replaces the existence of the word "John Doe" in a DOCX file using C#, but this time, the search will be case-sensitive.

{{< gist GroupDocsGists 21c0de0a57527723026b9e85128b8e17 "ReplaceExactPhraseCaseSensitive.cs" >}}

The output of the code is as follows.



{{< figure align=center src="images/Case-Sensitive-Exact-Phrase-Redaction.png" alt="">}}


## Replace Text in Word Files using Regular Expressions (RegEx) using C# {#replace-text-using-regex}

To find and replace any pattern of text in Word (DOC, DOCX) files you can use regular expressions. The following steps allow you to redact a Word document with RegEx using C#.

*   Load the Word document using [Redactor](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor) class.
*   Find the regex match using the [RegexRedaction](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/regexredaction) class with [ReplacementOptions](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/replacementoptions).
*   Use [Apply](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/apply/index) method to replace all the regex match texts.
*   Use the [Save](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/save/index) method to get the redacted Word file.

The following code shows how to find a text pattern in a Word file using RegEx and then replace/hide it with some other text using C#.

{{< gist GroupDocsGists 21c0de0a57527723026b9e85128b8e17 "ReplaceTextWithRegEx.cs" >}}

The output of the above code is as follows.



{{< figure align=center src="images/Regex-Redaction.png" alt="">}}


## Hide Confidential Text in Word Documents with Colored Box using C# {#hide-text-with-colored-box}

If you do not want to replace your private content but just want to cover it, the API allows you to hide that content by drawing a box over it. The following code places the black rectangle over the intended text to blackout text using C#.

{{< gist GroupDocsGists 21c0de0a57527723026b9e85128b8e17 "FindTextAndHide.cs" >}}

The output of the above code is as follows.



{{< figure align=center src="images/Colored-Box-Redaction.png" alt="">}}


## Get a Free API License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) in order to use the API without the evaluation limitations.

## Conclusion

To conclude, you learned how to find text in Word (DOC, DOCX) files using different techniques and replace the findings in different ways. More precisely, we discussed how to find text, word, or phrase even if it is a case-sensitive search or using a regular expression in C#. Later we replaced the search results with either some other text or by placing the colored rectangle box over the searched text.

For more about the API, visit [documentation](https://docs.groupdocs.com/redaction). For queries, contact us via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Build your Full-Text Search Solution in C#](https://blog.groupdocs.com/2021/06/03/build-your-full-text-search-solution-in-csharp/)
*   [Find Differences by Comparing two Images in C#](https://blog.groupdocs.com/2021/01/06/compare-images-in-csharp-dotnet/)




