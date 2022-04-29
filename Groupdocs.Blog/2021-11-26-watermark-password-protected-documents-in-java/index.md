---
title: 'Watermark Password Protected Documents in Java'
seoTitle: "Watermark Protected Files in Java | Text & Image Watermarks"
description: "Use Java API to add text & image watermark to password-protected Word, PDF, PowerPoint, Excel files. Customize watermark appearance using GroupDocs API."
date: Fri, 26 Nov 2021 09:36:00 +0000
draft: false
url: /2021/11/26/watermark-password-protected-documents-in-java/
author: 'Shoaib Khan'
summary: ''
tags: ['Document Watermarking', 'Watermark Protected Documents using Java', 'Watermark Protected Files', 'Watermark Protected Files using Java', 'watermark using java', 'watermarking API for Java']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/watermark-protected-files-using-java.jpg" alt="Watermark Protected Docs using Java">}}


Watermarks can be used to protect the content and claim ownership of your documents. Similarly, these can also be used for branding or labelling your documents as drafts. This article discusses **how to add watermarks to the password-protected files** in Java. We will add text, as well as image watermarks to the protected files using code examples.

The following topics are discussed here:

*   [Java API to Watermark Password Protected Files][1]
*   [Add Watermark to Protected Files using Java][2]
    *   [Insert Text Watermark][3]
    *   [Insert Image Watermark][4]

## Java API to Watermark Password Protected Files {#watermarking-java-api}

[GroupDocs.Watermark][5] showcases [watermarking Java API that allows working with watermarks][6] within your applications. We will use this API to insert text and image watermarks to the password-protected documents.

You can download the **JAR** file from the [downloads section][7] or use the latest repository and dependency [Maven][8] configurations within your Java applications.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-watermark</artifactId>
        <version>21.3</version> 
</dependency>
```

## Adding Watermark to Password-Protected Files using Java {#add-watermark-to-protected-files}

Just a few lines of code allow you to customize the watermark as needed and apply it to your files. Follow the following steps for adding both types of watermark.

*   **Load** the protected file.
*   **Apply** watermark.
*   **Save** the watermarked file.

Now, we will add text watermarks, and then image watermarks, one by one.

## Add Text Watermark to Protected Files in Java {#text-watermark-to-protected-files}

Text watermarks can be used to mention the documents as DRAFT or CONFIDENTIAL; or for similar purposes. The following steps show how to add text watermark to password-protected documents in Java.

*   Prepare the [loading option][9] using the exsiting password.
*   Use the loading options to load the protected file with [Watermarker][10] class.
*   Define the watermark using [TextWatermark][11] class.
*   Set the text, appearance, rotation, opacity, color, and other properties of watermark.
*   Add the watermark to the document using the [add()][12] method.
*   Save the watermarked file using the [save()][13] method.

The following Java code snippet inserts a text watermark to a protected PDF document.

{{< gist GroupDocsGists a2137cc50ad466d561e69947e0a9c99e "AddTextWatermarkToPasswordProtectedDocument.java" >}}

## Add Image Watermark to Protected Files in Java {#image-watermark-to-protected-files}

You can also insert any image or logo as a watermark. To add the image, use the **ImageWatermark** class. The following steps allow adding an image watermark to your password-protected documents in Java.

*   Prepare the [loading option][14] for the protected file using the exsiting password.
*   Load the file using the [Watermarker][15] class and **loading option**.
*   Load the image file using [ImageWatermark][16] class.
*   Set the watermark's appearance, alignment, coordinates, rotation, opacity, and other properties.
*   Now, add watermark to document using [add()][17] method.
*   Finally, save the watermarked file using the [save()][18] method.

The following Java code example inserts an image watermark to the protected PDF file.

{{< gist GroupDocsGists a2137cc50ad466d561e69947e0a9c99e "AddImageWatermarkToPasswordProtectedDocument.java" >}}

## Get a Free API License

You can use the APIs for free by [getting a temporary license][19].

## Conclusion

To sum up, we discussed adding text watermarks, as well as image watermarks to password-protected files within the Java applications. Further, we customized the appearance of watermarks when these are applied to the documents.

In a similar vein, you can insert watermarks to the specific **pages, slides, and sheets of documents**, **presentations**, and **workbooks** respectively.

See the [related articles][20] for details and learn more from its [documentation][21]. For queries, contact us via the [forum][22].

## Related Articles {#releated-articles}

*   [Find and **Remove Watermarks** from Documents in Java][23]
*   [Add Watermark to **Images** in Java][24]
*   [Password Protect Presentations in Java][25]
*   [Add Watermark to **Presentation Slides** using Java][26]
*   [Watermark **PDF** Files in Java][27]







[1]: #watermarking-java-api
[2]: #add-watermark-to-protected-files
[3]: #text-watermark-to-protected-files
[4]: #image-watermark-to-protected-files
[5]: https://products.groupdocs.com/watermark/
[6]: https://products.groupdocs.com/watermark/java/
[7]: https://downloads.groupdocs.com/watermark
[8]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs
[9]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.options/LoadOptions
[10]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[11]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[12]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[13]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String)
[14]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.options/LoadOptions
[15]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[16]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/ImageWatermark
[17]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[18]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String)
[19]: https://purchase.groupdocs.com/temporary-license
[20]: #releated-articles
[21]: https://docs.groupdocs.com/watermark/
[22]: https://forum.groupdocs.com/
[23]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/
[24]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[25]: https://blog.groupdocs.com/2022/02/10/lock-unlock-ppt-pptx-files-with-password-in-java/
[26]: https://blog.groupdocs.com/2021/06/09/watermark-presentation-slides-using-java/
[27]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/

