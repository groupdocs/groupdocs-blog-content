---
title: 'Adjust Contrast when Converting a Document to Image'
date: Tue, 08 Oct 2019 17:04:54 +0000
draft: false
url: /2019/10/08/adjust-contrast-when-converting-a-document-to-image/
author: 'Atir Tahir'
summary: ''
tags: ['adjust contrast of image', 'convert document to image', 'convert to image', 'convert to image in java']
categories: ['GroupDocs.Conversion Product Family']
---

Up till now, there was a simple document to image conversion process. With the [GroupDocs.Conversion for Java](https://products.groupdocs.com/conversion/java) release version [19.10](https://docs.groupdocs.com/display/conversionjava/GroupDocs.Conversion+for+Java+19.10+Release+Notes), we've added a number of interesting features for image conversion.

*   Set color mode when converting to JPEG
*   Option to set compression mode
*   Adjust image brightness and contrast
*   Set gamma
*   Option to flip image

Have a look at its implementation of the above features in Java  
{{< gist GroupDocsGists 65125164afea40cf0426eb3cba8c482f "imagesaveoptions.java" >}}

## **Conversion from CDR**

CDR is a vector graphics file. API now allows you to convert from CDR.

### **Improvements**

Along with new features, there are some improvements and bug fixes as well. Following are the major improvements:

*   Conversion from Excel95/5.0 XLS files
*   Set image quality when converting to WebP
*   Remove HideComments from SaveOptions

### **Bug Fixes**

Previously, there was an issue (_Exception: Cannot open an image_) in conversion of Cells to Image. We've fixed it.  
API conflict with _Ch.qos.logback_ is also resolved.  
Moreover, you can now generate scalable/Adjustable HTML. There is a property in _HtmlSaveOptions_ known as _FixedLayout_. Try to set it to false. This will generate simplified markup and layout.  
{{< gist GroupDocsGists 63c373b438e0e9f9f2c206d2f74dff8c "htmlsaveoptions.java" >}}

We'd recommend you to [download](https://downloads.groupdocs.com/conversion/java) and integrate API version 19.10 and enhance your document conversion experience. If you face any issue, post it on the [forum](https://forum.groupdocs.com/c/conversion).




