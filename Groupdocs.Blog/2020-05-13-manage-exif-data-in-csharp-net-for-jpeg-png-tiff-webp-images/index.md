---
seoTitle: "Manage EXIF Data of JPEG, PNG, TIFF & WebP Images in C#"
title: 'Manage EXIF Data of JPEG, PNG, TIFF &amp; WebP Images in C# .NET'
date: Wed, 13 May 2020 21:06:49 +0000
draft: false
url: /2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/
author: 'Shoaib Khan'
description: "Manage EXIF metadata of your images in C#. Extract, update, add or remove EXIF data of your images programmatically using the metadata .NET API."
summary: "In the [previous post][1], we discussed how to deal with EXIF data of images in Java. Here, today we will look into achieving the same but in C#. If you haven't visited the last post, but you want to **extract, update, add or remove EXIF data of your images programmatically in C#**, then this article will guide you through this."
tags: ['change exif data of images', 'extract exif data', 'extract exif data in csharp', 'extract metadata from images', 'remove exif data from images']
categories: ['GroupDocs.Metadata Product Family']
---

In the [previous post][2], we discussed how to deal with EXIF data of images in Java. Here, today we will look into achieving the same but in C#. If you haven't visited the last post, but you want to **extract, update, add or remove EXIF data of your images programmatically in C#**, then this article will guide you through this. We will cover the following ways to manipulate with EXIF data in C#:

*   [Read EXIF data][3]
*   [Read all EXIF tags from an image][4]
*   [Update EXIF properties][5]
*   [Remove EXIF metadata][6]

## Metadata Management C# Library



{{< figure align=center src="images/GroupDocs.MetaData_for_NET.png" alt="Metadata .NET API by GroupDocs">}}


[GroupDocs.Metadata for .NET][7] is metadata management .NET API. It has a long list of [features][8] for a wide variety of supported file formats. It has the ability to not only extract metadata from images but also it can add, edit, update, and remove metadata from the images and documents with various options.

In this article, we will use this API, so please make sure to [download][9] its binaries or install the API from [NuGet][10].

## Read EXIF Data from Images in C# {#extract-exif-data-from-images}

You can easily read the EXIF data properties by following the mentioned steps. Starting with the extraction of EXIF data from this picture, 93m tall Statue of Liberty. Here we will use a JPG file as an example image, however, we can use any file whether its a PNG, WebP, BMP, GIF, TIFF, or any other from the [supported file formats][11] mentioned at the end of this article.



{{< figure align=center src="images/statue-of-liberty.jpg" alt="Liberty JPG image for EXIF data">}}


*   Load the image source file containing EXIF data information using the [Metadata][12] class constructor.
*   Get its **root package** by calling [GetRootPackage()][13] method.
*   From the root package, get its [ExifPackage][14] from its [ExifPackage property][15].
*   Once you have the EXIF package, you can now access the EXIF properties of the image; like **Make**, **Model**, **Width**, **Length**, **DateTime**, Copyright, Software, etc as shown below in C# code example.

```
// Extract EXIF Data Package Information from image in C#
using (Metadata metadata = new Metadata("statue-of-liberty.jpg"))
{
    IExif root = metadata.GetRootPackage() as IExif;
    if (root != null && root.ExifPackage != null)
    {
        Console.WriteLine(root.ExifPackage.Make);
        Console.WriteLine(root.ExifPackage.Model);
        Console.WriteLine(root.ExifPackage.ImageWidth);
        Console.WriteLine(root.ExifPackage.ImageLength);
        Console.WriteLine(root.ExifPackage.DateTime);
     }
}
```

The above code will display the following available EXIF information of the provided JPG image.

```
Make : NIKON CORPORATION
Model : NIKON D7200 
Width : 640
Length : 384
DateTime : 2018:07:06 19:31:05
```

### Reading EXIF IFD & GPS Information of Image

