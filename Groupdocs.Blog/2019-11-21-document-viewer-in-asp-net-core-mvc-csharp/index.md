---
title: 'Create Document Viewer in ASP.NET Core MVC for 140+ File Formats'
date: Thu, 21 Nov 2019 05:30:45 +0000
draft: false
url: /2019/11/21/document-viewer-in-asp-net-core-mvc-csharp/
author: 'Usman Aziz'
summary: ''
tags: ['API', 'ASP.NET Core', 'C#', 'document viewer', 'Document viewer API', 'dotnet', 'MVC']
categories: ['GroupDocs.Viewer for .NET', 'GroupDocs.Viewer Product Family']
---

The **online document viewers** have become popular after the grown usage of digital documents, especially in the content management systems. The reason behind this popularity is you can view a variety of document formats without purchasing or installing dedicated software programs. Considering the importance of document viewers, I thought to write an article on how to create a universal document viewer in ASP.NET MVC.

We are going to create an **[ASP.NET MVC](https://dotnet.microsoft.com/apps/aspnet/mvc)** document viewer application that will target the  [**.NET Core**](https://en.wikipedia.org/wiki/.NET_Core) framework. For the document rendering at the backend, we'll use [**GroupDocs.Viewer for .NET**](https://products.groupdocs.com/viewer/net) API - a powerful **document viewer** API which supports over 140 document types including **PDF**, **Word**, **Excel**, **PowerPoint**, **Visio**, **CAD**, **Outlook**, and many other popular formats.

## Why .NET Core?

.NET Core is a valuable addition to the .NET ecosystem by Microsoft. It makes it possible to develop cross-platform applications without any additional efforts required by the developers. This is why I have selected .NET Core to be the targetted framework.

## Steps to Create Document Viewer in ASP.NET Core

**1.** Open Visual Studio and start a new project.

**2.** Select **.NET Core** from the project types and **ASP.NET Core Web Application** from templates.



{{< figure align=center src="images/1-ASP.NET-Core-Project.png" alt="">}}


**3.** Select **Web Application (Model-View-Controller)** and click Ok button.



{{< figure align=center src="images/2-MVC.png" alt="">}}


**4.** Install **GroupDocs.Viewer** from NuGet.



{{< figure align=center src="images/3.-GroupDocs.Viewer.png" alt="">}}


**5.** Open **Views/Home/Index.cshtml** file and replace its content with the following:

{{< gist GroupDocsGists 6976e6ad3866be7db972a52a390e3735 "ASP.NETCoreDocumentViewer_Script.html" >}}

**6.** Open **Controllers/HomeController.cs** and replace the content of the class with the following code.

{{< gist GroupDocsGists 6976e6ad3866be7db972a52a390e3735 "HomeController.cs" >}}

**7.** Append the following styles in the **wwwroot/css/site.css** file.

{{< gist GroupDocsGists 6976e6ad3866be7db972a52a390e3735 "navbar.css" >}}

**8.** Build the document viewer application and run in your favorite browser.



{{< figure align=center src="images/giphy.gif" alt="ASP.NET Core File Viewer">}}


## Download ASP.NET MVC Document Viewer

The source code of the ASP.NET MVC document viewer is open source and available for [download](https://github.com/usmanazizgroupdocs/ASP.NET-Core-MVC-Document-Viewer/archive/master.zip).




