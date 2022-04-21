---
title: 'Change Target File Format using GroupDocs.Assembly for .NET 18.9'
date: Tue, 02 Oct 2018 16:44:02 +0000
draft: false
url: /2018/10/02/change-target-file-format-using-groupdocs.assembly-for-.net-18.9/
author: 'Ali Ahmed'
summary: ''
tags: []
categories: ['GroupDocs.Assembly', 'GroupDocs.Assembly for .NET', 'GroupDocs.Assembly for .NET Releases', 'GroupDocs.Assembly Product Family']
---

![](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/04/groupdocs-assembly-net.png)We are delighted to announce a powerful new feature in the monthly release of [GroupDocs.Assembly for .NET](https://products.groupdocs.com/assembly/net) **18.9**. Using the latest version,  you can now change the target file format of an assembled document using file extension or explicit specification. You can change the target file format when assembling Word Processing, Spreadsheet, Presentation, Email and Text file formats. We recommend you to [install](https://www.nuget.org/packages/GroupDocs.Assembly/) and use the latest version of the API.

## Features IntroducedSince version 18.9, you can change the format of the assembled document either by specification of the file extension or using **LoadSaveOptions** as shown in the following code snippets.

### Changing the target file format using the file extension```
DataSourceInfo dataSourceInfo = new DataSourceInfo(...);
DocumentAssembler assembler = new DocumentAssembler();
  
assembler.AssembleDocument("template.docx", "result.pdf", dataSourceInfo);
```

### Changing target file format using explicit specification```
Stream sourceStream = ...;
Stream targetStream = ...;
  
DataSourceInfo dataSourceInfo = new DataSourceInfo(...);
DocumentAssembler assembler = new DocumentAssembler();
  
assembler.AssembleDocument(sourceStream, targetStream, 
new LoadSaveOptions(FileFormat.Pdf), dataSourceInfo);
```For more details on this feature, please visit [this](https://docs.groupdocs.com/display/assemblynet/Changing+Target+File+Format) documentation article. At the moment, GroupDocs.Assembly API provides the ability to change target file format when assembling the following file formats:

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
public void AssembleDocument(string sourcePath, string targetPath, params DataSourceInfo[] dataSourceInfos)
public void AssembleDocument(string sourcePath, string targetPath, LoadSaveOptions loadSaveOptions, params DataSourceInfo[] dataSourceInfos)
public void AssembleDocument(Stream sourceStream, Stream targetStream, params DataSourceInfo[] dataSourceInfos)
public void AssembleDocument(Stream sourceStream, Stream targetStream, LoadSaveOptions loadSaveOptions, params DataSourceInfo[] dataSourceInfos)
```

### Removed Members of DocumentAssemblerFollowing members of **DocumentAssembler** are removed in the latest version.```
public void AssembleDocument(string sourcePath, string targetPath, object dataSource)
public void AssembleDocument(string sourcePath, string targetPath, object dataSource, string dataSourceName)
public void AssembleDocument(string sourcePath, string targetPath, object[] dataSources, string[] dataSourceNames)
public void AssembleDocument(Stream sourceStream, Stream targetStream, object dataSource)
public void AssembleDocument(Stream sourceStream, Stream targetStream, object dataSource, string dataSourceName)
public void AssembleDocument(Stream sourceStream, Stream targetStream, object[] dataSources, string[] dataSourceNames)
```

### Breaking ChangesRemoved members of **DocumentAssembler** are replaced with new ones. Removed members were not marked as obsolete (deprecated) before removal as usual, because this would complicate migration to new members of **DocumentAssembler** in Java. Thus, we have introduced a breaking change and customers need to migrate their code from removed members of **DocumentAssembler** to newly added ones when upgrading to the new version of GroupDocs.Assembly. For more details, please visit [this](https://docs.groupdocs.com/display/assemblynet/Migrating+to+GroupDocs.Assembly+18.9+or+Higher) documentation article.

## Available Channels and ResourcesHere are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Assembly for .NET.

*   [Installation](https://www.nuget.org/packages/GroupDocs.Assembly/ "GroupDocs.Assembly Nuget Package") - Install GroupDocs.Assembly using NuGet
*   [Documentation](https://docs.groupdocs.com/display/assemblynet/Getting+Started "Assembly API documentation") - API Documentation
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-.NET/tree/master/Examples "How to use Assembly API") - Source Code Examples, Plugins, and Assembly Editor Application
*   [Video Tutorials](https://www.youtube.com/watch?v=7FfYiii_PcM&t=0s&list=PL25CTxMCj5vOzsaE9Rwjwd4-OwvdaWmJ8&index=2 "Assembly API YouTube Tutorials") - YouTube API Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/assembly) - Technical Support Forum for GroupDocs Assembly

## FeedbackAs always, if you have some questions, queries or suggestions about [GroupDocs.Assembly for .NET](https://products.groupdocs.com/assembly/net) API,  just share with us by creating a [forum thread](https://forum.groupdocs.com/c/assembly).




