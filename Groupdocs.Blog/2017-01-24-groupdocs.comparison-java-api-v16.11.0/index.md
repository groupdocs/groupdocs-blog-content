---
title: 'Releasing GroupDocs.Comparison for Java 16.11.0 - Compare more than just Text in Documents'
date: Tue, 24 Jan 2017 11:59:24 +0000
draft: false
url: /2017/01/24/groupdocs.comparison-java-api-v16.11.0/
author: 'Amindsk'
summary: ''
tags: []
categories: ['GroupDocs.Comparison for Java', 'GroupDocs.Comparison Product Family']
---

[![GroupDocs.Signature](https://blog.groupdocs.com/wp-content/uploads/sites/4/2016/09/java-comparison-logo.png)](https://www.groupdocs.com/products/comparison/java)

In order to enrich the document comparison experience, team GroupDocs is pleased to release [GroupDocs.Comparison for Java 16.11.0](https://www.groupdocs.com/products/comparison/java) that comes with multitude of new features such as comparison of comments, WordArt objects, forms and many more. API also sums up a lot of improvements and bug fixes. We would recommend you to download latest release of the API and integrate it in your project.

## GroupDocs.Comparison for Java 16.11.0 - New FeaturesAPI comes with following new features:

*   Added page numbers comparison for MS Word
*   Added comparison of group shapes for Word Documents
*   Comparison of comments for MS Word
*   Comparison of WordArt objects in MS Word
*   Comparison of tables in MS Word
*   Comparison of Forms in MS Word
*   Comparison of multi-language in MS Word
*   Object model of Paragraph for PDF
*   Implemented absorber of paragraphs for the basic cases for PDF
*   Added option to compose multiple result list from result lists of each document for MS Word
*   Support comparing multiple documents with track changes for MS Words
*   Added support of absorption of the Page Footer for PDF
*   Added support of absorption of the Page Header for PDF
*   Added apply/discard changes support for multiple result changes list for MS Word
*   Added support for new components: media objects, image positioning for PDF
*   Added support of comparing watermarks for PDF
*   Added support of comparing charts for MS Power Point Presentations
*   Added support of comparing comments for MS Power Point Presentations
*   Added support of style changes detection for MS Power Point Presentations
*   Added support of detection of Picture Frames for MS Power Point Presentations

## Document Comparison API for Java - ImprovementsFollowing are the features that are improved in the latest version of the **GroupDocs.Comparison API**:

*   Improve the comparison of tables, Some tables differ on two cell but algorithm not defined the tables as similar for MS Word
*   Improve comparison for contents list for MS Word
*   Improve cells performance for spreadsheets
*   Improve working with tables for PDF
*   implementation of tables absorption for simple cases for PDF
*   Implement the function cleanOperatorsList for PDF
*   Document processing performance improvement for MS Word
*   Divide text into paragraphs by checking if the text fragments are contained in different parent objects for PDF
*   Improved Comparison paragraph absorber for cases with plain text for PDF
*   Improved text comparison support for all Adobe Acrobat formats for PDF
*   Improved compare tables for PDF
*   Improved comparisonParagraphAbsorber for cases with tables for PDF
*   Improved document builder and page mapper for PDF
*   Improved comparisonParagraphAbsorber for cases with plain text for PDF
*   Improved comparison performance for MS Power Point Presentation
*   Extended engine to support all kind of images for MS Power Point Presentation
*   The case the comparison of tables with different results for all formats
*   Added support for new components to new core for PDF

## GroupDocs.Comparison for Java 16.11.0 - Bug FixesGiven below is the list of bug fixes:

*   Fix bug when you can not open document with tables after comparison for PDF
*   Files generating zero output (no change is detected ) for attached files only for MS Word
*   Some tables differ on two cell but algorithm not defined the tables as similar for PDF
*   The target file is modification of source file but defined as different for MS Word
*   Cannot open result file: graphics objects for MS Word
*   Some images (or graphical objects) are not displayed for MS Word
*   fix function getText of ComparisonCell class for PDF
*   Identical text from neighboring paragraphs is defined as deleted and inserted for MS Word
*   Files are not opened after comparison for MS Power Pint Presentation
*   If content of row is unique then row should be marked as Inserted or Deleted for Spreadsheets
*   The result table structure not conforming to primary table structure for Spreadsheets
*   Exception: The new Child was created from a different document than the one that created this node for MS Word
*   Comparing PDF documents neither generate any error nor the output PDF with Gradle

## For more details about supported document formats, please visit [Features Overview](https://www.groupdocs.com/docs/display/comparisonjava/Supported+Document+Formats).

## Available Channels and ResourcesHere are a few channels and resources for you to download, learn, try and get technical support on **GroupDocs.Comparison for Java API**:

*   [Downloads](http://downloads.groupdocs.com/comparison/java "Dwonloads")\-Zipped JARS
*   [Documentation](http://groupdocs.com/docs/display/comparisonjava/Home "Product Documentation") -Product Docs
*   [Support Forum](http://www.groupdocs.com/Community/forums/groupdocs.comparison-product-family/9/showforum.aspx "GroupDocs.Comparison for Java Forum") -Technical Support Forum
*   [Example / Plugins](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-java "GroupDocs.Comparison for Java Github")\-Github source code examples

### FeedbackYou are always welcome to share your feedback and suggestions to improve this product, we take it very seriously and try to incorporate it as much as its possible for upcoming releases . We will be happy to know your thoughts. Just create a [forum thread](http://www.groupdocs.com/Community/forums/groupdocs.comparison-product-family/9/showforum.aspx) and our dedicated support team will be there to respond.




