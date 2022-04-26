---
title: 'Add Ellipse Annotation in Multiple Documents'
date: Fri, 02 Aug 2019 11:37:50 +0000
draft: false
url: /2019/08/02/add-ellipse-annotation-in-multiple-documents/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Annotation for Java', 'GroupDocs.Annotation Product Family']
---

We are always keen to make our APIs rich in features and enhance usability. When we talk about annotation types. One cannot neglect ellipse annotation. Its a multi purposed annotation type. For instance you can use it to display extra information on your gauge or capture graph hits against a target line. Previously, Ellipse annotation was implemented in .NET version and it seemed very useful. We are pleased to announce that Ellipse annotation is now added in GroupDocs.Annotation for Java [19.7](https://docs.groupdocs.com/display/annotationjava/GroupDocs.Annotation+for+Java+19.7+Release+Notes). Java users can implement this annotation as follows: {{< gist GroupDocsGists 5e1eb75931fb40a23c8e881dcc9e30a0 "ellipseannotation.java" >}}  
This is how ellipse annotation will look like:  

*   

{{< figure align=center src="images/ellipse-3.jpg" alt="">}}

    

You can also set ellipse color, pen style (e.g. dash, dot, solid), pen width. _AnnotationInfo_ class gives you access to such properties.  
You might be wondering, what documents are actually supported for the ellipse annotation? Currently, this annotation is supported for the following file formats only:  

*   PDF
*   Word
*   Slide
*   Image
*   Cell
*   Diagram

**Setting Watermarks Angle**  
We've added ability to set text watermark angle. The process is same as adding Watermark annotation, but you should additionally set Watermark rotation angle by setting _AnnotationInfo.Angle_ property (in degrees).  
{{< gist GroupDocsGists 08726fe3264ff35a9531bc4fe65b991c "anglewatermark.java" >}}  

Aside new features, we've also fixed some bugs:

*   Only first page is saved in output when Multi-Tiff file is annotated
*   Import annotations for Images doesn't close stream
*   Annotation not apply if page number not defined in Words

We'd recommend you to [download](https://downloads.groupdocs.com/annotation/java) and integrate latest release of the API and share your concerns on [forum](https://forum.groupdocs.com/c/annotation).




