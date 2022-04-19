---
title: "Diapositives de présentation en filigrane à l'aide de Java"
date: Wed, 09 Jun 2021 17:36:49 +0000
draft: false
url: /fr/2021/06/09/watermark-presentation-slides-using-java/
author: 'Shoaib Khan'
summary: "Pour la protection des documents et des présentations contre une utilisation illégale, nous pouvons utiliser le filigrane. Dans cet article, nous apprendrons à appliquer par programmation des filigranes basés sur du texte et des images aux présentations ou à des diapositives spécifiques d'une présentation en Java. Dans un autre article, nous avons discuté de [l'application de filigranes aux présentations à l'aide de C#][1]."
tags: ['Add Watermark to Presentation in Java', 'Image Watermark to PPT in Java', 'Text Watermark to PPT in Java', 'Watermark PPT in Java', 'Watermark PPTX in Java']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/apply-watermarks-to-presentations-in-java.jpg" alt="Appliquer un filigrane à la présentation en Java">}}


Pour la protection des documents et des présentations contre une utilisation illégale, nous pouvons utiliser le filigrane. Dans cet article, nous apprendrons à appliquer par programmation des filigranes basés sur du texte et des images aux présentations ou à des diapositives spécifiques d'une présentation en Java. Dans un autre article, nous avons discuté de [l'application de filigranes aux présentations à l'aide de C#][2].

Les sujets suivants seront abordés ci-dessous :

