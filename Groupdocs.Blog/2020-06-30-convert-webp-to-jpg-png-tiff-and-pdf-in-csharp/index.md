---
title: 'Convert WebP to JPG, PNG, TIFF, and PDF in C#'
date: Tue, 30 Jun 2020 07:03:38 +0000
draft: false
url: /2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/
author: 'Shoaib Khan'
summary: 'In our previous [post][1], we discussed WebP images and learned to convert WebP Images in Java. Today, in this article, we will learn to programmatically convert the WebP images into JPG, PNG, TIFF, and other formats using C#.'
tags: ['convert webp in csharp', 'convert webp to jpg in csharp', 'convert webp to pdf in csharp', 'convert webp to png in csharp']
categories: ['GroupDocs.Conversion Product Family']
---

In our previous [post][2], we discussed WebP images and learned to convert WebP Images in Java. Today, in this article, we will learn to programmatically convert the WebP images into JPG, PNG, TIFF, and other formats using C#.



{{< figure align=center src="images/convert-webp-to-jpg-png-in-csharp.jpg" alt="Convert WebP image to JPG, PNG or PDF formats in CSharp">}}


First, we will have a look to convert the WebP images in the simplest way. Later we will convert with some customized options like tilt, flip, grayscale, resize, change gamma, contrast, and brightness, and add watermark to converted JPG images. Following are the quick links to topics:

*   [Convert WebP to JPG, PNG & TIFF in C#][3]
*   [WebP conversion with Advanced Options (Apply Effects)][4]
*   [Convert WebP to PDF in C#][5]

Steps in this article and code samples are using [GroupDocs.Conversion for NET][6]. So please make sure to install the API from any of the following methods:

*   Install using [NuGet][7] Package Manager.
*   [Download][8] the DLL and reference it into the project.

## Convert WebP to JPG in C# {#convert-webp-to-jpg-png-tiff-in-csharp}

To convert the WebP images into other formats, use the **Converter** class. For the simple conversion, you can use the below-mentioned few lines of C# code. This example shows the quick conversion of a WebP image to a JPG file. Just follow the steps:

1.  Instantiate the [Converter][9] object with the source WebP image.
2.  Instantiate the Image Conversion Options using [ImageConvertOptions][10] class and just set the Format to JPG.
3.  Call the [Convert][11] method with the output file path and the conversion options.

```
// Convert WebP image to JPG, PNG, BMP or any other format in C#
using (Converter converter = new Converter("./Resources/groupdocs\_conversion-brand.webp"))
{
    ImageConvertOptions options = new ImageConvertOptions
    { // Set the conversion format to JPG
        Format = ImageFileType.Jpg
    };
    converter.Convert(@"./Output/converted-image.jpg", options);
}
```

Here are the original WebP image and the converted JPG image that is converted using the above code:



{{< figure align=center src="images/groupdocs_conversion-brand.webp" alt="WebP Image" caption="WebP Image">}}
</td><td>

{{< figure align=center src="images/converted-image.jpg" alt="Converted from WebP to JPG" caption="Converted JPG Image">}}
</td></tr></tbody></table></figure>

### Convert WebP to PNG, TIFF and other Image Formats in C#

Using the same above code and by just changing the file format i.e. **"ImageFileType.Jpg"** and the output file name, you may easily convert your WebP files into JPEG, PNG, TIF, TIFF, BMP, etc.

This was the simple conversion, now let us convert with different effects.

## Convert WebP to JPG, PNG, TIFF with Advanced Options in C# {#convert-webp-and-apply-effects-in-csharp}

Along with the conversion of WebP to other formats, we can also add effects while converting. Below are some of the effects like; convert to **grayscale**; **flip** images horizontally or vertically; **rotate** the image to any angle; **resize** the image to make it smaller or larger; change the **contrast**, **brightness**, **gamma** values; or even apply **watermarks** to the converted images.



{{< figure align=center src="images/converted-image.jpg" alt="Converted from WebP to JPG" caption="WebP to JPG">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-grayscale.jpg" alt="Converted from WebP to JPG in Grayscale" caption="Grayscale">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-resize.jpg" alt="Converted from WebP to JPG with Resize" caption="Resize">}}
</td></tr><tr><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-flipped.jpg" alt="Converted from WebP to JPG with Horizontal Flip" caption="Flip">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-contrast-50.jpg" alt="Converted from WebP to JPG with changed Contrast" caption="Contrast">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-with-wateramrk.jpg" alt="Converted from WebP to JPG with Watermark" caption="Watermark">}}
</td></tr><tr><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-rotated-1.jpg" alt="Converted from WebP to JPG with Rotation" caption="Rotate">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-and-brightness-50.jpg" alt="Converted from WebP to JPG with Changed Brightness" caption="Brightness">}}
</td><td class="has-text-align-center" data-align="center">

