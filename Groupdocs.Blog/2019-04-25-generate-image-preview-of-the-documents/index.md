---
title: 'Generate Image Preview of the Documents'
date: Thu, 25 Apr 2019 16:01:39 +0000
draft: false
url: /2019/04/25/generate-image-preview-of-the-documents/
author: 'Usman Aziz'
summary: ''
tags: ['.NET API', 'document preview', 'document-metadata', 'file preview', 'Image preview', 'Java API', 'render document preview']
categories: ['GroupDocs.Metadata', 'GroupDocs.Metadata Product Family']
---

Image previews are now commonly used to present your file/document to the users. It is quite useful when you want the users to quickly have a look at your document without downloading or opening it. As an example, MS Windows has this ability to provide the preview of the files in the preview pane of File Explorer without opening the document in the dedicated software program.

Did you ever desire to have the ability to generate image previews in your application? If yes then it is the time to embed this feature in your application with a few lines of code using [GroupDocs.Metadata](https://products.groupdocs.com/metadata).

So, let's have a look at how to generate image previews for the documents.

We have introduced **_PreviewHandler_** class in the GroupDocs.Metadata for .NET and Java to get the document pages in the form of images. Using **_PreviewHandler_** you can access and select the document page(s), either a single page or all pages, that you want to render as image. Below are the code snippets that generate the images of the pages in a Word document.

**C#**  
{{< gist GroupDocsGists c659d025f32d195ad2ccf9263c531768 "GenerateImagePreview.cs" >}}

**Java**  
{{< gist GroupDocsGists c659d025f32d195ad2ccf9263c531768 "GenerateImagePreview.java" >}}

At the moment, we have launched this feature for the following documents:  

*   PDF documents
*   Presentations
*   Spreadsheets
*   Word processing documents
*   Vision diagrams
*   OneNote documents
*   Images

Let's not wait and try out this amazing feature by downloading the [latest version](https://downloads.groupdocs.com/metadata) of GroupDocs.Metadata for .NET and Java. You can explore and evaluate the API features by cloning/downloading the examples from the [GitHub repository](https://github.com/groupdocs-metadata).

In case you would have any questions or suggestions, we would love to have a conversation with you on our [forum](https://forum.groupdocs.com/).




