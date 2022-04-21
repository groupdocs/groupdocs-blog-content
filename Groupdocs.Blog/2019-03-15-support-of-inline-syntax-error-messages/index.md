---
title: 'Support of Inline Syntax Error Messages'
date: Fri, 15 Mar 2019 17:59:31 +0000
draft: false
url: /2019/03/15/support-of-inline-syntax-error-messages/
author: 'Usman Aziz'
summary: ''
tags: ['document automation', 'Document Generation API for .NET', 'Dynamic Report Generation', 'Report Generation API for .NET', 'Report Generation API for Java']
categories: ['GroupDocs.Assembly for .NET Releases', 'GroupDocs.Assembly for Java Releases', 'GroupDocs.Assembly Product Family']
---

We are back with the latest release of [GroupDocs.Assembly for .NET](https://products.groupdocs.com/assembly/net). In this post, I am going to give you an overview of the latest release including the demonstration and usage of an exciting feature. Let's not wait and walk through what's new in the latest release. You may also have a glance at the [release notes](https://docs.groupdocs.com/display/assemblynet/GroupDocs.Assembly+for+.net+19.3+Release+Notes) of the latest release.

GroupDocs.Assembly allows you to generate automated reports by populating the pre-defined document templates. The document templates contain the LINQ statements that are evaluated by GroupDocs.Assembly engine during the run-time. By default, the API throws an exception whenever some incorrect syntax is found in the template. The exception contains the reason and the tag/expression where the error has happened.

But, how would you find the exact place of error when you are dealing with a complex template containing a number of tags and expressions?

No need to worry at all. You can save your time and minimize the efforts in finding the place of error in the template using Inline Syntax Error Messages. Using the inline messages embeds the syntax error within the generated report at the same place where the error has occurred, as shown in the following screenshot:



{{< figure align=center src="images/image-1.png" alt="">}}


Now you may wonder how to achieve this. Well, it's just a piece of cake and you only need to set _DocumentAssembler.Options_ property to _DocumentAssemblyOptions.InlineErrorMessages_ as shown in the following code snippet:**.**

{{< gist GroupDocsGists ba66cecb1eacc47b0a6dd18867c3dc04 "InlineError.cs" >}}

For working examples, you may consult our documentation article on how to use [inline error messages](https://docs.groupdocs.com/display/assemblynet/Use+of+In-line+Syntax+Error+Messages+into+Templates).

## Enhancements in v19.3

Along with the aforementioned feature, we have added a couple of enhancements in the latest release. These enhancements allow you to use null values for image tag and doc tag expressions.

Now, you would have got the idea of how the integration of the latest version may enhance your applications. You may quickly try out the API features by [downloading](https://downloads.groupdocs.com/assembly/net) the latest version as well as cloning and exploring the examples project from [GitHub repository](https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-.NET). In case you would have any questions or queries, just reach us on our [forum](https://forum.groupdocs.com/) and we would love to have a conversation with you.




