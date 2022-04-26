---
title: 'Support for Diagrams in GroupDocs.Merger'
date: Thu, 21 Mar 2019 08:53:55 +0000
draft: false
url: /2019/03/21/support-for-diagrams-in-groupdocs.merger/
author: 'Samicheema'
summary: ''
tags: []
categories: ['GroupDocs.Merger for .NET', 'GroupDocs.Merger for Java', 'GroupDocs.Merger Product Family']
---



{{< figure align=center src="images/groupdocs-merger.png" alt="GroupDocs Editor for .NET">}}


GroupDocs.Merger now supports diagram formats such as VSDFX, VSDM, VSSX, VSSM and VTX . It allows you to swap, rotate or trim pages in diagrams. Apart for that, you can also set or remove password protection of diagrams. This API comes in both Java and .NET platforms and could be integrated in any your .NET or Java application without any dependency.

# Features for Diagrams Format

## Swap Pages:

This feature allows you to exchange the position of two pages in the document. Following are the lines of code which can be used to swap pages in the diagram:

{{< gist GroupDocsGists 1db6771e3a1b9930667bd13e10a31034 "GroupDocs.Meger-for-.NET_SwapPagesInDiagrams.cs" >}}

Above lines of code are used to swap pages of following VSDX file:



{{< figure align=center src="images/source-1-1024x598.png" alt="">}}


Finally, after performing swap operation on VSDX, the output looks as follows:  



{{< figure align=center src="images/Output-1-1024x600.png" alt="">}}


## Move Page:

This feature allows you to change position of the pages within the document. Following are the lines of code which can be used to change order of the pages in the diagram:

{{< gist GroupDocsGists 778bb12890c352658adca5ab88855867 "GroupDocs.Meger-for-.NET_ChangePageOrderInDiagrams.cs" >}}

## Remove Page:

Using this feature you can remove single or collection of pages from the document. Following example demonstrates how to remove pages in the diagram:

{{< gist GroupDocsGists 9a16a7e5ba191c2169f2287bc5cee091 "GroupDocs.Meger-for-.NET_RemovePagesInDiagrams.cs" >}}

## Split Document:

You can split document into several resulting documents using this feature. Following is the example to split diagram:

{{< gist GroupDocsGists e7f1b9dcbe46acf1bf8754278ada7de0 "GroupDocs.Meger-for-.NET_SplittingByPageRangesInDiagrams.cs" >}}

## Trim Document:

This feature allows you to cut the specific pages of the document. Following are the lines of code which can be used to trim the diagram:

{{< gist GroupDocsGists e16475c2d74c0d5f2aa3a3ea85b6833a "GroupDocs.Meger-for-.NET_TrimDocumentByPageNumListInDiagrams.cs" >}}

## Change Pages Orientation:

This feature allows you to change pages orientation. Following code sample shows how to change orientation of the pages in the diagram:

{{< gist GroupDocsGists 8048d97a30e52a7d6eeaa70617146836 "GroupDocs.Meger-for-.NET_ChangePageOrientationInDiagram.cs" >}}




