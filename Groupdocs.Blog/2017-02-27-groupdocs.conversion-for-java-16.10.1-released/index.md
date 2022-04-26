---
title: 'GroupDocs.Conversion for Java 16.10.1 Implements PSD Conversion'
date: Mon, 27 Feb 2017 11:01:50 +0000
draft: false
url: /2017/02/27/groupdocs.conversion-for-java-16.10.1-released/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Conversion for Java', 'GroupDocs.Conversion Product Family']
---

[![GroupDocs.Conversion](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/09/conversion.png?itok=MpNabR9F)](#)

Team [GroupDocs](http://www.groupdocs.com/) is keen to announce another release of GroupDocs.Conversion for Java 16.10.1. Numerous customers reported bugs are resolved in this release. Moreover, API encompasses multitude of new features. Support of converting documents to and from PSD format is introduced. Using latest version of the API developers can implement multi-thread conversion as well. We would recommend you to download and experience GroupDocs.Conversion for Java 16.10.1 and share your feedback.

## Document Conversion API for Java - Features

*   [Implement document conversion from stream with auto detect source file type](https://docs.groupdocs.com/conversion/java/)
*   Autodetect source document type when converting from stream
*   [Report conversion progress](https://docs.groupdocs.com/conversion/java/)
*   Return all supported conversions types with single method
*   When converting to PDF return each page in separate stream
*   When converting to HTML return each page in separate stream
*   [](https://docs.groupdocs.com/conversion/java/)Place watermark in the converted document
*   [Add support for converting to PSD format](https://docs.groupdocs.com/conversion/java/)
*   [Add support for converting from PSD format](https://docs.groupdocs.com/conversion/java/)
*   [Implement ConversionCompleted event with conversion details](https://docs.groupdocs.com/conversion/java/)
*   [ConversionStart event](https://docs.groupdocs.com/conversion/java/)
*   [Introducing two public interfaces IConversionProgressListener and IConversionStatusListener](https://docs.groupdocs.com/conversion/java/)
*   [Show grid lines when converting Excel files](https://docs.groupdocs.com/conversion/java/)
*   [Show hidden sheets when converting Excel files](https://docs.groupdocs.com/conversion/java/)
*   [Option for removing comments when converting slides documents](https://docs.groupdocs.com/conversion/java/)
*   Implement SVG document conversion
*   Implement XPS document conversion
*   Implement conversion to ICO
*   [Option when converting from Words for show/hide markup and tack changes](https://docs.groupdocs.com/conversion/java/)
*   Html to image conversion
*   Convert from CAD documents to Cells, Html, Image, Pdf, Slides, Words
*   Setting default Fonts
*   Add FixedLayout option to Words to Html conversions
*   Add FixedLayout option to Pdf to Html conversions
*   Implement functionality for convert Project file to multipage Tiff file

## GroupDocs Document Conversion API - Improvements

*   Return conversion guid in ConversionProgressEventArgs

## GroupDocs.Conversion for Java 16.10.1 - Bug Fixes

*   Client Response - In-Proper conversion From PPTX to PDF, Image and Word Document formats
*   Exception when converting from ODP to PPT and PPS
*   While Converting Xlsx file to HTML with HtmlSaveOptions Specific Pages (Sheets) does not work
*   Client Response - HTML to Doc and Docx is not proper for Headings and contents are mixed
*   Client Response - Only first page converts to PNG from TIF file (With and Without License)
*   Client Response - Convert to HTML from Excel, PDF, MS Word overlaps the images AND some of Words with styling
*   Can not find CallBack function to get Conversion Progress for MVC/WebForms Applications
*   Client Respose - Could not open the file stream on azure
*   Client Response - FileType not supported Exceptions are not handled
*   Client Response - Error for Empty Input Documents as Stream for Conversion
*   xlsx to png Object null Reference exception
*   Conversion from XLSX to PNG/JPG/HTML not Working Properly
*   Converted File Name issue in Excel file to PNG
*   Converting large XLS file to image with UsePdf=false is producing blurred images
*   Missing pages when converting XLS file to image with UsePdf=true
*   Excel to PNG/JPG/JPEG Low Image Quality Dpi not effecing
*   PDF to Image conversion - target resolution is not changed when setting Dpi
*   Words to Image conversion - target resolution is not changed when setting Dpi
*   Slides to Image conversion - target resolution is not changed when setting Dpi
*   Tasks to Image conversion - target resolution is not changed when setting Dpi
*   Image to Image conversion - target resolution is not changed when setting Dpi
*   Diagram to Image conversion - target resolution is not changed when setting Dpi
*   Image to Image conversion - target resolution is not changed when setting Dpi
*   Diagram to Image conversion - target resolution is not changed when setting Dpi
*   Txt to Pdf is causing "Unknown format" exception
*   % symbol in the file name trowns an exception
*   Exception in HTML to Excel Conversion
*   Convert Excel from Html - Table with background colour and some html controls are not converted properly
*   Coversion with document as Stream input not working
*   Multithread conversion is not working
*   Unable to convert excel files containing empty sheets
*   Converting excel file to HTML not displaying the entire excel file
*   After conversion can't render first page , throws an error "Out of Memory"
*   Conversion .pptx to .pdf doesn't work with multi-threading
*   Header and footer incorrect rendered after conversion to .html
*   Using resolution parameter together height and width parameters
*   Count pages does not match specified number of pages after conversion
*   Static logger binder warning
*   Converted tiff file has incorrect page count in some TIFF viewers
*   Incorrect converts to png format
*   Conversion Jpg to Png trows an error "LoadingException"
*   Incorrectly resizing documents when converting to image
*   Aspose.Words 15.8.0: Lost text after convert
*   Incorrect order of the documents after merging
*   Output file after CCITT4 compression not rendered well in IBM Viewer and Google viewer
*   Path to image isn't correct after conversion .xls document to .html
*   Image resolution/size is not effecting by changing DPI
*   com.groupdocs.conversion.exception.InternalException: Can't convert to image! for conversion from .xls to multipage .tiff file
*   ConversionHandler not releasing the source file's resource

**Available Channels and Resources** Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Conversion:

*   [API Home](http://www.groupdocs.com/products/conversion/java "Product Home") - GroupDocs.Conversion for Java
*   [Download](http://www.groupdocs.com/downloads/conversion/java "Download API") - GroupDocs.Conversion for Java Download
*   [Documentation](https://docs.groupdocs.com/display/conversionjava/Home "Documentation") - Product Documentation
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-Java "Example projects") - Github source code examples
*   [Product Support Forum](http://groupdocs.com/Community/forums/groupdocs.conversion-product-family/7/showforum.aspx "Support forum") \- Technical Support Forum for GroupDocs.Conversion