* [API de filigrane Java][3]
* [Ajouter des filigranes de texte aux diapositives de présentation][4]
* [Ajouter des filigranes d'image aux diapositives de présentation][5]

## API de filigrane Java pour les présentations {#java-watermarking-api}

[GroupDocs.Watermark][6] fournit l'API Java pour le filigrane, qui permet d'ajouter des filigranes de texte et d'image aux présentations de votre application.

Parallèlement aux présentations, l'API prend en charge l'ajout, la suppression et l'extraction de filigranes à partir de documents de traitement de texte, de feuilles de calcul, de messages électroniques, de fichiers PDF, d'images et de nombreux autres formats.

Parmi les formats de fichiers de présentation, il prend en charge [PPT][7], [PPTX][8], [PPS][9], [PPTM][10], [PPSX][11] et autres. À partir de la [documentation][12], vous pouvez vérifier davantage les fonctionnalités et les [formats de fichiers pris en charge][13].

### Télécharger et configurer

Vous pouvez obtenir la bibliothèque de filigrane à partir de la [section téléchargements][14]. Pour les applications Java basées sur Maven, ajoutez simplement la configuration pom.xml suivante. Ensuite, vous pouvez essayer des exemples de filigrane de cet article ainsi que de nombreux autres exemples de [GitHub][15]. Pour plus de détails, vous pouvez visiter la [API Reference][16].

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
        <artifactId>groupdocs-watermark</artifactId>
        <version>21.3</version> 
</dependency>
```

## Ajouter un filigrane de texte aux diapositives de présentation en Java {#text-watermark-to-slides}

À l'aide de l'API, vous pouvez appliquer des personnalisations tout en ajoutant du texte aux diapositives de la présentation sous forme de filigrane. Les étapes suivantes montrent comment appliquer un filigrane aux présentations dans l'application Java.

* Chargez la présentation à l'aide de [Filigrane][17].
* Définissez le texte et le style du filigrane à l'aide de [TextWatermark][18].
* Définissez les propriétés du filigrane telles que la taille, l'emplacement, l'opacité, la rotation et la couleur.
* Indiquez l'index de la diapositive sur laquelle appliquer le filigrane. _(Optionnel)_
* Ajoutez le filigrane de texte formaté à l'aide de la méthode [add][19].
* Enregistrez la présentation en filigrane en appelant la méthode [save][20].

L'exemple de code suivant montre comment ajouter un filigrane de texte en PPT ou PPTX sur toutes les diapositives avec rotation à l'aide de Java.

```
/*
* Exemple : Comment ajouter des filigranes de texte aux diapositives de présentation en Java
*/
Watermarker watermarker = new Watermarker("path/presentation.pptx");

// Préparer le texte, sa taille, son emplacement et son apparence
TextWatermark watermark = new TextWatermark("Watermark", new Font("Arial", 36));
watermark.setRotateAngle(-45);
watermark.setX(100);
watermark.setY(100);
watermark.setHeight(400);
watermark.setWidth(400);
watermark.setOpacity(0.3);
watermark.setForegroundColor(Color.getDarkBlue());
watermark.setHorizontalAlignment(HorizontalAlignment.Center);
watermark.setVerticalAlignment(VerticalAlignment.Center);

// PresentationWatermarkSlideOptions imageWatermarkOptions = new PresentationWatermarkSlideOptions();
// imageWatermarkOptions.setSlideIndex(0);

// Ajouter un filigrane de texte à la présentation
watermarker.add(watermark);
watermarker.save("path/text-watermarked-presentation.pptx");

watermarker.close();
```

Si l'index des diapositives n'est pas défini, le filigrane sera appliqué à toutes les diapositives de la présentation par défaut. Le code ci-dessus montre également comment mentionner l'index de la diapositive. Voici la sortie avec un filigrane de texte sur toutes les diapositives de la présentation PPTX.



{{< figure align=center src="images/text-watermark-to-slide-in-Java.png" alt="Texte en filigrane sur la diapositive de présentation">}}


## Ajouter un filigrane d'image aux diapositives PPT à l'aide de Java {#image-watermark-to-slides}

Vous pouvez également ajouter des filigranes d'image sur les fichiers de présentation avec une approche similaire. Utilisez simplement la classe [ImageWatermark][21] au lieu de TextWatermark.

Les étapes suivantes expliquent comment ajouter un filigrane d'image aux diapositives de présentation dans vos applications Java.

* Chargez le fichier de présentation à l'aide de [Filigrane][22].
* Chargez l'image, le logo ou la photo à l'aide de [ImageWatermark][23]. Il sera utilisé comme filigrane d'image.
* Définissez les propriétés du filigrane de l'image telles que la rotation, la taille, l'opacité, la couleur et la position.
* Définissez l'index de diapositive sur lequel le filigrane sera appliqué.
* Ajoutez le filigrane de l'image à la présentation à l'aide de la méthode [add][24].
* Enregistrez la présentation avec le filigrane d'image à l'aide de la méthode [save][25].

L'exemple de code suivant ajoute un filigrane d'image à la deuxième diapositive de la présentation PPTX en Java.

```
/*
* Exemple : Comment ajouter des filigranes d'image aux diapositives de présentation en Java
*/
Watermarker watermarker = new Watermarker("path/presentation.pptx");

// Préparer l'image, sa taille, son emplacement et son apparence
ImageWatermark imageWatermark = new ImageWatermark("path/watermarkImage.png");
imageWatermark.setX(80);
imageWatermark.setY(110);
imageWatermark.setOpacity(0.7);
// Définir l'index de diapositive pour le filigrane
PresentationWatermarkSlideOptions imageWatermarkOptions = new PresentationWatermarkSlideOptions();
imageWatermarkOptions.setSlideIndex(1);

// Ajouter un filigrane d'image à la présentation
watermarker.add(imageWatermark, imageWatermarkOptions);
watermarker.save("path/image-watermarked-presentation.pptx");

watermarker.close();
imageWatermark.close();
```

Ce qui suit est la sortie du code avec un filigrane d'image uniquement sur la deuxième diapositive du PPT/PPTX.



{{< figure align=center src="images/image-watermark-to-slide-in-Java.png" alt="Filigrane d'image sur la diapositive de présentation">}}


## Obtenez une licence API gratuite {#Get-a-Free-API-License}

Vous pouvez [obtenir une licence temporaire gratuite][26] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, vous avez appris à ajouter des filigranes aux présentations en Java. Pour être plus précis, nous avons expliqué comment insérer des filigranes de texte ainsi que des filigranes d'image dans des présentations au sein d'applications basées sur Java. Vous pouvez appliquer des filigranes à toutes les diapositives ainsi qu'à n'importe quelle diapositive spécifique des présentations.

En savoir plus sur l'API à l'aide de [documentation][27]. Des exemples sont disponibles sur [GitHub][28]. Pour toute question, contactez-nous via le [forum][29].

## Voir également

* [Feuilles Excel en filigrane en Java][30]
* [Ajouter un filigrane aux images et aux photos en Java][31]
* [Rechercher et supprimer des filigranes de documents en Java][32]
* [Diapositives de présentation en filigrane utilisant C #][33]







[1]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[2]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/
[3]: #java-watermarking-api
[4]: #text-watermark-to-slides
[5]: #image-watermark-to-slides
[6]: https://products.groupdocs.com/watermark/
[7]: https://docs.fileformat.com/presentation/ppt/
[8]: https://docs.fileformat.com/presentation/pptx/
[9]: https://docs.fileformat.com/presentation/pps/
[10]: https://docs.fileformat.com/presentation/pptm/
[11]: https://docs.fileformat.com/presentation/ppsx/
[12]: https://docs.groupdocs.com/watermark/java/
[13]: https://docs.groupdocs.com/watermark/java/supported-document-formats/
[14]: https://downloads.groupdocs.com/watermark
[15]: https://github.com/groupdocs-watermark
[16]: https://apireference.groupdocs.com/conversion/java
[17]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[18]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[19]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[20]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.io.OutputStream)
[21]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/ImageWatermark
[22]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[23]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/ImageWatermark
[24]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[25]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String,%20com.groupdocs.watermark.options.SaveOptions)
[26]: https://purchase.groupdocs.com/temporary-license
[27]: https://docs.groupdocs.com/watermark/
[28]: https://github.com/groupdocs-watermark
[29]: https://forum.groupdocs.com/
[30]: https://blog.groupdocs.com/2021/11/10/watermark-excel-sheets-in-java/
[31]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[32]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/
[33]: https://blog.groupdocs.com/2021/05/01/add-watermark-to-presentations-using-csharp/


