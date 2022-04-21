---
title: 'Simple JSP Front End example for GroupDocs.Viewer for Java users'
date: Mon, 31 Oct 2016 11:49:53 +0000
draft: false
url: /2016/10/31/groupdocs-viewer-java-jsp-frontend/
author: 'Amindsk'
summary: ''
tags: []
categories: ['GroupDocs.Viewer Product Family']
---

[![GroupDocs Annotation logo](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/05/GD_VWR_JavaIcon_114.png)](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/05/GD_VWR_JavaIcon_114.png) We are excited to announce a simple front-end for [GroupDocs.Viewer for Java](http://www.groupdocs.com/java/document-viewer-library) API so newbies can start using it quickly, instead of learning the rich features and complexities provided in [GroupDocs.Viewer for Java using Struts2](https://github.com/groupdocs-viewer/) or [GroupDocs.Viewer for Java Using Servlets](https://github.com/groupdocs-viewer/).

Simplicity comes with many advantages and disadvantages. JSP front-end is a minimum implementation and demonstrates how simple it is to get started with GroupDocs.Viewer for Java. This removes features some useful features, like the user cannot download the document, cannot print, zoom, etc. It just renders the document into HTML, SVG and CSS to make them display on the browser.

# JSP-based Front-end

The application contains single JSP page, that creates a UI, and a Java class which is a wrapper for GroupDocs.Viewer for Java API. The following features have been removed:

*   Thumbnails
*   Page Zooming
*   Document Downloading
*   Document Printing
*   File Browser
*   Watermark
*   Ajax-based Document Navigation

### Supported Formats

Widely used document formats for viewer are Word Document Formats (DOC, DOCM, DOCX, DOT, DOTX, DOTM), Excel Document Formats (XLS, XLSX, XLSM, XLSB), Presentation Document Formats (PPT, PPTX, PPS, PPSX), and Portable Document Formats (PDF) documents.

### Pre-requisitesIn order to run GroupDocs.Viewer for Java JSP Front-end you’ll need:

*   [Java Development Kit 7](http://www.oracle.com/technetwork/java/javase/downloads/index.html)
*   [Maven 3](https://maven.apache.org/download.cgi)
*   Any modern web browser like Mozilla Firefox, Google Chrome, Safari

### Running the applicationFollowing steps should be followed in order to run GroupDocs.Viewer for Java JSP Front-end:

*   Navigate to the project directory
*   Copy your desired file to `storage` folder
*   Set the filename in `index.jsp`
*   Using command prompt and run `mvn jetty:run` command.
*   Navigate to http://localhost:8080/ in your web browser.

### Available Channels and Resources

Find more channels and resources to download, learn, try and get technical support on **GroupDocs.Viewer for Java:**

*   [Product Home](http://www.groupdocs.com/java/document-viewer-library) - GroupDocs.Viewer for Java.
*   [Documentation](http://www.groupdocs.com/docs/display/viewerjava/Home) - Product Documentations.
*   [Product Support Forum](http://groupdocs.com/Community/forums/groupdocs.viewer-product-family/4/showforum.aspx) - Technical Support Forum for GroupDocs.Viewer.
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-Java) - Github source code examples.

## FeedbackAs always, you are welcome to share your feedback to improve this product. We will be happy to know your thoughts. Just create a [forum thread](http://groupdocs.com/Community/forums/groupdocs.viewer-product-family/4/showforum.aspx) and our dedicated support team will be there to respond.




