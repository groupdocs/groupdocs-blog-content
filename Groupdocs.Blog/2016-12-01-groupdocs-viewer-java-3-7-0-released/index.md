---
title: 'GroupDocs.Viewer for Java 3.7.0 makes easy to render Email attachments and PDF document with layered content'
date: Thu, 01 Dec 2016 07:22:12 +0000
draft: false
url: /2016/12/01/groupdocs-viewer-java-3-7-0-released/
author: 'Amindsk'
summary: ''
tags: ['GroupDocs Viewer for Java']
categories: ['GroupDocs.Viewer Product Family']
---

[![GroupDocs Viewer for Java](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/05/GD_VWR_JavaIcon_114.png)](http://www.groupdocs.com/products/viewer/java)

Team GroupDocs is excitedly releasing a new version of [GroupDocs.Viewer for Java](http://www.groupdocs.com/products/viewer/java "GroupDocs.Viewer for Java"). Many of the new features have been introduced in GroupDocs.Viewer for Java 3.7.0, such as the rendering of Email attachments and Rendering PDF document with layered content. Some of the important fixes about outstanding issues and improvements have also packed with this release. In order to enable all the rich features in your project please upgrade your document viewer applications with the latest version of the API. For more details, please continue to read on.

## Java Document Viewer API - New FeaturesFollowing features has included in this release of **GroupDocs.Viewer**.

*   [Render Attachment as HTML from Email Document](https://docs.groupdocs.com/viewer/java "GroupDocs.Viewer")
*   Render PDF as Html with layered content
*   Support for hyperlinks referencing a worksheet in the same document
*   Opacity setting for Watermark

See more features [here](https://docs.groupdocs.com/viewer/java "GroupDocs.Viewer features").

## Viewer API - FixesFollowing are the issues that were found in previous versions and are fixed in version 3.7.0.

*   **GetDocumentInfo** Method Throws Exception in Evaluation Mode
*   The **HtmlResourcePrefix {page-number}** is not set in DiagramToHtmlConverter
*   Some characters are not showing in correct format when render as HTML
*   **System.OutOfMemoryException** thrown while rendering as image
*   Only first frame or tiff document converted in image mode
*   MSG file is not rendering properly
*   Failed to get document information in image mode with text from epub document
*   Failed to get document information in image mode with text in trial
*   File description document type format is Unknown when extension is upper case
*   Small images are not visible in image mode
*   **Invalid parameter exception** while converting mpt to image
*   File is corrupted or **damaged exception** while converting mpt document to image
*   **Project reading exception** in multithreading environment
*   **GetPdfFile** returns all pages in trial mode
*   **JpegQuality** is not applied for watermarked images
*   Incorrect Rendering of Excel File into Html and Image
*   **GetPages** for Email Attachment Throws **Path Exception** for Relative Storage Path
*   **Invalid Parameter Exception** in Html Rendering
*   **GetPages** Throws Exception In Case of Stream Object
*   Failed to load xps document in image mode with pdf
*   API Renders First Sheet Twice in Excel Workbook
*   Incorrect Spacing between Characters in Html Rendering
*   Cannot add page to pdf document
*   **OutOfMemoryException** raised when total readed file size reached upto 250MB
*   The operation is not supported error raised when loading epub document
*   **IOException** is raised when try to move a loaded document(into the viewer) to any other directory
*   Cell shading is not applied uniformly while converting spreadsheet to HTML
*   Ott file stream detects as ods file format
*   **GetDocumentInfo** Throws **Parameter is not valid Exception**
*   Excel file is not properly rendering into HTML
*   Header contents of Word document are not appearing in rendered html or images
*   Exception generated while calling **handler.getDocumentInfo(guid)**
*   Exception when calling **GetPdfFile/RotatePage/ReorderPage** with guid without extension
*   Incorrect watermark position and text in PDF file
*   **Out Of Memory Exception** While Rendering Excel File into HTML
*   The bookmark range is invalid for .docx
*   Text document format detected as Unknown
*   **GetPages** Method Throws "Parameter is not valid" Exception
*   Output html contains garbled characters and few characters are merged
*   **GetPages** throws exception for email attachments
*   API throws exception in Mono
*   User can't catch **GroupDocsException**
*   Html watermark style block contains garbage characters.
*   Watermark is Rendered Incorrectly in Html Representation
*   Wmf file dimmensions are different from dimmensions in the MS Paint.
*   TeX to Html conversion error
*   Incorrect Rendering of PDF Document into Image
*   The output pdf file contains black pages instead of content when converting djvu to pdf.
*   Slanting line does not appear in html rendering
*   **DefaultRegularFont** setting doesn't work properly
*   Specific pdf document can't be saved as HTML
*   Exception when converting document to html after cleanup
*   Some characters not displayed when render HTML or PNG
*   Different HTML generated for the same document
*   Outlines are rendered incorrectly in HTML
*   Some text extracted from document twice
*   Text is shifted and duplicated in a PDF produced from VSD
*   Diagram file rendering regression
*   Incorrect saving XLSX to HTML
*   Text coordinates are incorrect for a specific document
*   Not all content of the Visio file is stored when converting to the PDF

## Document Viewer API - ImprovementsFollowing features are improved in the latest version of **document viewer API for Java**.

*   The GroupDocs.Viewer 3.x is slower than 2.19 in performance
*   Update DocumentInfoOptions Cells/Words/Email DocumentInfoOptions properties names and types
*   Remove duplicated document name header in Project document converted to html
*   Deprecated border in html that was converted from words document
*   Implement adding prefix to font-family property if it can be overriden
*   Added transparent watermarking in html mode
*   Improve performance of extracting document information in image mode
*   Apply HtmlResourcePrefix to fonts mentioned in css files
*   Load document only when not cached
*   Changed temp files folder structure
*   Faster Processing remote files by Uri
*   New RotatePage method that returns void
*   Better API performance
*   Applying watermark more quickly
*   Brushed up get pdf file performance
*   Enhanced GetPdfFile method usability
*   Boost Words files to html rendering speed
*   Applied saving file data separately based on options
*   Converters resources can be released now
*   Changed applying pdf document transformations
*   Ability to set the encoding standard automatically
*   No more GetDocumentInfo method response
*   Detach XHTML xmlns attribute
*   Cleanup html markup for Cells documents
*   Convert Pdf Dynamic XFA Form to Standard AcroForm
*   Mark CachedPageDescription redundant constructor as Obsolete
*   Save html resources to cache without saving them to local disc.
*   Implement GetPdfFile from stream or remote file
*   Hide the hidden sheets for .xls file
*   A document page can be converted to JPEG in about 0.1 second
*   Links for mail attachments

## Related Links and ResourcesHere are a few channels and resources for you to download, learn, try and get technical support on **document viewer API**:

*   [Download](http://downloads.groupdocs.com/viewer/java "Download API") - JAR
*   [Documentation](https://docs.groupdocs.com/viewer/java "Document Viewer API Documentation ") - Product Docs
*   [Forum](http://groupdocs.com/Community/forums/groupdocs.viewer-product-family/4/showforum.aspx "Technical Support Forum") - Technical Support Forum
*   [Example / Plugins](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-Java "download example project and front ends") - Github Source Code Examples
*   [Sample Front Ends](https://github.com/groupdocs-viewer "Open Source Document Viewer Applications") - Open Source **Document Viewer** Applications
*   [Document Viewer API Tutorials](https://www.youtube.com/channel/UCgO8dwgI5KAsQCVegviVXYA "video tutorials") - YouTube Tutorials

## FeedbackAs always, we shall be happy to know your thoughts. Just create a [forum thread](http://groupdocs.com/Community/forums/groupdocs.viewer-product-family/4/showforum.aspx "Technical Support Forum") to share your issues or suggestions with us.




