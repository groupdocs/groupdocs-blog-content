---
title: 'GroupDocs.Viewer 2.0 - Enhancements and New Features in the Document Viewer for .NET Library (Part A)'
date: Tue, 20 May 2014 16:38:18 +0000
draft: false
url: /2014/05/20/enhancements-and-new-features-in-the-document-viewer-for-net-library-part-a/
author: 'Denis Gvardionov'
summary: ''
tags: ['document viewer for .net', 'GroupDocs Viewer', 'viewer for .net library', 'zArchive']
---

Greetings!![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/03/GD_VWR_NETIcon_114.png) We're pleased to announce a major update of the [GroupDocs.Viewer for .NET library](http://groupdocs.com/dot-net/document-viewer-library): version 2.0. This version of the document viewer has a lot of new features, improvements and bug fixes. You'll find a complete list of updates and the new library itself [here](http://groupdocs.com/Community/files/8/.net-libraries/groupdocs_viewer_for_.net/entry1177.aspx). In this and the next article, I'd like to take a closer look at the updates that I think you'll be the most interested. So here we go:

### Desktop .NET Document ViewerWithout a doubt, the main new feature is support for non-web-based applications. GroupDocs.Viewer for .NET can now be used in desktop-based WinForms apps that have no relation to ASP.NET and internet. You can create a standalone EXE application, which will be able to display almost all popular document types without requiring any third-party plugins or middleware. We've prepared a couple of short guides that show how to integrate GroupDocs.Viewer into a desktop application:

*   [How to Use the GroupDocs.Viewer WinForms Control](https://docs.groupdocs.com/viewer/net)
*   [Description of the GroupDocs.Viewer WinForms Control Methods](https://docs.groupdocs.com/viewer/net)

### HTML-Based Rendering ModeGroupDocs.Viewer v.2.0 includes a new HTML-based rendering mode, opposite to the default image-based one. The mode is focused on the textual information of the document: all texts from an original document are extracted and then rendered in a browser as real text, not images, while document background is rendered using [SVG vector images](http://en.wikipedia.org/wiki/Scalable_Vector_Graphics). This is completely different from the image-based rendering mode, where documents are rendered to a set of images and parsed text is placed over the images. The feature might be very useful, since when the HTML-based mode is enabled, all text parsed from a document is placed on a web-page directly, so you can perform browser-based search for text within the document. **Please note**, that the image-based mode is enabled by default. In order to switch to the HTML-based one, please set the _.UseHtmlBasedEngine(true)_ method's parameter value to **true**.

### Switching Between PNG and SVG ImagesWhen using the HTML-based rendering mode, GroupDocs.Viewer converts the original document to a combination of HTML markup and SVG images. However, since Internet Explorer 8 and other older browsers don't support SVG, we've supplied the viewer with an additional mode that converts background images to PNG format instead of SVG. Image conversion can be used in conjunction with the HTML-based rendering described earlier. To use PNG images for backgrounds, you just need to invoke the _UseHtmlBasedEngine_ method and set the value of the second optional parameter - _usePngImagesForHtmlBasedEngine_ - to **true**:```
…ViewerClientCode(). … .UseHtmlBasedEngine(true, true)

```

### WatermarksYou can now add text watermarks to any document. For this, use the _Watermark_ method when invoking GroupDocs.Viewer on a web-page (an ASPX page in case of WebForms, or view in case of MVC). This method has two parameters: the first is mandatory and takes the string of text that should be placed on a document. The second is optional and takes the text color. If you omit the second parameter, text is displayed in red. Here is an example:```
…ViewerClientCode(). … .Watermark("text for watermark", Color.Aqua)

```A few notes regarding the feature that can save you time: 1. When added, a text watermark will be presented on every page of the document. You cannot specify which pages should contain the watermark. You also can't place different watermarks on different pages in the same document. 2. Watermarks are only added to web-pages on the client-side. The original documents on the server are not modified. When a user downloads a watermarked document, they receive the original version of the document without any watermarks. 3. Watermarks can't be added to a document when using the HTML-based rendering mode.

### Enabling/Disabling Document Downloading and PrintingWhen a document is displayed in a browser, users can download and print the original file using buttons on the GroupDocs.Viewer’s toolbar. In previous versions of the viewer, you had to replace the default HTTP-handlers with your own to restrict (disable) the printing and downloading options. Such a scenario is described in the following article: [How to Replace HTTP Handlers to Set up User Permissions in the GroupDocs.Viewer for .NET Library](https://docs.groupdocs.com/viewer/net). With the release of version 2.0, you can do the same thing with a single line of code. In particular, the _ClientHelper_ class (available via the _ViewerClientCode_ method) now has two new methods: _ShowDownload_ and _ShowPrint_. Each of these has one Boolean optional parameter. When the parameter value is set to **true** (the default value), users see the **Download** and **Print** buttons and can download or print the original file. When set to **false**, the **Download** and **Print** buttons are hidden and users can't download or print the original document. Of course, you can also enable only one of the options, while keeping the other disabled. For example, the following code:```
…ViewerClientCode(). … .ShowDownload(true).ShowPrint(false)

```allows users to download a document, while restricting printing. Only the **Download** button will be displayed in the toolbar.

### Downloading Documents in PDF FormatIn addition to the standard download option, which allows users to download a document in the original file format, GroupDocs.Viewer for .NET version 2.0 can convert displayed documents to PDF, so that each time users try to download a document, they get a PDF copy of the original file. This feature is powered by our universal document conversion library: [GroupDocs.Conversion for .NET](http://groupdocs.com/dot-net/document-conversion-library). You can find a complete list of document formats that can be converted to PDF on [this page](http://groupdocs.com/dot-net/document-conversion-library/features#allFormats). In order to activate the feature, just invoke the _DownloadPdfFileIfPossible_ method with the _downloadPdfFile_ parameter's value set to **true**:```
…ViewerClientCode(). … .DownloadPdfFileIfPossible(true)

```

### New Layout for Page ThumbnailsIn earlier versions of our .NET document viewer, page thumbnails could only be displayed in the document area. (When clicking on the **Thumbs** button, a thumbnail panel slides over the document. As a result, a part of the document is hidden under the panel.) If this is an issue for your customers, GroupDocs.Viewer version 2.0 allows you to move thumbnails to the left side of the viewport. To do this, invoke the _UseInnerThumbnails_ method and set the value of the use parameter to **true**:```
…ViewerClientCode(). ….UseInnerThumbnails(true)

```

### Extended Stream SupportI've already written a detailed article showing [how to load documents from streams](https://docs.groupdocs.com/viewer/net) with the GroupDocs.Viewer for .NET library. And since we've received a lot of positive feedback and suggestions on this feature, we decided to expand it in version 2.0 as follows:

#### Extended Signature of the Stream MethodThe _ClientHelper_ class' _Stream_ method now has one mandatory and 3 optional parameters. Its signature is as follows:```
public ClientHelper Stream(Stream stream, string fileName = null, string fileExtension = null, string fileDisplayName = null)

```As you can see, only the stream object itself is mandatory, all other parameters have the value **null** by default. Here are their descriptions:

*   _fileName_ - specifies the name of the file that will be created by the GroupDocs.Viewer and stored in the **RootStoragePath** folder. The stream content will be written to this file.
*   _fileExtension_ - specifies the file extension of the document in this stream. If an extension is provided, GroupDocs.Viewer will use it. If it isn't, GroupDocs.Viewer uses its own document type recognition mechanism.
*   _fileDisplayName_ - specifies a file name which will be displayed when a user hits the **Download** or **Print** button.

**Important notice:** the signature of the new _Stream_ method is not compatible with its predecessor in the GroupDocs.Viewer version 1.x.

#### Support for Multiple StreamsOne more improvement - the _Streams_ method with the next signature:```
public ClientHelper Streams(IEnumerable streams)

```As you can see, it receives a set of streams. But before proceeding, let’s look at the _StreamDefinition_ class from the metadata:```
public class StreamDefinition
{
   public StreamDefinition();
   public string FilenameExtension { get; set; }
   public Stream Stream { get; set; }
}

```It is a simple container class for the document that is presented as a stream. It has only two fields: the stream itself and a filename extension. Please note that this class does not implement the [IDisposable](http://msdn.microsoft.com/en-us/library/system.idisposable.aspx) interface so you should take care of stream disposal yourself. Let’s get back to the _Streams_ method. Now you see that it simply obtains a set of streams, and, what is very important when using multiple streams, it will display all of them! In fact, the _Streams_ method makes it possible to display more than one document within the GroupDocs.Viewer UI. Let me show you how:```
ViewerClientCode()
.TargetElementSelector("#test")
…
.Streams
        (
            new List(2)
            {
                new StreamDefinition()
                {
                    FilenameExtension = "pdf",
                    Stream = new FileStream(@"\\doc1.pdf",
FileMode.Open, FileAccess.Read, FileShare.Read)
                },
                new StreamDefinition()
                {
                    FilenameExtension = "docx",
                    Stream = new FileStream(@"\\doc2.docx",
FileMode.Open, FileAccess.Read, FileShare.Read)
                }
            }
        )

```In this example we have two documents, two streams and two _StreamDefinition_ instances. When executing this code, both of the documents are displayed sequentially, one after another! This is it for this article, but not for the new release. I'll publish another post describing the rest of the new functionality and improvements (also very promising) in a few days. Stay in touch!




