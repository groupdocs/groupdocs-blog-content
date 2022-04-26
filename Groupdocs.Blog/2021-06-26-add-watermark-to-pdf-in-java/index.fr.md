---
title: "Filigrane des fichiers PDF en Java"
date: Sat, 26 Jun 2021 09:48:16 +0000
draft: false
url: /fr/2021/06/26/add-watermark-to-pdf-in-java/
author: 'Shoaib Khan'
summary: "Que vous souhaitiez appliquer une image de marque à vos documents ou que vous souhaitiez protéger nos fichiers de toute utilisation illégale, le filigrane fait le travail pour vous. Dans cet article, vous apprendrez à ajouter par programme les filigranes à vos fichiers PDF à l'aide de Java."
tags: ['Image Watermark PDF in Java', 'Text Watermark PDF in Java', 'Watermark in Java', 'Watermark PDF in Java', 'Watermarking Java API']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/apply-watermarks-to-pdf-in-java.jpg" alt="Appliquer un filigrane au PDF en Java">}}


Que vous souhaitiez appliquer une image de marque à vos documents ou que vous souhaitiez protéger les fichiers de toute utilisation illégale, le filigrane fait le travail pour vous. Dans cet article, vous apprendrez à ajouter par programme les filigranes à vos fichiers PDF à l'aide de Java.

Les sujets suivants sont traités ci-dessous :

