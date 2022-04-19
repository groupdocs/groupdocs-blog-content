---
title: "使用 Java 的文档和图像的元数据清理器"
date: Thu, 17 Dec 2020 10:02:00 +0000
draft: false
url: /zh/2020/12/17/remove-metadata-from-documents-and-images-using-java/
author: 'Shoaib Khan'
summary: "**元数据**是提供有关实际数据的信息的数据。 它通常被描述为“**关于数据的数据**”。 将文件发送给某人时，将元数据一起发送并不是一个好习惯。 它可以向接收者透露您可能不想分享的信息。 一些例子包括： 名称、公司名称、文档修改日期、相机的品牌和型号等。在本文中，我们将**使用 Java 以编程方式从图像和文档中删除元数据**。"
tags: ['metadata cleaner using Java', 'remove metadata from documents in Java', 'remove metadata from images in Java', 'remove metadata using Java']
categories: ['GroupDocs.Metadata Product Family']
---

**元数据** 是提供有关实际数据的信息的数据。它通常被描述为“**关于数据的数据**”。将文件发送给某人时，将元数据一起发送并不是一个好习惯。它可以向接收者透露您可能不想分享的信息。一些例子包括：名称、公司名称、文档修改日期、相机的品牌和型号等。在本文中，我们将**使用 Java 以编程方式从图像和文档中删除元数据**。

* [Java 元数据清理 API][1]
* [从文档中删除元数据][2]
* [从图像中清除元数据][3]
* [从文档和图像中删除选择性元数据][4]

## Java 元数据清理器 API {#java-metadata-cleaner-api}

[GroupDocs.Metadata for Java][5] 是一个 Java 元数据 API，支持大多数流行的元数据标准，如 EXIF、XMP、IPTC、ID3 标签等。它允许 Java 开发人员添加、修改、提取和删除元数据从文档、图像和其他文件的 [支持的格式][6] 大列表中提供各种选项。

本文中的步骤和代码示例使用 GroupDocs.Metadata API。因此，在继续之前，请确保使用以下任何选项准备开发环境：

* 从 [下载][7] 部分获取 JAR 文件。
* 在基于 Maven 的 java 应用程序中添加以下 pom.xml 配置

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
        <artifactId>groupdocs-metadata</artifactId>
        <version>20.11</version> 
</dependency>
```

## 使用 Java 从文档中删除元数据 {#remove-documents-metadata}

要在不应用任何过滤器的情况下删除所有可用的元数据属性，并在 COVID-19 时代保持安全，请使用 **sanitize** 方法。以下是使用 GroupDocs.Metadata for Java 从文档中删除元数据的步骤。

* 实例化[Metadata][8]类的对象，传入目标文档的路径作为参数。
* 调用 [sanitize][9] 方法。它返回已删除的元数据属性的数量。
* 使用 [save][10] 方法保存带有清除元数据的输出文件。

以下 Java 代码示例展示了如何从文档中删除和清除元数据。

```
/*
* 从 Word、Excel、 
* PowerPoint、PDF 和其他使用 Java 的文档
*/
Metadata metadata = new Metadata("filePath/document.pdf");
int affected = metadata.sanitize();
metadata.save("filePath/output.pdf"); // Save the output document with no metadata 
```

## 使用 Java 从图像中删除元数据 {#remove-images-metadata}

如果要使用 Java 从图像中删除所有元数据，可以按照相同的步骤使用相同的清理方法：

* 创建[Metadata][11]类的对象，传入目标文档路径作为参数。
* 调用 [sanitize][12] 方法。
* 使用 [save][13] 方法保存输出文件。

```
/*
* 从 JPEG、PNG、
* WebP、BMP、GIF、TIFF等图片使用Java
*/
Metadata metadata = new Metadata("filePath/document.jpg");
int affected = metadata.sanitize();
metadata.save("filePath/output.jpg"); // Save the output image having no metadata
```

## 使用 Java 从文档和图像中删除选择性元数据 {#remove-selective-metadata}

并不总是需要从文件中删除所有可用的元数据，但是，我们有时希望删除选择性元数据属性。以下步骤显示如何使用属性的特定名称查找和删除元数据。

* 创建 [Metadata][14] 对象以加载目标文档或图像文件。
* 创建个性化规范以查找元数据属性。
* 调用[removeProperties][15]方法，传递个性化规范。
* 使用 [save][16] 方法保存输出文件。

```
// 使用 Java 从满足自定义过滤器的文档和图像中删除元数据属性
public class RemoveMetadataProperties {
	public static void removeMetadataProperties() {
		Metadata metadata = new Metadata("filePath/document.docx");
		/*
		 * Remove all the properties that: 
		 * contains the name of the document author OR
		 * it refers to the last editor OR 
		 * the property value is a string AND equal to the given string "GroupDocs"
		 */
		int affected = metadata.removeProperties(new ContainsTagSpecification(Tags.getPerson().getCreator())
				.or(new ContainsTagSpecification(Tags.getPerson().getEditor()))
				.or(new OfTypeSpecification(MetadataPropertyType.String)
						.and(new RemoveMetadataProperties().new WithValueSpecification("GroupDocs"))));

		System.out.println(String.format("Properties removed: %s", affected));

		metadata.save("outputPath/document.docx");
	}

	// Create personalized specifications to filter metadata properties
	public class WithValueSpecification extends Specification {
		public WithValueSpecification(Object value) {
			setValue(value);
		}

		public final Object getValue() {
			return auto_Value;
		}

		private void setValue(Object value) {
			auto_Value = value;
		}

		private Object auto_Value;

		public boolean isSatisfiedBy(MetadataProperty candidate) {
			return candidate.getValue().getRawValue().equals(getValue());
		}
	}
}
```

## 结论

在本文中，我们学习了使用 Java 从文档和图像中清理元数据。现在您可以构建自己的元数据清理器 Java 应用程序。它可以支持从文字处理文档、电子表格、演示文稿、PDF 文件、图像、电子邮件、电子书、绘图、zip 文件等中删除元数据。您可以从 [文档][17] 中探索有关 Java 元数据 API 的更多信息。

## 也可以看看

* [使用 C# 删除文档和图像的元数据][18]
* [使用Java管理图像的EXIF数据][19]
* [用C#管理图片的EXIF数据][20]







[1]: #java-metadata-cleaner-api
[2]: #remove-documents-metadata
[3]: #remove-images-metadata
[4]: #remove-selective-metadata
[5]: https://products.groupdocs.com/metadata/java
[6]: https://docs.groupdocs.com/metadata/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/metadata/java
[8]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata
[9]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#sanitize()
[10]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#save(java.lang.String)
[11]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata
[12]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#sanitize()
[13]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#save(java.lang.String)
[14]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata
[15]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#removeProperties(com.groupdocs.metadata.search.Specification)
[16]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#save(java.lang.String)
[17]: https://docs.groupdocs.com/metadata/java/
[18]: https://blog.groupdocs.com/2020/12/29/remove-metadata-of-documents-and-images-using-csharp/
[19]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/
[20]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/


