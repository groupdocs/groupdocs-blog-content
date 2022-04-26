---
title: 'How to Build an ASP.NET WebForms HTML5 Document Viewer Using Web Services'
date: Sat, 10 Aug 2013 14:03:07 +0000
draft: false
url: /2013/08/10/build-asp-net-webforms-html5-document-viewer/
author: 'Derek Hyland'
summary: ''
tags: ['ASP.NET', 'asp.net document viewer', 'GroupDocs Viewer', 'GroupDocs Viewer for .NET', 'html5 document viewer', 'zArchive']
---

[![GroupDocs.Viewer for .NET Library](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/04/GD_VWR_NETIcon_114.png)](https://docs.groupdocs.com/viewer/net)Customers who integrate our [HTML5 document viewer](http://groupdocs.com/html5-document-viewer "html5 document viewer") into their website can plug it into other websites too. This article shows how to build an ASP.NET WebForms HTML5 document viewer using the [.NET version of the GroupDocs.Viewer](http://groupdocs.com/dot-net/document-viewer-library "GroupDocs.Viewer for .NET Library").

## Requirements

1.  IIS 7 or later.
2.  Microsoft Visual Studio 2012

## Part A: Creating A GroupDocs.Viewer Web ServiceFollow the steps given below to create a GroupDocs online document viewer service: 1. Open Visual Studio 2012 and create a new ASP.NET Web Forms Project: ![Create a new ASP.NET Web Forms Project](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/10/webforms_image001.jpg) 2. Add a **New Item** to the Project and then click **Add** to create a web service, **WebServiceProvidingViewer**: ![Create a web service: WebServiceProvidingViewer](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/10/webforms_image002.jpg) 3. Add the following lines to **WebServiceProvidingViewer.asmx** to import the GroupDocs.Viewer library using Groupdocs.Web.UI:```
public WebServiceProvidingViewer() { GroupdocsViewer.SetRootStoragePath(Server.MapPath(@"~/documents")); } \[WebMethod\] public string GetJavaScriptLibraries() { //Fetches the script bocks. return Groupdocs.Web.UI.GroupdocsViewer.CreateScriptLoadBlock().LoadJquery().LoadJqueryUi().UseHttpHandlers().ToString(); } \[WebMethod\] public string GetInlineDocumentScript() { // Fetches the file contents. string groupdocsViewercript; using (FileStream fileStream = new FileStream(@"TestDoc.docx", FileMode.Open)) { groupdocsViewercript = Groupdocs.Web.UI.GroupdocsViewer.ClientCode() .TargetElementSelector("#doc") .Stream(fileStream, "docx") .DocViewerId("doc\_viewer") .EnableRightClickMenu(true) .ShowThumbnails(true) .OpenThumbnails(true) .ZoomToFitWidth() .ToString(); } return groupdocsViewercript; }
```4\. If you intend to use GroupDocs.Viewer for .NET on IIS version 7 or later in Classic Pipeline Mode, IIS version 6 or Visual Studio ASP.NET Development Server, then insert the following HTTP handler descriptions into the **system.web** section of your site’s **web.config** file:```
<system.web> <httpHandlers> <addverb="GET,POST"path="document-viewer/ViewDocumentHandler"type="Groupdocs.Web.UI.Handlers.ViewDocumentHandler, Groupdocs.Viewer, Culture=neutral" /> <addverb="GET,POST"path="document-viewer/GetDocumentPageImageHandler"type="Groupdocs.Web.UI.Handlers.GetDocumentPageImageHandler, Groupdocs.Viewer, Culture=neutral" /> <addverb="GET,POST"path="document-viewer/LoadFileBrowserTreeDataHandler"type="Groupdocs.Web.UI.Handlers.LoadFileBrowserTreeDataHandler, Groupdocs.Viewer, Culture=neutral" /> <addverb="GET,POST"path="document-viewer/GetImageUrlsHandler"type="Groupdocs.Web.UI.Handlers.GetImageUrlsHandler, Groupdocs.Viewer, Culture=neutral" /> <addverb="GET"path="document-viewer/CSS/GetCssHandler"type="Groupdocs.Web.UI.Handlers.CssHandler, Groupdocs.Viewer, Culture=neutral" /> <addverb="GET"path="document-viewer/images/\*"type="Groupdocs.Web.UI.Handlers.EmbeddedImageHandler, Groupdocs.Viewer, Culture=neutral" /> <addverb="GET,POST"path="document-viewer/GetScriptHandler"type="Groupdocs.Web.UI.Handlers.ScriptHandler, Groupdocs.Viewer, Culture=neutral"/> <addverb="GET"path="document-viewer/GetFileHandler"type="Groupdocs.Web.UI.Handlers.GetFileHandler, Groupdocs.Viewer, Culture=neutral" /> <addverb="GET,POST"path="document-viewer/GetPdf2JavaScriptHandler"type="Groupdocs.Web.UI.Handlers.GetPdf2JavaScriptHandler, Groupdocs.Viewer, Culture=neutral" /> <addverb="GET,POST"path="document-viewer/GetPdfWithPrintDialogHandler"type="Groupdocs.Web.UI.Handlers.GetPdfWithPrintDialogHandler, Groupdocs.Viewer, Culture=neutral" /> </httpHandlers>
```5\. If you intend to use GroupDocs.Viewer for .NET on IIS version 7 or later in Integrated Pipeline Mode, then insert the following HTTP handler descriptions into the **system.webServer** section of your site’s **web.config **file:```
<system.webServer> <handlers> <addname="ViewDocumentHandler"verb="GET,POST"path="document-viewer/ViewDocumentHandler"type="Groupdocs.Web.UI.Handlers.ViewDocumentHandler, Groupdocs.Viewer, Culture=neutral" /> <addname="GetDocumentPageImageHandler"verb="GET,POST"path="document-viewer/GetDocumentPageImageHandler"type="Groupdocs.Web.UI.Handlers.GetDocumentPageImageHandler, Groupdocs.Viewer, Culture=neutral" /> <addname="LoadFileBrowserTreeDataHandler"verb="GET,POST"path="document-viewer/LoadFileBrowserTreeDataHandler"type="Groupdocs.Web.UI.Handlers.LoadFileBrowserTreeDataHandler, Groupdocs.Viewer, Culture=neutral" /> <addname="GetImageUrlsHandler"verb="GET,POST"path="document-viewer/GetImageUrlsHandler"type="Groupdocs.Web.UI.Handlers.GetImageUrlsHandler, Groupdocs.Viewer, Culture=neutral" /> <addname="GetCssHandler"verb="GET"path="document-viewer/CSS/GetCssHandler"type="Groupdocs.Web.UI.Handlers.CssHandler, Groupdocs.Viewer, Culture=neutral" /> <addname="images"verb="GET"path="document-viewer/images/\*"type="Groupdocs.Web.UI.Handlers.EmbeddedImageHandler, Groupdocs.Viewer, Culture=neutral" /> <addname="GetScriptHandler"verb="GET,POST"path="document-viewer/GetScriptHandler"type="Groupdocs.Web.UI.Handlers.ScriptHandler, Groupdocs.Viewer, Culture=neutral" /> <addname="GetFileHandler"verb="GET"path="document-viewer/GetFileHandler"type="Groupdocs.Web.UI.Handlers.GetFileHandler, Groupdocs.Viewer, Culture=neutral" /> <addname="GetPdf2JavaScriptHandler"verb="GET,POST"path="document-viewer/GetPdf2JavaScriptHandler"type="Groupdocs.Web.UI.Handlers.GetPdf2JavaScriptHandler, Groupdocs.Viewer, Culture=neutral" /> <addname="GetPdfWithPrintDialogHandler"verb="POST"path="document-viewer/GetPdfWithPrintDialogHandler"type="Groupdocs.Web.UI.Handlers.GetPdfWithPrintDialogHandler, Groupdocs.Viewer, Culture=neutral" /> </handlers>
```6\. Deploy the project to IIS. Make sure that this project has a static URL and it has started successfully. You can check the availability of a public web service using this URL: "http://your-domain/WebServiceProvidingViewer.asmx". If all works fine, you will see two available operations (webmethods): "GetInlineDocumentScript" and "GetJavaScriptLibraries". You must also be able to call these webmethods by clicking the Invoke button.

## Part B: Creating the GroupDocs.Viewer Consumer Web ApplicationFollow the steps given below to create an ASP.NET Web Forms project that consumes the **GroupDocs.Viewer Web Service**: 1. Create a new ASP.NET Web Forms Application: ![Create a Web Forms Application](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/10/webforms_image003.jpg) 2. Add a web reference in the project for the web service created in the other application. To add a web reference, right-click the project, and then click **Add Web Reference**: ![Click Add Web Reference](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/10/webforms_image004.gif) The **Add Web Reference** window is displayed. 3. Fill in the URL and Web reference name in the **URL** and **Web Reference** name fields: ![Fill in the URL and Web reference name](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/10/webforms_image005.jpg) 4. Add the following controls in the **Default.aspx** file:```
<head id="HeadControl" runat="server">
    <title></title>
</head>
<body id="BodyControl"  runat="server">
    <div id="test" style="width:600px;height:400px;position:relative"></div>
</body>
```5\. Add the following lines in the **Page\_Load** function:```
// Creating object of Web Service WebServiceProvidingViewer webServiceProvidingViewer = new WebServiceProvidingViewer(); // Calling the operation GetJavaScriptLibraries from the webservice string scriptLibraries = webServiceProvidingViewer.GetJavaScriptLibraries(); // Calling the operation GetInlineDocumentScript from the webservice string inlineDocPreviewScript = webServiceProvidingViewer.GetInlineDocumentScript(); // The contents are added to the HeadControl HeadControl.Controls.Add(new Literal() { Text = scriptLibraries }); // The contents are added to the BodyControl BodyControl.Controls.Add(new Literal() { Text = inlineDocPreviewScript });
```6\. Compile and run the project. You can run it from Microsft Visual Studio using ASP.NET Development Server, it is not necessary to deploy it to the IIS, as with the previous one. Please note that while running this "consumer" application, the previous **GroupDocs.Viewer Web Service** application must already be running. You can see that the GroupDocs.Viewer is consumed in the running application: ![The running application](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/10/webforms_image006.jpg) Thus, the GroupDocs document viewer service, integrated in a web application, is consumed in another ASP.NET Web Forms Application. You may download the [**sample code**](https://www.dropbox.com/s/ubok1fprdvppm0n/GroupDocsViewerDemos.zip) of the project described.

## RemarkThe **GroupDocs.Viewer Web Service** is available for requests only from the local machine by default. So, when a consumer application is located on a different machine, it won't be able to get an access to the web service. In order to fix this, just insert the following configuration code into the **web.config** of the **GroupDocs.Viewer Web Service** application:```
<configuration>
<system.web>
<webServices>
<protocols>
<add name="HttpGet"/>
<add name="HttpPost"/>
</protocols>
</webServices>
</system.web>
</configuration>
```




