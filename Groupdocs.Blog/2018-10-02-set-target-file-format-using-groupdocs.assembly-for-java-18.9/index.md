---
title: 'Set Target File Format using GroupDocs.Assembly for Java 18.9'
date: Tue, 02 Oct 2018 16:44:06 +0000
draft: false
url: /2018/10/02/set-target-file-format-using-groupdocs.assembly-for-java-18.9/
author: 'Ali Ahmed'
summary: ''
tags: []
categories: ['GroupDocs.Assembly', 'GroupDocs.Assembly for Java', 'GroupDocs.Assembly for Java Releases', 'GroupDocs.Assembly Product Family']
---

[![Document Assembly API](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/03/groupdocs-assembly-java-1.png)](https://www.groupdocs.com/products/assembly/java)We are excitedly announcing a new feature in the monthly release of [GroupDocs.Assembly for Java](https://products.groupdocs.com/assembly/java) **18.9**.  Using the latest version,  you can now change the target file format of an assembled document using file extension or explicit specification. You can change the target file format when assembling Word Processing, Spreadsheet, Presentation, Email and Text file formats. We recommend you to [install](https://artifact.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-assembly/maven-assembly.xml) the latest version of the API for a better user experience.

## Features IntroducedSince version 18.9, you can change the format of the assembled document either by specification of the file extension or using **LoadSaveOptions** as shown in the following code snippets.

### Changing the target file format using the file extension```
DataSourceInfo dataSourceInfo = new DataSourceInfo(...);
DocumentAssembler assembler = new DocumentAssembler();
  
assembler.assembleDocument("template.docx", "result.pdf", dataSourceInfo);
```

### Changing target file format using explicit specification```
InputStream sourceStream = ...;
OutputStream targetStream = ...;
  
DataSourceInfo dataSourceInfo = new DataSourceInfo(...);
DocumentAssembler assembler = new DocumentAssembler();
  
assembler.assembleDocument(sourceStream, targetStream, new LoadSaveOptions(FileFormat.PDF), dataSourceInfo);
```For more details on this feature, please visit [this](https://docs.groupdocs.com/display/assemblyjava/Changing+Target+File+Format) documentation article. At the moment, GroupDocs.Assembly API provides the ability to change target file format when assembling the following file formats:

*   Word Processing documents
*   Spreadsheet documents
*   Presentation documents
*   Email documents
*   Text documents

Supported output file formats depending on input file formats can be found at this page.

## API Changes

### Newly Added TypesFollowing types are added in the latest version.```
public class DataSourceInfo
public enum FileFormat
public class LoadSaveOptions 
```

### Newly Added Members of DocumentAssemblerFollowing members of **DocumentAssembler** are added in the latest version.```
public void assembleDocument(String sourcePath, String targetPath, DataSourceInfo... dataSourceInfos) throws Exception
public void assembleDocument(String sourcePath, String targetPath, LoadSaveOptions loadSaveOptions, DataSourceInfo... dataSourceInfos) throws Exception
public void assembleDocument(InputStream sourceStream, OutputStream targetStream, DataSourceInfo... dataSourceInfos) throws Exception
public void assembleDocument(InputStream sourceStream, OutputStream targetStream, LoadSaveOptions loadSaveOptions, DataSourceInfo... dataSourceInfos) throws Exception 
```

### Removed Members of DocumentAssemblerFollowing members of **DocumentAssembler** are removed in the latest version.```
public void assembleDocument(String sourcePath, String targetPath, Object dataSource)
public void assembleDocument(String sourcePath, String targetPath, Object dataSource, String dataSourceName)
public void assembleDocument(String sourcePath, String targetPath, Object[] dataSources, String[] dataSourceNames)
public void assembleDocument(InputStream sourceStream, OutputStream targetStream, Object dataSource)
public void assembleDocument(InputStream sourceStream, OutputStream targetStream, Object dataSource, String dataSourceName)
public void assembleDocument(InputStream sourceStream, OutputStream targetStream, Object[] dataSources, String[] dataSourceNames)
```

### Breaking ChangeRemoved members of **DocumentAssembler** were replaced with new ones. Removed members were not marked as obsolete (deprecated) before removal as usual, because this would complicate migration to new members of **DocumentAssembler** in Java. Thus, we have introduced a breaking change and customers need to migrate their code from removed members of **DocumentAssembler** to newly added ones when upgrading to the new version of GroupDocs.Assembly. For more details, please visit [this](https://docs.groupdocs.com/display/assemblyjava/Migrating+to+GroupDocs.Assembly+18.9+or+Higher) documentation article. Since version 18.9, the Metered licensing security has been improved. Metered licensing is now applicable only in Java runtime version _8u101_ or above. Please use other types of licensing if you are using v18.9 or greater in Java 7.

## Available Channels and ResourcesHere are a few channels and resources for you to download, try, learn and get technical support on GroupDocs.Assembly for Java:

*   [Installation](https://artifact.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-assembly/maven-assembly.xml) - Install GroupDocs.Assembly from Maven
*   [Documentation](https://docs.groupdocs.com/display/assemblyjava/Getting+Started) – API docs
*   [Examples](https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-Java) – Source code examples
*   [Product Support Forum](https://forum.groupdocs.com/c/assembly) – Technical support forum for GroupDocs.Assembly product family

## FeedbackWe always love to hear your valuable feedback. Share your suggestions, questions, or queries related to GroupDocs.Assembly for Java at our [forum](https://forum.groupdocs.com/c/assembly).




