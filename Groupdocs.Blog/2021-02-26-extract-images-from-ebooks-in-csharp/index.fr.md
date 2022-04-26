---
title: "Extraire des images d'EPUB, FB2, CHM eBooks en C#"
date: Fri, 26 Feb 2021 07:26:57 +0000
draft: false
url: /fr/2021/02/26/extraire-des-images-des-ebooks-dans-csharp/
author: 'Shoaib Khan'
summary: "An electronic book, popularly known as **eBook**, is a book in digital form that is readable on various electronic devices. These devices include dedicated eReaders like Kindle, or laptops, desktop computers, and smartphones. There are many popular file formats of eBooks in-use in the market that include; **EPUB**, FictionBook **FB2**, Microsoft Compiled HTML Help - **CHM**, **DjVu**, **MOBI**, **PDF**, and many others. As a programmer, this article will help you to **programmatically extract images from eBooks in C#** within .NET applications."
tags: ['Extract Images from CHM in CSharp', 'Extract Images from eBooks in CSharp', 'Extract Images from EPUB in CSharp', 'Extract Images from FB2 in CSharp', 'Parse eBooks in CSharp', 'Parse eBooks to Extract Images in CSharp']
categories: ['GroupDocs.Parser Product Family']
---

Un livre électronique, communément appelé **eBook**, est un livre sous forme numérique lisible sur divers appareils électroniques. Ces appareils incluent des liseuses dédiées telles que [Kindle][2], ou des ordinateurs portables, des ordinateurs de bureau et des smartphones. Il existe de nombreux formats de fichiers populaires de livres électroniques utilisés sur le marché qui incluent ; **EPUB**, FictionBook **FB2**, Microsoft Compiled HTML Help - **CHM**, **DjVu**, **MOBI**, **PDF** et bien d'autres. En tant que programmeur, cet article vous aidera à **extraire par programme des images de livres électroniques en C#** dans des applications .NET.

Les sujets suivants seront abordés ci-dessous :

* [API .NET pour l'extraction d'images à partir de livres électroniques][3]
* [Extraire des images d'un livre électronique EPUB en C#][4]
* [Extraire des images de FB2, CHM eBooks en C#][5]

## API .NET pour l'extraction d'images à partir de livres électroniques {#image-extraction-dotnet-api-for-ebooks}

Pour l'extraction d'images à partir d'eBooks, j'utiliserai l'API [GroupDocs.Parser for .NET][6] dans les exemples C# de cet article. Outre les livres électroniques, cette API prend en charge l'analyse et l'extraction d'images à partir de documents de traitement de texte, de feuilles de calcul, de PDF, de présentations, d'e-mails, d'archives ZIP et de nombreux autres formats de documents.

Vous pouvez télécharger les DLL ou le programme d'installation MSI à partir de la [section des téléchargements][7] ou installer l'API dans votre application .NET via [NuGet][8].

```
PM> Install-Package GroupDocs.Parser
```

## Extraire des images d'un livre électronique EPUB en C# {#extract-images-from-epub-in-csharp}

Commençons par l'eBook EPUB pour l'analyser à la recherche d'images. Les étapes suivantes suivies par le code C # analysent le livre électronique EPUB et en extraient toutes les images.

* Créer un objet de classe [Parser][9].
* Utilisez la méthode [GetImages][10] pour extraire toutes les images du livre électronique EPUB.
* Parcourez les images extraites pour les [enregistrer][11], une par une.



{{< figure align=center src="images/alice.png" alt="Alice EPUB" caption="Livre électronique EPUB d'Adobe [Sample eBook Library][12]">}}


Le code C # suivant implémente les étapes d'analyse mentionnées pour analyser le livre électronique EPUB illustré ci-dessus et enregistre les images extraites une par une sur le disque.

```
// Analyser des livres électroniques pour extraire des images d'un fichier EPUB, FB2, CHM et les enregistrer sur le disque en C #
using (Parser parser = new Parser("ebook.epub"))
{
    // Extract images from the eBook
    IEnumerable<PageImageArea> images = parser.GetImages();
    ImageOptions options = new ImageOptions(ImageFormat.Jpeg);
    int imageNumber = 0;
    // Iterate over extracted images
    foreach (PageImageArea image in images)
    {
        image.Save(("Image-" + imageNumber.ToString() + image.FileType.Extension), options);
        imageNumber++;
    }
}
```



{{< figure align=center src="images/alice-image-from-epub.jpg" alt="Extraire l'image de l'EPUB en C#">}}


En conséquence, toutes les images disponibles seront enregistrées. Voici l'une des images présentées à titre d'exemple.

Vous pouvez enregistrer les images extraites dans l'un des formats de fichier image pris en charge suivants :

*JPG
*PNG
* WEBP
* GIF
* BMP

## Extraire des images de FB2, CHM eBooks en C # {#extract-images-from-fb2-chm-in-csharp}

Si vous avez le livre électronique au format FB2, CHM ou dans un autre format, vous pouvez extraire ses images de la même manière. Il vous suffit de passer votre eBook au constructeur **Parser** lors de la création de l'objet. Ensuite, la méthode **GetImages** extraira les images de n'importe lequel des livres électroniques fournis en utilisant le même code C#.

```
// Pass the FB2, CHM, PDF, or any other eBook to Parser contructor
Parser parser = new Parser("ebook.fb2"); // FB2
// Parser parser = new Parser("ebook.chm"); // CHM
// Parser parser = new Parser("ebook.pdf"); // PDF
IEnumerable<PageImageArea> images = parser.GetImages();
```

## Conclusion

J'espère que vous serez maintenant à l'aise pour obtenir par programmation toutes les images des livres électroniques avec EPUB, FB2, CHM et d'autres formats de fichiers dans vos applications .NET. Vous pouvez même créer votre propre application d'extraction d'images à l'aide de l'API [GroupDocs.Parser for .NET][13].

Pour en savoir plus sur l'API, vous pouvez consulter la [documentation][14] ou des exemples open source sur GitHub. Pour tout autre problème, vous pouvez contacter le support rapide sur le [forum][15].

## Voir également

* [Extraire des images de Word, Excel. Fichiers PPT utilisant C#][16]
* [Extraire des images de documents PDF à l'aide de C #][17]
* [Extraire des images de documents à l'aide de Java][18]







[1]: https://blog.groupdocs.com/2021/02/26/extract-images-from-ebooks-in-csharp/
[2]: https://en.wikipedia.org/wiki/Amazon_Kindle
[3]: #image-extraction-dotnet-api-for-ebooks
[4]: #extract-images-from-epub-in-csharp
[5]: #extract-images-from-fb2-chm-in-csharp
[6]: https://products.groupdocs.com/parser/net
[7]: https://downloads.groupdocs.com/parser/net
[8]: https://www.nuget.org/packages/groupdocs.parser
[9]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser
[10]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/getimages/index
[11]: https://apireference.groupdocs.com/parser/net/groupdocs.parser.data/pageimagearea/methods/save/index
[12]: https://www.adobe.com/solutions/ebook/digital-editions/sample-ebook-library.html
[13]: https://products.groupdocs.com/parser/net
[14]: https://docs.groupdocs.com/parser/net/
[15]: https://forum.groupdocs.com/c/parser/
[16]: https://blog.groupdocs.com/2020/10/28/extract-images-from-pdf-word-excel-ppt-using-csharp/
[17]: https://blog.groupdocs.com/2019/10/04/extract-images-from-pdf-files-in-csharp/
[18]: https://blog.groupdocs.com/2020/10/27/extract-images-from-pdf-word-excel-ppt-using-java/


