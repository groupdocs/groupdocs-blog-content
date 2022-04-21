---
title: 'Skip Unreadable Characters During Watermark Search using GroupDocs.Watermark for .NET 18.8'
date: Mon, 20 Aug 2018 06:19:05 +0000
draft: false
url: /2018/08/20/skip-unreadable-characters-during-watermark-search-using-groupdocs.watermark-for-.net-18.8/
author: 'Usman Aziz'
summary: ''
tags: ['.NET Watermarking API', 'Document Watermarking', 'Watermarking API C#']
categories: ['GroupDocs.Watermark for .NET', 'GroupDocs.Watermark for .NET Release', 'GroupDocs.Watermark Product Family']
---

[![GroupDocs Watermark for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/05/GroupDocs-Watermark-for-.NET_.png)](https://products.groupdocs.com/watermark/net)We are delighted to announce the release of version 18.8 of [GroupDocs.Watermark for .NET](https://products.groupdocs.com/watermark/net). The latest version allows skipping unreadable characters during text watermark search. Furthermore, we have also added a new feature to strengthen protection of text watermark in presentation documents. Please continue to read more about the new features, enhancements and bug fixes added in version 18.8.

# Features Introduced

## Skipping Unreadable Characters During Text Watermark SearchThis feature allows finding text watermark even if it contains unreadable characters between the letters. The following code sample shows how to skip unreadable characters when searching for the watermark.```
string inputFileName = @"d:\input.pptx";
  
using (SlidesDocument document = Document.Load(inputFileName))
{
    string watermarkText = "Company name";
    TextSearchCriteria criterion = new TextSearchCriteria(watermarkText);
  
    // Enabling skipping of unreadable characters
    criterion.SkipUnreadableCharacters = true;
  
    PossibleWatermarkCollection result = document.FindWatermarks(criterion);
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/watermark/net) documentation article.

## Protecting Text Watermark in Presentation DocumentsThis feature allows strengthening the protection of text watermark. Using unreadable characters in the watermark text forbids its modification using Find and Replace dialog. The following code sample shows how to include unreadable characters in watermark text.```
string inputFileName = @"d:\input.pptx";
string outputFileName = @"d:\output.pptx";
  
using (SlidesDocument document = Document.Load(inputFileName))
{
    TextWatermark watermark = new TextWatermark("Watermark text", new Font("Arial", 19));
    
    // Include unreadable characters
    SlidesShapeSettings settings = new SlidesShapeSettings();
    settings.IsLocked = true;
    settings.ProtectWithUnreadableCharacters = true;
  
    // Add wattermark
    document.AddWatermark(watermark, settings);
  
    // Save document
    document.Save(outputFileName);
}
```For more details on this feature, please visit [this](https://docs.groupdocs.com/watermark/net) documentation article.

# Enhancements

## Support of SmartArt and CustomXml Drawing Types in Spreadsheet DocumentsThe current version of GroupDocs.Watermark allows finding and removing SmartArt and CustomXml shape types from the worksheet as shown in the following code sample.```
string inputFileName = @"G:\Input.xlsx";
string outputFileName = @"G:\Output.xlsx";
   
using (CellsDocument document = Document.Load(inputFileName))
{
    var shapes = document.Worksheets[0].Shapes;
    // check if shape is SmartArt or CustomXml
    for (int i = shapes.Count - 1; i >= 0; i--)
    {
        CellsShape shape = shapes[i];
        if (shape.MsoDrawingType == CellsMsoDrawingType.SmartArt ||
            shape.MsoDrawingType == CellsMsoDrawingType.CustomXml)
        {
            shapes.RemoveAt(i);
        }
    }
    // Save document
    document.Save(outputFileName);
} 
```

# Bug Fixes

GroupDocs.Watermark for .NET 18.8 includes the following bug fix.

*   Locking watermark in PPTX, PPT is not working

# Available Channels and Resources

Here are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Watermark:

*   [Installation](https://www.nuget.org/packages/GroupDocs.Watermark/ "Install from NuGet Package") - Install GroupDocs.Watermark using NuGet
*   [Documentation](https://docs.groupdocs.com/watermark/net "Watermark API documentation") - API Documentation
*   [Examples](https://github.com/groupdocs-watermark/GroupDocs.watermark-for-.NET "How to use Watermark API") - Code Examples
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPusvdhHD52X_Q8bTjObAc9) – YouTube Video Tutorials
*   [Product Support Forum](https://forum.groupdocs.com/c/watermark) - Technical Support Forum for GroupDocs.Watermark

# Feedback

As always, we would love to hear your queries and suggestions at our [forum](https://forum.groupdocs.com/c/watermark "Technical Support Forum").




