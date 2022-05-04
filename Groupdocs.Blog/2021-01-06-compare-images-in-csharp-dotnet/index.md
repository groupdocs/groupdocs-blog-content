---
title: "Image Comparison in C# to Spot the Differences"
seoTitle: "Compare Images in C# to Highlight Differences | Comparison API"
description: "Perform image comparison using C# within .NET applications. Compare JPG, PNG, BMP, GIF, DICOM, DCM, or DjVu images using image comparing .NET API."
date: Wed, 06 Jan 2021 17:52:00 +0000
draft: false
url: /2021/01/06/compare-images-in-csharp-dotnet/
aliases:
    - /2019/09/12/compare-two-images-in-c-.net-and-java/
    - /2019/09/12/compare-two-images-in-csharp-.net-and-java/
    - /2019/09/12/compare-two-images-in-csharp-dotnet-and-java/
author: 'Shoaib Khan'
summary: "Whether you want to build an application with spot the difference feature or if you want to compare two images within any of your image processing .NET based applications, you are at the right place. After this article, you can easily compare JPG, PNG, BMP, or images with some other file formats. Without wasting time, let us compare images in C# using the [.NET API for document and image conversion][1]."
tags: ['compare images in csharp', 'compare jpg or png in csharp', 'Image Comparison', 'image comparison in csharp']
categories: ['GroupDocs.Comparison Product Family']
---

Whether you want to build an application with spot the difference feature or if you want to compare two images programmatically within any of your .NET based image processing applications, you are at the right place. After this article, you can easily compare JPG, PNG, BMP, or images with some other file formats. Without wasting time, let's compare images in C# using the [.NET API for document and image comparison][2].



{{< figure align=center src="images/compare-images-to-find-differences-in-dotnet.jpg" alt="Compare Images for Differences using .NET">}}


## .NET Image Comparison API

I will be using [GroupDocs.Comparison for .NET][3] API for comparing images in this article. This API supports comparing **JPG, PNG, BMP, DICOM, DCM, DjVu** images along with many other [supported file formats][4].

You can download the DLLs or MSI installer from the [downloads section][5] or install the API in your .NET application via [NuGet][6].

```
PM> Install-Package GroupDocs.Comparison
```

## Compare Images in C# to Highlight Differences

Comparing two images in C# is too easy with GroupDocs.Comparison within .NET application. The following steps explain how we can compare any two JPG, PNG, BMP, or any other image. It successfully detects the changes and highlights them in the output/resultant image.

*   Define the first image using the [Comparer][7] class.
*   Add the second image using [Add][8] method of Comparer object.
*   Call [Compare][9] method to compare both the images and save the resultant image that highlights the differences among both the images.

The code below shows how to compare two images in C#. As an example, it compares two JPG images and saves the output with differences.

{{< gist GroupDocsGists d1153909e5e54a8c00ccd5ee422a450c "CompareImages.cs" >}}

The images shown at the start of the article are used in this code. Images on the left are compared, and the output is shown on the right side that highlights the differences.

## Conclusion

In this article, we learned how to compare two images in C# using image comparison API. Now you can build your own image comparison application that can compare images and highlight the found differences to its users.

To get a complete idea about the features of the API, you can go through the [documentation][10]. You may also contact the [Free Support Team][11] or [Free Consulting Team][12] that even writes code to help you understand the usage of GroupDocs APIs as per your requirements.

## See Also

*   [Compare Images in Java to Find Differences][13]
*   [Compare Excel, Word, PDF, or PowerPoint files in C#][14]







[1]: https://products.groupdocs.com/comparison/net
[2]: https://products.groupdocs.com/comparison/net
[3]: https://products.groupdocs.com/comparison/net
[4]: https://docs.groupdocs.com/comparison/net/supported-document-formats/
[5]: https://downloads.groupdocs.com/comparison/net
[6]: https://www.nuget.org/packages/groupdocs.comparison
[7]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer
[8]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/add/index
[9]: https://apireference.groupdocs.com/comparison/net/groupdocs.comparison/comparer/methods/compare/index
[10]: https://docs.groupdocs.com/comparison/net/
[11]: https://forum.groupdocs.com/c/comparison
[12]: https://groupdocs-free-consulting.github.io/
[13]: https://blog.groupdocs.com/2021/06/16/compare-images-in-java/
[14]: https://blog.groupdocs.com/2020/03/10/compare-excel-word-pdf-files-in-csharp/

