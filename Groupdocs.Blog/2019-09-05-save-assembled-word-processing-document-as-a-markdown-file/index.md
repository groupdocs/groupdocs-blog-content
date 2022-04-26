---
title: 'Save Assembled Word Processing Document as a Markdown File'
date: Thu, 05 Sep 2019 11:02:00 +0000
draft: false
url: /2019/09/05/save-assembled-word-processing-document-as-a-markdown-file/
author: 'Usman Aziz'
summary: ''
tags: ['document automation', 'report generator']
categories: ['GroupDocs.Assembly', 'GroupDocs.Assembly Product Family']
---

[Markdown](https://wiki.fileformat.com/specification/word-processing/md/) is a well known and one of the popular markup languages these days. The appearance of the text in Markdown is controlled using the syntax instead of using rich text editors or applications such as MS Word. The best thing is, it is a lightweight language and can be written in the plain text editors such as Notepad. As far as its usage is concerned, Markdown is popular in writing wikis, readme files, and others. This is the reason why we added the support of Markdown (.md) files in our document automation API - [GroupDocs.Assembly](https://products.groupdocs.com/assembly).

The following is a glimpse of the Markdown syntax:



{{< figure align=center src="images/Markdown.png" alt="">}}


And this is how the text will be formatted:



{{< figure align=center src="images/MD-Output.png" alt="">}}


Although the syntax of Markdown is simple, still you could find it difficult to remember when writing the templates for longer reports. So how could you make this process easier for you? Let me tell you one possible workaround for this.

*   Create a Word template with required text formatting
*   Populate the template with data
*   Save the generated report as Markdown (.md) file

Now, let's come to point on how you can automate the above-mentioned steps. The solution is simple and uses a few lines of code but only if you are using GroupDocs.Assembly. Yes, you can now use the Word template to generate the report and then save the generated report as a Markdown file. So let me show you how this could be done.

Just assume that you need to dynamically generate a report in Markdown format (.md). For this, instead of creating the Markdown template, you can create the Word template and format the text as you need. Once the template is ready, just populate the data and save the generated report as a Markdown file. For the demonstration, I have created ReadMe.docx template for you that will be used in the following code samples.

**C#**

{{< gist usman-aziz 70acd9812c5dbdb4b9259fcc9493763c "SaveWordReportAsMD.cs" >}}

**Java**

{{< gist usman-aziz 70acd9812c5dbdb4b9259fcc9493763c "SaveWordReportAsMD.java" >}}

The resultant Markdown file that you will get from these code samples is ReadMe\_Out.md.

You can see how easy it is to save the assembled report as a Markdown file by just changing the extension of the output file from "_.docx"_ to _".md"_. In addition to this feature, we have also added support for:

*   Saving assembled Markdown document as Word Processing formats
*   Saving assembled email as a Markdown document

At the moment, the following Markdown features are supported:

*   Headings
*   Blockquotes
*   Horizontal rules
*   Bold emphasis
*   Italic emphasis

But no need to worry because we shall keep extending the supported features in the upcoming releases of GroupDocs.Assembly.

In case you want to use these features in your application, just [download](https://downloads.groupdocs.com/assembly) the latest release (v19.8) of GroupDocs.Assembly for .NET or Java. For the ready-to-run source code examples, download or clone the examples project from [GitHub repository](https://github.com/groupdocs-assembly).

As always, we welcome you on our [forum](https://forum.groupdocs.com/categories) in case you would have any suggestions or queries.




