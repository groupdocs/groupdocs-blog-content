---
title: 'Embed Inline Syntax Error Messages in Generated Reports using GroupDocs.Assembly for Java 19.3'
date: Fri, 22 Mar 2019 16:10:48 +0000
draft: false
url: /2019/03/22/embed-inline-syntax-error-messages-in-generated-reports-using-groupdocs.assembly-for-java-19.3/
author: 'Usman Aziz'
summary: ''
tags: ['automated report generation', 'document automation', 'Dynamic Report Generation', 'report generation', 'Report Generation API for Java']
categories: ['GroupDocs.Assembly for Java', 'GroupDocs.Assembly for Java Releases', 'GroupDocs.Assembly Product Family']
---

In the latest version of [GroupDocs.Assembly for Java](https://products.groupdocs.com/assembly/java) we have introduced an exciting feature of Inline Syntax Error Messages. Are you thinking about what does make this feature so exciting? Well, I am going to answer it in this post.

First, let's have a brief overview of how does GroupDocs.Assembly generate the reports. GroupDocs.Assembly uses pre-defined document templates that contain the LINQ statements. These templates are evaluated, processed and then populated by API's engine during the run-time. An exception is thrown in case something is wrong with the syntax of the LINQ statements. The exception contains the reason and the tag/expression where the error has happened.

This is not a big deal to find and locate the incorrect syntax in a small template with a few LINQ statements. But, how would you find the exact place of error when you are dealing with a complex template containing a number of tags and expressions?

Here comes the usefulness of Inline Syntax Error Messages. With this feature, the API embeds the error message within the generated report at the same place where the error has occurred, as shown in the following screenshot:



{{< figure align=center src="images/image-1.png" alt="">}}


Now you may wonder how to achieve this. Well, it's just as easy as a pie and you only need to set the options using _DocumentAssembler.setOptions(_  
_DocumentAssemblyOptions.InlineErrorMessages)_ as shown in the following code snippet:**.**

{{< gist GroupDocsGists ba66cecb1eacc47b0a6dd18867c3dc04 "InlineError.java" >}}

For working examples, you may consult our documentation article on how to use [inline error messages](https://docs.groupdocs.com/display/assemblyjava/Use+of+In-line+Syntax+Error+Messages+into+Templates).

Alright! Now you would have got the real picture of how this new feature may help you in your report generation process. So, let's try out the API features by [downloading](https://downloads.groupdocs.com/assembly/java) the latest version as well as cloning and exploring the examples project from [GitHub repository](https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-Java).

Do you have any questions or queries? We welcome you to have a conversation with us on our [forum](https://forum.groupdocs.com/).




