---
title: 'Find and Replace Text in PDF using C#'
date: Sat, 19 Feb 2022 04:42:16 +0000
draft: false
url: /2022/02/19/find-and-replace-text-in-pdf-using-csharp/
author: 'Shoaib Khan'
summary: 'Templates are widely used to generate customized documents. This article guides about **how to find and replace text and words in PDF documents using C#**. We will separately discuss how to programmatically replace words and phrases, replacement of words with case-sensitive search, replacing using regular expressions. Finally, we will also learn how to hide the searched string using C#.'
tags: ['Blackout Text in PDF', 'Find &amp; Replace Text in PDF', 'Find Text in PDF', 'Hide Text in PDF', 'Redact PDF files']
categories: ['GroupDocs.Redaction Product Family']
---

Templates are widely used to generate customized documents. This article guides about **how to find and replace text and words in PDF documents using C#**. We will separately discuss how to programmatically replace words and phrases, replacement of words with case-sensitive search, replacing using regular expressions. Finally, we will also learn how to hide the searched string using C#.

The following topics are going to be covered below:

*   [.NET API for Replacing Text](#dotnet-redaction-api)
*   [Find & Replace Words or Phrase](#replace-word-or-phrase)
*   [Case-Sensitive Word Search & Replacement](#case-sensitive-text-redaction)
*   [Replacing with Regular Expressions (RegEx)](#replace-text-using-regex)
*   [Hide Text with Colored Box](#hide-text-with-colored-box)

## .NET Redaction API for Replacing Text {#dotnet-redaction-api}

GroupDocs showcases GroupDocs.Redaction for .NET, the API to redact, hide, or remove content & even metadata of documents, presentations, spreadsheets, PDF files, and images within .NET application. For further details about the API, visit its documentation.

You can download the **DLLs** or **MSI** installer from the [downloads section](https://downloads.groupdocs.com/redaction) or install the API in your .NET application via [NuGet](https://www.nuget.org/packages/groupdocs.redaction).

```
PM> Install-Package GroupDocs.Redaction
```

No need to install any PDF editor, or any other third-party software for redaction. The following is the screenshot of a PDF document that is used in the below examples. The same approach will work for other document formats with hardly very little or no change in the code.



{{< figure align=center src="images/original-doc.png" alt="">}}


## Find and Replace Word or Phrase in PDF using C# {#replace-word-or-phrase}

You can use this feature to hide any confidential data, and also to create a new customized document from the template. The following step explains how to find any word/phrase in a PDF document with some other text within the C# application.

*   **Load** the PDF file using [Redactor](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor) class.
*   **Find the exact phrase or word**, using the [ExactPhraseRedaction](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/exactphraseredaction) and [ReplacementOptions](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/replacementoptions).
*   **Apply the redaction** using [Apply()](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/apply/index) method.
*   **Save** the new document with changes using the [Save()](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/save/index) method.

The following code finds and replaces the word in C#. More precisely, it hides all the occurrences of "John Doe" by replacing it with the word "\[censored\]".

{{< gist GroupDocsGists 350afb0feb5749b5381d4c8806792b43 "ReplaceExactPhraseInPdf.cs" >}}

The output of the code is as follows.



{{< figure align=center src="images/Exact-Phrase-Replacement.png" alt="">}}


## Find and Replace Case-Sensitive Text or Phrase in PDF using C# {#case-sensitive-text-redaction}

You can perform the case-sensitive search & redaction. The following code replaces the case-sensitive existence of the word "John Doe" but not "john doe" in C#.

{{< gist GroupDocsGists 350afb0feb5749b5381d4c8806792b43 "ReplacePdfExactPhraseCaseSensitive.cs" >}}

The output of the code is as follows.



{{< figure align=center src="images/Case-Sensitive-Exact-Phrase-Redaction.png" alt="">}}


## Replace Text in PDF with Regular Expressions (RegEx) using C# {#replace-text-using-regex}

You can also replace any specific text pattern using regular expressions. The following steps allow you to redact PDF after the search using regular expression (RegEx) within your .NET application.

*   **Load** the PDF document using [Redactor](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor) class.
*   **Find the regex match** using the [RegexRedaction](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/regexredaction) class with [ReplacementOptions](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/replacementoptions).
*   Put in the changes to document using [Apply()](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/apply/index) method.
*   **Save** the redacted document using appropriate [Save()](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/save/index) method.

The following code shows how to find a certain text pattern in a PDF document using RegEx and later replace/hide it with some other text using C#.

{{< gist GroupDocsGists 350afb0feb5749b5381d4c8806792b43 "ReplaceTextInPdfWithRegEx.cs" >}}

The output of the above code is as follows.



{{< figure align=center src="images/Regex-Redaction.png" alt="">}}


## Replace the Text with Colored Box in C# {#hide-text-with-colored-box}

If you just want to hide the searched content (private information) of your PDF file, you can simply put a cover on it. The API allows you to hide the searched text. The following C# code places the black rectangle over the mentioned private text.

{{< gist GroupDocsGists 350afb0feb5749b5381d4c8806792b43 "FindTextAndHideInPdf.cs" >}}

The output of the above code is as follows.



{{< figure align=center src="images/Colored-Box-Redaction.png" alt="">}}


## Get a Free API License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) in order to use the API without the evaluation limitations.

## Conclusion

To conclude, we learned how to find certain text in PDF files using different search techniques. Later we discussed how to redact PDF files either by replacing or hiding the text within the .NET application using C#. More precisely, we simply searched for the words, phrases, search with case sensitivity, and by using regular expressions in C#. Lastly, we replaced the search results with either some other text or by hiding it with a rectangle box over it.

For more details about the API, visit the [documentation](https://docs.groupdocs.com/redaction). For queries, contact us via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Redact Scanned PDF Documents in C#](https://blog.groupdocs.com/2021/09/25/redact-text-and-scanned-images-using-csharp/)
*   [Search Synonyms in Multiple Files using C#](https://blog.groupdocs.com/2021/09/17/find-synonyms-in-multiple-files-using-csharp/)
*   [Build your Full Text Search Solution in C#](https://blog.groupdocs.com/2021/06/03/build-your-full-text-search-solution-in-csharp/)