EXIF data also include the Exif **IFD** (Image File Directory) and **GPS** (Global Positioning System) Information. Now for IFD and GPS package information, you just have to access the respective properties of **EXIF package** i.e. [ExifIfdPackage][16] or [GpsPackage][17]. From these packages, you can extract much more information than mentioned below:

*   Device serial number
*   Camera Owner name
*   CFA Pattern
*   Speed
*   Image Direction
*   Date Stamp
*   Area Information
*   Altitude
*   Latitude
*   Longitude
*   etc.

Below mentioned code can be added in your above method to display EXIF data along with IFD & GPS information.

```
// Display EXIF IFD Package Properties like Serial Number and Camera Owner.
Console.WriteLine(root.ExifPackage.ExifIfdPackage.BodySerialNumber);
Console.WriteLine(root.ExifPackage.ExifIfdPackage.CameraOwnerName);
Console.WriteLine(root.ExifPackage.ExifIfdPackage.UserComment);
// Display EXIF GPS Information like Latitude, Longitude, etc.
Console.WriteLine(root.ExifPackage.GpsPackage.Altitude);
Console.WriteLine(root.ExifPackage.GpsPackage.LatitudeRef);
Console.WriteLine(root.ExifPackage.GpsPackage.LongitudeRef);
```

## Read All EXIF Tags of Images in C# {#extract-all-exif-tags-from-images}

You can extract all the EXIF properties of any image, you may do it in an almost similar fashion as above:

*   Load the image with [Metadata][18] constructor.
*   Get the **root package** by calling the method [GetRootPackage()][19].
*   Get the **EXIF package** from the [ExifPackage property][20] of the root package.
*   Iterate the EXIF package and get desired name-value pairs.
*   Similarly, get the IFD & GPS packages to displays its keys and values.

```
// Extract all EXIF Metadata from the image
using (Metadata metadata = new Metadata("statue-of-liberty.jpg"))
{
    IExif root = metadata.GetRootPackage() as IExif;
    if (root != null && root.ExifPackage != null)
    {
        const string pattern = "{0} = {1}";
        // Read all EXIF Package Tags and values.
        foreach (TiffTag tag in root.ExifPackage.ToList()) {
            Console.WriteLine(pattern, tag.Name, tag.Value);
        }
        // Read all EXIF IFD Package Tags and values.
        foreach (TiffTag tag in root.ExifPackage.ExifIfdPackage.ToList()) {
            Console.WriteLine(pattern, tag.Name, tag.Value);
        }
         // Read all EXIF GPS Package Tags and values.
        foreach (TiffTag tag in root.ExifPackage.GpsPackage.ToList()) {
            Console.WriteLine(pattern, tag.Name, tag.Value);
        }
    }
}
```

## Update EXIF Properties in C# {#update-exif-properties}

You can change the existing EXIF data of any image easily. Following are the steps you may follow:

### **Update EXIF Package**

*   Get the **root package** by calling the method [GetRootPackage()][21].
*   Set the ExifPackage properties by assigning the new values to corresponding properties like assign new value to:
    *   **root.ExifPackage.Copyright** - to set updated copyrights information.
*   Similarly, you can set the values for the artist, make, model, software, image width & height, DateTime, etc.

### **Update EXIF IFD Package**

Similar to the setting properties of the EXIF package, we can update the properties of EXIF IFD and GPS packages.

*   Assign value to **root.ExifPackage.ExifIfdPackage.CameraOwnerName** to set camera owner.

You may visit the [ExifIfdPackage][22] or [ExifGpsPackage][23] classes to get an idea about how much you can customize for your images.

