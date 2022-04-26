---
title: 'A Complete Guide for Developing a GroupDocs.Viewer for .NET Plugin for Kentico CMS'
date: Fri, 08 May 2015 21:36:39 +0000
draft: false
url: /2015/05/08/complete-guide-for-developing-a-groupdocs-viewer-for-net-plugin-for-kentico-cms/
author: 'Denis Gvardionov'
summary: ''
tags: ['.net library', 'GroupDocs Viewer', 'kentico', 'zArchive']
---

[![GroupDocs.Viewer for .NET](https://blog.groupdocs.com/wp-content/uploads/sites/4/2014/04/GD_VWR_NETIcon_114.png)](https://docs.groupdocs.com/viewer/net)As you may have already noticed, GroupDocs has many [plugins available for 3rd party platforms](http://groupdocs.com/marketplace/plugins) and across all products we offer. We constantly expand this list and a few months ago we have [announced](https://blog.groupdocs.com/display-pdf-microsoft-office-and-other-document-types-on-your-kentico-site) a release of the new GroupDocs.Viewer for .NET plugin for Kentico CMS. This new plugin is very different from the cloud-based version we released earlier. The cloud-based version simply creates an iframe on a web-page where you want to display a document and redirects all input documents to the GroupDocs’ cloud API. This requires your documents to be temporary stored on GroupDocs’ servers. Although we use secure Amazon EC2 infrastructure, there are cases when you need to keep documents on your own servers without exposing them to the Internet. For example, you may have confidential documents that you definitely don’t want to send via Internet, or your website may be located on the intranet, etc. Unlike the cloud-based version, this new plugin is a truly low-level integration that doesn’t require any external API calls, or use of iframes. More than that, the viewer was integrated right into an existing Kentico component, extending its basic functionality. Today, I’d like to share a detailed guide showing all the steps I went through while developing the plugin. Please note that the article is not a step-by-step manual on how to install the plugin (you can find such manuals inside the plugin package). Instead, in this article I’d like to share my experience in developing a full-integration plugin for Kentico CMS. The article may help you in developing your own plugins for Kentico, see what issues I’ve encountered with and how I solved them when developing the plugin. Of course, the article will be also useful for those of you who’d like to have more details on how GroupDocs.Viewer works inside Kentico, how to install the viewer and eliminate any possible obstacles. So here we go – please find the article on [this page](https://docs.groupdocs.com/viewer/net).




