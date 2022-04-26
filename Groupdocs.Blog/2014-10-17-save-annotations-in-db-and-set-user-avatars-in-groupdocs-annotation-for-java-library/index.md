---
title: 'Save Annotations in a DB and Set User Avatars in the GroupDocs.Annotation for Java Library'
date: Fri, 17 Oct 2014 12:33:52 +0000
draft: false
url: /2014/10/17/save-annotations-in-db-and-set-user-avatars-in-groupdocs-annotation-for-java-library/
author: 'Ihor Mykhalevych'
summary: ''
tags: ['annotation for java library', 'GroupDocs Annotation', 'zArchive']
---

[![](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/04/GD_ANT_JavaIcon_1141.png "GroupDocs.Annotation for Java")](http://groupdocs.com/java/document-annotation-library)Today, I’d like to present several great enhancements that we’ve implemented in the [GroupDocs.Annotation for Java library](http://groupdocs.com/java/document-annotation-library) version 1.6.0:

### User AvatarsRemote collaboration in groups is much more engaging and productive when we can see each other (or at least put a face to each other). In this release we’ve implemented functionality that allows users to use personal avatars when annotating documents in a group. The avatar functionality can be easily configured through the library’s API. The {{AnnotationHandler}} has two new methods for handling user icons:```
public byte\[\] getUserAvatar(String userGuid)

``````
public void setUserAvatar(String userGuid, byte\[\] avatarFile)

```The array used in these methods contains a binary picture that can be set for each user. For example, you can check if an avatar is already set, and if not, load one:```
if (annotationHandler().getUserAvatar(userGuid) == null){
    FileInputStream avatarStream = new FileInputStream(new File("E:\\\\Images\\\\smile.jpeg"));
    byte\[\] bytes = new byte\[avatarStream.available()\];
    IOUtils.readFully(avatarStream, bytes);
    Utils.closeStreams(avatarStream);
    annotationHandler().setUserAvatar(userGuid, bytes);
}

```

### Save Annotations in a DBIn this release we’ve added the capability to configure how you store annotation metadata. The [ORMLite](http://ormlite.com/) persistence framework is now used to support a huge variety of storage providers. You can still use good old local file storage but if you need more consistency you can now easily integrate GroupDocs.Annotation with your application’s database, be it a MySQL, Microsoft SQL Server, PostgreSQL, or other supported DB. For more detail on this feature, please see [this page](http://groupdocs.com/docs/display/annotationjava/How+to+store+annotations+in+a+DB).

### New Annotation ObjectsGroupDocs.Annotation for Java version 1.6.0 has two new annotation tools:

*   **Ruler** - allows users to measure the distance between specified points in pixels.
*   **Underline tool** - allows users to underline selected text.

Besides, we’ve improved support for native PDF and Word annotations and added the capability to export annotated Word documents to a final .doc/.docx file with the Word’s “Track Changes” feature active.

### Print PreviewOne more enhancement that you may be interested in is the ability to generate a document print preview when users try to print the annotated document. The print preview displays documents with annotations added. To see a full list of changes and download the GroupDocs.Annotation for Java library version 1.6.0, please visit our [download archive](http://groupdocs.com/Community/files/9/java-libraries/groupdocs_annotation_for_java/entry2604.aspx). For more information on the library please visit its [homepage](http://groupdocs.com/java/document-annotation-library) and [documentation](http://groupdocs.com/docs/display/annotationjava/Home). We also encourage you to use the [code examples](http://groupdocs.com/Community/files/9/java-libraries/groupdocs_annotation_for_java/category1043.aspx) that we’ve prepared to help you explore the library’s functionality quickly.




