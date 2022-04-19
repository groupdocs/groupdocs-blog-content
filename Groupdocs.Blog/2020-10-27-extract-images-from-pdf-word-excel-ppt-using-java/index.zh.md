---
title: "使用 Java 从文档中提取图像"
date: Tue, 27 Oct 2020 05:04:09 +0000
draft: false
url: /zh/2020/10/27/extract-images-from-pdf-word-excel-ppt-using-java/
author: 'Shoaib Khan'
summary: "今天，我们将学习**使用 Java 以编程方式从 PDF、Excel、PowerPoint 和 Word 文档中提取图像**。 对于图像的提取，我们将使用 [GroupDocs.Parser for Java][1]。 此 Java API 支持从文字处理文档、电子表格、演示文稿、档案和电子邮件文档中解析文档和提取图像、文本和元数据。 提取的图像可以保存为 **BMP**、**GIF**、**JPEG**、**PNG** 和 **WebP** 格式。"
tags: ['extract images from documents in java', 'extract images from PDF in Java', 'extract images from word in java', 'extract images in Java']
categories: ['GroupDocs.Parser Product Family']
---

如果您有一个文档，并且想在其他文档中使用该文档中的图像，这里是其中一种解决方案。在本文中，我们将学习**使用 Java 以编程方式从 PDF、Excel、PowerPoint 和 Word 文档中提取图像**。

* [图像提取Java API][2]
* [用Java从PDF文档中提取图像][3]
* [用Java从Word、Excel、PowerPoint文档中提取图像][4]
* [用Java从特定页面提取图像][5]



{{< figure align=center src="images/extract-images-from-documents-in-java-1.png" alt="从 Java 文档中提取图像">}}


## 图像提取 Java API {#image-extraction-java-api}



{{< figure align=center src="images/groupdocs-parser-java.png" alt="在 Java 中解析文档和提取数据">}}


对于图像的提取，我们将使用 [GroupDocs.Parser for Java][6]。此 Java API 支持**文档解析**和**从**文字处理文档**、**电子表格**、**演示文稿、档案中提取图像、文本**和**元数据** ,** 和 **email** 文件。以下是 Java API 支持的用于图像提取的文档格式。

<figure class="wp-block-table is-style-stripes"><table><tbody><tr><td>**文字处理文件</td><td>DOC、DOCX、DOCM、DOT、DOTX、DOTM、ODT、OTT、RTF</td></tr><tr><td><strong>电子表格</strong></td><td>XLS、XLSX、XLSM、XLSB、XLT、XLTX、XLTM、ODS、OTS、XLA、XLAM、数字</td></tr><tr><td><strong>演示文稿</strong></td><td>PPT、PPTX、PPTM、PPS、PPSX、PPSM、POT、POTX、POTM、ODP、OTP</td></tr><tr><td><strong>便携式文件</strong></td><td>PDF格式</td></tr><tr><td><strong>电子邮件</strong></td><td>EML、EMLX、味精</td></tr><tr><td><strong>档案**</strong></td><td>压缩</td></tr></tbody></table></figure>

在开始下面的示例之前，我建议通过从 [下载部分][7] 下载最新版本的文档解析 Java API 来设置环境，或者您可以在 **maven-based* 中设置以下配置* java应用程序：

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
	<groupId>com.groupdocs</groupId>
	<artifactId>groupdocs-parser</artifactId>
	<version>20.8</version> 
