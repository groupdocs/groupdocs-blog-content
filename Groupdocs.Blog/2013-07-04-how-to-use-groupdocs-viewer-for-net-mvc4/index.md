---
title: 'How to Use GroupDocs'' Document Viewer for .NET MVC4'
date: Thu, 04 Jul 2013 10:29:10 +0000
draft: false
url: /2013/07/04/how-to-use-groupdocs-viewer-for-net-mvc4/
author: 'Derek Hyland'
summary: ''
tags: ['.NET', '.NET MVC4', 'document viewer', 'GroupDocs Viewer', 'GroupDocs Viewer for .NET', 'online document viewer', 'View documents online', 'zArchive']
---

We are often asked whether our GroupDocs Viewer for .NET works with Microsoft ASP.NET MVC 4. The answer is YES, it works well. In this article, we will learn how to use the ASP.NET HTML5 DLL version of GroupDocs' document viewer with .NET MVC 4.

## **Requirements**

*   GroupDocs Viewer
*   Microsoft ASP.NET MVC 4

## Сonnection and useTo use the DLL version of GroupDocs' document viewer for .NET in an ASP.NET MVC Project:

1.  Download GroupDocs Viewer for .NET to your local PC. You can buy or download trial version [here](http://groupdocs.com/dot-net/document-viewer-library).
2.  Copy the **GroupDocs Viewer.dll** file to the project's **reference** folder.
3.  Add a reference to the **Groupdocs.Viewer.dll** assembly to your project.
4.  Insert the following calls into the **Application\_Start** method of your **Global.asax.cs**:
    
    ```
    GroupdocsViewer.InitRoutes();// registers routes for the Viewer
    GroupdocsViewer.SetLicensePath(<path to your license file if you have one>);
    GroupdocsViewer.SetRootStoragePath(<path to the directory where you store your documents and image cache of the Viewer>);
    ```
    
5.  Insert the following code to load GroupDocs Viewer for .NET scripts and CSS into the **<head>** section of your **\_Layout.vbhtml**file:
    
    ```
     @imports Groupdocs.Web.UI
    ```
    
6.  In the **Global.asax**file, add this code just after AreaRegistration.RegisterAllAreas()
    
    ```
    Groupdocs.Web.UI.GroupdocsViewer.InitRoutes()
    Groupdocs.Web.UI.GroupDocsViewer.SetLicensePath(<path to your license file if you have one>);
    Groupdocs.Web.UI.GroupdocsViewer.SetRootStoragePath("<path to the directory where you store your documents and image cache of the Viewer>")
    ```
    
7.  Insert the following code to load Groupdocs Viewer for .NET scripts and CSS into the **<head>**section of your page:
    
    ```
        
    
    	@Html.CreateViewerScriptLoadBlock()
    ```
    
    You can set options to insert code which will load jQuery and jQuery UI scripts:
    
    ```
    @Html.CreateViewerScriptLoadBlock().LoadJquery().LoadJqueryUi()
    ```
    
    This call will create a number of **<script type='text/javascript'> **blocks.****  

*   To show GroupDocs' online document viewer on the page, simply add this code:
    
    ```
    <div id="test" style="width:800px;height:700px"></div>
    
    	@(Html.ViewerClientCode()
                .TargetElementSelector("#test")
                .FilePath("mass\_media.doc")
    			.DocViewerId("doc\_viewer1")
                .EnableRightClickMenu(true)
                .ShowThumbnails(true)
                .OpenThumbnails(true)
                .ZoomToFitWidth()
                .Width(500)
                .Height(300))
    ```
    
    Where:

*   <div id="test" style="width:800px;height:700px"></div> – the div in which the iframe will be inserted.
*   .TargetElementSelector("#test") \_ – select the div with ID "test".
*   .FilePath("GroupDocs\_Signature\_Demo.pdf") \_ – the name of the file which you want to embed in the iframe. This file must be in the directory where you store documents and the Viewer's image cache.
*   .DocViewerId("doc\_viewer1") \_ – the iframe's ID.

**Note**: If the GroupDocs Viewer icons are not loaded in the added iframe, do the following:

*   Go to the project properties -> web and set **Use Visual Studio Development server** then run project

When the code runs, we see an iframe with GroupDocs Viewer on the page. \[caption id="attachment\_2980" align="alignnone" width="600" caption="GroupDocs' online document viewer in action"\]![GroupDocs' online document viewer in action](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/07/GroupDocs-online-document-viewer-in-action2.png "GroupDocs' online document viewer in action")\[/caption\]




