---
title: 'How to Build a SharePoint Document Viewer Using GroupDocs.Viewer for .NET'
date: Tue, 24 Sep 2013 14:01:15 +0000
draft: false
url: /2013/09/24/how-to-build-sharepoint-document-viewer-using-groupdocs-viewer-for-net/
author: 'Denis Gvardionov'
summary: ''
tags: ['GroupDocs Viewer', 'GroupDocs Viewer for .NET', 'SharePoint', 'zArchive']
---

When we released [GroupDocs.Viewer for .NET](http://groupdocs.com/dot-net/document-viewer-library), we got lots of questions from SharePoint users about whether it could be used to build a SharePoint document viewer. Finally, the answer is yes: our online document viewer allows integration with SharePoint web applications. Moreover, SharePoint websites using GroupDocs.Viewer for .NET can also be used for cross-domain document viewing. \[caption id="attachment\_3916" align="alignnone" width="600"\]![How to Build a SharePoint Document Viewer Using GroupDocs.Viewer for .NET](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/GD_VWR_SharePoint_02.png)\[/caption\] Just follow these simple step-by-step instructions to embed our online document viewer in your SharePoint websites as a Web Part: **Requirements**

*   Server running the GroupDocs document viewer service
*   Microsoft SharePoint 2010
*   Microsoft Visual Studio 2010

The following steps illustrate a typical process for creating of a Web Part which can be used to run the GroupDocs document viewer service: 1. Open Visual Studio 2010 as administrator and create a new **Empty SharePoint Project**. ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/create_1.jpg "Create a new Empty SharePoint Project") **Note:** If you have not run as an administrator, then Visual Studio will prompt you to restart using different credentials as shown below: ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/2-restart-under-different-credentials.jpg "Restart using different credentials")   2. Specify the local SharePoint server and then click **Finish**. ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/3-specify-server.jpg "Specify the local SharePoint server") **Note:** You cannot use a SharePoint instance outside your workstation. All the necessary files are created as shown below: ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/soln_explorer_3.gif "Solution Explorer")   3. To create a Web Part in the project, click **Web Part** and then click **Add**. ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/webpart_4.jpg "Create a Web Part in the project") The necessary files needed for the Web Part are created as shown. ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/soln_explorer_5.gif "Solution Explorer")   4. We are using WebPartConsumer.cs to write functions to access the GroupDocs document viewer service. Add the following lines to the WebPartConsumer.cs file:

```
protected override void RenderContents(HtmlTextWriter writer)
        {
// Fetch JavaScript Libraries
  string scriptLibraries = GetHtmlPageContents("http://localhost:2020/Home/GetJavaScriptLibraries");
// Fetches the  inline Scripts
  string inlineDocPreviewScript = GetHtmlPageContents("http://localhost:2020/Home/GetInlineDocumentScript");

            writer.Write(scriptLibraries);
            writer.Write("
```

```
");
            writer.Write(inlineDocPreviewScript);
          // Renders the contents to the page.
            base.RenderContents(writer);
        }
//Function to get the contents from a given URL
    private static string GetHtmlPageContents(string strURL)
        {
            String strResult;
            WebResponse objResponse;
            WebRequest objRequest = HttpWebRequest.Create(strURL);
            objResponse = objRequest.GetResponse();
            using (StreamReader sr = new StreamReader(objResponse.GetResponseStream()))
           	 {
            	    strResult = sr.ReadToEnd();
           	 }
            return strResult;
        }
```

  5. Now, deploy the project. The **Output** screen is displayed: ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/deploy_6.jpg "The Output screen") On the **Output** screen, you can see that the solution **ViewConsumer.wsp** is successfully deployed to the SharePoint server.   6. To view the control in a local SharePoint instance, you have to add it to your page as a web part. ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/site_7.jpg "Viewing the control in a local SharePoint instance")   7. To add the control, go to a page intended for editing. ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/site_edit_8.jpg "Adding a Web Part")   8. Add the Web Part by using the option **Add a Web Part** as shown below. ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/addwebpart_9.jpg "Adding a Web Part")   9. The Web Part (**WebPartConsumer**) is listed as shown below. ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/webpartconsumer_10.jpg "WebPartConsumer")   10. Click **Add** to add the Web Part to the page. 11. Click **Stop Editing** to save the page. After saving, you can see the WebPart, **WebPartConsumer**, in action as shown below. ![Building a SharePoint Document Viewer Using The GroupDocs.Viewer for .NET](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/09/site_11.jpg "WebPartConsumer") Thus, the GroupDocs document viewer service, integrated in a web application, is consumed in a SharePoint website.




