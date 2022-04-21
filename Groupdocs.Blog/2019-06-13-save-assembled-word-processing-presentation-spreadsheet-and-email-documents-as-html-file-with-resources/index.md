---
title: 'Save Assembled Word Processing, Presentation, Spreadsheet and Email Documents as HTML File with Resources'
date: Thu, 13 Jun 2019 17:41:55 +0000
draft: false
url: /2019/06/13/save-assembled-word-processing-presentation-spreadsheet-and-email-documents-as-html-file-with-resources/
author: 'Usman Aziz'
summary: ''
tags: ['Assemble Documents', 'automated report generation', 'document automation', 'Dynamic Report Generation', 'HTML reporting', 'report generation', 'Report Generation API for .NET', 'Report Generation API for Java']
categories: ['GroupDocs.Assembly Product Family']
---



{{< figure align=center src="images/groupdocs-assembly.png" alt="">}}


The HTML format is widely used for creating the webpages or, in other words, the HTML files. These days, every operating system, whether it be of desktop or mobile, contains the built-in web browser that supports viewing the HTML files. Other than that, many free web browsers are also available in the market. This means that any information or the content that is available in the form of HTML pages can easily be viewed just having installed a web browser.

Just imagine a scenario where you have some Word documents created in MS Word and you want to display them in your web application. So how would you view the content of the file? A suitable and easy solution is if you could get the HTML form of that Word document then it can be viewed within your application in the web browser.

Now, you could imagine the usefulness of the HTML format. So, let's now find out how did we make use of HTML format in making GroupDocs.Assembly more powerful and useful for you.

Since version 19.5 of GroupDocs.Assembly, the assembled Word Processing documents, Spreadsheets, Presentations and Email files could be saved as HTML with resources. This means that the generated reports can now be saved as HTML files along with the resources such as images and, as I have mentioned before, you would be able to embed and view the content of the generated reports within your web application.  

Let's take the example of generating the report from the Word template and see how we can save the report as an HTML file. For saving the generated report as HTML with resources, we have added a new property _ResourceSaveFolder_ to the _LoadSaveOptions_ class to specify the folder that will be used to store the resource files. If no folder is specified, by default, external resource files will be stored to a folder having the same name as that of the HTML file (without extension) plus the "\_files" suffix. The following code snippets demonstrate this feature:  

**C#**

{{< gist GroupDocsGists 1b8866949d347fc0e83bea19ad1aa615 "SaveAsHtmlWithResources.cs" >}}  

**Java**

{{< gist GroupDocsGists 1b8866949d347fc0e83bea19ad1aa615 "SaveAsHtmlWithResources.java" >}}  

Along with this feature, we have also added the facility of loading HTML template documents referencing external resource files to be assembled and saved to non-HTML formats. For this, the containing folder of the template file is used as a base URI to resolve external resource files' relative URIs to absolute ones by default, as shown in the following code snippet:  

**C#**

{{< gist GroupDocsGists 1b8866949d347fc0e83bea19ad1aa615 "LoadHtmlWithResources.cs" >}}  

**Java**

{{< gist GroupDocsGists 1b8866949d347fc0e83bea19ad1aa615 "LoadHtmlWithResources.java" >}}  

Well, this would definitely be a really attracting release for you guys. So let's not wait and [download](https://downloads.groupdocs.com/assembly) the latest version to check how these features can make your report generation applications more powerful.  

For any questions or suggestions, have a conversation with us on our [forum](https://forum.groupdocs.com/).




