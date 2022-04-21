---
title: 'A simplified and easy to use document comparison API'
date: Thu, 19 Sep 2019 14:10:42 +0000
draft: false
url: /2019/09/19/a-more-simplified-and-easy-to-use-document-comparison-api/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Comparison for .NET', 'GroupDocs.Comparison Product Family']
---

A major advantage of GroupDocs.Comparison for .NET is its ability to tightly integrate with any .NET project. This integration gives an extra mark to your application or project. GroupDocs.Comparison for .NET [19.9](https://docs.groupdocs.com/display/comparisonnet/GroupDocs.Comparison+for+.NET+19.9+Release+Notes) comes with a lot of breaking changes. The legacy API have been moved into Legacy namespace**.** So, when you update to this version it is required to make project-wide replacement of namespace usages from **GroupDocs.Comparison**. to **GroupDocs.Comparison.Legacy** to resolve build issues.

Below are the **key reasons** to use the new updated API since version 19.9:  

*   _Comparer_ class introduced as a single entry point to compare documents of any supported file format with various options and ability to accept/reject found differences in resultant document
*   Overall document related classes are unified to common
*   API architecture is redesigned from scratch in order to simplify passing options and classes to manipulate comparison
*   Document information and preview generation procedures are simplified

**How to migrate?**

Lets see briefly that how much things have been changed. Below is the code snippet that we used to write for documents comparison in older versions:

{{< gist GroupDocsGists bbfd2f409e3d06d755d83054279099a6 "oldcomparison.cs" >}}

And given below is the most recent/updated code:

{{< gist GroupDocsGists 79581e353096926250aced7110bc8aae "newcomparison.cs" >}}

**Is there any updated support material?**

Yes, we have updated GitHub [examples](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-.NET) and [documentation](https://docs.groupdocs.com/display/comparisonnet/Developer+Guide) as well. Please download or clone latest example project and observe the difference yourself.

If you would face any issue while using or upgrading to the latest release, just post it on our [forum](https://forum.groupdocs.com/categories) and we will assist you.




