---
title: 'EmailOptions Class is Introduced in GroupDocs.Conversion for Java 18.7'
date: Wed, 01 Aug 2018 06:43:19 +0000
draft: false
url: /2018/08/01/emailoptions-class-is-introduced-in-groupdocs.conversion-for-java-18.7/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Conversion for Java', 'GroupDocs.Conversion Product Family']
---

[![GroupDocs.Conversion](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/09/conversion.png?itok=MpNabR9F)](#)

GroupDocs.Conversion for Java 18.7 covers a new feature and a bug fix. MSG to PDF conversion issue is now resolved. Please take a look over the [release notes](https://docs.groupdocs.com/display/conversionjava/GroupDocs.Conversion+for+Java+18.7+Release+Notes) to get an idea about the changes introduced.

## MailOption to control conversions from emailA new class **EmailOptions** is implemented in **SaveOptions**. Using that email options can be managed.```
PdfSaveOptions options = new PdfSaveOptions();
EmailOptions emailOptions = options.getEmailOptions();
emailOptions.setDisplayHeader(true);
emailOptions.setDisplayEmailAddress(true);        
emailOptions.setDisplayFromEmailAddress(true);
emailOptions.setDisplayToEmailAddress(true);
emailOptions.setDisplayCcEmailAddress(true);
emailOptions.setDisplayBccEmailAddress(true);
```

## Bug Fixes

*   MSG to PDF conversion displays incorrect time in the header

## Available Channels and ResourcesHere are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Conversion:

*   [API Home](https://products.groupdocs.com/conversion/java "Product Home") - GroupDocs.Conversion for Java
*   [Download](https://downloads.groupdocs.com/conversion/java "Download API") - GroupDocs.Conversion for Java Download
*   [Documentation](https://docs.groupdocs.com/display/conversionjava/Home "Documentation") - Product Documentation
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-Java "Example projects") - GitHub source code examples
*   [Video Tutorials](https://www.youtube.com/playlist?list=PL25CTxMCj5vPNfkcX3UXzMLKEOZwNpkzN) - YouTube Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/conversion "Support forum") \- Technical Support Forum for GroupDocs.Conversion




