---
title: 'GroupDocs.Viewer for Java Library Version 2.5.0 – A Universal Document Viewer for Your Web, Mobile & Desktop Apps'
date: Thu, 30 Oct 2014 17:11:49 +0000
draft: false
url: /2014/10/30/groupdocs-viewer-for-java-library-universal-document-viewer-for-your-web-mobile-desktop-apps/
author: 'Ihor Mykhalevych'
summary: ''
tags: ['GroupDocs Viewer', 'viewer for java library', 'zArchive']
---

[![GroupDocs.Viewer for Java](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/06/GD_VWR_JavaIcon_1141.png)](http://groupdocs.com/java/document-viewer-library)In this post I'm going to introduce new features that became available with version 2.5.0 of the Java document viewer library from GroupDocs. [GroupDocs.Viewer for Java](http://groupdocs.com/java/document-viewer-library) is a lightweight document viewer library that supports more than 50 file formats, including Microsoft Office documents, PDFs, images, OpenDocument files, emails and others. Initially, the library was geared towards integration into web apps and websites. Starting from this release, we overcame the boundaries of the “web” prefix and made the viewer available for any type of applications, including desktop and mobile ones! As well as this change, we improved the core engine and the web UI that comes with the library. Check all the new stuff in detail below:

### Open APIThis is probably the most remarkable feature in this release. With an open API for the user interface, you can now build custom applications based on the viewer, irrespective of the platform you work with. In other words, GroupDocs.Viewer for Java can now be smoothly integrated into any web, mobile or desktop app. The new methods don’t require HTTP requests and responses. They are enclosed in the ViewerHandler and you can use them to manage the document view:

*   getImageUrls(Image image) – Get thumbnails and other image files
*   getPrintableHtml(PrintDocument doc) – Get the print document in HTML
*   loadFileBrowserTreeData(FileBrowserTreeData treeData) – Load a tree of files from the base directory
*   viewDocument(ViewDocument viewDocument) – Generate a list of images/pages

### Cache ControlTo help you better maintain your project’s storage space limitations, we’ve implemented the cache size control feature which allows you to set the upper boundary of the cache volume. GroupDocs.Viewer for Java maintains this by removing the oldest data from cache when its size grows beyond the limit. This can be configured with the following method:```
Long com.groupdocs.viewer.config.IBackEndConfiguration.getMaxCacheSize()

```GroupDocs.Viewer for Java uses it to get the cache size limit in megabytes.

### Microsoft Azure Storage SupportIn this release we also implemented an out-of-the-box connector for the Microsoft Azure storage provider. It is represented as a custom input data handler:```
com.groupdocs.viewer.handlers.input.AzureInputDataHandler

```You can use it as any other custom InputDataHandler. Initialize the AzureInputDataHandler instance with the Azure account credentials and GroupDocs.Viewer configuration:```
public AzureInputDataHandler(String accountName, String accoutnKey, ServiceConfiguration config)

```Then apply it to the ViewerHandler on the initialization stage:```
public ViewerHandler(ServiceConfiguration config, InputDataHandler inputDataHandler)

```Or you can set it later in the application using the InputDataHandler's static method:```
public static void setInputDataHandler(InputDataHandler inputDataHandler)

```

### Page PreloadingBy default, GroupDocs.Viewer for Java loads only pages that a user is currently viewing. All subsequent pages of the document are retrieved only when the user scrolls down to them. This behavior is called “lazy-loading” and aims to meet bandwidth limitations. In this release we’ve added the possibility to specify the number of pages that should be preloaded, so that when a user navigates to them they are quickly retrieved from the cache. You can now set pages to be fully loaded on the front-end at the start before they even appear in the viewport.```
public Boolean isPreloadPagesOnBrowserSide()

```The number of pre-loaded pages is controlled with the same method as for the background caching:```
public Integer getPreloadPagesCount()

```

### Tabbed Rendering of Excel SpreadsheetsMicrosoft Excel, ODS and other documents that have several sheets are now rendered with tab controls that allow end users to quickly switch between spreadsheets, just like in native applications.

### New LocalizationsThe UI is now available in English, Norwegian, Polish, Portuguese, Russian and Spanish. Furthermore, the localization functionality is fully adapted to the UTF-8 standard, to make it easy to customize the UI with any additional languages. The new version of the GroupDocs.Viewer for Java library is available for download from our [downloads archive](http://groupdocs.com/Community/files/9/java-libraries/groupdocs_viewer_for_java/entry2958.aspx). Also, please feel free to download our [samples](http://groupdocs.com/Community/files/9/java-libraries/groupdocs_viewer_for_java/category1004.aspx) to explore the Java version of the document viewer quickly. For more detailed installation and usage instructions, please see the [documentation wiki](http://groupdocs.com/docs/display/viewerjava/Home).