</dependency>
```

## 用Java从PDF文档中提取图像 {#extract-images-from-pdf-in-java}



{{< figure align=center src="images/PDF-with-Images.png" alt="提取图像的 PDF 文档">}}


按照这些简单的步骤从 PDF 文档中获取所有图像。

1. 实例化 [**Parser**][8] 类对象。
2. 调用 Parser 类的 **[getImages][9]** 方法获取所有图像。
3. 使用 **[PageImageArea][10]** 迭代图像。
4. 使用 PageImageArea 的 save 方法保存图像。

完成。请参阅下面的完整代码。提取的图像可以保存为 **BMP**、**GIF**、**JPEG**、**PNG** 和 **WebP** 格式。

```
// 使用 GroupDocs.Parser for Java 以编程方式从 Word、Excel、PowerPoint、PDF 文档中提取图像
try (Parser parser = new Parser("path/document.pdf")) {
	// Extract images
	Iterable<PageImageArea> images = parser.getImages();

	// Create the options to save images in PNG format
	ImageOptions options = new ImageOptions(ImageFormat.Png);
	int imageNumber = 0;

	// Iterate over images and Save
	for (PageImageArea image : images) {
		// Print the page index, rectangle and image file type:
		System.out.println(String.format("Page: %d, R: %s, Type: %s", image.getPage().getIndex(), 
				image.getRectangle(), image.getFileType()));
		image.save(String.format("filesPath/image_%d.png", imageNumber), options);
		imageNumber++;
	}
}
```

这些是使用上述代码从 PDF 文档中检索到的图像。



{{< figure align=center src="images/Extracted-Images-from-PDF-using-GroupDocs.Parser-for-Java.png" alt="使用 Java 从文档中提取图像">}}


## 用 Java 从 Word、Excel、PowerPoint 文件中提取图像 {#extract-images-from-word-excel-ppt-in-java}

同样，所有的图像都可以从文字处理文件、电子表格、演示文稿中取出，而代码库没有改变。你必须改变什么？只是源文档路径和正确的文件扩展名。

```
Parser parser = new Parser("path/document.docx") // Word Document
// Parser parser = new Parser("path/document.xlsx") // Excel Spreadsheet
// Parser parser = new Parser("path/document.pptx") // PowerPoint Presentation
// Parser parser = new Parser("path/document.pdf") // PDF Document

```

## 从 Java 中的特定文档页面提取图像 {#extract-images-from-specific-page-in-java}

如果您不想从整个文档中提取所有图像，而是从某个特定页面中提取。下面的代码演示了我们如何从 Java 文档的特定页面中提取图像。

```
// 使用 GroupDocs.Parser 从 Java 中的 Word、Excel、PowerPoint、PDF 的特定页面中提取图像
try (Parser parser = new Parser("path/document.pdf"")) {
	// Get the document info
	IDocumentInfo documentInfo = parser.getDocumentInfo();

	// Create the options to save images in PNG format
	ImageOptions options = new ImageOptions(ImageFormat.Jpeg);
	int imageNumber = 0;

	// Iterate over pages
	for (int pageIndex = 0; pageIndex < documentInfo.getPageCount(); pageIndex++) {
		// Print Page Numbers
		System.out.println(String.format("Page %d/%d", pageIndex + 1, documentInfo.getPageCount()));

		// Iterate over images - Ignoring NULL-Checking in the examples
		for (PageImageArea image : parser.getImages(pageIndex)) {
			// Print Image Information and Save file
			System.out.println(String.format("R: %s, Text: %s", image.getRectangle(), image.getFileType()));
			image.save(String.format("filesPath/image_%d.jpeg", imageNumber), options);
			imageNumber++;
		}
	}
}
```

## 结论

今天，我们学习了**如何从整个文档中提取图像，以及 Java 中文字处理文档、电子表格、演示文稿和 PDF 的特定页面**。如果我们必须从不同文件格式的文件中提取图像，则代码没有区别。我们只需要传递正确的路径和名称。就是这样。

## 也可以看看

* [用C#从文档中提取图像][11]
* [使用Python从云端文档中提取图像][12]







[1]: https://products.groupdocs.com/parser/java
[2]: #image-extraction-java-api
[3]: #extract-images-from-pdf-in-java
[4]: #extract-images-from-word-excel-ppt-in-java
[5]: #extract-images-from-specific-page-in-java
[6]: https://products.groupdocs.com/parser/java
[7]: https://downloads.groupdocs.com/parser/java
[8]: https://apireference.groupdocs.com/java/parser/com.groupdocs.parser/Parser
[9]: https://apireference.groupdocs.com/java/parser/com.groupdocs.parser/Parser#getImages()
[10]: https://apireference.groupdocs.com/java/parser/com.groupdocs.parser.data/PageImageArea
[11]: https://blog.groupdocs.com/2020/10/28/extract-images-from-pdf-word-excel-ppt-using-csharp/
[12]: https://blog.groupdocs.cloud/2020/10/25/extract-images-from-word-excel-ppt-pdf-using-python/


