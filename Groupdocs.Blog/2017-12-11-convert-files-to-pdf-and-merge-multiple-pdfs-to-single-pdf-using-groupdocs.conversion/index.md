---
title: 'BoardPro Converts Files into PDF and Merge Multiple PDFs to Single PDF using GroupDocs.Conversion'
date: Wed, 22 Jan 2020 09:56:00 +0000
draft: false
url: /2017/12/11/convert-files-to-pdf-and-merge-multiple-pdfs-to-single-pdf-using-groupdocs.conversion/
aliases:
    - /2020/01/22/converting-files-into-pdf-and-merging-multiple-pdfs-to-single-pdf-using-groupdocs.conversion/
author: 'Zeeshan Bhatti'
summary: ''
tags: ['Success Stories']
---

## About BoardPro



{{< figure align=center src="images/boardpro-logo.png" alt="">}}


[BoardPro](https://www.boardprohub.com/) is an innovative cloud-based startup developing board management software specifically designed to meet the requirements and governance workflows of the board of directors of small to medium businesses and non-profits. It is an easy-to-use software for board meetings, responsibilities, and documents. It is designed specifically to meet the challenges of limited resources and limited experience. Professional corporate boards can afford extensive governance and administration resources, freeing directors to focus on making a powerful contribution. However, many SME’s and non-profit organisations lack these dedicated resources, meaning they often run less effectively, despite the quality of their directors. BoardPro has taken best practices from corporate boards and simplified and automated these for SME and non-profit boards. Today, still in its early days, BoardPro is used by over 200 boards. In the first 10 months has hosted over 1000 meetings and converted more than 31,000 documents.

## Problem

One of the core features of BoardPro is the production of the meeting “Board Pack”. All the reports and papers for each meeting compiled from a variety of user-uploaded files into a single PDF.

The executives of the organisation are able to go into BoardPro, find the scheduled meeting, and can attach their monthly reports, special papers to the specific agenda items they relate to.

The reports could be uploaded in a wide variety of formats – .pdf, .doc, .docx, .ppt, .pptx, .rtf, .txt, .jpg, etc.

Each file is converted to PDF and then merged into a single PDF in the correct order, with an internally linked Index and Agenda file.

The Board Pack is then distributed to the board members, who can prepare for the board meeting from this single file. No longer are board members receiving multiple documents attached to an email, where they are left wondering which document relates to which agenda item, etc.

## Solution

> BoardPro Limited Using GroupDocs.Conversion to convert user files to PDF
> 
> **Zeeshan Bhatti, BoardPro CTO**

### Our Initial Implementation

To create the Board Pack solution, BoardPro needed a .NET solution for converting a variety of files to PDF. As the executives of the organisation are chronically time-poor, they need to be able to load their reports into BoardPro in the format in which they are written. This means that BoardPro needs to accept the most common office document formats: .pdf, .doc, .docx, .ppt, .pptx, .rtf. txt, .jpg, etc.

These documents are stored in their original format in Azure Blob Storage with SQL Server Table enabling the indexing to enable searching of documents. When the Board Pack is requested, an asynchronous service processes this request, converting all attached files into PDF and combining them into a single resultant PDF.

### System Architecture Level Issues

The earlier implementation of Board Pack feature utilized SyncFusion, a set of libraries for converting various file formats into PDF. Even during the feature implementation phase, we had to constantly work around issues like thread-safety and consistency of behavior and revise system architecture multiple times. Some of these issues are described below.

*   SyncFusion lacked support for conversion of documents on managed Azure services, and required us to launch our Board Pack service hosted in a virtual machine (VM).
*   Single-threaded implementation meant that we could process one request per VM. This was a major bottleneck in the overall system.
*   Some documents caused the Board Pack service VM to suspend. This caused a domino effect of failure to cause all subsequent requests to be blocked.
*   We had to implement redundancy to avoid total system failure as presented in the following diagram.



{{< figure align=center src="images/redundancy-syncfusion.png" alt="redundancy-syncfusion" caption="Fig 1. Redundancy to avoid total system failure when Syncfusion causes VM to suspend">}}


### Document Rendering Issues

After performing a reasonable amount of testing, we launched this feature for our customers and then the disaster struck – many times over.

As soon as the feature was launched, we started getting failures when the uploaded Microsoft Word and PowerPoint documents included embedded objects, linked tables or graph objects. Some of the problems we faced during the conversion of these documents are presented as follows.

*   In some cases, the document conversion failed completely, and users were frequently advised to **convert to PDF** first in the native client. This caused cognitive dissonance among our customers.
*   Some documents were rendered incorrectly e.g., images were rotated at a wrong angle or the chart trendlines were incorrect.
*   All charts were rendered as raster images with low-quality JPEG compression. See an example of this conversion issue as follows.



{{< figure align=center src="images/trendlinechart.png" alt="trendlinechart" caption="Fig 2. Original trendline chart on the left (screenshot from Word), incorrect raster rendering by SyncFusion on the left (screenshot from PDF).">}}


As a result of these issues, we had to constantly apologize to our customers and suggest inconvenient workarounds. Many of these issues could not be reported to SyncFusion because of the sensitivity of user data. However, the issues that were reported, were confirmed to be defects in their product. The disruption and cost to clients and the business sent us in search of another solution that would provide a superior conversion experience.

## Experience

### Benefits gained by switching to GroupDocs

Previously BoardPro had been using SyncFusion generating Board Pack PDFs, which involved converting the user uploaded documents into PDFs and combining them together. This process, as discussed above, was riddled with bugs and scalability issues. After reporting an average of approximately two issues per month to SyncFusion support team, we decided to start looking for alternatives.

Our search lead us to discover [**GroupDocs.Conversion**](https://products.groupdocs.com/conversion). We wanted to be cautious and evaluated GroupDocs for both scalability and reliability before making the final call. In both our evaluation and later implementation to replaced SyncFusion, we have found GroupDocs.Conversion to be a complete winner.

### System Architecture Improvements for Scalability

Unlike SyncFusion that requires special VMs and has thread-safety issues, GroupDocs works flawlessly on Azure App Service, Azure WebJobs, as well as Azure Functions. This allowed us to leverage the massive scalability of Azure Functions. For our customers, this means that the Board Pack queue will no longer be choked, even in the rare cases the feature fails. The following diagram illustrates the improved architecture that uses Azure Functions to achieve scalability in a serverless manner.



{{< figure align=center src="images/leverage-serverless.png" alt="leverage-serverless" caption="Fig 3. Leveraging serverless architecture to achieve massive scalability of the BoardPack feature using GroupDocs.Conversion. This was previously not possible using SyncFusion">}}


### Improved Document Conversion

Having switched to GroupDocs.Conversion, we are yet to discover a single instance where the document conversion fails. In the past, we had kept anonymized versions of the customer documents that failed to convert using SyncFusion, so that we could report them. With GroupDocs.Conversion, we are pleased to find that each one of that document converts flawlessly. All images and tables are rendered correctly, and above all, charts are rendered as vector images that do not distort or introduce JPEG compression artifacts on higher zoom levels. See an example of this conversion as follows.



{{< figure align=center src="images/resultantpdf.png" alt="Flawless rendering of Word Document by GroupDocs.Conversion to convert to PDF. Generates Vector image in the resultant PDF." caption="Fig 4. Original trendline chart on the left (screenshot from Word), flawless rendering by GroupDocs.Conversion on the right (screenshot from PDF). GroupDocs.Conversion generates a Vector image in the resultant PDF.">}}


## Next Steps

BoardPro is continually offering new services to boards of SME’s and non-profit organisations. We have plans for digital signatures, custom document templates and offering a wider range of supported documents to be attached. We are convinced that all of this will be possible using the range of products offered by [GroupDocs](https://products.groupdocs.com/) and [Aspose](https://products.aspose.com/).

## Summary

BoardPro no longer uses its previous solution for converting various document formats to PDF for building the Board Pack – this has been completely replaced using [GroupDocs.Conversion for .NET](https://products.groupdocs.com/conversion/net).

GroupDocs.Conversion was easy to implement and an elegant solution for our requirements at BoardPro. It has allowed us to offer higher scalability and reliability to our customers. We found GroupDocs.Conversion more stable and more effective at converting documents than our previous solution.

The fidelity of documents is very good. Our biggest concern, that executives can upload their files with the complex components they need for their reporting. The concern has been adequately addressed and we have absolute confidence that these will seamlessly be converted and integrated into the Board Pack. Thanks to GroupDocs.Conversion.

We have found GroupDocs [documentation](https://docs.groupdocs.com/) and [support forums](https://forum.groupdocs.com/) to be very helpful. Overall BoardPro has been very impressed with the product and support offered. We wish we had found GroupDocs sooner.

## Contact

For more information on this case study and to request details on the customer’s previous supplier, please contact us at [www.boardprohub.com](https://www.boardprohub.com/)