{{< figure align=center src="images/converted-with-gamma-0.5.jpg" alt="Converted from WebP to JPG with Gamma Change" caption="Gamma">}}
</td></tr></tbody></table></figure>

Here is the code that is used to apply these effects. You may apply these effects one by one or in combination to get the desired results.

```
// Apply effects while converting WebP image to other formats in C#
using (Converter converter = new Converter("./Resources/groupdocs\_conversion-brand.webp"))
{
    ImageConvertOptions options = new ImageConvertOptions
    {
        Format = ImageFileType.Jpg,
        Grayscale = true,   // Convert the image in Grayscale
        Height = 141,       // Resize the Image Height
        Width = 167,        // Resize the image Width
        FlipMode = ImageFlipModes.FlipX,    // Flip the image
        Contrast = 50,      // Change the contrast of image
        RotateAngle = 90,   // Rotate the image
        Brightness = 50,    // Change the brightness
        Gamma = 0.5F,       // Gamma Setting
        Watermark =         // Watermark Settings
        {
            Text = "GroupDocs",
            Width = 100,
            Height = 100,
            Background = false,
            Top = 70,
            Left = 90,
            RotationAngle = -45,
        }
    };
    converter.Convert(@"./Output/converted-with-options.jpg", options);
}
```

## Convert WebP to PDF in C# {#convert-webp-to-pdf-in-csharp}

Along with the conversion of WebP images to other image file formats, we can also convert images to PDF format. Following 3 lines of code will do the trick and help you converting the WebP image to PDF format.

```
// Convert WebP to PDF in C#
using (Converter converter = new Converter("./Resources/groupdocs\_conversion-brand.webp"))
{
    PdfConvertOptions options = new PdfConvertOptions();
    converter.Convert(@"./Output/converted-webp-image.pdf", options);
}
```

For more details and advance options to convert into PDF, you may visit the [documentation][12].

## See Also

*   [Convert WebP to JPG, PNG, and PDF in Java][13]

There are many other open-source examples that are publicly available at [GitHub Repository][14]. Download the source code and quickly run the examples using the [getting started][15] guide. In case of any difficulty, look at the [documentation][16] or reach us at any time on the [forum][17].







[1]: https://blog.groupdocs.com/2020/01/26/convert-webp-to-jpg-png-and-pdf-in-java/
[2]: https://blog.groupdocs.com/2020/01/26/convert-webp-to-jpg-png-and-pdf-in-java/
[3]: https://blog.groupdocs.com/2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/#convert-webp-to-jpg-png-tiff-in-csharp
[4]: https://blog.groupdocs.com/2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/#convert-webp-and-apply-effects-in-csharp
[5]: https://blog.groupdocs.com/2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/#convert-webp-to-pdf-in-csharp
[6]: https://products.groupdocs.com/conversion/net
[7]: https://www.nuget.org/packages/groupdocs.conversion
[8]: https://downloads.groupdocs.com/conversion/net
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[10]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/imageconvertoptions
[11]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.converter/convert/methods/16
[12]: https://docs.groupdocs.com/conversion/net/convert-to-pdf-with-advanced-options/
[13]: https://blog.groupdocs.com/2021/01/18/convert-webp-to-jpg-png-and-pdf-in-java/
[14]: https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET
[15]: https://docs.groupdocs.com/display/conversionnet/Getting+Started
[16]: https://docs.groupdocs.com/display/conversionnet/Home
[17]: https://forum.groupdocs.com/c/conversion

