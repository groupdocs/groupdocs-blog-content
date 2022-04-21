---
title: 'Adding Ellipse Annotation in a PDF Document'
date: Fri, 09 Aug 2019 11:45:49 +0000
draft: false
url: /2019/08/09/adding-ellipse-annotation-in-pdf-documents/
author: 'Samicheema'
summary: ''
tags: ['Annotation', 'Ellipse', 'Ellipse Annotation']
categories: ['GroupDocs.Annotation', 'GroupDocs.Annotation Product Family']
---

**GroupDocs.Annotation API**

_GroupDocs.Annotation_ comes with an extensive set of tools that you can use to easily add common shapes to your documents as an annotation. The list of tools is not limited to area, point, text, polyline, etc. In this section, we will primarily discuss how the Ellipse annotation could be added in a PDF document by using _GroupDocs.Annotation_ API.

**Adding Ellipse Annotation**

While discussing the family of annotation types, we cannot ignore ellipse annotation. It could be regarded as a multi-purposed annotation type. For example, it could be used to display extra information on your graphs or you can use it to circle important information. _AnnotationInfo_ could be used to set color, page, opacity, creator name and many more. At minimum following two properties of _AnnotationInfo_ have to be set for drawing an ellipse, which determine the size and type of the annotation:  
{{< gist GroupDocsGists 830d1f1f5e6eb2489829b152f7a6d889 "InitializeEllipseAnnotation.cs" >}} Fixed value_AnnotationType.Ellipse_ is always used as _Type_ for adding an Ellipse Annotation_._

**Code Example for a PDF Document**

For adding ellipse to a PDF document, first we will need to get the document in form of Stream by using following line of code:  
{{< gist GroupDocsGists 840a8aecb2e466e8b11e2110bd7f9563 "InputStream.cs" >}}  
Then the Ellipse annotation is added to the list of annotations:  
{{< gist GroupDocsGists efda5562031b02b9d701981f52aa4789 "ListAnnotation.cs" >}} Finally, we will export the annotation and save the output file:  
{{< gist GroupDocsGists 795ac8604817b8be9d6cbf380d1cd1a1 "ExportFile.cs" >}} This way we have added an Ellipse annotation to our PDF document using _GroupDocs.Annotation_ API.  

The complete C# code will look like this:  
{{< gist GroupDocsGists fcb0736c7f0e3cef3d8d03ed4a0844de "AddingEllipseAnnotationInPDF.cs" >}}  
The code in Java will look like this:  
\[gist id="705c29f24cf3c7a5efffe88768bde0a0" file=addingEllipseAnnotationInPDF.Java"\] After adding Ellipse annotation the output document will looks like following screenshot:



{{< figure align=center src="images/EllipseAnnotation-1024x601.png" alt="">}}





