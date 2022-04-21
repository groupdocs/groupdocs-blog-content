---
title: 'Manage EXIF Data of JPEG, PNG, TIFF &amp; WebP  Images in Java'
date: Tue, 12 May 2020 07:09:04 +0000
draft: false
url: /2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/
author: 'Shoaib Khan'
summary: '**EXIF** (_Exchangeable Image File Format_) is the standard to specify the image and sound formats mainly used by digital cameras and scanners. EXIF data includes the tagging and metadata information about the captured image file. Metadata may contain information like camera make, model, shutter speed, date and time, aperture, exposure time, X resolution, Y resolution. etc.'
tags: ['exif data', 'exif data of jpeg in java', 'exif metadata', 'exif metadata in java', 'extract exif data', 'extract exif data in java', 'remove exif data from images', 'remove exif metadata', 'update exif']
categories: ['GroupDocs.Metadata Product Family']
---

**EXIF** (_Exchangeable Image File Format_) is the standard to specify the image and sound formats mainly used by digital cameras and scanners. EXIF data includes the tagging and metadata information about the captured image file. Metadata may contain information like camera make, model, shutter speed, date and time, aperture, exposure time, X resolution, Y resolution. etc.

If you want to **manage, extract, update, or remove EXIF data of your images programmatically**, then this article is for you. This article will cover the following ways to manipulate with EXIF data in Java:

*   [Extract EXIF data - EXIF Data Viewer][1]
*   [Extract all EXIF tags from images][2]
*   [Update EXIF properties][3]
*   [Remove EXIF metadata][4]

## Java Metadata Manipulation Library

{{< figure align=center src="images/GroupDocs.MetaData_for_Java.png" alt="Metadata Java API by GroupDocs">}}


[GroupDocs.Metadata for Java][5] is an easy to use metadata management Java API. It has the ability to not only extract metadata from images like JPG, PNG, or WebP but also it can add, edit, update, and remove metadata from the images and other documents with different options.

I am using this API in this article so please make sure to [download][6] or integrate it in your Maven-based applications by just adding the following configurations to the pom.xml.

### Repository & Dependency
```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-metadata</artifactId>
    <version>20.5</version>
    <classifier>javadoc</classifier>
</dependency>
```

## Extract EXIF Data from Images in Java - Metadata Viewer {#extract-exif-data-from-images}

You can read the EXIF data properties by following simple steps. Let's start with the extraction of EXIF data from this picture of Eiffel Tower. I have selected a JPG file as an example image, you can use any of your files whether its a PNG, WebP, BMP, GIF, or TIFF.



{{< figure align=center src="images/eiffel-tower.jpg" alt="Eiffel Tower Picture for EXIF Data">}}


*   Load the image source file containing EXIF data information using the [Metadata][7] class constructor.
*   Get its **root package** by calling [getRootPackage()][8] method.
*   From the root package, get its **EXIF package** by calling [getExifPackage()][9] method.
*   Once you have the EXIF package, you can get image EXIF properties like **Make**, **Model**, **Width**, **Length**, **Date-Time**, etc as shown in the below Java code example.

```
// Extract EXIF Data Package Information from image in Java
try (Metadata metadata = new Metadata("eiffel-tower.jpg")) {
	IExif root = (IExif) metadata.getRootPackage();
	if (root.getExifPackage() != null) {
		// Extract EXIF Package
		ExifPackage exifPackage = root.getExifPackage();
		System.out.println("Make : " + exifPackage.getMake());
		System.out.println("Model : " + exifPackage.getModel());
		System.out.println("Width : " + exifPackage.getImageWidth());
		System.out.println("Length : " + exifPackage.getImageLength());
		System.out.println("DateTime : " + exifPackage.getDateTime());					
	} 
}
```

Here is the EXIF information you will get as a result of the above code.

```
Make : NIKON CORPORATION
Model : NIKON D3000
Width : 640
Length : 424
DateTime : 2014:08:09 10:35:13
```

For further **IFD** (Image File Directory) and **GPS** (Global Positioning System) package information, you just have to call the respective methods of **EXIF package** i.e. [getExifIfdPackage()][10] or [getGpsPackage()][11]. From these packages, you may extract more information like;

*   Image capture device **serial number**
*   Camera **Owner name**
*   **User comments**
*   **Altitude**
*   **Latitude**
*   **Longitude**
*   etc.

Here is the code that you can add in your above method to display EXIF data along with IFD and GPS information.

```
// EXIF IFD Package
ExifIfdPackage exifIfdPackage = exifPackage.getExifIfdPackage();
System.out.println("BodySerialNumber : " + exifIfdPackage.getBodySerialNumber());
System.out.println("CameraOwnerName : " + exifIfdPackage.getCameraOwnerName());
System.out.println("UserComment : " + exifIfdPackage.getUserComment());
// EXIF GPS Information Package
ExifGpsPackage exifGpsPackage = exifPackage.getGpsPackage();
System.out.println("getAltitude : " + exifGpsPackage.getAltitude());
System.out.println("Latitude Ref : " + exifGpsPackage.getLatitudeRef());
System.out.println("LongitudeRef : " + exifGpsPackage.getLongitudeRef());
```

## Read All EXIF Tags of Images using Java {#extract-all-exif-tags-from-images}

If you want to show or extract all the EXIF properties of any image or file, you may do it in steps similar to the above examples:

*   Just load the file with [Metadata][12] constructor.
*   Get the **EXIF root package** by calling the method [getRootPackage()][13].
*   Get the **EXIF package** by calling [getExifPackage()][14] method.
*   Iterate through the EXIF package to get your desired name-value pairs.
*   Similarly, get the IFD and GPS packages and displays its keys and values.

