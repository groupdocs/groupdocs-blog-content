---
title: 'Configurable Redaction using an XML File'
date: Tue, 26 Mar 2019 08:12:01 +0000
draft: false
url: /2019/03/26/configurable-redaction-using-an-xml-file/
author: 'Muhammad Umar'
summary: ''
tags: ['Configurable Redaction', 'metadata redaction', 'Phrase redaction']
categories: ['GroupDocs.Redaction for .NET', 'GroupDocs.Redaction Product Family']
---

  
A configuration file defines the initial or commonly used parameters, options, settings or preferences applied to operating systems, infrastructure devices or applications in an IT context.  

## When the Need Arises

If you have large size data (may consist of multiple files of different file formats) or corporate sensitive data which need to be redacted without specifying the rules in your code.

## What is the Solution

The **GroupDocs.Redaction** API provides the way to define a removal policy by writing the list of pre-configured redaction rules in an XML file. Hence, you do not need to specify the rules in your code. You can have as many policies, as you need to redact your documents.

The example of redaction policy XML file is as follows:

{{< gist GroupDocsGists f83062174ce885476d9a1664e33757b9 "RedactionPolicy.xml" >}}

## How to Apply Redaction Policy

The example below shows:

*   how to apply the redaction policy to all files by giving inbound folder
*   Save the output files to one of outbound folders
*   The successfully updated files and failed one will save to their respected folders
*   The current date and time is used as a part of output file name
*   The successfully updated files and failed one will save to their respected folders

{{< gist GroupDocsGists e2ed425ec7b856a1889c084019f2ddec "ConfigurableRedaction_19.3.cs" >}}

The complete ready to run code sample is available on [GitHub](https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET/).




