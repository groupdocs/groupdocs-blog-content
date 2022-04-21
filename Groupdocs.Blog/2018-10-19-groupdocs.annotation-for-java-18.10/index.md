---
title: 'Introducing Point Annotation for Words in GroupDocs.Annotation for Java 18.10'
date: Fri, 19 Oct 2018 11:50:44 +0000
draft: false
url: /2018/10/19/groupdocs.annotation-for-java-18.10/
author: 'Samicheema'
summary: ''
tags: []
categories: ['GroupDocs.Annotation for Java', 'GroupDocs.Annotation Product Family']
---

[![Logo Image](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/12/groupdocs-annotation-java.png)](https://products.groupdocs.com/annotation/java)We are excitedly announcing another monthly release of **GroupDocs.Annotation for Java 18.10**. Using this latest version, you can add Point, Polyline and Watermark annotations in Words and Diagrams document. Beside this, a multitude of bug fixes are also introduced in this release. We therefore recommend you to download this [latest](https://downloads.groupdocs.com/annotation/java) release for a better API experience.

# Features

## Add Watermark, Polyline and Point Annotations in Words and Diagrams documentYou can add Watermark, Polyline and Point Annotations in **Words** and **Diagrams** document using this latest release. Following example demonstrates how to add Point annotation in Words document:```
// Initialize list of AnnotationInfo
List annotations = new List();
// Point annotation
AnnotationInfo pointAnnnotation = new AnnotationInfo();
pointAnnnotation.setCreatedOn(new Date());
pointAnnnotation.setType(AnnotationType.Point);
pointAnnnotation.setBox(new Rectangle(150.32f, 99.22f, 0, 0));
pointAnnnotation.setPageNumber(0);

annotations.add(pointAnnnotation); 
```

## Change Highlight Color of Fonts in WordsThis latest release of the API allows users to change highlight color of fonts for Text Annotations in Words document.

## Support of Metadata in SlidesSupport for Metadata in Slides document is also introduced in this latest release.

# Fixes

*   Cleanup in PDF doesn't remove watermarks
*   Highlight color is not changed in footnotes for highlight annotations in Words
*   Exception while running project on macOS
*   isValidLicense() property of License class always returns false
*   An exception raises while accessing the source document
*   TIFF/Multi TIFF file is either corrupted or black and white when annotated
*   Some annotations are missing while exporting to file
*   Exception while exporting Line and Distance annotation
*   Unable to retrieve un-annotated page image from annotated document

## Available Channels and ResourcesHere are a few channels and resources for you to download, learn, try and get technical support on **Documentation Annotation API**:

*   [Download](https://downloads.groupdocs.com/annotation/java) - Zipped JARs
*   [Documentation ](https://docs.groupdocs.com/display/annotationjava/Home)\- API Documentation
*   [Examples](https://github.com/groupdocs-annotation/GroupDocs.Annotation-for-java "Examples") - GitHub source code examples
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vMLFYnGGrSc3o10Ma9vMVxR "video tutorials") - YouTube videos
*   [API References](https://apireference.groupdocs.com/java/annotation "API References") - Annotation API References
*   [Product Support Forum](https://forum.groupdocs.com/c/annotation "Support forum") - Technical Support Forum for GroupDocs.Annotation

## FeedbackAs always, you are welcome to share your feedback to improve this product. We will be happy to know your thoughts. Just create a [forum thread](https://forum.groupdocs.com/c/annotation) and our dedicated support team will be there to respond.

# Feedback

We always appreciate and welcome to our valuable users to share their feedback to improve this product. We will be happy to know your thoughts and suggestions. Just create a [forum thread](https://forum.groupdocs.com/c/annotation) and our dedicated support team will be there to respond.




