---
title: "Ajouter un filigrane aux images en Java"
date: Tue, 15 Sep 2020 14:16:12 +0000
draft: false
url: /fr/2020/09/15/ajouter-un-filigrane-aux-images-en-java/
author: 'Shoaib Khan'
summary: "Dans cet article, nous allons apprendre à ** ajouter des filigranes de texte et d'image aux images à l'aide de Java **. Il peut y avoir deux façons d'ajouter un filigrane aux images. Soit vous souhaitez ajouter le filigrane avec le texte personnalisé, soit ajouter un filigrane d'image sur l'image source. Nous verrons les deux scénarios. Actuellement, en plus du JPG et du PNG, cette API Java prend en charge les formats d'image BMP, GIF, JP2, TIFF et WebP pour y ajouter des filigranes. Nous pouvons également modifier le style, l'orientation et l'apparence du texte du filigrane."
tags: ['add text and image watermarks java', 'add text to images in Java', 'image watermarks in Java', 'text watermarks in Java']
categories: ['GroupDocs.Watermark Product Family']
---

Vous vous demandez comment écrire du texte par programmation sur une image à l'aide de Java ? Dans cet article, nous allons apprendre à ** ajouter des filigranes de texte et d'image aux images à l'aide de Java **. Auparavant, nous avons déjà vu la même chose en utilisant C# dans un autre [post][1].



{{< figure align=center src="images/text-watermark-on-png-using-java.png" alt="Ajouter un filigrane de texte à une image PNG à l'aide de Java">}}


Il peut y avoir deux façons d'ajouter un filigrane aux images. Soit vous souhaitez ajouter le filigrane avec le texte personnalisé, soit ajouter un filigrane d'image sur l'image source. Nous verrons les deux scénarios.

* [Insérer un **texte en filigrane** dans les images][2]
* [Insérer un **filigrane d'image** dans les images][3]

## API Java de filigrane de texte et d'image

Dans les exemples ci-dessous, nous utiliserons l'API [GroupDocs.Watermark pour Java][4] pour ajouter un filigrane basé sur le texte et l'image des images JPG et PNG. Ce sera mieux si vous [téléchargez][5] l'API de filigrane à partir de la section des téléchargements ou si vous l'intégrez dans vos applications basées sur Maven avec les configurations mentionnées sur la même page.

## Ajouter du texte aux images en filigrane à l'aide de Java {#add-text-watermark-to-images-in-java}

En suivant les étapes ci-dessous et le code Java, nous pouvons rapidement ajouter du texte à n'importe quel fichier image en tant que filigrane. J'ai filigrané les images JPG et PNG suivantes en utilisant les mêmes étapes et le code mentionné ci-dessous.



{{< figure align=center src="images/text-watermark-on-jpg-using-java.jpg" alt="Ajouter un filigrane de texte à une image JPG à l'aide de Java">}}


Actuellement, en plus des **JPG** et **PNG** affichés, cette API Java prend également en charge les formats d'image **BMP, GIF, JP2, TIFF et WebP** pour y ajouter des filigranes.

* Instanciez l'objet [TextWatermark][6] avec le texte et le style personnalisés.
* Ajustez les paramètres du filigrane de texte.
* Instanciez le [Filigrane][7] avec l'image source.
* Insérez le filigrane dans l'image en utilisant la méthode [add][8].
* Enregistrez l'image de sortie à l'aide de la méthode [save][9].

Voici le code source Java qui ajoute le filigrane de texte à l'image JPG. Si nous devons appliquer le filigrane à une image autre que JPG, aucun grand changement n'est nécessaire. Fournissez simplement cette image avec l'extension au _Watermarker_ et la méthode _save_. C'est ça.

Nous pouvons également modifier le **style**, l'**orientation** et l'**apparence** du texte du filigrane.

```
// Ajouter un filigrane de texte au PNG à l'aide de Java
TextWatermark watermark = new TextWatermark("GroupDocs", new Font("Arial", 30, FontStyle.Bold | FontStyle.Italic));

// Définir les propriétés du filigrane
watermark.setForegroundColor(Color.getBlack());
watermark.setTextAlignment(TextAlignment.Right);
watermark.setRotateAngle(-30);
watermark.setOpacity(0.4);
watermark.setX(70);
watermark.setY(70);

// Ajouter un filigrane à l'image PNG source
Watermarker watermarker = new Watermarker(Constants.PNG_GD);
watermarker.add(watermark);
watermarker.save(Constants.OUTPUT_PNG_PATH);
watermarker.close();
```

## Insérer un filigrane d'image sur des images à l'aide de Java {#add-image-watermark-to-images-in-java}



{{< figure align=center src="images/image-watermark-on-jpg-image-using-java.jpg" alt="Ajouter un filigrane d'image à une image JPG à l'aide de Java">}}


Au lieu d'ajouter du texte à une image, nous pouvons également ajouter une image en filigrane sur l'image source. Suivez les étapes similaires mentionnées ci-dessus, mais vous devez maintenant utiliser la classe **[ImageWatermark][10]** au lieu de _TextWatermark_ utilisée précédemment pour ajouter du texte sur les images JPG et PNG.

Cette [image][11] est créée à l'aide du code source Java mentionné ci-dessous et montre comment nous pouvons ajouter un filigrane d'image PNG sur l'image source JPG :

```
// Ajouter un filigrane d'image PNG à JPG en utilisant Java
ImageWatermark watermark = new ImageWatermark(Constants.Watermark_PNG);
watermark.setX(20);
watermark.setY(80);
// Ajoutez un filigrane à l'image JPG source et enregistrez la sortie
Watermarker watermarker = new Watermarker(Constants.JPG_IMAGE);
watermarker.add(watermark);
watermarker.save(Constants.JPG_IMAGE_OUTPUT);
watermark.close();
watermarker.close();
```

## Conclusion

Nous avons vu comment ajouter du texte et une image en filigrane sur n'importe quelle image par programmation à l'aide de Java. De plus, nous modifions le style de texte et l'orientation du texte du filigrane.

Vous pouvez explorer la [documentation][12] pour de nombreuses autres fonctionnalités de GroupDocs.Watermark pour Java. Pour toute ambiguïté, vous pouvez contacter directement le [support gratuit][13] pour une réponse rapide,

## Voir également

* [Ajouter un filigrane aux images à l'aide de C #][14]
* [Feuilles Excel en filigrane en Java][15]
* [Supprimer les filigranes des documents en Java][16]







[1]: https://blog.groupdocs.com/2019/10/21/add-watermark-to-images-using-csharp-dotnet-api/
[2]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/#add-text-watermark-to-images-in-java
[3]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/#add-image-watermark-to-images-in-java
[4]: https://products.groupdocs.com/watermark/java
[5]: https://downloads.groupdocs.com/watermark/java
[6]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[7]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[8]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[9]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String)
[10]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/ImageWatermark
[11]: https://blog.groupdocs.com/wp-content/uploads/sites/4/2020/09/image-watermark-on-jpg-image-using-java.jpg
[12]: https://docs.groupdocs.com/watermark/java/
[13]: https://forum.groupdocs.com/c/watermark
[14]: https://blog.groupdocs.com/2020/12/20/add-watermark-to-images-using-csharp-dotnet/
[15]: https://blog.groupdocs.com/2021/11/10/watermark-excel-sheets-in-java/
[16]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/


