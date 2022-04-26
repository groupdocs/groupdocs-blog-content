---
title: 'Cleanup Temporary Files using GroupDocs.Viewer for Java 17.5.1 Hotfix'
date: Tue, 03 Jul 2018 08:13:02 +0000
draft: false
url: /2018/07/03/cleanup-temporary-files-using-groupdocs.viewer-for-java-17.5.1-hotfix/
author: 'Usman Aziz'
summary: ''
tags: ['document viewer', 'document viewer API for Java', 'Java document viewer API', 'viewer']
categories: ['GroupDocs.Viewer for Java', 'GroupDocs.Viewer for Java Releases', 'GroupDocs.Viewer Product Family']
---

[![Logo Image](http://joomla-groupdocs.dynabic.com/templates/groupdocs/images/product-logos/90x90/groupdocs-viewer-java.png?v2)](http://www.groupdocs.com/products/viewer/java)We are pleased to announce the release of [GroupDocs.Viewer for Java](https://products.groupdocs.com/viewer/java) 17.5.1. This is a hotfix release that contains 2 bug fixes and a new feature. The latest version allows you to manually cleanup the temporary files that are created during document rendering. Please continue to read the details about the new feature and the bug fixes.

## Cleanup Temporary FilesWhile rendering documents, GroupDocs.Viewer creates temporary files which were removed automatically after each operation. As removing temporary files is a time-consuming operation, therefore, a new method **clearTempFiles** is introduced. This method is thread-safe and can be called any time so it won't affect documents' rendering. GroupDocs.Viewer uses default system's temporary folder to store temp files and it can be changed by setting temporary directory in process properties e.g. _System.setProperty("java.io.tmpdir", "c:/my\_temp\_files/")._ The following code sample shows how to cleanup temporary files.```
// Setup GroupDocs.Viewer config
ViewerConfig config = new ViewerConfig();
config.setStoragePath(STORAGE_PATH);
   
// Create image or html handler
ViewerImageHandler handler = new ViewerImageHandler(config);
  
// Cleanup temporary files
handler.clearTempFiles();
```

## Bug FixesFollowing bugs have been fixed in this hotfix release:

*   NullPointerException when rendering PDF as HTML
*   Performance degradation during consequent iterations through the same documents

## Related Links and ResourcesFollowing resources will help you to download, learn, try and get technical support.

*   [Product Home](https://products.groupdocs.com/viewer/java) – API Home Page
*   [Installation](https://artifact.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-viewer "GroupDocs.viewer for Java Downloads") - Install GroupDocs.Viewer from Maven
*   [Documentation](https://docs.groupdocs.com/display/viewerjava/Home) – Product Documentation
*   [Product Support Forum](https://forum.groupdocs.com/c/viewer) – Technical Support Forum for GroupDocs.Viewer
*   [Examples](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-Java) – Source Code Examples
*   [Sample Front End App](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-Java-App) - Open Source **Document Viewer** Application

## FeedbackAs always, you are welcome to share your feedback to improve this product. We will be happy to know your thoughts. Just create a [forum thread](https://forum.groupdocs.com/c/viewer) and our dedicated support team will be there to respond.




