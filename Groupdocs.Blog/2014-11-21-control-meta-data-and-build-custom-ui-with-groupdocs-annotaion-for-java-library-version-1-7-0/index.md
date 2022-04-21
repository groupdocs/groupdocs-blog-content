---
title: 'Control Meta-Data and Build a Custom UI with the New GroupDocs.Annotation for Java Library Version 1.7.0'
date: Fri, 21 Nov 2014 17:57:46 +0000
draft: false
url: /2014/11/21/control-meta-data-and-build-custom-ui-with-groupdocs-annotaion-for-java-library-version-1-7-0/
author: 'Ihor Mykhalevych'
summary: ''
tags: ['annotation for java library', 'GroupDocs Annotation', 'Uncategorized']
---

[![GroupDocs.Annotation for Java Library](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/04/GD_ANT_JavaIcon_1141.png)](http://groupdocs.com/java/document-annotation-library) [GroupDocs.Annotation for Java](http://groupdocs.com/java/document-annotation-library) is a lightweight library that allows end users to annotate PDF and Microsoft Office documents, raster images, AutoCAD drawings and 50+ types of files without the need to install the software that the documents or images were created in. A convenient web UI allows users to view, annotate, redact, comment on and share documents from any web-enabled device. Recently we’ve released a new GroupDocs.Annotation for Java library – version 1.7.0. We’ve greatly enhanced the metadata storage APIs, revealed the public document manipulation API and made a couple of other useful tweaks. In this post I’d like to discuss these updates in more detail.You can seamlessly integrate GroupDocs.Annotation for Java into your own web, desktop or mobile application to enhance your users’ document collaboration experience. The underlying APIs allow you to customize the web UI that comes with the library, or build your own desktop or mobile interface from scratch.

## Store Metadata in any DB or File FormatIn the previous version of the library we introduced [support for databases](https://blog.groupdocs.com/save-annotations-in-db-and-set-user-avatars-in-groupdocs-annotation-for-java-library). We quickly realized that this was not enough and completely redesigned the library to provide developers with a more flexible and manageable solution. To this end, we’ve re-implemented the existing functionality in an OOP manner. Now, you can store annotations, user comments, profile details, etc. in JSON and XML formats. Also, the list of supported databases now includes the following: MSSQL, MySQL, SQLite and PostgreSQL. Please find more details on how to work with DBs and store files meta-data in the [documentation](http://groupdocs.com/docs/display/annotationjava/How+to+store+annotations+in+a+DB).

## Build Mobile, Desktop or Server ApplicationsFollowing the GroupDocs.Viewer for Java library, the AnnotationHandler API is now also extended with pure methods that do not require HTTP requests and response objects. The methods allow developers to build any kind of user interaction, be it a web, desktop or mobile UI. Now you can even process documents in the background as part of your Java server application. Similarly to the HTTP handler methods, here is a list of new, context-independent ones that are available in the AnnotationHandler class:```
restoreAnnotationReplies
getPrintDocumentPageImage
listAnnotations
exportAnnotations
createAnnotation
getAvatar
addAnnotationReply
editAnnotationReply
deleteAnnotationReply
deleteAnnotation
saveTextField
setTextFieldColor
moveAnnotationMarker
resizeAnnotation
getDocumentCollaborators
uploadFile
importAnnotations
getPrintView
```For the full signatures and detailed info on these methods, please refer to the JavaDoc that comes with the library in a JAR package.

## Other ImprovementsAlong with new features, we also improved the existing functionality a bit. For example, you can now configure the underline and strikeout tools’ color by overloading new configuration methods:```
String getStrikeOutColor()
String getUnderlineColor()
```Other fixes and improvements have been made to the front-end and exporting functionality. Please check the full list of updates on the GroupDocs.Annotation for Java library [download page](http://groupdocs.com/Community/files/9/java-libraries/groupdocs_annotation_for_java/entry3111.aspx). For more information on the library, please visit its [homepage](http://groupdocs.com/java/document-annotation-library).




