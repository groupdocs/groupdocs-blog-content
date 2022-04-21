---
title: 'Restart the List Numbering Dynamically within Your Document'
date: Thu, 25 Jul 2019 08:07:21 +0000
draft: false
url: /2019/07/25/restart-the-list-numbering-dynamically-within-your-document/
author: 'Usman Aziz'
summary: ''
tags: ['.NET', 'API', 'document automation', 'Dynamic Report Generation', 'Generate Reports', 'java', 'numbered list', 'Report Generation API for .NET', 'Report Generation API for Java', 'restart numbered list']
categories: ['GroupDocs.Assembly for .NET Releases', 'GroupDocs.Assembly for Java Releases', 'GroupDocs.Assembly Product Family']
---

Nested or the multi-level numbered lists allow you to group the items based on the parent item. Put it simply, you can separately list the items under each group. This becomes very useful when you have to list the items having multiple sub-items. Let's have a look at the following figure which makes it simpler to understand the scenario.



{{< figure align=center src="images/Lists-2-1024x1024.png" alt="">}}


In this figure, you can observe that there are listed 3 groups and each group further has multiple items listed under it. So, in such cases nested numbered list is used.

Lets now check out how could you populate a numbered list within your Word documents using _GroupDocs.Assembly_. Assume that you have the _Order_ and _Service_ classes defined in your application in such a way that each order instance has multiple services. The following template will be used to output the orders along with the services they have using the API:

{{< gist GroupDocsGists 8cc73fe8a55e64e0e7d5c59e347724c4 "list_template.h" >}}

The Word document that will be generated in the result of the above template will contain the following listing:



{{< figure align=center src="images/output-1.png" alt="">}}


The perfect output, isn't it? No, not at all. You would have noticed that the numbering of the list is disturbed. Yes, the numbering sequence is continued and it hasn't restarted for the second list. Well, this is the expected behavior when you generate the numbered list using this template.

So how would you deal with such a situation when you want to restart the list's numbering? Well, believe me, it is as simple as a pie. Just place a _restartNum_ tag before the inner _foreach_ and you are done.

This is how the updated version of the template will look like. We have now placed _restartNum_ tag to restart the list numbering for each order.

{{< gist GroupDocsGists 8cc73fe8a55e64e0e7d5c59e347724c4 "list_template_restart.h" >}}

And what we have got in the output is:



{{< figure align=center src="images/output2.png" alt="">}}


**Perfect!**

At the moment, you can restart the list numbering within the Word Processing documents as well as email messages with HTML and RTF bodies.

So if you want to have this feature in your application, just [download](https://downloads.groupdocs.com/assembly) and integrate **v19.7** of _GroupDocs.Assembly for .NET_ or _Java_. For working code samples, download or clone the examples project from the [GitHub repository](https://github.com/groupdocs-assembly/). Cheers!




