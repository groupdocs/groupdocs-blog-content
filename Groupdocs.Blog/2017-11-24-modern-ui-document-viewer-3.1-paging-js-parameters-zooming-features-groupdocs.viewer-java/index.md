---
title: 'Modern UI Document Viewer 3.1 with Paging JS Parameters and Zooming Features - GroupDocs.Viewer for Java'
date: Fri, 24 Nov 2017 11:43:51 +0000
draft: false
url: /2017/11/24/modern-ui-document-viewer-3.1-paging-js-parameters-zooming-features-groupdocs.viewer-java/
author: 'Aamir Waseem'
summary: ''
tags: []
categories: ['GroupDocs.Viewer Product Family']
---

[![GroupDocs Viewer for Java](http://joomla-groupdocs.dynabic.com/templates/groupdocs/images/product-logos/90x90/groupdocs-viewer-java.png?v2)](http://groupdocs.com/java/document-viewer-library)

Today, we are pleased to announce another release of Java Modern UI Document Viewer 3.1.0 using [GroupDocs.Viewer for Java](https://products.groupdocs.com/viewer/java) version 17.2.0. This release **v3.1.0** comes up with new features and improvements to view document in both **HTML** and **Image** representations for different document formats like DOCX, PDF, XLSX, PPTX, MSG with attachments and allow user to **Zoom**, **Navigate to Pages,** set **Watermark** and tools/features configuration options through **JS Parameters** and many [more features](https://docs.groupdocs.com/viewer/java).

Let's have a look at it.

![](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/11/GD-NET-Viewer-Modern-UI-V3.1.png)

We recommend you to [download](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-Java-App/releases/tag/v3.1.0) and explore this new version.

Let's explore new features in more detail.

# Page Navigation for HTML & Image View

Paging feature is enabled for both HTML & Image mode rendering and now user can navigate to pages as:

*   Move to First Page.
*   Move to Last Page.
*   Move to Next Page.
*   Move to Previous Page.
*   Go to User Entered Page.

# Zooming for HTML & Image View

Zooming feature is now fully enabled and enhanced for **both HTML & Image** mode rendering and now user can zoom as:

*   Zoom- In.
*   Zoom-Out.
*   Zoom by Level.

# Show/Hide & Configure Tools from JS Parameters

User can now show or hide any available tools from JS/JavaScript parameters by simply passing "true" or "false" value, this JS parameters options enable user to control the default configuration values such as **Default File** selection,  **Watermark Properties** (watermark text, color, angle and opacity level), **Default Zoom Level** and default document **Rendering Mode** (Image or HTML) view etc.

Let’s have a look at these JS parameters those can be set directly from Index view.

 `// Show/Hide Tools ShowWatermark = true; ShowImageToggle = true; ShowZooming = true; ShowRotateImage = true; ShowDownloads = true; ShowFileSelection = true; ShowThubmnailPanel = true; ShowPagingPanel = true; EnableContextMenu = false; // Set Default values DefaultFilePath = 'calibre.docx'; // leave empty to skip default file loading. isImageToggle = false; // set true to display image mode rendering by default. RotateAngel = 0; // integer value e.g 0 or 90 or 180 or 270. ZoomValue = 100; // integer values, zoom level default value in percentage (%) 5% to 600%. // Set Watermark properties WatermarkText = "my watermark text"; WatermarkColor = 4366342; // integer values represents the ARGB color. WatermarkPosition = 'Diagonal'; // e.g Diagonal, TopLeft, TopCenter, TopRight etc. WatermarkWidth = 70;`

# Download & Open Document as PDF

Download feature enhanced and now allow user to either directly download the document as PDF or open document as PDF in web browser.

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Viewer.

*   [Download](https://downloads.groupdocs.com/viewer/java "Download API") - API Package
*   [Documentation](https://docs.groupdocs.com/display/viewerjava/Home "Document Viewer API Documentation ") - Product Docs
*   [Forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum") - Technical Support Forum for GroupDocs.Viewer for Java
*   [Example](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-Java "Download example project and front ends") - Github Source Code Examples
*   [Sample Front Ends](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-Java-App "Open Source Document Viewer Applications") - Open Source **Document Viewer** Applications

# Feedback

We always appreciate and welcome to our valuable users to share their feedback to improve this front-end application. We will be happy to know your thoughts and suggestions. Just create a [forum thread](https://forum.groupdocs.com/c/viewer "Technical Support Forum") and our dedicated support team will be there to respond.




