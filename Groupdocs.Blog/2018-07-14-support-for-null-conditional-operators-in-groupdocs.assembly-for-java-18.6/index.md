---
title: 'Support for Null-Conditional Operators in GroupDocs.Assembly for Java 18.6'
date: Sat, 14 Jul 2018 07:04:04 +0000
draft: false
url: /2018/07/14/support-for-null-conditional-operators-in-groupdocs.assembly-for-java-18.6/
author: 'Ali Ahmed'
summary: ''
tags: []
categories: ['GroupDocs.Assembly Product Family']
---

[![Document Assembly API](http://blog.groupdocs.com/wp-content/uploads/sites/4/2017/03/groupdocs-assembly-java-1.png)](https://www.groupdocs.com/products/assembly/java)We are excitedly announcing the monthly release of [GroupDocs.Assembly for Java](https://products.groupdocs.com/assembly/java) **18.6**. Using the latest version, you can now use null-conditional operators **?. **and **?\[\]**. Change the color of chart series and individual point series dynamically for Email Messages with HTML and RTF bodies. Furthermore, to enhance the API,  colors are preserved for a pie chart in the Word Processing document, fonts are preserved for a chart title, and static colors are preserved for chart series in the Email document. We recommend you to [install](https://artifact.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-assembly/maven-assembly.xml) the latest version of API for a better experience.

## Features IntroducedFollowing new features are introduced in version 18.6 of the API.

*   [Chart Series Coloring in Email Document](https://docs.groupdocs.com/display/assemblyjava/Chart+Series+Coloring+in+Email+Document)
*   [Individual Point Series Coloring in Email Document](https://docs.groupdocs.com/display/assemblyjava/Individual+Series+Point+Coloring+in+Email+Document)
*   [Support null-conditional ?. and ?\[\] operators in template expressions ](https://docs.groupdocs.com/display/assemblyjava/Template+Syntax+-+Part+1+of+2#TemplateSyntax-Part1of2-UsingOperators)

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

## Available Channels and ResourcesHere are a few channels and resources for you to download, try, learn and get technical support on GroupDocs.Assembly for Java:

*   [Installation](https://artifact.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs/groupdocs-assembly/maven-assembly.xml) - Install GroupDocs.Assembly from Maven
*   [Documentation](https://docs.groupdocs.com/display/assemblyjava/Getting+Started) – API docs
*   [Examples](https://github.com/groupdocs-assembly/GroupDocs.Assembly-for-Java) – Source code examples
*   [Product Support Forum](https://forum.groupdocs.com/c/assembly) – Technical support forum for GroupDocs.Assembly product family

## FeedbackWe always love to hear your valuable feedback. Share your suggestions, questions, or queries related to GroupDocs.Assembly for Java at our [forum](https://forum.groupdocs.com/c/assembly).




