---
title: 'Document Viewer 2.0.0 with Image Mode, Page navigation and Zooming Features ASP.NET WebForms Modern UI – GroupDocs.Viewer for .NET'
date: Fri, 08 Dec 2017 17:45:32 +0000
draft: false
url: /2017/12/08/asp.net-webforms-modern-ui-document-viewer-2.0.0-image-mode-paging-zooming-features-groupdocs.viewer-.net/
author: 'Aamir Waseem'
summary: ''
tags: []
categories: ['GroupDocs.Viewer Product Family']
---

[![GroupDocs Viewer for .NET](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/11/groupdocs-viewer-net.png)](http://groupdocs.com/.NET/document-viewer-library)

Today, we are pleased to announce another release of ASP.NET WebForms Modern UI Document Viewer 2.0.0 using [GroupDocs.Viewer for .NET](https://products.groupdocs.com/viewer/NET) version 17.11.0. This release **[v2.0.0](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET-WebForms-App/milestone/1?closed=1)** comes up with new features and improvements to view document in both **HTML** and **Image** representations for different document formats like DOCX, PDF, XLSX, PPTX, MSG with attachments and allow user to **Zoom**, **Navigate to Pages,** set **Watermark** and tools/features configuration options through **JS Parameters** and many [more features](https://docs.groupdocs.com/viewer/net).

Let's have a look at it.

![](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/12/GD-NET-Viewer-Modern-UI-V2.0.png)

We recommend you to [download](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET-WebForms-App/releases/tag/v2.0.0) and explore this new version.

Let's explore new features in more detail.

# Document Image Representation

In addition to document HTML representation now document Image rendering mode is also enabled that allow user to view document as image representation and switching between **Image & HTML** representation is just a click away.

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

 `// Show/Hide Tools ShowWatermark = true; ShowImageToggle = true; ShowZooming = true; ShowRotateImage = true; ShowDownloads = true; ShowFileSelection = true; ShowThubmnailPanel = true; ShowPagingPanel = true; EnableContextMenu = false; // Set Default values DefaultFilePath = 'calibre.docx'; // leave empty to skip default file loading. isImageToggle = false; // set true to display image mode rendering by default. ZoomValue = 100; // integer values, zoom level default value in percentage (%) 5% to 600%. // Set Watermark properties WatermarkText = "my watermark text"; WatermarkColor = 4366342; // integer values represents the ARGB color. WatermarkPosition = 'Diagonal'; // e.g Diagonal, TopLeft, TopCenter, TopRight etc. WatermarkWidth = 70;`

# Download & Open Document as PDF

Download feature enhanced and now allow user to either directly download the document as PDF or open document as PDF in web browser.

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Viewer.

*   [Download](https://downloads.groupdocs.com/viewer/net "Download API") - MSI Package as well as Zipped DLLs
*   [NuGet Package](https://www.nuget.org/packages/GroupDocs.Viewer/ "Install from NuGet Package") - NuGet Install
*   [Documentation](https://docs.groupdocs.com/display/viewernet/Home "Document Viewer API Documentation ") - Product Docs
*   [Forum](https://forum.groupdocs.com/c/viewer "Technical Support Forum") - Technical Support Forum for GroupDocs.Viewer for .NET
*   [Video Tutorials](https://www.youtube.com/channel/UCgO8dwgI5KAsQCVegviVXYA/playlists "GroupDocs.Viewer video tutorials") - YouTube Videos
*   [Example / Plugins](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET "Download example project and front ends") - Github Source Code Examples
*   [ASP.NET Webforms Modern UI](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET-WebForms-App "Open Source Document Viewer Applications") - Open Source **Document Viewer** Applications

# Feedback

We always appreciate and welcome our valuable users to share their feedback to improve this front-end application. We will be happy to know your thoughts and suggestions. Just create a [forum thread](https://forum.groupdocs.com/c/viewer "Technical Support Forum") and our dedicated support team will be there to respond.




