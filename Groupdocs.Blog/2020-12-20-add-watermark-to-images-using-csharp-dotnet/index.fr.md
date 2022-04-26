---
title: "Ajouter un filigrane aux images à l'aide de C #"
date: Sun, 20 Dec 2020 11:03:00 +0000
draft: false
url: /fr/2020/12/20/ajouter-un-filigrane-aux-images-en-utilisant-csharp-dotnet/
aliases:
- /2019/10/21/add-watermark-to-images-using-csharp-dotnet-api/
- /2019/10/21/csharp-dotnet-api-to-add-watermark-to-images/
- /2019/10/21/c-api-to-add-watermark-on-photos-or-images/
author: 'Shoaib Khan'
summary: "Voyons aujourd'hui, comment ajouter des filigranes aux images. Cela vous aide à personnaliser votre photographie officielle et protège vos photos de toute utilisation non autorisée. Cet article vous guidera pour **ajouter par programmation des filigranes de texte et d'images à vos fichiers image à l'aide de C#**. Dans un article précédent, nous avons vu la même chose pour [ajouter des filigranes basés sur du texte et des images aux images à l'aide de Java][1]. Après avoir lu cet article, il ne vous sera pas difficile d'ajouter des filigranes aux images **JPG/JPEG, PNG, WebP, GIF, TIFF, JP2, BMP** en utilisant C# dans votre application .NET."
tags: ['add watermark in csharp', 'how to add watermark in csharp', 'watermark dotnet api', 'watermark images in csharp']
categories: ['GroupDocs.Watermark Product Family']
---

Voyons aujourd'hui, comment ajouter des filigranes aux images. Cela vous aide à marquer votre photographie officielle et protège vos photos de toute utilisation non autorisée. Cet article vous guidera pour **ajouter par programmation des filigranes de texte et d'image à vos fichiers image à l'aide de C#**. Dans un article précédent, nous avons vu la même chose pour [ajouter des filigranes basés sur du texte et des images aux images à l'aide de Java][2]. Après avoir lu cet article, il ne vous sera pas difficile d'ajouter des filigranes aux images **JPG/JPEG, PNG, WebP, GIF, TIFF, JP2, BMP** en utilisant C# dans votre application .NET.

Voyons maintenant séparément comment nous pouvons facilement ajouter des filigranes basés sur du texte et des images sur vos images, photos ou fichiers image en C# à l'aide de [.NET Watermarking API for documents and images][3].

