---
title: 'Edit Watermark Objects in Word Documents using GroupDocs.Watermark for .NET 18.2'
date: Wed, 07 Feb 2018 14:45:49 +0000
draft: false
url: /2018/02/07/edit-watermark-objects-in-word-documents-groupdocs.watermark-for-.net-18.2/
author: 'Usman Aziz'
summary: ''
tags: ['.NET Watermarking API', 'C# Watermarking API', 'Document Watermarking', 'document-watermark', 'Watermarking API C#', 'Watermarking API for .NET']
categories: ['GroupDocs.Watermark for .NET Release', 'GroupDocs.Watermark Product Family']
---

[![GroupDocs Watermark for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/05/GroupDocs-Watermark-for-.NET_.png)](https://products.groupdocs.com/watermark/net)We are pleased to announce the release of version 18.2 of [GroupDocs.Watermark for .NET.](https://products.groupdocs.com/watermark/net) The latest version allows you to edit the objects that can be considered as watermark in **Word** documents. Following are the features that are introduced in GroupDocs.Watermark for .NET 18.2.

# Editing Watermark Objects in Word Documents

## Replacing text for particular shapesWe have added the support of replacing text for particular shapes in a Word document. Following code sample shows how to use this feature.```
using (WordsDocument doc = Document.Load(@"D:\input.docx"))
{
    foreach (WordsShape shape in doc.Sections[0].Shapes)
    {
        if (shape.Text.Contains("Some text"))
        {
            shape.Text = "Another text";
        }
    }
    doc.Save(@"D:\output.docx");
}
```

## Replacing shape's text with formattingUsing GroupDocs.Watermark for .NET 18.2, you can replace the text of the shapes with formatted text by specifying font family, font size, font style, font color etc.. Following code sample shows how to replace shape's text with formatted text.```
using (WordsDocument doc = Document.Load(@"D:\input.docx"))
{
    foreach (WordsShape shape in doc.Sections[0].Shapes)
    {
        if (shape.Text.Contains("Some text"))
        {
            shape.FormattedTextFragments.Clear();
            shape.FormattedTextFragments.Add("Another text", new Font("Calibri", 19, FontStyle.Bold), Color.Red, Color.Aqua);
        }
    }
    doc.Save(@"D:\output.docx");
}
```

## Replacing shape's imageIn version 18.2, we have also added the feature of replacing image of the shape in a Word document. Following code sample shows how to set the image of a shape.```
using (WordsDocument doc = Document.Load(@"D:\input.doc"))
{
    foreach (WordsShape shape in doc.Sections[0].Shapes)
    {
        if (shape.Image != null)
        {
            shape.Image = new WordsWatermarkableImage(File.ReadAllBytes(@"D:\test.png"));
        }
    }
    doc.Save(@"D:\output.doc");
}
```

## Modifying shape's propertiesUsing version 18.2, you can also modify the properties of a shape in Word documents. The following code sample shows the properties that can be modified using GroupDocs.Watermark.```
using (WordsDocument doc = Document.Load(@"D:\input.docx"))
{
    foreach (WordsShape shape in doc.Sections[0].Shapes)
    {
        if (shape.Text.Contains("Some text"))
        {
            shape.AlternativeText = "watermark";
            shape.RotateAngle = 30;
            shape.X = 200;
            shape.Y = 200;
            shape.Height = 100;
            shape.Width = 400;
            shape.BehindText = false;
        }
    }
    doc.Save(@"D:\output.docx");
}
```

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Watermark:

*   [Download](https://downloads.groupdocs.com/watermark/net "GroupDocs.Watermark MSI") - MSI Package as well as Zipped DLLs
*   [NuGet](https://www.nuget.org/packages/GroupDocs.Watermark/ "GroupDocs.Watermark Nuget Package") - NuGet Install
*   [Documentation](https://docs.groupdocs.com/watermark/net "Watermark API documentation") - API Documentation
*   [Examples](https://github.com/groupdocs-watermark/GroupDocs.watermark-for-.NET "How to use Watermark API") - Code Examples
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPusvdhHD52X_Q8bTjObAc9) – YouTube Video Tutorials
*   [Product Support Forum](https://forum.groupdocs.com/c/watermark) - Technical Support Forum for GroupDocs.Watermark

# Feedback

As always, we would love to hear your queries and suggestions at our [forum](https://forum.groupdocs.com/c/watermark "Technical Support Forum").




