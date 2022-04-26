---
title: 'How to Install and Use GroupDocs'' Online Document Viewer Plugin for Alfresco on Linux'
date: Fri, 21 Jun 2013 13:25:24 +0000
draft: false
url: /2013/06/21/how-to-install-and-use-groupdocs-online-document-viewer-plugin-for-alfresco-on-linux/
author: 'Derek Hyland'
summary: ''
tags: ['Alfresco', 'GroupDocs Viewer', 'GroupDocs Viewer Plugin', 'Linux', 'online document management system', 'online document viewer', 'View documents online', 'zArchive']
---

Let me show you how to install and use GroupDocs online document viewer plugin for Alfresco CMS on Linux.

## **Requirements**

*   Java jdk
*   Java jre
*   Alfresco
*   GroupDocs Viewer plugin
*   Apache Tomcat
*   PostGRE SQL

## **Preparation**First of all, you should have Alfresco CMS installed in your machine. [Download](http://www.alfresco.com/products/community) and [install](http://docs.alfresco.com/4.1/concepts/welcome-infocenter.html) a community version if you don't have one already. Alfresco is a Java CMS, so we need Apache tomcat and PostGRE SQL installed. But don't worry! you don't need to install them manually. They come as a package with Alfresco and they will be installed and configured automatically along with the Alfresco installation if you choose the standard installation. If you choose advanced installation, you will be able to select which software to install and which not. Also, in advanced mode, you can configure your Alfresco, Tomcat and Database settings such as PORT, locations, etc. I'm using standard installation for this tutorial; however, if you prefer advanced installation, you can refer to Alfresco docs on how to install it in advanced mode.

## **Plugin Installation**GroupDocs Viewer plugin is a compiled package for Alfresco CMS. So we should put plugins files to the WAR file of the CMS, which will be unpacked when you start Tomcat service. After you install the plugin, Alfresco folder will be deleted by the apply\_amps.sh script from the Webapp folder. But don't worry! all necessary folders and files will be created as soon as you start the Tomcat service. GroupDocs plugin for Alfresco is now available as Version 1.0 and have minimal functionality such as embed iframe with document. The embedding is made available only via inserting a file ID and the size (Height and Width) of the iframe. But, the coming versions will include functionality like uploading files to your GroupDocs account, browsing these GroupDocs files directly from within the plugin interface, and then select a preferred file for embedding. So let's get on with the installation process. To install GroupDocs Viewer plugin for Alfresco, do the following:

1.  Download the _.jar_ and _.amp_ files from [GitHub repository](https://github.com/groupdocs).
2.  Start **ALFRESCO\_INSTALL\_DIR/manager-windows.exe** and stop tomcat if it's running. ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/06/service_manager1.png "service_manager")
3.  Copy **alfresco-groupdocs-viewer-share-1.0.jar** file and paste it to _ALFRESCO\_INSTALL\_DIR/tomcat/webapps/share/WEB-INF/lib_ directory. ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/06/copy_jar.png "copy_jar")
4.  Copy **alfresco-groupdocs-viewer-repo-1.0.amp** file and paste it to _ALFRESCO\_INSTALL\_DIR/amps_ directory. ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/06/copy_amp.png "copy_amp")
5.  Run script **ALFRESCO\_INSTALL\_DIR/bin/apply\_amps**.**Result**: The plugin installation is completed. ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/06/run_apply_amps.png "run_apply_amps")

## Plugin UsageNow, let's have a look at how to use the plugin. GroupDocs Viewer supports multiple file formats; importantly, all common and business file formats. For example, this all-in-one viewer can be used as an online:

*   PDF viewer
*   Word viewer (DOC, DOCX, TXT, RTF, ODT)
*   PowerPoint viewer (PPT, PPTX)
*   Spreadsheet viewer (XLS, XLSX)
*   Image file viewer (JPG, BMP, GIF, TIFF)

With the help of this add-on, you can simply embed documents to your Alfresco pages so that your website visitors can view documents online using GroupDocs' high-fidelity online document viewer. The application is so intuitive that even novice users can easily view documents online using it. And now the moment of truth, lets use it. To add GroupDocs iframe to your site, do the following:

1.  Log in to the Alfresco admin panel using your admin credentials and then click **Create content in your home space**. **![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/06/create_content1.png "create_content")Result**: The **Create Content Wizard** page is loaded.
2.  Add a name, select content type as **HTML**, and then click **Next**. ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/06/content_type.png "content_type")**Result**: The TinyMCE editor is displayed.
3.  Click the GroupDocs icon. ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/06/gd_button1.png "gd_button")**Result**: A window with **File ID**, **Height** and **Width** fields is popped up.
4.  Paste the file ID (or GUID) in the **File ID** field, enter the height and width in px, and then click **Insert**. **![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/06/form1.png "form")Result**: The embedded document is displayed. **Note**: To find more information, please refer to the online help on [how to find the file ID](https://docs.groupdocs.cloud/total/getting-started/)? ![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2013/06/result.png "result")**Note**: For security reasons, Alfresco strips off IFRAME tag from HTML in Blogs and Discussions. According to this blog entry, that will become configurable in the next version.

Congratulations! you've successfully embedded the document, complete with GroupDocs Viewer to Alfresco CMS.