* [Ajouter du texte sur les images en filigrane][4]
* [Insérer un filigrane d'image dans les images][5]

## API de filigrane de texte et d'image pour .NET {#mce_0}



{{< figure align=center src="images/groupdocs-watermark-net.png" alt="API de filigrane pour .NET - GroupDocs">}}


**GroupDocs.Watermark pour .NET** est une API permettant d'ajouter des filigranes aux images ou aux documents de différents formats de fichiers dans les applications .NET. Il fournit des méthodes de filigrane efficaces qui vous permettent d'ajouter des filigranes de texte ainsi que des filigranes d'image difficiles à supprimer automatiquement par d'autres outils tiers.

À partir de la [documentation][6], vous pouvez vérifier davantage les fonctionnalités et les [formats de fichiers pris en charge][7].

Vous pouvez télécharger les DLL ou le programme d'installation MSI à partir de la [section des téléchargements][8] ou l'obtenir à partir de [NuGet][9].

```
Install-Package GroupDocs.Watermark
```

## Ajouter du texte aux images en filigrane à l'aide de C# {#add-text-watermark-to-image-using-csharp}



{{< figure align=center src="images/text-watermark-on-png-using-java.png" alt="Ajouter un filigrane de texte à une image PNG à l'aide de Java et .NET">}}


L'API vous permet d'ajouter du texte aux images sous forme de filigrane avec de nombreuses personnalisations. Les étapes suivantes expliquent comment appliquer un filigrane sur nos fichiers d'images, photos ou images à l'aide de C # dans l'application .NET.

1. Chargez l'image à l'aide de [Filigrane][10].
2. Définissez le texte et le style du filigrane à l'aide de [TextWatermark][11].
3. Définissez d'autres propriétés de filigrane telles que la position, la rotation, l'opacité, etc.
4. Ajoutez le filigrane de texte à l'image à l'aide de la méthode [Ajouter][12].
5. Enregistrez l'image de sortie avec la méthode [Save][13].

L'exemple de code C# suivant ajoute une étiquette de texte sur une image JPG en tant que filigrane avec une certaine rotation du texte.

```
// Ajouter un filigrane de texte au JPG à l'aide de C#
using (Watermarker watermarker = new Watermarker("filePath/image.jpg"))
{
    // Set the Text and Watermark Font
    Font font = new Font("Arial", 30, FontStyle.Bold | FontStyle.Italic);
    TextWatermark watermark = new TextWatermark("GroupDocs", font);

    // Set Watermark Properties
    watermark.ForegroundColor = Color.Black;
    watermark.TextAlignment = TextAlignment.Right;
    watermark.X = 70;
    watermark.Y = 70;
    watermark.RotateAngle = -30;
    watermark.Opacity = 0.4;
    // watermark.BackgroundColor = Color.Blue;

    // Add the configured watermark to JPG Image
    watermarker.Add(watermark);
    watermarker.Save("filePath/outputImage.jpg");
}
```

## Insérer un filigrane d'image dans les images à l'aide de C# {#add-image-watermark-to-image-using-csharp}



{{< figure align=center src="images/image-watermark-on-jpg-image-using-java.jpg" alt="Ajouter un filigrane d'image à une image JPG à l'aide de GroupDocs.Watermark">}}


De même, nous pouvons également ajouter une autre image en filigrane sur nos fichiers image source. Pour cela, utilisez la classe **ImageWatermark** et ses propriétés pour personnaliser l'apparence du filigrane.

* Créez un objet de classe [Watermarker][14] pour charger l'image source.
* Préparez le filigrane d'image à l'aide de la classe [ImageWatermark][15].
* Définissez les propriétés du filigrane.
* Ajoutez le filigrane de l'image sur l'image source à l'aide de la méthode [Ajouter][16].
* Enregistrez l'image de sortie à l'aide de la méthode [Save][17].

L'exemple de code C# suivant ajoute une image PNG sur un autre fichier PNG en tant que filigrane à l'emplacement préféré.

```
// Ajouter un filigrane d'image PNG sur une image à l'aide de C#
using (Watermarker watermarker = new Watermarker("filePath/image.png"))
{
    using (ImageWatermark watermark = new ImageWatermark("filePath/watermarkLogo.png"))
    {
        // Set Watermark Properties
        watermark.X = 20;
        watermark.Y = 80;
        // Add watermark on image file and save the output
        watermarker.Add(watermark);
        watermarker.Save("filePath/outputImage.png");
    }
}
```

## Conclusion

Je suis convaincu que vous pouvez désormais facilement ajouter un filigrane à vos fichiers image à l'aide de C#. Même vous pouvez créer votre propre application .NET qui prend en charge le filigrane des documents et des images de différents formats de fichiers.

Vous pouvez avoir une [Licence temporaire gratuite][18] pour découvrir tous les aspects du produit. L'assistance gratuite se fera un plaisir de vous sortir de toute confusion et [résolvez vos questions liées au filigrane sur le forum][19].

## Voir également

* [Ajouter un filigrane aux feuilles Excel à l'aide de C #][20]
* [Supprimer le filigrane des documents en C #][21]
* [Ajouter un filigrane aux images en Java][22]







[1]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[2]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[3]: https://products.groupdocs.com/watermark/net
[4]: #add-text-watermark-to-image-using-csharp
[5]: #add-image-watermark-to-image-using-csharp
[6]: https://docs.groupdocs.com/watermark/net/
[7]: https://docs.groupdocs.com/watermark/net/supported-document-formats/
[8]: https://downloads.groupdocs.com/watermark/net
[9]: https://www.nuget.org/packages/GroupDocs.Watermark/
[10]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[11]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/textwatermark
[12]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[13]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[14]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker
[15]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark.watermarks/imagewatermark
[16]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/add/index
[17]: https://apireference.groupdocs.com/watermark/net/groupdocs.watermark/watermarker/methods/save/index
[18]: https://purchase.groupdocs.com/temporary-license
[19]: https://forum.groupdocs.com/c/watermark
[20]: https://blog.groupdocs.com/2021/11/04/watermark-excel-sheets-using-csharp/
[21]: https://blog.groupdocs.com/2020/11/27/find-and-remove-watermarks-from-documents-in-csharp/
[22]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/


