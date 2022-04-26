---
title: 'Footnote Comparison Issue is  Resolved'
date: Fri, 24 May 2019 08:54:04 +0000
draft: false
url: /2019/05/24/footnote-comparison-issue-is-resolved/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Comparison for .NET', 'GroupDocs.Comparison Product Family']
---

Footnote appears at bottom of the page and used to cite information. Previously, API was not comparing Footnotes correctly. But with the release of GroupDocs.Comparison for .NET [19.5](https://docs.groupdocs.com/display/comparisonnet/GroupDocs.Comparison+for+.NET+19.5+Release+Notes), we fixed this issue. Please have a glance.



{{< figure align=center src="images/footnote-comparison-1024x588.png" alt="">}}


But this is not it we have a lot more to tell you. Along with bug fixes, some features and improvements are also introduced.

Lets talk about new features first. Did you ever think of getting _coordinates_ of document changes or differences? It could be confusing at first but let me elaborate this. In your output or resultant document, you get every detail of inserted, deleted or style changed items. What else you can get now is the coordinate details where changes or differences actually occurred. Currently this feature is supported for only PDF, Slide and Diagram formats.



{{< figure align=center src="images/coordinates-changes-1-1024x286.png" alt="">}}


To use this feature you should specify _CalculateComponentCoordinates_ property in _ComparisonSettings_.

{{< gist GroupDocsGists 7c8087bd2dfc512d00d728b133ea6ccd "CalculateComponentCoordinates.cs" >}}

Let's see a complete use-case.

{{< gist GroupDocsGists 3460009559be7e1449de5b8564c39cb0 "CalculateComponentCoordinatesusecase.cs" >}}

Coming to the second feature, its about _DocumentInfo_. This class contains following properties:

*   NumberOfPages (read only) - count of document pages
*   PagesData (read only) - list of _PageInfo_ classes

_PageInfo_ class contains following properties:

*   Width - the width of page
*   Height - the height of page

{{< gist GroupDocsGists c5dddc79f55368c9c8c0e9ffaa27568e "documentinfo.cs" >}}

Following are the improvements:

*   Change detection in tables for Word documents
*   Error handling improvements for all the formats

Major Bug Fixes

*   Can't get images for HTML files
*   Incorrect difference info in PDF
*   Font detection exception
*   Word separation exception

We'd recommend you to [download](https://www.nuget.org/packages/GroupDocs.Comparison/) latest release of the API and enhance your document comparison experience.




