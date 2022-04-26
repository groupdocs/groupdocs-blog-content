---
title: 'Compare two documents - Control header and footer comparison in C#'
date: Mon, 02 Dec 2019 07:39:52 +0000
draft: false
url: /2019/12/02/compare-two-documents-control-header-and-footer-comparison-in-csharp/
author: 'Atir Tahir'
summary: ''
tags: ['CSharp', 'document comparison', 'dotnet api', 'GroupDocs']
categories: ['GroupDocs.Comparison Product Family']
---

**Compare two documents but ignore or include header and footer content**. Is this what you need in your document comparison application? Then you must try GroupDocs.Comparison for .NET. This back-end [API](https://products.groupdocs.com/comparison/net) can be implemented in any of your .NET application without any third party tool/software dependency. Those who are already using this API, we have some interesting features and few bug fixes introduced in GroupDocs.Comparison for .NET [19.11](https://docs.groupdocs.com/display/comparisonnet/GroupDocs.Comparison+for+.NET+19.11+Release+Notes).

## Set output paper size

A new property **PaperSize** is introduced in **CompareOptions** class using that you can adjust paper size of the resultant document (e.g. PaperSize.A4). If you don't set PaperSize value, output file will has paper size same as target document by default.

\[gist id="29d72ee453257df10c4051cb19e16807" name="papersize.cs"\]

## Multi comparer for Email and Text formats

API now allows you to compare more than one email and text (target) files.

\[gist id = "49d4bd20d6f1431d80a47f60584958de" name = "multiemailcomparison.cs"\]

Comparing multiple text files follow same procedure.

## Switch header and footer comparison

A new property **HeaderFootersComparison** is introduced in **CompareOptions** class. If you don't want to compare header/footer of a document, just set this property to false.

\[gist id="50bc0ac4ff27812b1e2cc909aec3bf08" name="headerfootercomp.cs"\]

Following are some of the main bug fixes introduced in latest release:

*   API is not releasing file handles
*   Incorrect box dimensions and position
*   Exception during comparing PDF-files without license

Get API from [download](https://downloads.groupdocs.com/comparison/net) section. Explore [developer guide](https://docs.groupdocs.com/display/comparisonnet/Developer+Guide) and in case of any issue, post it on [forum](https://forum.groupdocs.com/c/comparison).




