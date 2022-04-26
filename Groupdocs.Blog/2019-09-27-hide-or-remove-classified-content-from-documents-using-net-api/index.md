---
title: 'Redact Classified Content from Documents using All-New GroupDocs.Redaction for .NET'
date: Fri, 27 Sep 2019 12:32:31 +0000
draft: false
url: /2019/09/27/hide-or-remove-classified-content-from-documents-using-net-api/
author: 'Usman Aziz'
summary: ''
tags: []
categories: ['GroupDocs.Redaction for .NET', 'GroupDocs.Redaction Product Family']
---

We are continuing the journey of revamping our products to bring a more simplified and easy to use interfaces for you. We have done it for many of our document manipulation APIs and recently, we have released all-new **[GroupDocs.Redaction for .NET](https://products.groupdocs.com/redaction/net)** API for you as  [**v19.9**](https://downloads.groupdocs.com/redaction/net). With this release, we have made it even easier for you to programmatically **remove or mask classified information** from **text**, **metadata**, and the **annotations** in **MS Word**, **Excel**, **PowerPoint**, and **PDF** documents as well as **images**.

## Why upgrade to the new API?

First of all, let's have a look at why the new API is different from the previous one. The following are the key points about the changes we have introduced in the latest release.

*   The architecture of the API has been revamped to perform major product optimization.
*   The classes and methods have been renamed to make it even simpler to understand and use.
*   The _Document_ class has been replaced with the _[Redactor](https://apireference.groupdocs.com/net/redaction/groupdocs.redaction/redactor)_ class as a  single entry point to manage the redaction process for all the supported document formats.
*   The methods _RedactWith() _of the _Document _class have been replaced with similar _[Apply()](https://apireference.groupdocs.com/net/redaction/groupdocs.redaction/redactor/methods/apply/index) _methods in _Redactor _class. 
*   The method _Document.Save(Stream, SaveOptions)_ has been replaced with _[Redactor.Save(Stream, RasterizationOptions)](https://apireference.groupdocs.com/net/redaction/groupdocs.redaction.redactor/save/methods/2)._
*   Renamed _RedactionSummary_ to _[RedactorChangeLog](https://apireference.groupdocs.com/net/redaction/groupdocs.redaction/redactorchangelog),_ _RedactionLogEntry_ to _[RedactorLogEntry](https://apireference.groupdocs.com/net/redaction/groupdocs.redaction/redactorlogentry)_, and _MetadataFilter _to _[MetadataFilters](https://apireference.groupdocs.com/net/redaction/groupdocs.redaction.redactions/metadatafilters)_.
*   The classes for options and exceptions have been put into separate namespaces. 
*   Obsolete members have been removed from public API.
*   Added a number of new exception classes and base exception class for _[GroupDocs.Redaction](https://apireference.groupdocs.com/net/redaction/groupdocs.redaction.exceptions/)_ exceptions.

## How to migrate?

The migration to an API version with major updates is always hard since it requires considerable efforts to update the code. However, these efforts are valuable when you get something more improved and efficient in the return. So if you are already using _GroupDocs.Redaction for .NET_ and want to migrate to the new API, let me give you a code comparison between the new and the older versions. This way, you will get an idea of how things would be changed after migration.

**Old coding style**

{{< gist GroupDocsGists c92f9fc528c82c94a5d7a377bd11eee3 "RedactTextInWordDocumentOld.cs" >}}

**New coding style (since v19.9)**

{{< gist GroupDocsGists c92f9fc528c82c94a5d7a377bd11eee3 "RedactTextInWordDocumentNew.cs" >}}

For a complete list of all public API changes, please have a look at the [release notes](https://docs.groupdocs.com/display/redactionnet/GroupDocs.Redaction+for+.NET+19.9+Release+Notes).

Alright! Are you interested in trying out the new API? If yes, [download](https://github.com/groupdocs-redaction/GroupDocs.Redaction-for-.NET) or clone the complete source code examples from the GitHub repository. You can consult the [documentation](https://docs.groupdocs.com/display/redactionnet/GroupDocs.Redaction+Overview) to get details about all the features of the API. In case you find any issue or something confusing, do let us know via our [forum](https://forum.groupdocs.com/).




