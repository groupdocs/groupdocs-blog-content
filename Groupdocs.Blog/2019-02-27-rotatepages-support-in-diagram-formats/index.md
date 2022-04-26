---
title: 'RotatePages Support in Diagram Formats'
date: Wed, 27 Feb 2019 14:54:38 +0000
draft: false
url: /2019/02/27/rotatepages-support-in-diagram-formats/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Merger for Java', 'GroupDocs.Merger Product Family']
---

Page rotation mechanism is one of the fundamental techniques when it comes to document manipulation and modification. As you know this feature is already supported by the API but for the limited file formats. Hence, in this month's release of GroupDocs.Merger for Java [19.2](https://docs.groupdocs.com/display/mergerjava/GroupDocs.Merger+for+Java+19.2+Release+Notes), we implemented this feature for Diagram formats. By defining page number(s) and rotation angle you can achieve the purpose. Let's see how simple it is.

{{< gist GroupDocsGists c5d682dc8ba12d4f10cf4f26910d34a0 "rotatePagesOnKnownForamt.java" >}}

We also added **SwapPages** support for Note format.

{{< gist GroupDocsGists 17c3111caf511725760bbd3db43beee3 "swapProtectedKnownFormat.java" >}}

## Bug Fixes

*   Document Save method throws exception: System.ObjectDisposedException
*   PostScript document is loading with error
*   Page rotation is not saving for EPUB format

You can try GroupDocs.Merger for Java today without any third-party dependency. Download API [here](https://downloads.groupdocs.com/merger/java). If you have any questions or comments about this blog post, please use [forum](https://forum.groupdocs.com/c/merger).




