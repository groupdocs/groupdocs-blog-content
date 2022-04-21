---
title: 'Show Tracked Changes in Word Documents using GroupDocs.Viewer for Java 17.5.0'
date: Wed, 10 Jan 2018 06:23:02 +0000
draft: false
url: /2018/01/10/show-tracked-changes-in-word-documents-groupdocs.viewer-for-java-17.5.0/
author: 'Usman Aziz'
summary: ''
tags: ['document rendering API', 'document rendering API for Java', 'document viewer', 'Document viewer API', 'document viewer API for Java', 'Java document viewer API']
categories: ['GroupDocs.Viewer for Java', 'GroupDocs.Viewer for Java Releases', 'GroupDocs.Viewer Product Family']
---

[![Logo Image](http://joomla-groupdocs.dynabic.com/templates/groupdocs/images/product-logos/90x90/groupdocs-viewer-java.png?v2)](http://www.groupdocs.com/products/viewer/java)We are excited to announce the release of version 17.5.0 of [GroupDocs.Viewer for Java](https://products.groupdocs.com/viewer/java). The latest version has come with **9** new features, **16** improvements, and more than **20** bug fixes. Please continue to read more about this major release of GroupDocs.Viewer for Java.

# GroupDocs.Viewer for Java 17.5.0 - New Features

Following are the most notable features of GroupDocs.Viewer for Java 17.5.0.

## Support of New File FormatsWe have added the support of following file formats in this latest release.

*   VSTX and VSSX (Microsoft Visio)
*   ONE (OneNote)
*   DjVu (multi-layer raster image)

## Show/Hide Tracked Changes in Word DocumentWhen rendering a Word document, the API does not provide results with tracked changes. We have added a setting to override the default behavior of the API. If you want to see tracked changes in your rendering result, use **_getWordsOptions.setShowTrackedChanges_** method of RenderOptions (**_ImageOptions_**, **_HtmlOptions_** or **_PdfFileOptions_**) and pass it to corresponding ViewerHandler (_ViewerImageHandler_ or _ViewerHtmlHandler_) as shown in the following code snippet.```
// Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.setStoragePath(STORAGE_PATH);
  
// Create HTML handler
ViewerHtmlHandler htmlHandler = new ViewerHtmlHandler(config);
String guid = "document.docx";
  
// Set options to render tracked changes
HtmlOptions options = new HtmlOptions();
options.getWordsOptions().setShowTrackedChanges(true); // Default value is false
  
// Get pages 
List pages = htmlHandler.getPages(guid, options);
  
for (PageHtml page : pages) {
    System.out.println("Page number: " + page.getPageNumber());
    System.out.println("Html content: " + page.getHtmlContent());
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/java) documentation article.

## Rendering PDF Document Excluding AnnotationsWhen rendering PDF documents, by default, annotations are included in the resultant document. If required, you can tell the API not to include the annotations in the rendering results. Just set **_getPdfOptions.setDeleteAnnotations_** of RenderOptions (**_ImageOptions_**, **_HtmlOptions_** or **_PdfFileOptions_**) as _true _and pass it to _getPages or getPdfFile _method of corresponding ViewerHandler (_ViewerImageHandler_ or _ViewerHtmlHandler_) as shown in the following code snippet.```
// Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.setStoragePath(STORAGE_PATH);
  
// Create HTML handler
ViewerHtmlHandler htmlHandler = new ViewerHtmlHandler(config);
String guid = "DocumentWithAnnotations.pdf";
  
// Set pdf options to render content without annotations
HtmlOptions options = new HtmlOptions();
options.getPdfOptions().setDeleteAnnotations(true); // Default value is false
  
// Get pages
List pages = htmlHandler.getPages(guid, options);
  
for (PageHtml page : pages) {
    System.out.println("Page number: " + page.getPageNumber());
    System.out.println("Html content: " + page.getHtmlContent());
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/java) documentation article.

## Adjusting the Size when Rendering CAD DocumentsWhen CAD documents are rendered, the size of the rendering result is adjusted by API automatically depending on the size of the initial document. You may also adjust the size of resulting document by setting height and width as shown in the following code sample.```
// Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.setStoragePath(STORAGE_PATH);
  
// Create image handler
ViewerImageHandler imageHandler = new ViewerImageHandler(config);
String guid = "document.dwg";
  
// Set Cad options to render content with a specified size
ImageOptions options = new ImageOptions();
options.getCadOptions().setHeight(750);
options.getCadOptions().setWidth(450);
  
// Get pages
List pages = imageHandler.getPages(guid, options);
  
for (PageImage page : pages)
{
    System.out.println("Page number: " + page.getPageNumber());
    InputStream imageContent = page.getStream();
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/java) documentation article.

## Rendering Layouts in CAD DocumentsWhen CAD documents are rendered, by default, you only get the Model's representation. In order to render Model and all non-empty Layouts within a CAD document, set **_getCadOptions().setRenderLayouts_** of _ImageOptions_ and _HtmlOptions_ to _true_ as shown in the following code sample.```
// Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.setStoragePath(STORAGE_PATH);
  
// Create HTML handler
ViewerImageHandler imageHandler = new ViewerImageHandler(config);
String guid = "document.dwg";
  
// Set CAD options to render Model and all non empty Layouts
ImageOptions options = new ImageOptions();
options.getCadOptions().setRenderLayouts(true);
  
// Get pages
List pages = imageHandler.getPages(guid, options);
  
for (PageImage page : pages)
{
    System.out.println("Page number: " + page.getPageNumber());
    InputStream imageContent = page.getStream();
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/java) documentation article.

## Rendering a Specific Layout in a CAD DocumentSince version 17.5.0, GroupDocs.Viewer also allows you to render a specific layout in a CAD document. Following code snippet demonstrates how to render a specific layout by providing its name.```
// Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.setStoragePath(STORAGE_PATH);
  
// Create HTML handler
ViewerImageHandler imageHandler = new ViewerImageHandler(config);
String guid = "document.dwg";
  
// Set CAD options to render specific Layout
ImageOptions options = new ImageOptions();
options.getCadOptions().setLayoutName("MyFirstLayout");
  
// Get pages
List pages = imageHandler.getPages(guid, options);
  
for (PageImage page : pages)
{
    System.out.println("Page number: " + page.getPageNumber());
    InputStream imageContent = page.getStream();
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/java) documentation article.

## Enabling Precise Mode when Rendering PDF DocumentsWhen PDF documents are rendered, we get similar representation in image and HTML formats. However, sometimes the result may contain shifted characters, symbols or document objects. To improve rendering results in such cases, we have added **_pdfOptions.setEnablePreciseRendering_** property as shown in the following sample code.```
// Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.setStoragePath(STORAGE_PATH);
  
// Create HTML handler
ViewerHtmlHandler htmlHandler = new ViewerHtmlHandler(config);
String guid = "document.pdf";
  
// Set pdf options to render content in a precise mode
HtmlOptions options = new HtmlOptions();
options.getPdfOptions().setEnablePreciseRendering(true); // Default value is false
  
// Get pages
List pages = htmlHandler.getPages(guid, options);
  
for (PageHtml page : pages) {
    System.out.println("Page number: " + page.getPageNumber());
    System.out.println("Html content: " + page.getHtmlContent());
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/viewer/java) documentation article.

## Rendering Documents with CommentsSome document types like Microsoft Word, Excel, OpenOffice Text and Spreadsheet may also contain comments. By default, the comments are not rendered. Since the version 17.5.0, there is a new option, **_setRenderComments_** of RenderOptions (**_ImageOptions_** or **_HtmlOptions_**), that tells the API to include the comments in the output. Currently, this option works for Microsoft Word, Excel, OpenOffice Text and Spreadsheet document types. To learn about the usage of this feature, please visit [this](https://docs.groupdocs.com/viewer/java) documentation article.

## Using Metered LicensingSince version 17.5.0, you can also set [Metered](https://docs.groupdocs.com/viewer/java) license as an alternative to license file. It is a new licensing mechanism that will be used along with existing licensing method. It is useful for the customers who want to be billed based on the usage of the API features. For more details, please refer to [Metered Licensing FAQ](https://www.groupdocs.com/corporate/purchase/faqs/metered-faq) section. Following code snippet shows how to set metered public and private keys for licensing.```
Metered metered = new Metered();
// set-up credentials
metered.setMeteredKey("Public_Key", "Private_Key");
```

# GroupDocs.Viewer for Java API - Bug Fixes

Following issues are fixed in the latest version of GroupDocs.Viewer for Java.

*   Color filling isn't displayed for some objects
*   Incorrect font color when rendering Excel to HTML
*   Email attachments are not found when setting setUsePDF to true
*   HTMLSaveOptions.DefaultFont setting doesn't work properly
*   Incomplete image when converting a specific DWG file
*   Character's size issue when rendering PDF document into HTML
*   API is rendering PDF document into blank HTML pages
*   Incorrect resource's relative path when rendering to HTML
*   Black background when rendering PPS or PPT to image
*   Issue in setHtmlResourcePrefix when rendering .msg file
*   Issue with underline text when rendering PDF into HTML
*   setIgnoreResourcePrefixForCss is ignored when rendering Word documents
*   Overflow text is not visible when rendering Excel sheet to HTML
*   PDF to HTML fixed layout issue
*   Lines are too thin when rendering PDF as HTML
*   Pdf to HTML space and positioning issues
*   PDF to HTML image color issue
*   getLastModificationDate is not showing last modification date as expected
*   GroupDocs.Viewer for Java latest JAR file lacks few imports
*   Excel file with blank sheets is not rendering to image
*   ImageOptions is not working as expected
*   PPTX/XLSX documents are not rendering into images properly
*   Duplicate pages are generated in cache if API is used in trial mode
*   Image-based rendering issues
*   Style-sheet link is incorrect if HTML is generated without embedded resources

# Document Rendering API - Improvements

We have made following improvements in GroupDocs.Viewer for Java 17.5.0.

*   Render one or range of worksheets from large excel file
*   Remove obsolete CountPagesToConvert and PageNumbersToConvert from RenderOptions
*   Remove members marked as obsolete in previous versions
*   Do not set resource prefix when HtmlResourcePrefix is empty string
*   Improve look of comments in API reference documentation
*   CellsOptions.ShowGridLines property does not work when rendering Cells to PDF
*   Extend support for setting JpegQuality when rendering documents as PDF
*   Throw GroupDocsViewerException when file type can't be determined for passed stream
*   Create lower-case name when rendering document from stream
*   CustomCacheHandler is written for S3 Bucket but still uses local disk for cache
*   Pdf rendering to HTML taking a lot of time
*   Add code examples to PdfOptions class documentation comments
*   Add code examples to CellsOptions class documentation comments
*   Add code examples to DiagramOptions class documentation comments
*   Add code examples to EmailOptions class documentation comments

# Additional Resources

Following resources will help you to download, learn, try and get technical support.

*   [Product Home](https://products.groupdocs.com/viewer/java) – API Home Page
*   [Download](https://downloads.groupdocs.com/viewer/java "GroupDocs.viewer for Java Downloads") - JAR Files
*   [Documentation](https://docs.groupdocs.com/display/viewerjava/Home) – Product Documentation
*   [Product Support Forum](https://forum.groupdocs.com/c/viewer) – Technical Support Forum for GroupDocs.Viewer
*   [Examples](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-Java) – Source Code Examples
*   [Sample Front End App](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-Java-App) - Open Source **Document Viewer** Application

## FeedbackAs always, you are welcome to share your feedback to improve this product. We will be happy to know your thoughts. Just create a [forum thread](https://forum.groupdocs.com/c/viewer) and our dedicated support team will be there to respond.