```
try (Metadata metadata = new Metadata("eiffel-tower.jpg")) {
	IExif root = (IExif) metadata.getRootPackage();
	if (root.getExifPackage() != null) {
		String pattern = "%s = %s";
		// Reading all EXIF tags.
		for (TiffTag tag : root.getExifPackage().toList()) {
			System.out.println(String.format(pattern, tag.getName(), tag.getValue()));
		}
		// Extract all EXIF IFD tags.
		for (TiffTag tag : root.getExifPackage().getExifIfdPackage().toList()) {
			System.out.println(String.format(pattern, tag.getName(), tag.getValue()));
		}
		// Extract all EXIF GPS tags
		for (TiffTag tag : root.getExifPackage().getGpsPackage().toList()) {
			System.out.println(String.format(pattern, tag.getName(), tag.getValue()));
		}
	}
}
```

## Update EXIF Properties in Java {#update-exif-properties}

You can even change the existing EXIF data of any image or any document easily. Steps are simple:

### **Update EXIF Package**

*   Get the EXIF package by calling [getExifPackage()][15] method.
*   Use the setter methods like;
    *   [setCopyright()][16] - to set updated copyrights information.
    *   [setImageDescription()][17] - to set description of the image.
*   Similarly, you can set the values for Artist, Make, Model, Software, Image Width & Height, Date, Time, etc.

### **Update EXIF IFD Package**

Just like updating the EXIF package, you can update the properties of EXIF IFD and GPS packages. Please visit the [ExifIfdPackage][18] or [ExifGpsPackage][19] class to know how much you can customize for your valuable images and documents.

```
// Update/Set new values in EXIF Data (EXIF Package and EXIF IFD Package).
try (Metadata metadata = new Metadata("eiffel-tower.jpg")) {
    IExif root = (IExif) metadata.getRootPackage();
    // Set the EXIF package if it's missing
    if (root.getExifPackage() == null) {
        root.setExifPackage(new ExifPackage());
    }
    ExifPackage exifPackage = root.getExifPackage();
    // Setting the desired values in EXIF Package and EXIF IFD Package.
    exifPackage.setCopyright("Copyright (C) 2011-2020 GroupDocs. All Rights Reserved.");
    exifPackage.setImageDescription("Eiffel Tower for EXIF");
    exifPackage.setSoftware("GroupDocs.Metadata");
    exifPackage.getExifIfdPackage().setBodySerialNumber("GD-2020");
    exifPackage.getExifIfdPackage().setCameraOwnerName("GroupDocs");
    exifPackage.getExifIfdPackage().setUserComment("Nice image captured in 2014");
    metadata.save("eiffel-tower-updated.jpg");
}
```

## Remove EXIF Metadata from Images in Java {#remove-exif-metadata}

This is very simple if you want to remove EXIF package from any file, just set its EXIF package to null by calling [setExifPackage(null)][20] of root package.

```
// Removing the EXIF data from an image.
try (Metadata metadata = new Metadata("eiffel-tower.jpg")) {
    IExif root = (IExif) metadata.getRootPackage();
    root.setExifPackage(null);
    metadata.save("eiffel-tower-no-exif.jpg");
}
```

## Supported Images & Other Formats

Here are the currently supported file formats by GroupDocs.Metadata. You may always visit the [documentation][21] for the updated information.

<figure class="wp-block-table is-style-stripes"><table class="has-fixed-layout"><tbody><tr><td>**Document Type</strong></td><td><strong>File Formats**</td></tr><tr><td><a href="https://wiki.fileformat.com/image/">Images</a></td><td>BMP, GIF, JPG, JPEG, JPE, JP2, PNG, DJVU, DWG, DXF, WebP, TIFF, PSD, EMF, WMF</td></tr><tr><td><a href="https://wiki.fileformat.com/audio">Audio</a> &amp; <a href="https://wiki.fileformat.com/video/">Video</a></td><td>MP3, WAV, AVI, MOV / QT, FLV, ASF, DICOM</td></tr></tbody></table></figure>

## See more about GroupDocs.Metadata

*   [Documentation][22]
*   Source code examples. [Java][23] | [.NET][24]
*   GroupDocs.Metadata – [The Metadata Management Solution][25]

**Let’s talk more @** [Free Support Forum.][26]

## Related Article

*   [Manage EXIF Data of Images in C#][27]







[1]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/#update-exif-properties
[2]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/#extract-all-exif-tags-from-images
[3]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/#update-exif-properties
[4]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/#remove-exif-metadata
[5]: https://products.groupdocs.com/metadata/java
[6]: https://downloads.groupdocs.com/metadata/java
[7]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata
[8]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#getRootPackage()
[9]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/IExif#getExifPackage()
[10]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifIfdPackage
[11]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifPackage#getGpsPackage()
[12]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata
[13]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#getRootPackage()
[14]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifIfdPackage
[15]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifIfdPackage
[16]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifPackage#setCopyright(java.lang.String)
[17]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifPackage#setImageDescription(java.lang.String)
[18]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifIfdPackage
[19]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifGpsPackage
[20]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/IExif#setExifPackage(com.groupdocs.metadata.core.ExifPackage)
[21]: https://docs.groupdocs.com/display/metadatajava/Supported+File+Formats
[22]: https://docs.groupdocs.com/display/metadatajava/Getting+Started
[23]: https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java
[24]: https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-.NET
[25]: https://products.groupdocs.com/metadata
[26]: https://forum.groupdocs.com/c/metadata
[27]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/