```
// Update or change new values in EXIF Data (EXIF Package & EXIF IFD Package).
using (Metadata metadata = new Metadata("statue-of-liberty.jpg"))
{
    IExif root = metadata.GetRootPackage() as IExif;
    if (root != null)
    {
        // Set the EXIF package if it is missing
        if (root.ExifPackage == null) {
            root.ExifPackage = new ExifPackage();
        }
       // Setting the desired values in EXIF Package and EXIF IFD Package.
        root.ExifPackage.Copyright = "Copyright (C) 2011-2020 GroupDocs. All Rights Reserved.";
        root.ExifPackage.ImageDescription = "Statue of Liberty for EXIF Data";
        root.ExifPackage.Software = "GroupDocs.Metadata for .NET"; 
        root.ExifPackage.ExifIfdPackage.BodySerialNumber = "GD-2020";
        root.ExifPackage.ExifIfdPackage.CameraOwnerName = "GroupDocs";
        root.ExifPackage.ExifIfdPackage.UserComment = "Nice image captured in 2018";
        metadata.Save("statue-of-liberty-updated.jpg");
    }
}
```

## Remove EXIF Metadata from Images in C# {#remove-exif-metadata}

If you want to remove EXIF package from any file, just set its ExifPackage property to **null**.

```
// Removing the EXIF data from an image.
using (Metadata metadata = new Metadata("statue-of-liberty.jpg"))
{
    IExif root = metadata.GetRootPackage() as IExif;
    if (root != null)
    {
        root.ExifPackage = null;
        metadata.Save("statue-of-liberty-no-exif.jpg");
    }
}
```

## Supported Images & Other Formats {#exif-supported-formats}

These are the currently supported file formats by GroupDocs.Metadata for EXIF data information of images, audios, and videos. You may always visit the [documentation][24] for the updated information.

<figure class="wp-block-table is-style-stripes"><table class="has-fixed-layout"><tbody><tr><td>**Document Type</strong></td><td><strong>File Formats**</td></tr><tr><td><a href="https://wiki.fileformat.com/image/">Images</a></td><td>BMP, GIF, JPG, JPEG, JPE, JP2, PNG, DJVU, DWG, DXF, WebP, TIFF, PSD, EMF, WMF</td></tr><tr><td><a href="https://wiki.fileformat.com/audio">Audio</a> &amp; <a href="https://wiki.fileformat.com/video/">Video</a></td><td>MP3, WAV, AVI, MOV / QT, FLV, ASF, DICOM</td></tr></tbody></table></figure>

## See more about GroupDocs.Metadata

*   Documentation ([.NET][25] | [Java][26]
*   [Source code examples][27]
*   [API Reference][28]
*   GroupDocs.Metadata – [The Metadata Management Solution][29]

**Let’s talk more @** [Free Support Forum.][30]

## Related Article

*   [Manage EXIF Data of Images in Java][31]







[1]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/
[2]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/
[3]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/#extract-exif-data-from-images
[4]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/#extract-all-exif-tags-from-images
[5]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/#update-exif-properties
[6]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/#remove-exif-metadata
[7]: https://products.groupdocs.com/metadata/net
[8]: https://docs.groupdocs.com/display/metadatanet/Features+Overview
[9]: https://downloads.groupdocs.com/metadata/net
[10]: https://www.nuget.org/packages/groupdocs.metadata
[11]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/#exif-supported-formats
[12]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata
[13]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/getrootpackage
[14]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/exifpackage
[15]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/iexif/properties/exifpackage
[16]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/exifpackage/properties/exififdpackage
[17]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/exifpackage/properties/gpspackage
[18]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata
[19]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/getrootpackage
[20]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/iexif/properties/exifpackage
[21]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/getrootpackage
[22]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/exififdpackage
[23]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/exifgpspackage
[24]: https://docs.groupdocs.com/display/metadatanet/Supported+File+Formats
[25]: https://docs.groupdocs.com/display/metadatanet/Getting+Started
[26]: https://docs.groupdocs.com/display/metadatajava/Getting+Started)
[27]: https://github.com/groupdocs-metadata/
[28]: https://apireference.groupdocs.com/metadata
[29]: https://products.groupdocs.com/metadata
[30]: https://forum.groupdocs.com/c/metadata
[31]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/

