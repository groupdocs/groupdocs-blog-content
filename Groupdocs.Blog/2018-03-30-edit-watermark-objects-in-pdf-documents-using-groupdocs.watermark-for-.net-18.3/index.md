---
title: 'Edit Watermark Objects in PDF Documents using GroupDocs.Watermark for .NET 18.3'
date: Fri, 30 Mar 2018 10:10:15 +0000
draft: false
url: /2018/03/30/edit-watermark-objects-in-pdf-documents-using-groupdocs.watermark-for-.net-18.3/
author: 'Usman Aziz'
summary: ''
tags: ['.NET Watermarking API', 'C# Watermarking API', 'Document Watermarking', 'document-watermark', 'GroupDocs.Watermark for .NET', 'GroupDocs.Watermark for .NET Release']
categories: ['GroupDocs.Watermark Product Family']
---

[![GroupDocs Watermark for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/05/GroupDocs-Watermark-for-.NET_.png)](https://products.groupdocs.com/watermark/net)We are really delighted to announce the release of version 18.3 of [GroupDocs.Watermark for .NET.](https://products.groupdocs.com/watermark/net) The latest version supports editing of the objects that can be considered as the watermark in **PDF** documents. Furthermore, the feature of replacing text and image for the found watermarks is also added for all the supported formats. Following are some highlighted features of version 18.3.

# Editing Watermark Objects in PDF Documents

## Replacing Text for Particular ObjectsYou can replace text for the particular XObjects, artifacts and the annotations in a PDF document. Furthermore, replacing text with formatting is also supported. Following sections demonstrate this feature with code samples.

### Replacing Text```
using (PdfDocument doc = Document.Load(@"D:\xobjects.pdf"))
{
    // Replace text for XObjects
    foreach (PdfXObject xObject in doc.Pages[0].XObjects)
    {
        if (xObject.Text.Contains("Test"))
        {
            xObject.Text = "Passed";
        }
    }
    // Replace text for artifacts
    foreach (PdfArtifact artifact in doc.Pages[0].Artifacts)
    {
        if (artifact.Text.Contains("Test"))
        {
            artifact.Text = "Passed";
        }
    }    

    // Replace text for annotations
    foreach (PdfAnnotation annotation in doc.Pages[0].Annotations)
    {
        if (annotation.Text.Contains("Test"))
        {
            annotation.Text = "Passed";
        }
    }
    doc.Save(@"D:\output.pdf");
}
```

### Replacing Text with Formatting```
using (PdfDocument doc = Document.Load(@"D:\xobjects.pdf"))
{
    // Replace text for XObjects    
    foreach (PdfXObject xObject in doc.Pages[0].XObjects)
    {
        if (xObject.Text.Contains("Test"))
        {
            xObject.FormattedTextFragments.Clear();
            xObject.FormattedTextFragments.Add("Passed", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
        }
    }
    // Replace text for artifacts
    foreach (PdfArtifact artifact in doc.Pages[0].Artifacts)
    {
        if (artifact.Text.Contains("Test"))
        {
            artifact.FormattedTextFragments.Clear();
            artifact.FormattedTextFragments.Add("Passed", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
        }
    }
    // Replace text for annotations
    foreach (PdfAnnotation annotation in doc.Pages[0].Annotations)
    {
        if (annotation.Text.Contains("Test"))
        {
            annotation.FormattedTextFragments.Clear();
            annotation.FormattedTextFragments.Add("Passed", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
        }
    }
    doc.Save(@"D:\output.pdf");
}
```

## Replacing Image for Particular ObjectsThe version 18.3 also supports replacing image for the particular XObjects, artifacts and the annotations as shown in the following code sample.```
using (PdfDocument doc = Document.Load(@"D:\xobjects.pdf"))
{
    // Replace image for XObjects
    foreach (PdfXObject xObject in doc.Pages[0].XObjects)
    {
        if (xObject.Image != null)
        {
            xObject.Image = new PdfWatermarkableImage(File.ReadAllBytes(@"D:\test.png"));
        }
    }
    // Replace image for artifacts
    foreach (PdfArtifact artifact in doc.Pages[0].Artifacts)
    {
        if (artifact.Image != null)
        {
            artifact.Image = new PdfWatermarkableImage(File.ReadAllBytes(@"D:\test.png"));
        }
    }
    // Replace image for annotations
    foreach (PdfAnnotation annotation in doc.Pages[0].Annotations)
    {
        if (annotation.Image != null)
        {
            annotation.Image = new PdfWatermarkableImage(File.ReadAllBytes(@"D:\test.png"));
        }
    }
    doc.Save(@"D:\output.pdf");
}
```

# Replacing Text and Image for Found Watermarks

The latest version allows replacing text and image for the found possible watermarks that we get in a search result. Following sections demonstrate how to replace text and image for the found watermarks.

## Replacing Text```
using (Document doc = Document.Load(@"D:\input.pptx"))
{
    TextSearchCriteria searchCriteria = new TextSearchCriteria("test", false);
    PossibleWatermarkCollection watermarks = doc.FindWatermarks(searchCriteria);
    foreach (PossibleWatermark watermark in watermarks)
    {
        try
        {
            watermark.Text = "passed";
        }
        catch (Exception e)
        {
            // Found entity may not support text editing
            // Passed argument can have inappropriate value
            // Process such cases here
        }
    }
 
    doc.Save(@"D:\output.pptx");
}
```

## Replacing Image```
byte[] imageData = File.ReadAllBytes(@"D:\new_logo.png");
 
using (Document doc = Document.Load(@"D:\input.pdf"))
{
    SearchCriteria searchCriteria = new ImageDctHashSearchCriteria(@"D:\logo.bmp");
    PossibleWatermarkCollection watermarks = doc.FindWatermarks(searchCriteria);
    foreach (PossibleWatermark watermark in watermarks)
    {
        try
        {
            watermark.ImageData = imageData;
        }
        catch (Exception e)
        {
            // Found entity may not support image replacing
            // Passed image can have inappropriate format
            // Process such cases here
        }
    }
 
    doc.Save(@"D:\output.pdf");
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/watermark/net) documentation article.

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Watermark:

*   [Download](https://downloads.groupdocs.com/watermark/net "GroupDocs.Watermark MSI") - MSI Package as well as Zipped DLLs
*   [NuGet](https://www.nuget.org/packages/GroupDocs.Watermark/ "GroupDocs.Watermark Nuget Package") - NuGet Installation
*   [Documentation](https://docs.groupdocs.com/watermark/net "Watermark API documentation") - API Documentation
*   [Examples](https://github.com/groupdocs-watermark/GroupDocs.watermark-for-.NET "How to use Watermark API") - Code Examples
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPusvdhHD52X_Q8bTjObAc9) – YouTube Video Tutorials
*   [Product Support Forum](https://forum.groupdocs.com/c/watermark) - Technical Support Forum for GroupDocs.Watermark

# Feedback

As always, we would love to hear your queries and suggestions at our [forum](https://forum.groupdocs.com/c/watermark "Technical Support Forum").





