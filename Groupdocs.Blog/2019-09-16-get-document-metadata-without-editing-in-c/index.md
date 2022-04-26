---
title: 'Get Document Metadata without Editing in C#'
date: Mon, 16 Sep 2019 11:19:01 +0000
draft: false
url: /2019/09/16/get-document-metadata-without-editing-in-c/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Editor for .NET', 'GroupDocs.Editor Product Family']
---

We have added a lot of new options and features in this major release/update of GroupDocs.Editor for .NET 19.9. All public methods/classes have been moved to **Legacy** namespace and they are marked as obsolete. Now, when you update to this latest version, it is required to make project-wide replacement of namespace usages from **GroupDocs.Editor**. to **GroupDocs.Editor.Legacy** to resolve build issues. Access release notes [here](https://docs.groupdocs.com/display/editornet/GroupDocs.Editor+for+.NET+19.9+Release+Notes).

**Why to migrate?**  

*   _Editor_ class introduced as a single entry point to manage the document editing process to any supported file format (instead of _EditorHander_ class from previous versions)
*   Architecture is redesigned to decrease memory usage
*   Simplified document editing and saving options

**See difference in code**  
This was supported in old API  
{{< gist GroupDocsGists ee2bd324e3a9bfc5b0c82f03b5d5eed1 "oldcodestyle.cs" >}}  

We have simplified and optimized code to this much in the new version  
{{< gist GroupDocsGists df88aa892e12c5afe202171bf9da546b "newcodestyle.cs" >}}

**What's new?**  
We have added a new _GetDocumentInfo_ method using this method you can get a document's metadata information without editing it.  
**What information exactly?**  

*   Family format and exact document format
*   Encryption flag
*   Number or pages/tabs
*   Size

**How it works?**  
The new _Editor_ class, which supersedes deprecated _EditorHandler_, contains this method. Once the document is loaded into the _Editor_ class, this method can be called to obtain meta information about the loaded document without opening it for the editing purpose.

**Text Save Options**

Previously, there was no direct option to save edited document in a plain text format. We used _WordProcessing_ save options for this purpose but that didn't allow to configure parameters while saving into text format.

GroupDocs.Editor for .NET version 19.9 contains a new _TextSaveOptions_ class that is actually implemented to save edited document to the plain text.  
_TextSaveOptions_ contains following settings:  

*   Ability to specify whether to add bi-directional marks before each BiDi run when exporting in plain text format
*   Ability to specify whether the program should attempt to preserve layout of tables when saving in the plain text format

**Implementation**  
The _Options_ namespace contains _TextSaveOptions_ class.  
{{< gist GroupDocsGists 59e844f056347c2d4412fafcf8edab92 "textsaveoptions.cs" >}}

As there are a lot of public API changes. Before getting started, we'd recommend you to go through API [references](https://apireference.groupdocs.com/editor/net) and example [project](https://github.com/groupdocs-editor/GroupDocs.Editor-for-.NET/).




