---
title: 'Change page orientation of a Word document in C#'
date: Wed, 13 Nov 2019 06:46:18 +0000
draft: false
url: /2019/11/13/change-page-orientation-of-a-word-document-in-csharp/
author: 'Atir Tahir'
summary: ''
tags: ['change orientation', 'page orientation']
categories: ['GroupDocs.Merger Product Family']
---

Do you want to change orientation (e.g. landscape, portrait) of a single or multiple pages in a Word document? GroupDocs.Merger for .NET allows you to do this with just a few lines of code.

**Usage**

Below are the steps to change page orientation:

*   Initialize _OrientationOptions_ class with desired orientation mode and page numbers
*   Instantiate _Merger_ objectwith source document path or stream
*   Call _ChangeOrientation_ method and pass _OrientationOptions_ object to it
*   Call _Save_ method specifying file path to save resultant document

**Code Implementation**

\[gist id="0e88b7ea17c45581f7d9d70cdaf1cd35" name=""pageorientation.cs\]

Have a look at the source DOCX file.

*   

{{< figure align=center src="images/source-809x1024.jpg" alt="">}}

    

After changing orientation of first page (from portrait to landscape)

*   

{{< figure align=center src="images/output-800x1024.jpg" alt="">}}

    

We have following helpful resources for you in order to get started:

*   [Download](https://downloads.groupdocs.com/merger/net)
*   [Documentation](https://docs.groupdocs.com/display/mergernet/Home)
*   [Example Project](https://github.com/groupdocs-merger/GroupDocs.Merger-for-.NET)

If you face any API related issue, please post it on [forum](https://forum.groupdocs.com/c/merger).




