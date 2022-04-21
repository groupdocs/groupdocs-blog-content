---
title: 'Word Search and Replace Text in PDF in Java'
date: Tue, 08 Mar 2022 10:10:00 +0000
draft: false
url: /2022/03/08/find-and-replace-text-in-pdf-in-java/
author: 'Shoaib Khan'
summary: 'Templates are widely used to generate personalized documents by replacing the template keys with respective values. This article guides about **how to find and replace text and words in PDF documents in Java**. We will separately discuss how to perform words and phrases search, case-sensitive word search, replacing the found text using regular expressions. Finally, we will learn how to hide the searched part of text using Java.'
tags: ['Blackout Text', 'Blackout Text in PDF', 'Find &amp; Replace Text in PDF', 'Find Text in PDF', 'Hide Text in PDF', 'Redact PDF files', 'Word Search in Java']
categories: ['GroupDocs.Redaction Product Family']
---

Templates are widely used to generate personalized documents by replacing the template keys with respective values. This article guides about **how to find and replace text and words in PDF documents in Java**. We will separately discuss how to perform words and phrases search, case-sensitive word search, replacing the found text using regular expressions. Finally, we will learn how to hide the searched part of text using Java.

The following topics are going to be covered below:

*   [Java API for Replacing Text](#java-redaction-api)
*   [Find & Replace Words or Phrase](#replace-word-or-phrase)
*   [Case-Sensitive Word Search & Replacement](#case-sensitive-text-redaction)
*   [Replace using Regular Expressions (RegEx)](#replace-text-using-regex)
*   [Hide Text with Colored Box](#hide-text-with-colored-box)

## Java Redaction API for Replacing Text {#java-redaction-api}

GroupDocs provides Java API for applying various types of redactions. It allows to redact, hide, or remove the content & even metadata of documents, presentations, spreadsheets, PDF files, and images within the application. For further details about the API, visit its [documentation](https://docs.groupdocs.com/redaction/java/).

### Download or Configure

You may download the **JAR** file from the [downloads section](https://downloads.groupdocs.com/redaction), or just get the latest repository and dependency configurations for the pox.xml of your **maven-based** Java applications.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-redaction</artifactId>
        <version>21.12</version> 
</dependency>
```

One of the good things is that there is no need to install any PDF editor, or any other third-party software for PDF redaction. The following is the content of the PDF document that is used in the below examples for redaction. The same approach will work for other document formats with hardly any difference in the source code.



{{< figure align=center src="images/original-doc.png" alt="">}}


## Find and Replace Word or Phrase in PDF in Java {#replace-word-or-phrase}

You can use this feature to hide any private data, and also to create a new customized document from any template. The following step explains how to find any word/phrase in a PDF document and replace it with some other text within the Java application.

*   **Load** the PDF file using [Redactor](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor) class.
*   **Find the exact phrase or word**, using the [ExactPhraseRedaction](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ExactPhraseRedaction) and [ReplacementOptions](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ReplacementOptions).
*   **Apply the redaction** using apply() method.
*   **Save** the new document with changes using the save() method.

The following code finds and replaces the words in a PDF file using Java. More precisely, it hides all the occurrences of "John Doe" by replacing it with the word "\[censored\]".

{{< gist GroupDocsGists 1098cf3a7914313b466c3e01dc77704a "ReplaceExactPhraseInPdf.java" >}}

The output of the above code is as follows.



{{< figure align=center src="images/Exact-Phrase-Replacement.png" alt="">}}


## Find and Replace Case-Sensitive Text or Phrase in PDF using Java {#case-sensitive-text-redaction}

You can perform the case-sensitive search & redaction. The following code replaces the case-sensitive occurrence of the word "John Doe" but not "john doe" within a PDF document using Java.

{{< gist GroupDocsGists 1098cf3a7914313b466c3e01dc77704a "ReplaceExactPhraseInPdfCaseSensitive.java" >}}

The output of the code is as follows.



{{< figure align=center src="images/Case-Sensitive-Exact-Phrase-Redaction.png" alt="">}}


## Replace Text in PDF with Regular Expressions (RegEx) in Java {#replace-text-using-regex}

Similarly, you can replace any specific text pattern using regular expressions. The following steps allow you to redact PDF after searching using regular expression (RegEx) within your Java applications.

*   **Load** the PDF document using [Redactor](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor) class.
*   **Find the regex match** using the [RegexRedaction](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/RegexRedaction) class with [ReplacementOptions](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ReplacementOptions).
*   Apply in the changes to document using apply() method.
*   **Save** the redacted document using appropriate save() method.

The following Java code shows how to find a certain text pattern in a PDF document using RegEx and later replace/hide it with some other text.

{{< gist GroupDocsGists 1098cf3a7914313b466c3e01dc77704a "ReplaceTextInPdfWithRegEx.java" >}}

The output of the above code is as follows.



{{< figure align=center src="images/Regex-Redaction.png" alt="">}}


## Replace the Text with Colored Box in Java {#hide-text-with-colored-box}

If you just want to hide the searched confidential information within your PDF file, you can simply put a cover on it. The API allows you to hide the searched text. The following code places the black rectangle over the mentioned private text in Java.

{{< gist GroupDocsGists 1098cf3a7914313b466c3e01dc77704a "FindTextAndHideInPdf.java" >}}

The output of the above code is as follows.



{{< figure align=center src="images/Colored-Box-Redaction.png" alt="">}}


## Get a Free API License

You can [get a free temporary license](https://purchase.groupdocs.com/temporary-license) in order to use the API without the evaluation limitations.

## Conclusion

To sum up, we learned how to find certain text in PDF files using different search techniques. Later we redacted the PDF files by replacing or hiding the text within the applications in Java. More precisely, we performed a simple search for the words, phrases, searched with case sensitivity, and by using RegEx in Java. Lastly, we changed the search results with either some other text or by simply hiding it with color over it.

For more details about the API, visit the [documentation](https://docs.groupdocs.com/redaction). For queries, contact us via the [forum](https://forum.groupdocs.com/).

## See Also

*   [Redact PDF Scanned Documents in Java](https://blog.groupdocs.com/2021/10/05/redact-text-and-scanned-images-using-java/)
*   [Search Synonyms in Multiple Files using Java](https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/)
*   [Build Full-Text Search Solution in Java](https://blog.groupdocs.com/2021/08/07/build-full-text-search-solution-in-java/)




