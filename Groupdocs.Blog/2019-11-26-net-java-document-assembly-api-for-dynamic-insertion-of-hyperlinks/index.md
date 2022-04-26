---
title: 'Dynamic Insertion of Links to Bookmarks, Cells and Slides using GroupDocs.Assembly 19.11'
date: Tue, 26 Nov 2019 07:18:07 +0000
draft: false
url: /2019/11/26/net-java-document-assembly-api-for-dynamic-insertion-of-hyperlinks/
author: 'Usman Aziz'
summary: ''
tags: ['Document Automation API', 'dotnet', 'java', 'report generation']
categories: ['GroupDocs.Assembly for .NET', 'GroupDocs.Assembly for Java', 'GroupDocs.Assembly Product Family']
---

[**Document Automation**](https://en.wikipedia.org/wiki/Document_automation) (or **document assembly**) is widely used by organizations for their reporting services and [**GroupDocs.Assembly**](https://products.groupdocs.com/assembly) for .NET and Java APIs provide a complete package of features required to build reports dynamically. Keeping the modern trends in mind and to meet the emerging requirements of our customers, we keep introducing the new features. Recently, we have released the v19.11 of our **document automation API** with quite a useful set of features. So in this article, I'll give you an overview of what is new in the latest release.

## Dynamic Insertion of Links to Bookmarks, Cells and Slides

[Hyperlinks](https://en.wikipedia.org/wiki/Hyperlink) in the documents prove to be useful in many cases, for example, adding links to bookmarks in Word documents, adding links to slides within PowerPoint presentations, inserting a link to cell (or a range of cells) in Excel spreadsheets, etc. Therefore, to handle the hyperlinks in the document automation process, we have introduced the dynamic insertion of hyperlinks to:

*   bookmarks for Word Processing documents and emails,
*   cells for Spreadsheet documents, and
*   slides for Presentation documents.

To insert the hyperlinks, the _link_ tag is used which is placed inside the template documents. The following is the syntax for the _link_ tag:

```
<<link [uri_or_bookmark_expression] [display_text_expression]>>
```

The _uri\_or\_bookmark\_expression_ in the tag defines a URI or the name of a bookmark within the same document. This expression is mandatory and must return a non-empty value. Whereas, _display\_text\_expression_ is the text to be displayed for the hyperlink. This expression is optional and in case it is omitted or returns empty, _uri\_or\_bookmark\_expression_ is used as hyperlink's text.

For more details along with the sample template documents, please visit the following documentation articles:

*   [Dynamic insertion of hyperlinks in Java](https://docs.groupdocs.com/display/assemblyjava/Inserting+Hyperlinks+Dynamically)
*   [Dynamic insertion of hyperlinks in C#](https://docs.groupdocs.com/display/assemblynet/Inserting+Hyperlinks+Dynamically)

## Code Blocks, Spans and Strikeout Text for Markdown

In the latest version of our document assembly API, we have extended the set of supported Markdown features. From now on, the following Markdown features will be supported when saving assembled Markdown documents to Word Processing formats and saving assembled Word Processing documents and emails to Markdown:

*   [Indented code blocks](https://spec.commonmark.org/0.29/#indented-code-blocks)
*   [Fenced code blocks](https://spec.commonmark.org/0.29/#fenced-code-blocks)
*   [Inline code spans](https://spec.commonmark.org/0.29/#code-spans)
*   [Strikethrough text](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#emphasis)

For more details, see how to work with Markdown documents using [.NET](https://docs.groupdocs.com/display/assemblynet/Using+Markdown+Documents#UsingMarkdownDocuments-MarkdownDocuments(MD)) and [Java](https://docs.groupdocs.com/display/assemblyjava/Using+Markdown+Documents#UsingMarkdownDocuments-MarkdownDocuments(MD)) API.

Alright! So this is it from my side and it's your turn to check out and use these amazing document assembling features to enhance your document automation process.

You can download our ready-to-run source code examples from the GitHub [repository](https://github.com/groupdocs-assembly/). The details of every feature are available in our [documentation](https://docs.groupdocs.com/display/assemblyproductfamily/Home) and as always, we would love to hear from you on our [forum](https://forum.groupdocs.com/c/assembly).




