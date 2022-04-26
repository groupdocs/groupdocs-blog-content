---
title: 'Color Chart Series Dynamically in Email Messages using GroupDocs.Assembly for .NET 18.6'
date: Sat, 14 Jul 2018 07:05:43 +0000
draft: false
url: /2018/07/14/color-chart-series-dynamically-in-email-messages-using-groupdocs.assembly-for-.net-18.6/
author: 'Ali Ahmed'
summary: ''
tags: ['Document Assembly API']
categories: ['GroupDocs.Assembly for .NET', 'GroupDocs.Assembly for .NET Releases', 'GroupDocs.Assembly Product Family']
---

![](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/04/groupdocs-assembly-net.png)[GroupDocs](https://www.groupdocs.com/) team is proudly announcing two new features and three enhancements in the monthly release of [GroupDocs.Assembly for .NET](https://products.groupdocs.com/assembly/net) **18.6**. Using the latest version, you can now use C# 6.0 null-conditional operators **?. **and **?\[\]**. Change the color of chart series and individual point series dynamically for Email Messages with HTML and RTF bodies. Furthermore, to enhance the API,  colors are preserved for a pie chart in the Word Processing document, fonts are preserved for a chart title, and static colors are preserved for chart series in the Email document. We recommend you to [install](https://www.nuget.org/packages/GroupDocs.Assembly/) and use the latest version of the API.

## Features IntroducedFollowing new features are introduced in version 18.6 of the API.

*   [Chart Series Coloring in Email Document](https://docs.groupdocs.com/display/assemblynet/Chart+Series+Coloring+in+Email+Document)
*   [Individual Point Series Coloring in Email Document](https://docs.groupdocs.com/display/assemblynet/Individual+Series+Point+Coloring+in+Email+Document)
*   [Support C# 6.0 null-conditional ?. and ?\[\] operators in template expressions ](https://docs.groupdocs.com/display/assemblynet/Template+Syntax+-+Part+1+of+2#TemplateSyntax-Part1of2-UsingOperators)

## Dynamic Coloring of Chart SeriesFor a chart with dynamic data, you can set colors of chart series dynamically based upon expressions. To use the feature, do the following steps:

*   Declare a chart with dynamic data in the usual way
*   For chart series to be colored dynamically, define corresponding color expressions in names of these series using **seriesColor** tags having the following syntax:

`<<seriesColor[color_expression]>>`

## Dynamic Coloring of Individual Series PointFor a chart with dynamic data, you can set colors of individual chart series points dynamically based upon expressions. To use the feature, do the following steps:

*   Declare a chart with dynamic data in the usual way
*   For chart series with points to be colored dynamically, define corresponding color expressions in names of these series using **pointColor** tags having the following syntax:

`<<pointColor[color_expression]>>`

## EnhancementsFollowing enhancements are introduced in version 18.6 of the API.

*   Preserve the color of an of pie chart split slice when using dynamic chart series coloring for Word Processing documents
*   Preserve the font of a chart title while changing its text dynamically in emails
*   Preserve the static color of a chart series when dynamically filling it with data in emails

## Available Channels and ResourcesHere are a few channels and resources for you to download, learn, try and get technical support on GroupDocs.Assembly for .NET.

*   [Installation](https://www.nuget.org/packages/GroupDocs.Assembly/ "GroupDocs.Assembly Nuget Package") - Install GroupDocs.Assembly using NuGet
*   [Documentation](https://docs.groupdocs.com/display/assemblynet/Getting+Started "Assembly API documentation") - API Documentation
*   [Examples/Plugins/Showcases](https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-.NET/tree/master/Examples "How to use Assembly API") - Source Code Examples, Plugins, and Assembly Editor Application
*   [Video Tutorials](https://www.youtube.com/watch?v=7FfYiii_PcM&t=0s&list=PL25CTxMCj5vOzsaE9Rwjwd4-OwvdaWmJ8&index=2 "Assembly API YouTube Tutorials") - YouTube API Videos
*   [Product Support Forum](https://forum.groupdocs.com/c/assembly) - Technical Support Forum for GroupDocs Assembly

## FeedbackAs always, if you have some questions, queries or suggestions about [GroupDocs.Assembly](https://products.groupdocs.com/assembly/net ".NET Assembly API") for .NET API,  just share with us by creating a [forum thread](https://forum.groupdocs.com/c/assembly).




