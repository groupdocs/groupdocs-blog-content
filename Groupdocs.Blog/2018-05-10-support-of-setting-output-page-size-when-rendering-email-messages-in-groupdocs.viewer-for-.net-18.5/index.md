---
title: 'Support of Setting Output Page Size when Rendering Email Messages in GroupDocs.Viewer for .NET 18.5'
date: Thu, 10 May 2018 07:45:11 +0000
draft: false
url: /2018/05/10/support-of-setting-output-page-size-when-rendering-email-messages-in-groupdocs.viewer-for-.net-18.5/
author: 'Usman Aziz'
summary: ''
tags: ['dotNET document rendering API', 'dotNET document viewer API', 'asp.net document viewer API', 'C# document viewer API', 'document rendering API', 'GroupDocs.Viewer for .NET Releases']
categories: ['GroupDocs.Viewer Product Family']
---

[![Document Viewer API](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-viewer-net.png)](https://www.groupdocs.com/products/viewer/net)

We have released version 18.5 of [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/net) with a couple of new features as well as 12 improvements and bug fixes. The latest version includes the feature of setting output page size when rendering email messages as image and PDF. Furthermore, you can now change the field labels in the header of the email messages. The feature of rendering password protected documents has also been extended for **ODT** and **OTT** formats. Below is the list of new features, improvements, and fixes added in GroupDocs.Viewer for .NET 18.5.

## Setting Output Page Size when Rendering Email MessagesSince the version 18.5, it is possible to set output page size when rendering Email messages as PDF and images. To enable this feature, set the _PageSize_property of the _EmailOptions_ class as shown in the following code snippet.```
string guid = "long-email.msg";
   
//Instantiate Viewer Hanlder 
ViewerImageHandler imageHandler = new ViewerImageHandler();
   
//Set page size  
ImageOptions imageOptions = new ImageOptions();
imageOptions.EmailOptions.PageSize = PageSize.A4;
  
//Render document with custom page size
List pages = imageHandler.GetPages(guid, imageOptions);
  
//Use Stream property of the PageImage class, to get output image.
foreach (PageImage page in pages)
{
    Console.WriteLine(page.Stream.Length);
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

## Changing Field Labels in Email's HeaderWhen rendering email messages, by default the API uses the English language to render field labels such as From, To, Subject etc.. Starting from 18.5, GroupDocs.Viewer provides a new property _FieldLabels _in _EmailOptions _class to change the field labels. Following code snippet shows how to use custom field labels.```
string guid = "email.msg";

//Instantiate Viewer Hanlder 
ViewerHtmlHandler htmlHandler = new ViewerHtmlHandler();

//Set field labels 
HtmlOptions htmlOptions = new HtmlOptions();
htmlOptions.EmailOptions.FieldLabels[EmailField.From] = "Sender";
htmlOptions.EmailOptions.FieldLabels[EmailField.To] = "Receiver";
htmlOptions.EmailOptions.FieldLabels[EmailField.Sent] = "Date";
htmlOptions.EmailOptions.FieldLabels[EmailField.Subject] = "Topic";
//Render document with custom field labels
List pages = htmlHandler.GetPages(guid, htmlOptions);
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/net) documentation article.

## Bug FixesFollowing issues are fixed in version 18.5 of GroupDocs.Viewer for .NET.

*   The voluminous email is not fully rendered into image
*   Images and diagrams are missing when rendering OTS file
*   Text's shadow appears in the output HTML
*   Issues when rendering Excel document with vertical Japanese writing
*   Text overlaps when viewing HTML in Mozilla Firefox
*   Content is missing when rendering PDF document into HTML
*   Link with external URL in PDF document is not rendered as the hyperlink
*   The output image is cropped when rendering HTML as image

## ImprovementsFollowing are the improvements that we have made in version 18.5.

*   Addition of new property EnableCaching which will replace UseCache property in ViewerConfig class
*   Support of rendering password protected ODT and OTT formats
*   Support of setting JpegQuality option when rendering OneNote documents into PDF
*   Extended support for DefaultFontName option for MS Project documents when rendering into PDF

## Related Links and ResourcesWe have a few channels and resources for you to download, learn, try and get technical support on our **document viewer API**.

*   [Download](http://downloads.groupdocs.com/viewer/net "Download API") - MSI Package and Zipped DLLs
*   [NuGet Package](https://www.nuget.org/packages/GroupDocs.Viewer/ "Install from NuGet Package") - NuGet Installation
*   [Documentation](https://docs.groupdocs.com/viewer/net "Document Viewer API Documentation ") - Product Docs
*   [Forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum") - Technical Support Forum
*   [Video Tutorials](https://www.youtube.com/watch?v=oqh4nROLRsY&list=PL25CTxMCj5vPVahuYtHx0uscArNA595GK "GroupDocs.Viewer video tutorials") - YouTube Videos
*   [Example / Plugins](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET "download example project and front ends") - GitHub Source Code Examples
*   [Sample Front End Apps](https://github.com/groupdocs-viewer/ "Open Source Document Viewer Applications") - Open Source **Document Viewer** Applications

## FeedbackAs always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum").





