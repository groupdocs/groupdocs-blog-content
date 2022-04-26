---
title: 'GroupDocs.Viewer for .NET Library Version 2.8.0 - New Page Layout, Smoother Scrolling and Enhanced Document Sharing Security'
date: Mon, 23 Feb 2015 17:13:09 +0000
draft: false
url: /2015/02/23/groupdocs-viewer-for-net-library-version-2-8-0-new-page-layout-smoother-scrolling-enhanced-document-sharing-security/
author: 'Denis Gvardionov'
summary: ''
tags: ['.net library', 'GroupDocs Viewer', 'release notes', 'zArchive']
---

[![GroupDocs.Viewer for .NET](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/04/GD_VWR_NETIcon_114.png)](https://docs.groupdocs.com/viewer/net)Recently we’ve updated our [GroupDocs.Viewer for .NET library](https://docs.groupdocs.com/viewer/net) up to the version 2.8.0. In this post I’d like to discover some of the most remarkable updates implemented in this latest version:

### New Page Layout OptionsSo far, when viewing documents, you had the following page layout options:

*   **Scroll view** – pages are placed in a continuous chain, one after another.
*   **One page in a row** – one page fit to client’s screen. No page turn animation.
*   **Double page flip** – two adjacent pages fit to client’s screen, plus flipping page animation (available in the image-based rendering mode only).

Starting with this new version, you have a choice between two more options:

*   **Two pages in a row** - two adjacent pages fit to client’s screen. No flipping page animation. This layout is available in both the images-based and the HTML-based rendering modes. This layout is especially useful when viewing documents on a widescreen display, as it allows users to cover unused screen space appearing when viewing documents with the scroll view or one page in a row layout.
*   One more layout added in this release is actually a modification of the above one – **a cover and then two pages in a row**. This is useful when reading books, as the cover page can be placed apart from the subsequent adjacent pages.

All the options can be configured by end users on their own, straight from the viewer’s GUI. You can also set a default layout using the Layout method from the GroupDocs.Viewer widget. This method accepts a Groupdocs.Web.UI.ViewerMode enumeration, which has the following values: ScrollView, DoublePageFlip, OnePageInRow, TwoPagesInRow, CoverThenTwoPagesInRow.

### Italian LocalizationThe geography of clients using the viewer grows rapidly. This time we have good news for our customers from Italy – an Italian GUI localization has been finally added in this build. The following are all GUI localizations currently available:

*   ar-AE - Arabic (U.A.E.)
*   en-US - American English, the default
*   es-ES - Spanish
*   it-IT - Italian (Standard)
*   nb-NO - Norwegian
*   pl-PL - Polish
*   pt-PT - Portuguese
*   ru-RU – Russian

The default localization is **en-US**. You can change it to any other from the list above by using the Locale method from the GroupDocs.Viewer widget. There are two overloads of this method: the first one accepts the needed locale as a string code, while the second one accepts an enumeration value. They are completely equal, so you can use any of them.

### Virtual ScrollingThe new virtual scrolling feature improves page scrolling speed in client browsers. This is useful when displaying large documents of more than 1k pages. When enabled, the viewer streams to the DOM tree only the pages that are currently visible in the browser. New pages are added to the DOM only when the document is actually scrolled to those exact pages. This way, instead of rendering all document pages, the viewer needs to handle only a few pages at a time. An accompanying effect of this feature is the ability to get rid of the "_Script hanging_" message, which occasionally appears when opening or closing large documents (>1k pages). The message was caused by the JavaScript code used to render wrappers for each individual page within a document, or when deleting the wrappers upon switching to another document. To enable the virtual scrolling feature, you should apply the **true** Boolean value for the UseVirtualScrolling method in the GroupDocs.Viewer widget. When set to **false**, the virtual scrolling feature is off.

### Faster Word Documents RenderingA new parameter has been added – embedImagesIntoHtmlForWordFiles – to the UseHtmlBasedEngine method. When set to **true**, it forces the viewer to convert documents to HTML with SVG or raster images embedded straight into the HTML markup as Base64. Otherwise, images are stored as external files. Embedding images into the HTML markup significantly increases browsers’ rendering speed of Word documents that have a lot of images in them. Naturally, this parameter is available only in the HTML-based rendering mode.

### Share Documents with WatermarksNow you can let viewers to print or download a PDF copy of the original documents you share, along with watermarks burned in. This is useful when you want to prevent users from copying your content, while still need to share it with others. When enabled, viewers can print or download only a PDF copy of your original document with your custom watermarks in them. While viewers get a PDF copy with watermarks, your original documents stored on the server stay intact. In order to enable this feature, you should apply watermarks, using the Watermark method from the GroupDocs.Viewer widget, and set the **true** value for the last parameter - printWithWatermark. Please note that this feature is disabled by default! You need to set it explicitly.

### Other Enhancements

*   Added an XML documentation file (called **Groupdocs.Viewer.XML**) into installers to enable IntelliSense in Visual Studio.
*   A new SupportListOfContentControls option added. It allows you to display content controls with their headers, similar to what Microsoft Word does. Currently this option is available only in the HTML-based rendering mode.
*   Numerous code optimizations and bug fixes.

The new version of the GroupDocs.Viewer for .NET library is already available in our files archive, so you are welcome to [download it](http://groupdocs.com/Community/getting-started/dot-net/document-viewer-library.aspx), test it and report any issues or suggestions in our [forum](http://groupdocs.com/Community/forums/groupdocs.viewer-product-family/4/showforum.aspx).




