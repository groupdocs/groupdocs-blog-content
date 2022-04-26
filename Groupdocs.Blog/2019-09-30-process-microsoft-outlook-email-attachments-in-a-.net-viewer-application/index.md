---
title: 'Process the Microsoft Outlook Email Attachments in a .NET Viewer Application'
date: Mon, 30 Sep 2019 07:47:51 +0000
draft: false
url: /2019/09/30/process-microsoft-outlook-email-attachments-in-a-.net-viewer-application/
author: 'Muhammad Umar'
summary: ''
tags: ['.NET', '.NET API', 'ASP.NET', 'Attachment', 'C#', 'Email', 'GroupDocs Viewer', 'Microsoft Outlook', 'MS Outlook']
categories: ['GroupDocs.Viewer Product Family']
---

  
An ‘attachment’ is a file such as a document or a photo that is attached to an email. It’s easy to attach pictures, files, contacts, emails and many other items to your Outlook messages. If you selected a file on your local computer or group document library for the attachment purpose, a copy of the file is attached to the email.

**The case:** A software developer is making a document viewing application. Although, his application is capable to render the MS Outlook Emails, but he also wants to add a feature to render the email attachments.

## The GroupDocs.Viewer for .NET API for Processing Attachments

The [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net) API provides the functionality to process attachments from document types that support them, e.g. Email documents, Outlook data files, Archives and PDF documents.

You'll see in the below sections that how we can process the Microsoft Outlook Email attachments in various ways.

## Render document attachments

To achieve this by using [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net) you should:

*   Instantiate _Viewer _object for the initial document that contains attachment;
*   Call _SaveAttachment _method and save attachment somewhere (for example, to local disk or memory stream);
*   Instantiate another one V_iewer _object and path saved attachment to it;
*   Specify view options dependent on desired output format - _HtmlViewOptions / PngViewOptions / JpgViewOptions / PdfViewOptions_;
*   Call _View_ method and render an attachment.

Following example demonstrates how to render document attachments.

{{< gist GroupDocsGists aa13f2abc182802de634edeefaf38e34 "RenderFileAttachment.cs" >}}

## Retrieve and print document attachments {#Retrieveandprintdocumentattachments-Retrieveandprintdocumentattachments}

GroupDocs.Viewer enables you to retrieve and print document attachments. The steps to get the list of all attachments are given below:

*   Instantiate _Viewer _object for the initial document that contains attachment;
*   Call Get_Attachments _method and obtain collection of document attachments ;
*   Iterate through attachments collection and print attachment names.

Following example demonstrates the implementation of the above steps.

{{< gist GroupDocsGists 81f22e87f96725ed2bb2dace253387c5 "PrintAttachments.cs" >}}

## Save document attachments {#Retrieveandsavedocumentattachments-Retrieveandsavedocumentattachments}

[GroupDocs.Viewer](https://products.groupdocs.com/viewer/) enables you save document attachments to stream. Here are the steps for saving attachments:

*   Instantiate _Viewer _object for the initial document that contains attachment;
*   Call Get_Attachments _method and obtain collection of document attachments ;
*   Iterate through attachments collection and save attachment calling Save_Attachment _method.

Following example demonstrates how to retrieve and save attachments.

{{< gist GroupDocsGists 1b36d099e167b1936cf41d387a3906e8 "SaveAttachments.cs" >}}

The API offers many other handful features for your viewing applications. For more details, please feel free to visit [documentation.](https://docs.groupdocs.com/display/viewernet/Home) To explore more examples you can access our open source [examples](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET) and in case you would have any query, please feel to contact us using our [forum](https://forum.groupdocs.com/).




