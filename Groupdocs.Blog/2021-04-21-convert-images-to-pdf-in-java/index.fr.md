---
title: "Convertir des images en PDF en Java"
date: Wed, 21 Apr 2021 10:57:00 +0000
draft: false
url: /fr/2021/04/21/convert-images-to-pdf-in-java/
author: 'Shoaib Khan'
summary: "As PDF is the most common portable document format used to exchange files, there arises the requirement to convert documents as well as images to PDF format without losing the quality. In this article, we will learn to programmatically convert images to PDF format in Java."
tags: ['Convert Image to PDF in Java', 'Image Conversion Java API', 'Image to PDF in Java', 'JPG to PDF in Java', 'PNG to PDF in Java', 'WebP to PDF in Java']
categories: ['GroupDocs.Conversion Product Family']
---

Le format PDF étant le format de document portable le plus couramment utilisé pour échanger des fichiers, il est nécessaire de convertir des documents ainsi que des images au format PDF sans perdre en qualité. Dans cet article, nous apprendrons à convertir par programmation des images JPG, PNG, GIF et autres au format PDF à l'aide de Java.



{{< figure align=center src="images/convert-images-to-pdf-in-java.jpg" alt="Convertir des images en PDF en utilisant Java">}}


Voici les sujets abordés brièvement ci-dessous :

