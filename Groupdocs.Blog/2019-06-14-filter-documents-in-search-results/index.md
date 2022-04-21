---
title: 'Generate Search Results from Filtered Documents'
date: Fri, 14 Jun 2019 13:48:08 +0000
draft: false
url: /2019/06/14/filter-documents-in-search-results/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Search for .NET', 'GroupDocs.Search Product Family']
---

Sometimes, we have a lot of different formatted documents. We create index then perform search and API shows hits from all the indexed documents. Ever thought to get search results from desired documents only?

Let's dig it further. Suppose, you have multiple TXT, XLSX and DOCX documents. What if you want to search a word or text only in TXT and DOCX files with specific word occurrence in file names? We've now improved _ISearchDocumentFilter_ interface for such a purpose in GroupDocs.Search. This interface represents search document filter and it uses _SearchDocumentFilter_ class for creation of a filter instances.

Let's now understand this with a use-case.  
**C#**  
  
{{< gist GroupDocsGists 4dfcdf9857e743254611fd918a2cbc86 "searchdocumentfilter.cs" >}}**Java**  
  
{{< gist GroupDocsGists 9219657f9f98d68c9719ccd7ca5fc5d2 "searchdocumentfilter.java" >}}

What we did in this example? We initiated a request to search occurrence of a word **hobbit** in all the TXT and DOCX files with word **task** in their file names. In this snippet, you can see a method _CreateConjuction_. It creates logical conjunction (logical and) of the specified filters.

**Settings for Log Functionality**

This improvement allows to set up log file name and maximum log file size. Below are the public API changes.  
Following class has been added to GroupDocs.Search namespace and com.groupdocs.search package:  

*   LogSettings

Following properties are added to GroupDocs.Search.LogSettings and com.groupdocs.search.LogSettings class: **C#**

*   string FileName
*   double MaxSize

**Java**

*   String getFileName()
*   void setFileName(String value)
*   double getMaxSize()
*   void setMaxSize(double value)

Below properties are added to GroupDocs.Search.Index and com.groupdocs.search.Index classes respectively:

*   LogSettings LogSettings
*   LogSettings getLogSettings()

  
Let's go through the implementation:  
**C#**  
  
{{< gist GroupDocsGists e334ad082c0414bbbace70c424f64136 "logsettings.cs" >}}  
**Java**  
  
{{< gist GroupDocsGists 314c845edb2685e5c90118f5472e2437 "logsettings.java" >}}

**Add English Synonyms**

This improvement adds English synonyms to default synonym dictionary.  
**C#**  
  
{{< gist GroupDocsGists e3a3cf6c2a28a8716b19978a10951b4b "defaultsynonym.cs" >}}  
**Java**  
  
{{< gist GroupDocsGists 2f917505c1ad1f5c5895fe77ec45f2d1 "defaultsynonym.java" >}}

Above are the major improvements introduced in version 19.5. Please go through all the other changes in release notes:  

*   [Java](https://docs.groupdocs.com/display/searchjava/GroupDocs.Search+for+Java+19.5+Release+Notes)
*   [.NET](https://docs.groupdocs.com/display/searchnet/GroupDocs.Search+for+.NET+19.5+Release+Notes)

Avail these exciting improvements now in your project. This release is available for [download](https://downloads.groupdocs.com/search). Please share your feedback or concerns [here](https://forum.groupdocs.com/c/search).




