---
title: 'Manipulate Metadata Properties in Documents with All-New GroupDocs.Metadata for .NET'
date: Fri, 29 Nov 2019 15:02:30 +0000
draft: false
url: /2019/11/29/manipulate-metadata-properties-in-documents-groupdocs-metadata-net-api/
author: 'Usman Aziz'
summary: ''
tags: ['API', 'document properties', 'dotnet', 'Metadata', 'metadata management']
categories: ['GroupDocs.Metadata for .NET Releases', 'GroupDocs.Metadata Product Family']
---

We have a major update for our customers who are using our **metadata manipulation API** - [GroupDocs.Metadata for .NET](https://products.groupdocs.com/metadata/net). We have revamped the architecture of the API to improve and simplify the process of reading, updating, searching or removing the metadata properties from the documents. So let's take a tour of version 19.11.

## Why do you need to upgrade?

You should upgrade to the latest release because:

*   The_ [Metadata](https://apireference.groupdocs.com/net/metadata/groupdocs.metadata/metadata)_ class is introduced as a single entry point to manage metadata in all supported formats.
*   Extracting and updating metadata has been unified for all supported formats.
*   The product architecture has been redesigned from scratch in order to simplify the most common operations with metadata properties.
*   The process of getting document information and preview generation has been simplified.

## How to migrate?

All public types of the legacy API have been moved from the _GroupDocs.Metadata_ namespace to the _[GroupDocs.Metadata.Legacy](https://apireference.groupdocs.com/metadata/net)_ namespace. Furthermore, all the legacy types have been marked as obsolete and will be removed in future releases.

Once you upgrade to the latest release, you will have to do the project-wide replacement of _GroupDocs.Metadata._ namespace with the _GroupDocs.Metadata.Legacy._ to successfully build your solution.

## Comparison of Coding Styles

Since the API has gone under the major updates, the classes/properties/methods and the way they are used has also been changed. The following is the code comparison of some common metadata operations. This will give you an overview of how things have changed.

### **Finding Metadata using Regular Expressions** {#MigrationNotes-FindingMetadatausingRegularExpressions}

The following code samples retrieve metadata from a file using a regular expression.

#### **Legacy API**

{{< gist GroupDocsGists b02f66ab5a9408f72b920cf030ce064a "ExtractMetadataFromDocument_old.cs" >}}

#### **v19.11 or Later**

{{< gist GroupDocsGists b02f66ab5a9408f72b920cf030ce064a "ExtractMetadataFromDocument_new.cs" >}}

### **Replacing Metadata using Regular Expressions** {#MigrationNotes-FindingMetadatausingRegularExpressions}

The following code samples show how to replace metadata properties using a regular expression.

#### **Legacy API**

{{< gist GroupDocsGists b02f66ab5a9408f72b920cf030ce064a "ReplaceMetadata_old.cs" >}}

#### **v19.11 or Later**

{{< gist GroupDocsGists b02f66ab5a9408f72b920cf030ce064a "ReplaceMetadata_new.cs" >}}

For more details, please have a look at the [migration notes](https://docs.groupdocs.com/display/metadatanet/Migration+Notes).

You can download and evaluate the source code examples of the latest release from the [GitHub repository](https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-.NET). For more details about every feature of the API, please visit the [documentation](https://docs.groupdocs.com/display/metadatanet/Home). In case you find something difficult for you, feel free to contact us via our free support [forum](https://forum.groupdocs.com/c/metadata).




