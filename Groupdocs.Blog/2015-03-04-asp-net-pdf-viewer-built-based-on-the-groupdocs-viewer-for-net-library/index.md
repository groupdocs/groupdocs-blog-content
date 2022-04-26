---
title: 'C# Demo Project of an ASP.NET PDF Viewer Built Based on the GroupDocs.Viewer for .NET Library'
date: Wed, 04 Mar 2015 08:16:18 +0000
draft: false
url: /2015/03/04/asp-net-pdf-viewer-built-based-on-the-groupdocs-viewer-for-net-library/
author: 'Stanislav Tatarin'
summary: ''
tags: ['.net library', 'asp.net pdf viewer', 'c# demo', 'GroupDocs Viewer', 'PDF viewer']
categories: ['GroupDocs.Viewer Product Family']
---



{{< figure align=center src="images/pdf.png" alt="ASP.NET PDF Viewer - C# Sample">}}


Building a simple ASP.NET PDF viewer is quite a trivial task. There are tens of different open source projects across the web that offer a quick and free solution to display PDF documents in both ASP.NET MVC and Web Forms. Often a simple implementation of a PDF viewer is all you actually need. But things become a lot more complicated when the viewer needs to meet your customer’s business requirements. The most common are:

**1\. Security.** This obvious business demand creates great challenges for developers when implementing a PDF viewer. Businesses demand uncompromised security for their confidential documents. You need to prevent any access to source PDFs from the client-side and limit or totally restrict viewers from being able to download, print or copy the shared PDF documents.

**2\. Cross-Platform Compatibility.** Businesses require being able to share PDFs with customers, partners and team members without worrying about whether they have the software needed to open the documents. Hence, you need to be sure that end users can access and view the shared PDF documents from any web-enabled device and regardless of the browser used.

**3\. Usability.** Finally, businesses want to have tools delivered by standard office software, such as Adobe Reader, to be able to seamlessly browse and collaborate on PDF documents from a web-browser.

If you’ve been looking for an ASP.NET PDF viewer that meets all the mentioned requirements, you may be interested to try out this C# demo which is built based on the [GroupDocs.Viewer for .NET library](https://products.groupdocs.com/viewer/net). The demo helps you quickly setup, configure and explore key features and functionality of the out-of-the-box PDF viewer for ASP.NET.

Before proceeding, I’d like to clarify that the GroupDocs.Viewer for .NET is a commercial library and is not free or open source. The C# demo includes a free evaluation copy of the library that has several functional restrictions. However, I’d strongly encourage you to [contact GroupDocs support](https://forum.groupdocs.com/c/viewer) for a free 30-day license to be able to test the ASP.NET PDF viewer without any restrictions.

So, here we go. First, let’s look into how the library works:

### Back-End

GroupDocs.Viewer for .NET is a downloadable library (DLL) that allows you to display different types of documents (including PDF) on the web. What makes it stand out from other web-based PDF viewers is its **client-server** (or “thin client”) architecture.

Unlike **client-based** viewers, GroupDocs.Viewer for .NET doesn’t download source PDFs to end user machines. Instead, the library converts original documents stored on the server into a set of HTML markup, CSS and images. Once converted, a web-compatible copy of the PDF document is streamed to clients and rendered in web-browsers just like a regular web-page. Web copies look exactly like the original PDFs. Layouts are retained and fonts are sharp.

Such “thin client” architecture allows you to build an ASP.NET PDF viewer that meets both of the two core business requirements – security and cross-platform compatibility. End users can view PDF documents using a standard web-browser and without having to install Adobe Reader, Flash or any other plugins. For sure, PDF documents can be properly displayed in Chrome, Mozilla Firefox, Safari5+, Opera and, what is important, in commonly used by large organizations – Internet Explorer 8+.

The original PDF files are not downloaded to user machines during view sessions, but stay secure on your server and behind your firewalls. Combined with the in-built Digital Rights Management (DRM) features, this allows businesses to share PDF documents in a “**read-only**” mode. DRM controls all document copy options available in a web-browser, including downloading, printing and text copy/pasting. It allows users to decide on their own which PDFs to share in the “read-only” mode and which – with full access rights.

When displaying PDF documents in a web-browser there is another potential security flaw, called “Print Screen”. This is where even DRM won’t help. To deal with the issue, we’ve implemented a capability to add watermarks over the displayed PDF documents. The watermarks are only rendered as a separate layer on top of the displayed documents, so that your original PDFs are not altered.

Now, what about usability?

### Front-End

GroupDocs.Viewer for .NET comes with an out-of-the-box GUI which can be seamlessly white-labeled and integrated into any ASP.NET site. The GUI provides end users with tools needed for convenient viewing and navigation of PDF documents in a browser. Our sample PDF viewer for ASP.NET provides all the most commonly used UI controls available in native Adobe Reader’s plugin, including:

*   Scroll view, one page in a row, two pages in a row view, double page flipping
*   Page rotation and zooming
*   Page thumbnails
*   Text selection and copying to the clipboard
*   Text search with different match types
*   Document downloading and printing

The GUI can be seamlessly customized and embedded straight to your ASP.NET site. Alternatively, you can build your own GUI from scratch to meet your customer’s requirements.

But enough with words – let’s take a look how this works. Below is an example of how your ASP.NET PDF viewer built based on the GroupDocs.Viewer for .NET library may look:

### Requirements

*   Being a “thin client” solution, GroupDocs.Viewer for .NET doesn’t require any downloads or installations on the client side. End users can view PDF documents from any standard web-browser, including IE8+, Mozilla Firefox, Chrome, Opera, Safari5+ and their mobile versions.
*   To deploy and properly configure the sample on the server, you will need a **.NET Framework** version 4.0+ and a “.NET-compatible” web-server: **IIS**, **IIS Express** or **ASP.NET Development Server (Cassini)**.
*   The viewer works with both **ASP.NET Web Forms** and **ASP.NET MVC** version 3+ frameworks.

### Running the Sample

To help you setup and run the ASP.NET PDF viewer quickly, we’ve prepared a quick start guide. Please [refer to this page](https://downloads.groupdocs.com/viewer/net) for further instructions, as well as to download the C# demo itself.

For more details on the GroupDocs.Viewer for .NET library and the list of all supported file formats, please go to the [products homepage](https://products.groupdocs.com/viewer/net).




