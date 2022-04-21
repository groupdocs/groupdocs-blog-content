---
title: 'Issue with Footnote Number is Resolved'
date: Tue, 09 Jul 2019 12:30:01 +0000
draft: false
url: /2019/07/09/issue-with-footnote-number-is-resolved/
author: 'Atir Tahir'
summary: ''
tags: []
categories: ['GroupDocs.Conversion for Java', 'GroupDocs.Conversion Product Family']
---

If you worked with earlier versions of the API, you are probably aware that there was issue in footnote number conversion. A Word document with such footnotes was converted to PDF or any other supported file format successfully but the footnote number order was disturbed.

There was one more issue reported in the forum. It was about converting a PowerPoint document with black SmartArt text to PDF. And the SmartArt text in the resultant document was changed to white text.  

**What else is fixed?**

*   Issue with conversion .docx (with table of content) to .html
*   Conversion of .pdf to .png (or .jpeg) with watermark as background
*   Inconsistent conversion from email file formats when converting to Cells
*   Receiving Aspose.Pdf.InvalidValueFormatException when converting a PDF file

In GroupDocs.Conversion for Java [19.6](https://docs.groupdocs.com/display/conversionjava/GroupDocs.Conversion+for+Java+19.6+Release+Notes), we have fixed these issues.  

**Do we have to take any extra step in order to get right output?**  
No, these were back-end level issues and they have been fixed. That means you just have to write your normal document conversion code.

There are few regular yet helpful improvements:

*   SVG to Slides conversion is improved
*   Set watermark as background when converting to Image format

Lastly, we've added a new file format VCF. you can now do conversion from VCF to any other [supported](https://docs.groupdocs.com/display/conversionjava/Supported+Document+Formats) file format.  

Please download latest release [here](https://downloads.groupdocs.com/conversion/java). Your feedback is very important for us. If you run into issues or have questions while trying out this latest release, post your concerns [here](https://forum.groupdocs.com/c/conversion).




