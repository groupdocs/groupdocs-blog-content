---
title: 'Access Metadata Properties from PPS, PPSX, PPSM, and vCard Formats'
date: Wed, 12 Jun 2019 18:11:09 +0000
draft: false
url: /2019/06/12/access-metadata-properties-from-pps-ppsx-ppsm-and-vcard-formats/
author: 'Usman Aziz'
summary: ''
tags: ['Access Metadata', 'document properties', 'document-metadata', 'get metadata', 'PPS', 'PPSM', 'PPSX', 'vCard', 'VCF']
categories: ['GroupDocs.Metadata Product Family']
---

Another month, another release! We have recently released version 19.5 of GroupDocs.Metadata for .NET and Java and today I am going to give you an overview of what's new that we have brought for you in the latest release.

In v19.5, we mainly focused on providing the support of some major as well as popular formats. So, this resulted in the addition of the following file formats:

*   **[PPS](https://wiki.fileformat.com/presentation/pps/)** - The PowerPoint Slideshow file format that is created using Microsoft PowerPoint and it is used for the slide show purpose. It is similar to the PPT format, however, unlike PPT, the presentation mode starts automatically when the PPS file is opened.
*   **[PPSX](https://wiki.fileformat.com/presentation/ppsx/)** - An updated version of the PPS format that was supported by Microsoft PowerPoint 97-2003 versions.
*   **[PPSM](https://wiki.fileformat.com/presentation/ppsm/)** - It represents a Macro-enabled Slide Show file format that is created with Microsoft PowerPoint 2007 or higher for running the slideshow.
*   **[vCard](https://wiki.fileformat.com/email/vcf/)** - Or VCF (Virtual Card Format) is a digital format that is used to store the contact information. It is a popular and widely used file format for information exchange.

The PPS, PPSX and PPSM file formats will be accessed in the same way that you have been using for other presentation formats using _PptFormat_ class. For the vCard format, we have introduced _VCardFormat_ class and this is how you can access the properties of a .vcf file.

**C#**

{{< gist GroupDocsGists 44b809a3798c4aed596e63064bf5b40d "GetPropertiesFromVCard.cs" >}}

**Java**

{{< gist GroupDocsGists 44b809a3798c4aed596e63064bf5b40d "GetPropertiesFromVCard.java" >}}

Not only this but we have also added the feature of checking the amount of credits that are spent using the metered license.

**C#**

{{< gist GroupDocsGists 44b809a3798c4aed596e63064bf5b40d "GetSpentCredit.cs" >}}

**Java**

{{< gist GroupDocsGists 44b809a3798c4aed596e63064bf5b40d "GetSpentCredit.java" >}}

Well, that's it from my side and now, it's your turn to evaluate these features by downloading and using the [latest version](https://downloads.groupdocs.com/metadata) of the APIs. In case of any confusion or query, please feel free to post on our [forum](https://forum.groupdocs.com/).




