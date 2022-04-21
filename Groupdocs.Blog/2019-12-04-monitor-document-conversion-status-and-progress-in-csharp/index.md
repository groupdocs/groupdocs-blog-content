---
title: 'Monitor Document Conversion Status and Progress in C#'
date: Wed, 04 Dec 2019 17:22:19 +0000
draft: false
url: /2019/12/04/monitor-document-conversion-status-and-progress-in-csharp/
aliases:
    - /2019/12/04/monitor-document-conversion-status-and-progress-in-c/
author: 'Atir Tahir'
summary: ''
tags: ['document conversion', 'document conversion progress monitor', 'monitor conversion progress in Csharp', 'monitor conversion status']
categories: ['GroupDocs.Conversion Product Family']
---

With the release of **[GroupDocs.Conversion for .NET](https://products.groupdocs.com/conversion/net)** v[19.11](https://docs.groupdocs.com/display/conversionnet/GroupDocs.Conversion+for+.NET+19.11+Release+Notes) you can now **monitor document conversion progress and status using C#**. There are way many conversions supported by the API, that are listed in the [documentation](https://docs.groupdocs.com/conversion/net/supported-document-formats/).

A new property **Listener** is added. The document converter listener implementation is used for monitoring conversion status and progress. Have a look at **ConverterListener** class that implements **IConverterListener**interface

\[gist id="a6cfd341a0c31ed4a4032930ca924cd0" name="converterlistener.cs"\]

Below is the usage

\[gist id="00650b814d3f850f96d0e2a497a52864" name = "listener.cs"\]

Coming to the improvement, MPP to XLS conversion is improved. Previously, there was an issue in PNG image conversion (e.g. PNG to Word or Presentation). This issue is now fixed. There was another document conversion issue, a particular Word file to PDF with exception: _Could not create the bitmap with the specified parameters._ This bug is also resolved.

Get the latest version from the [download](https://downloads.groupdocs.com/conversion/net) section. If you want to evaluate API features, we have an open-source example project for you that could be downloaded from [GitHub](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET).




