---
title: 'Partial Rendering of Large Excel Sheets are Supported in GroupDocs.Viewer for Java 17.2.0'
date: Tue, 25 Apr 2017 12:07:03 +0000
draft: false
url: /2017/04/25/partial-rendering-large-excel-sheets-supported-groupdocs.viewer-java-17.2.0/
author: 'Atir Tahir'
summary: ''
tags: ['GroupDoccs.Viewer for Java']
categories: ['GroupDocs.Viewer Product Family']
---

[![Logo Image](http://joomla-groupdocs.dynabic.com/templates/groupdocs/images/product-logos/90x90/groupdocs-viewer-java.png?v2)](http://www.groupdocs.com/products/viewer/java) We are pleased to announce another monthly release of **GroupDocs.Viewer for Java 17.2.0**. Numerous customers reported bugs are resolved in this release. Furthermore, API comes with multitude of improvements and new features such as implementation of settings to prevent glyph grouping when rendering PDF documents. We'd recommend you to download latest version of the API and share your valuable feedback.

## GroupDocs.Viewer for Java 17.2.0 - New Features

*   [Mobi format support](https://docs.groupdocs.com/display/viewerjava/Supported+Document+Formats)
*   Ability to set default font when rendering Email documents
*   [Add OTP format support](https://docs.groupdocs.com/display/viewerjava/Supported+Document+Formats)
*   [OTS format support](https://docs.groupdocs.com/display/viewerjava/Supported+Document+Formats)
*   WebP file format support
*   [Implement setting to prevent glyphs grouping when rendering pdf documents](https://docs.groupdocs.com/viewer/java)
*   [Partial rendering of large Excel sheets in HTML mode](https://docs.groupdocs.com/viewer/java)
*   Implement parameterless ViewerHtmlHandler and ViewerImageHandler constructors
*   Add possibility to configurate ViewerConfig class via app.config or web.config file
*   Rendering password-protected MPP(2003) files
*   [LaTeX file format support](https://docs.groupdocs.com/display/viewerjava/Supported+Document+Formats)

## Document Rendering API - Improvements

*   Remove embedded audios from presentation
*   Improve public API of ViewerConfig class
*   Improve rendering CAD (dwg, dxf) documents to Pdf
*   Improve public API of IInputDataHandler interface
*   Display HTML pages of two different documents in the same page in browser without overriding css classes
*   Use current directory when storage path is not specified
*   Implement responsive html output for Slides documents
*   Implement setting to configure content ordering in resultant html document
*   Improve Email documents rendering
*   Implement saving fonts and styles separately when converting Words to Html
*   Add {resource-name} pattern to HtmlOptions.HtmlResourcePrefix
*   Add CountPagesToRender and PageNumbersToRender properties to RenderOptions class
*   Implement IDisposable for container classes
*   Implement setting which allows render pdf document layers separately
*   Add code examples to documentation comments

## GroupDocs.Viewer for Java API - Bug Fixes

*   Invalid rendering of DWG file into Image or HTML
*   GetDocumentInfo() method is throwing exception
*   Failed to load XPS file in evaluation mode
*   Dwg document is rendered into small image
*   Invalid rendering of DWG file into HTML and Image
*   SheetRender.GetPageSize throws an exception when sheet is empty
*   FormattedText does not return TextWidth for Japanese characters
*   The background is missed for IE 11
*   Special characters like accents, umlauts and circumflex are displayed incorrectly when saving specific PDF to HTML
*   A ligature is shown incorrectly in HTML produced from PDF
*   Invalid characters while rendering Word document into HTML
*   Throws unsupported file format exception when loading specific doc file
*   Getting exception "File type 'doc' is not supported"
*   Parameter is not valid exception when rendering xlsx to image
*   Extra blank page created when convering dwg to pdf
*   Failed to convert wmf file to image in Asp.Net application
*   Incorrect Rendering of Radio Buttons, Checkboxes and their Label into Html
*   No text when converting Pdf to Html with FontAbsorber
*   Different exception messages for password encrypted Word document
*   Failed to load SAI image
*   Large scrollbars when viewing pdf converted to html with embedded resources in IE Edge
*   IE Edge displays large scrollbars for generated HTML
*   Failed to load Tex file from stream
*   Failed to load XCF file
*   Position of graph lines is not correct in output HTML or image file
*   Printing Radio Buttons from HTML page
*   Links are converted into plain text when converting PDF to HTML
*   Merged cells in xlsx are not displayed as merged in html
*   Alignment of radio button text and checkbox text is not proper
*   Jumbling words when rendering PDF document to HTML
*   Creates only one page in text(txt) document
*   Radio buttons are not showing as 'selected' or 'checked' when converting to fixed html
*   Radio buttons are not showing as 'selected' or 'checked'
*   Missing characters, invalid formating when saving to html
*   Incorrect conversion from DOCX to PDF
*   Header-links in PDF files do not work
*   Input stream must be FileStream exception when loading Tex file from stream
*   Getting GroupDocs.Foundation Dependency Exception in SharePoint 2013
*   Background image is missing when converting to image
*   Text and text alignment is messed up in 01\_the\_manure\_tool\_baltic\_20131215\_incl\_logo.xlsx
*   A lot of temporary files with name ASPOSE\_24\_14xxx are created in temp folder
*   Fields are duplicated in fd.xml file
*   Exception is thrown by the API when an XLSX file is queried for info using com.groupdocs.viewer.handler.ViewerHandler.getDocumentInfo
*   Exception when getPages is accessed from multiple threads
*   PDF to HTML rendering generates an exception
*   Attachments present in MSG files are not rendering to HTML
*   EML and MSG files are not properly rendering to HTML and Images
*   ODS files/documents are not rendering to HTML and Images
*   FileData is not serializable
*   Doesn't viewed .doc file
*   Text loss on to HTML conversion
*   Appends null at the end of the path for resources HTML
*   EPUB document loading issue

## Additional ResourcesFollowing resources will help you to download, learn, try and get technical support.

*   [Product Home](http://www.groupdocs.com/products/viewer/java) – GroupDocs.Viewer for Java.
*   [Download](https://downloads.groupdocs.com/viewer/java "GroupDocs.viewer for Java Downloads") - JAR Files
*   [Documentation](http://www.groupdocs.com/docs/display/viewerjava/Home) – Product Documentations.
*   [Product Support Forum](http://groupdocs.com/Community/forums/groupdocs.viewer-product-family/4/showforum.aspx) – Technical Support Forum for GroupDocs.Viewer.
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-Java) – Github source code examples.

## FeedbackAs always, you are welcome to share your feedback to improve this product. We will be happy to know your thoughts. Just create a [forum thread](http://groupdocs.com/Community/forums/groupdocs.viewer-product-family/4/showforum.aspx) and our dedicated support team will be there to respond.