* [API Java de conversion d'images][2]
* [Convertir une image JPG en PDF][3]
* [Convertir des images PNG, GIF, BMP en PDF][4]
* [Conversion d'image en PDF avec options][5]

## API Java de conversion d'images {#java-image-conversion-api}

Pour la conversion d'images et de documents au sein de vos applications Java, GroupDocs propose une API [GroupDocs.Conversion for Java][6] native et spécialisée. Il permet de convertir des documents entiers, des pages spécifiques, d'appliquer des rotations, des filigranes même sur des fichiers protégés par mot de passe. L'API a une longue liste de documents et d'images [formats de fichiers pris en charge][7] qui peuvent être convertis dans les deux sens.

### Télécharger et configurer

[Obtenez la bibliothèque de conversion][8] à partir des téléchargements ou ajoutez la configuration pom.xml suivante dans vos applications Java basées sur Maven. Après cela, vous pouvez essayer des exemples de cet article et de nombreux autres exemples disponibles sur [GitHub][9]. Pour plus de détails, vous pouvez visiter la [API Reference][10].

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
        <artifactId>groupdocs-conversion</artifactId>
        <version>21.4</version> 
</dependency>
```

## Convertir JPG en PDF en Java {#jpg-to-pdf}



{{< figure align=center src="images/mount-everest.jpg" alt="Montagne JPG Image">}}


Pour convertir des images au format PDF, il existe un moyen simple. Commençons par une image JPG et suivons les étapes pour convertir une image JPG en un document PDF.

* Chargez l'image JPG en utilisant la classe [Converter][11].
* Convertissez l'image fournie en PDF en utilisant la méthode [convert][12].
* Obtenez l'image PDF convertie à partir de l'emplacement où elle a été enregistrée.

L'exemple de code suivant montre comment convertir une image JPG en PDF en utilisant Java en seulement 2 lignes de code.

```
// Convertir des images JPG en PDF en Java.
Converter converter = new Converter("path/image.jpg");
converter.convert("output/convertedJpg.pdf", new PdfConvertOptions());
```

## Convertir des images PNG, GIF, BMP en PDF en Java {#png-gif-bmp-to-pdf}

L'API n'est pas limitée aux seules images JPG. Il prend en charge une large gamme de formats d'image pour leur conversion en PDF de la même manière. Qu'il s'agisse de PNG en PDF, de GIF en PDF, de BMP en PDF ou de toute autre conversion, cela peut être effectué de la même manière.

Voici les étapes pour convertir n'importe quelle image en un document PDF.

* Chargez n'importe quelle image en utilisant la classe [Converter][13].
* Convertissez l'image fournie en PDF à l'aide de la méthode [convert][14].

L'exemple de code suivant montre comment convertir une image PNG en PDF de la même manière.

```
// Convertir des images en PDF en Java. PNG, WebP, GIF, BMP, TGA et bien d'autres ...
Converter converter = new Converter("path/image.png");
converter.convert("output/convertedImage.pdf", new PdfConvertOptions());
```

## Conversion d'image en PDF en Java avec options {#image-to-pdf-advanced}

Voici les étapes pour convertir des images en un document PDF avec quelques personnalisations selon les besoins. Vous pouvez ajuster les **marges**, **hauteur**, **largeur**, **DPI**, appliquer le **filigrane** et quelques autres options lors de la conversion des images au format PDF.



{{< figure align=center src="images/image-to-pdf-with-watermark-and-margin.png" alt="Converti JPG en PDF">}}


* Chargez l'image en utilisant la classe [Converter][15].
* Initialisez les options de conversion PDF à l'aide de [PdfConvertOptions][16].
* Définissez les marges, la hauteur et la largeur en utilisant les méthodes respectives.
* Appliquez un filigrane à l'aide de [WatermarkOptions][17].
* Convertissez l'image fournie en PDF avec les options définies à l'aide de la méthode [convert][18].

L'exemple de code suivant montre comment convertir une image JPG en un document PDF à l'aide de Java avec des options telles que ; définir des **marges**, une **taille** spécifique, appliquer un **filigrane** avec **rotation** et **transparence**.

```
// Convertissez JPG, PNG ou d'autres images en PDF en Java. Appliquez un filigrane, redimensionnez, définissez le DPI et définissez les marges.
Converter converter = new Converter("path/image.jpg", new ImageLoadOptions());
// Définir les options de conversion PDF
PdfConvertOptions options = new PdfConvertOptions();
options.setDpi(200);
// Définir les marges
options.setMarginBottom(10);
options.setMarginLeft(10);
options.setMarginRight(10);
options.setMarginTop(10);
//options.setRotate(Rotation.On90); // Rotation
options.setWidth(640);
options.setHeight(426);
// Appliquer un filigrane à l'image en PDF 
WatermarkOptions watermarkOptions = new WatermarkOptions();
watermarkOptions.setText("Watermark");
watermarkOptions.setColor(Color.WHITE);
watermarkOptions.setRotationAngle(-45);
watermarkOptions.setTransparency(0.1);
watermarkOptions.setLeft(10);
watermarkOptions.setTop(75);
options.setWatermark(watermarkOptions);
// Enregistrez le fichier PDF converti
converter.convert("output/convertedJpgToPdfAdv.pdf", options);
```

## Obtenez une licence API gratuite {#Get-a-Free-API-License}

Vous pouvez [obtenir une licence temporaire gratuite][19] pour utiliser l'API sans limitation d'évaluation.

## Conclusion

Dans cet article, vous avez appris comment convertir les images au format PDF. Plus précisément, nous avons discuté de la conversion d'images JPG, PNG, BMP en PDF à l'aide de Java. De plus, vous avez vu comment définir les marges, la taille, appliquer un filigrane lors de la conversion d'images PDF.

Pour en savoir plus sur l'API de conversion Java, vous pouvez consulter la [documentation][20]. Pour toute question, contactez-nous via le [forum][21].

## Voir également

* [Convertir des images en PDF à l'aide de C#][22]
* [Convertir des feuilles de calcul (XLS, XLSX) en PDF en Java][23]







[1]: https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/
[2]: #java-image-conversion-api
[3]: #jpg-to-pdf
[4]: #png-gif-bmp-to-pdf
[5]: #image-to-pdf-advanced
[6]: https://products.groupdocs.com/conversion/java
[7]: https://docs.groupdocs.com/conversion/java/supported-document-formats/
[8]: https://downloads.groupdocs.com/conversion/java
[9]: https://github.com/groupdocs-conversion
[10]: https://apireference.groupdocs.com/conversion/java
[11]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[12]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.io.OutputStream,%20com.groupdocs.conversion.contracts.ConvertedDocumentStream,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[13]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[14]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.io.OutputStream,%20com.groupdocs.conversion.contracts.ConvertedDocumentStream,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[15]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[16]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/PdfConvertOptions
[17]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/WatermarkOptions
[18]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#convert(java.io.OutputStream,%20com.groupdocs.conversion.contracts.ConvertedDocumentStream,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[19]: https://purchase.groupdocs.com/temporary-license
[20]: https://docs.groupdocs.com/conversion/
[21]: https://forum.groupdocs.com/
[22]: https://blog.groupdocs.com/2021/05/19/convert-images-to-pdf-in-csharp/
[23]: https://blog.groupdocs.com/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/


