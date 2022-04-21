---
title: 'Retrieve Count of Credits Consumed In GroupDocs.Conversion for .NET'
date: Thu, 11 Jul 2019 12:56:17 +0000
draft: false
url: /2019/07/11/retrieve-count-of-credits-consumed-in-groupdocs.conversion-for-.net/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Conversion for .NET', 'GroupDocs.Conversion Product Family']
---

As you know that API already supports metered licensing.  
**Can we get count of credits consumed?**  
Yes, we have a good news for you. There is a new method _GetConsumptionCredit()_ implemented in _Metered_ class. This method returns count of credits that are consumed in case of Metered licensing is used.  
{{< gist GroupDocsGists 11ed47d2b812b551d2b16dc227bed5da "billingservice.cs" >}}Following example demonstrates how to retrieve count of credits consumed.  
{{< gist GroupDocsGists e84246d14ae0888bd537cb06ca80b198 "getconsumptioncredit.cs" >}}

Let's talk about the new file formats introduced. Most of you might be working with XLAM, an Excel Macro-Enabled Add-In file format. We have added support for this format in GroupDocs.Conversion for .NET [19.6](https://docs.groupdocs.com/display/conversionnet/GroupDocs.Conversion+for+.NET+19.6+Release+Notes) release. You can now do back and forth conversion to XLAM. This is not it. Conversion from following file extensions to any other [supported](https://docs.groupdocs.com/display/conversionnet/Supported+Document+Formats) file format is now possible:

*   MPX
*   JPC
*   DWT
*   JPEF-LS (JIS)

We've also improved Diagram to Word conversion.  
Moreover, converting a PowerPoint document with black SmartArt text to PDF issue is resolved. Previously, SmartArt text in the resultant document was changed to white text.

With all such features and improvements, why wait to give it a try? Download latest release from [here](https://downloads.groupdocs.com/conversion/net) and share your feedback/concerns on our [forum](https://forum.groupdocs.com/c/conversion).




