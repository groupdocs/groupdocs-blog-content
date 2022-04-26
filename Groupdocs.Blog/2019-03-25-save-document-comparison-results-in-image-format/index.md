---
title: 'Save Document Comparison Results in Image Format'
date: Mon, 25 Mar 2019 11:03:50 +0000
draft: false
url: /2019/03/25/save-document-comparison-results-in-image-format/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Comparison for .NET', 'GroupDocs.Comparison Product Family']
---

Yes, you heard it right. We've implemented ability to save document comparison results in image format as well. In this blog post we'll review the new feature and bug fixes introduced in monthly release of GroupDocs.Comparison for .NET [19.3.1](https://docs.groupdocs.com/display/comparisonnet/GroupDocs.Comparison+for+.NET+19.3.1+Release+Notes).

Let's talk about image representation of the document pages. The moment you save comparison results in your directory, you have a control to save results in image format as well using **ICompareResult.SaveImages** Method. Quite simple, isn't it?

The good thing is that you just have to pass the output folder path and API will take care of conversion mechanism itself.

Is there a way to get number of converted images? Can images be saved in separate directory?

The answer is yes, you can retrieve a list of converted pages and also save them in some separate directory. Let's see full implementation of this feature.

{{< gist GroupDocsGists 00e02fd174763521e39ce9ac4e6010bb "Examples-CSharp-CommonComparision-GetImageRepresentationOfDocumentPages.cs" >}}

## Bug Fixes

In addition to the new features, we also emphasis to improve/resolve consistency, usability and issues. We will highlight the major bug fixes below.

### SuperScript and SubScript

You may be familiar with these characters. They are slightly below or above the normal line and are usually smaller than the rest of the text.



{{< figure align=center src="images/superscript-subscript.jpg" alt="">}}


There was issue in SuperScript and SubScript elements in Word document. API was not processing such characters. But this issue is now resolved.

### StyleSettings is not working for HTML

Let us first give you an overview of StyleSettings. Using this you can set following properties:

*   BeginSeparatorString
*   Bold
*   EndSeparatorString
*   Fontcolor
*   HighlightColor
*   Italic
*   StrikeThrough
*   Underline

Previously, there was no impact of such properties in the output HTML.  
Can we now strikeout or change color of deleted component?  
Of course, we are pleased to inform you that you can now successfully set such properties during HTML comparison and see their impact in the resultant file.

### EndNote Comparison

When we want to add reference information about a quoted material, we use Endnote. Previously, API was not considering Endnotes and there was no Endnote comparison at all. However, its fixed now. In the image below, we have source, target and resultant files. And if you see resultant file, it clearly shows a Endnote comparison.



{{< figure align=center src="images/endnote-comparison.jpg" alt="">}}


## Further Reading

Get started with GroupDocs.Comparison for .NET [Developer Guide](https://docs.groupdocs.com/display/comparisonnet/Developer+Guide).  
Go through the [release notes](https://docs.groupdocs.com/display/comparisonnet/Release+Notes) in order to get more insights. Articulate your concerns or feedback on [Forum](https://forum.groupdocs.com/c/comparison).

We'd now recommend you to integrate latest release of the API in your project and enhance your document comparison experience.




