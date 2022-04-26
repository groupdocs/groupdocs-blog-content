---
title: 'Add Ellipse Annotation in Slides'
date: Mon, 08 Apr 2019 14:35:31 +0000
draft: false
url: /2019/04/08/add-ellipse-annotation-in-slides/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Annotation for .NET', 'GroupDocs.Annotation Product Family']
---

We try our best to provide minimal yet appropriate solutions to our customers. Hence, in this month's release of GroupDocs.Annotation for .NET 19.3 you will observe some new "easy-to-implement" features. Lets start with ellipse annotation. You might be looking for it, we've now added its support for different document formats.

## Ellipse Annotation

{{< gist GroupDocsGists d8c97ca1a39d059735cbabe41239958a "Examples-GroupDocs.Annotation.Examples.CSharp-GroupDocs.AnnotationExamples-PDFAnnotation-AddEllipseAnnotation.cs" >}}

GroupDocs.Annotation for .NET 19.3 provides _GetThumbnail_ method for **PageImage** class, that helps you in getting thumbnails of PDF document pages.

## Get Thumbnails

{{< gist GroupDocsGists bf83acf3db01ad01bd687557758c32e3 "Examples-GroupDocs.Annotation.Examples.CSharp-GroupDocs.AnnotationExamples-PDFAnnotation-GetThumnailsOfPagesForPDF.cs" >}}

You'll be glad to hear that **multipage TIFF** file can be processed by API. Have a glance at [release notes](https://docs.groupdocs.com/display/annotationnet/GroupDocs.Annotation+for+.NET+19.3+Release+Notes).

## Bug Fixes

Now coming to your issues, we'll discuss some major fixes introduced in this release. There was issue in applying **PenWidht** and **PenColor** properties but now this is fixed.

_AnnotationImageHandler.GetDocumentInfo_ exception while evaluating API in trial mode is now resolved. API now closes stream when you import annotations for Images. Lastly, issue in setting comments to shapes in Slides is fixed.

Learn more about API integration and usage check out the docs [here](https://docs.groupdocs.com/display/annotationnet/Home).