* [API de filigrane Java][1]
* [Appliquer un filigrane de texte au PDF][2]
* [Appliquer un filigrane d'image au PDF][3]

## API de filigrane pour Java {#java-watermarking-api}

[GroupDocs.Watermark pour Java][4] est une API de filigrane qui permet de travailler avec des filigranes de texte et d'image dans les fichiers PDF. Outre les fichiers PDF, l'API permet d'ajouter, de supprimer et d'extraire des filigranes pour les documents de traitement de texte, les feuilles de calcul, les présentations, les messages électroniques, les images, les dessins Visio et de nombreux autres formats. À partir de la [documentation][5], vous pouvez vérifier davantage les fonctionnalités et les [formats de fichiers pris en charge][6].

### Télécharger et configurer

Obtenez la bibliothèque de filigrane PDF à partir de la section [téléchargements][7]. Pour les applications Java basées sur Maven, ajoutez la configuration suivante dans pom.xml. Plus tard, vous pourrez essayer les exemples de cet article ainsi que de nombreux autres de [GitHub][8]. Pour plus de détails, vous pouvez également consulter la [API Reference][9].

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

## Ajouter un filigrane de texte au PDF à l'aide de Java {#text-watermark-to-pdf}

Le filigrane de texte peut être appliqué aux fichiers PDF en ajoutant le texte formaté sur toutes les pages ou sur une page sélective à l'emplacement défini.

Les étapes suivantes montrent comment ajouter du texte aux fichiers PDF en tant que filigrane.

* Chargez le document PDF à l'aide de la classe [Watermarker][10].
* Initialisez le filigrane de texte à l'aide de la classe [TextWatermark][11].
* Définissez l'apparence en modifiant l'angle de rotation, les positions xy, l'opacité, les couleurs de premier plan et d'arrière-plan, etc.
* Définir l'index de la page ciblée (facultatif). Si vous ne définissez pas l'index, le filigrane sera appliqué à toutes les pages par défaut.
* Ajoutez le filigrane de texte au filigrane.
* Enregistrez le fichier filigrané en utilisant la méthode [save][12] appropriée.

Le code source montre comment ajouter un filigrane de texte aux fichiers PDF en Java.

```
// Appliquer un filigrane de texte à toutes les pages du fichier PDF en Java
PdfLoadOptions loadOptions = new PdfLoadOptions();
Watermarker watermarker = new Watermarker("path/document.pdf", loadOptions);

// Ajouter du texte au centre de toutes les pages
TextWatermark textWatermark = new TextWatermark("Watermark", new Font("Arial", 80));
textWatermark.setRotateAngle(-45);
textWatermark.setOpacity(0.3);
textWatermark.setForegroundColor(Color.getDarkBlue());
textWatermark.setHorizontalAlignment(HorizontalAlignment.Center);
textWatermark.setVerticalAlignment(VerticalAlignment.Center);

// PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
// imageWatermarkOptions.setPageIndex(0);
watermarker.add(textWatermark);

// Enregistrez le PDF en filigrane
watermarker.save("path/text-watermark.pdf");
watermarker.close();
```

La sortie du code source ci-dessus affiche le filigrane de texte sur les deux pages du fichier PDF donné.



{{< figure align=center src="images/text-watermark-to-pdf-in-java-1024x585.png" alt="Filigrane texte au format PDF">}}


## Ajouter un filigrane d'image au PDF à l'aide de Java {#image-watermark-to-pdf}

De même, vous pouvez ajouter des images à n'importe quel fichier PDF à n'importe quel endroit, tout comme les options de filigrane de texte.

Les étapes suivantes montrent comment ajouter une image aux fichiers PDF en tant que filigrane.

* Chargez le document PDF à l'aide de la classe [Watermarker][13].
* Initialisez le filigrane de l'image à l'aide de la classe [ImageWatermark][14].
* Définissez l'apparence en ajustant l'angle de rotation, les positions xy, l'opacité et d'autres options.
* Définissez l'index de la page ciblée. (Optionnel)
* Ajoutez le filigrane de l'image au filigrane.
* Enregistrez le fichier filigrané en utilisant la méthode [save][15] appropriée.

Le code source montre comment ajouter un filigrane d'image aux fichiers PDF à l'aide de Java.

```
// Appliquer le filigrane d'image à la deuxième page du fichier PDF en Java
PdfLoadOptions loadOptions = new PdfLoadOptions();
Watermarker watermarker = new Watermarker("path/document.pdf", loadOptions);

// Charger l'image et définir l'apparence
ImageWatermark imageWatermark = new ImageWatermark(Constants.LockPng);
imageWatermark.setOpacity(0.7);
imageWatermark.setX(130);
imageWatermark.setY(390);

// Ajouter une image à la deuxième page du fichier PDF
PdfArtifactWatermarkOptions imageWatermarkOptions = new PdfArtifactWatermarkOptions();
imageWatermarkOptions.setPageIndex(1);
watermarker.add(imageWatermark, imageWatermarkOptions);
imageWatermark.close();

// Enregistrez le PDF en filigrane
watermarker.save("path/image-watermark.pdf");
watermarker.close();
```

La sortie du code source ci-dessus montre le filigrane de l'image sur la deuxième page du fichier PDF donné.



{{< figure align=center src="images/image-watermark-to-pdf-in-java-1024x585.png" alt="Filigrane d'image au format PDF">}}


## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][16] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

En résumé, vous avez appris à appliquer des filigranes aux fichiers PDF à l'aide de Java. Nous avons discuté de l'ajout de texte ainsi que d'images sur des fichiers PDF en tant que filigranes. Pour plus de détails ou en savoir plus sur l'API, consultez la [documentation][17]. Pour toute question, contactez-nous via le [forum][18].

## Voir également

* [Ajouter un filigrane aux images en Java][19]
* [Feuilles Excel en filigrane en Java][20]
* [Ajouter un filigrane aux présentations en Java][21]







[1]: #java-watermarking-api
[2]: #text-watermark-to-pdf
[3]: #image-watermark-to-pdf
[4]: https://products.groupdocs.com/watermark/java
[5]: https://docs.groupdocs.com/watermark/java/
[6]: https://docs.groupdocs.com/watermark/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/comparison/java
[8]: https://github.com/groupdocs-comparison
[9]: https://apireference.groupdocs.com/comparison/java
[10]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[11]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[12]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.io.OutputStream)
[13]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[14]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/ImageWatermark
[15]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.io.OutputStream)
[16]: https://purchase.groupdocs.com/temporary-license
[17]: https://docs.groupdocs.com/watermark/
[18]: https://forum.groupdocs.com/
[19]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[20]: https://blog.groupdocs.com/2021/11/10/watermark-excel-sheets-in-java/
[21]: https://blog.groupdocs.com/2021/06/09/watermark-presentation-slides-using-java/


