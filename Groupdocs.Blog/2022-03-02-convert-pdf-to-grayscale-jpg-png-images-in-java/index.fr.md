---
title: "Convertir un PDF en niveaux de gris en Java"
date: Wed, 02 Mar 2022 15:53:00 +0000
draft: false
url: /fr/2022/03/02/convert-pdf-to-grayscale-jpg-png-images-in-java/
author: 'Shoaib Khan'
summary: "Presque tous les formats de document ou d'image (y compris les images) peuvent être convertis en une image monochrome en noir et blanc ou en niveaux de gris. Dans cet article, nous verrons comment convertir des documents PDF couleur en **formats d'image JPG et PNG en niveaux de gris en Java**."
tags: ['convert document to image', 'convert to grayscale', 'Convert to Grayscale in Java', 'PDF to Grayscale', 'PDF to Grayscale in Java', 'PDF to JPG Grayscale', 'PDF to PNG Grayscale']
categories: ['GroupDocs.Conversion Product Family']
---

Presque tous les documents ou formats d'image (y compris les images) peuvent être convertis en images en noir et blanc ou en niveaux de gris. Dans cet article, nous verrons comment convertir des documents PDF couleur en **formats d'image JPG et PNG en niveaux de gris en Java**.



{{< figure align=center src="images/Converted-Colored-PDF-to-Grayscale-1024x577.jpg" alt="PDF converti en niveaux de gris">}}


## API Java pour convertir des documents en niveaux de gris

[GroupDocs.Conversion](https://products.groupdocs.com/conversion/net/) fournit une API Java pour convertir des documents entre une multitude de [formats de fichiers et types d'images pris en charge](https://docs.groupdocs.com/conversion/net/supported-document-formats/). Les résultats de conversion peuvent être personnalisés à l'aide de plusieurs options avancées. J'utiliserai cette API [GroupDocs.Conversion pour Java](https://products.groupdocs.com/conversion/java/) pour convertir les documents PDF en images JPG et PNG en niveaux de gris.

### Télécharger ou configurer

Vous pouvez télécharger le fichier **JAR** à partir de la [section des téléchargements](https://downloads.groupdocs.com/conversion), ou simplement obtenir les configurations du référentiel et des dépendances pour le pox.xml de votre **Maven-based** Applications Java.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>22.3</version> 
</dependency>
```

## Convertir un PDF en image JPG en niveaux de gris en Java

En commençant par la conversion de documents PDF couleur et en les transformant en formats d'image. Les étapes suivantes montrent comment convertir le PDF en JPG en niveaux de gris en Java.

* Chargez le document PDF à l'aide de la classe [Converter](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter).
* Préparez les [options de conversion d'image](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/ImageConvertOptions).
* Définissez le format de fichier de conversion sur **JPG**.
* Définissez l'option de niveaux de gris sur true.
* Convertir en image en utilisant la méthode **convert()** appropriée avec des options.

Le code source Java suivant convertit le document PDF en une image JPG en niveaux de gris.

```
// Convertir un PDF en PNG en niveaux de gris en Java
Converter converter = new Converter("path/document.pdf");

ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Jpg);
options.setGrayscale(true);
/*
options.setFlipMode(ImageFlipModes.FlipY);
options.setBrightness(50);
options.setContrast(50);
options.setGamma(0.5F);
*/
converter.convert("path/grayscaleDocument.jpg", options);
```

De plus, il existe de nombreuses autres options pour personnaliser la hauteur, la largeur, le retournement horizontal et vertical, les rotations de documents et des propriétés telles que la luminosité, le gamma et le contraste. De plus, vous pouvez appliquer les filigranes avec différents paramètres à l'image de sortie.

## Convertir un PDF en image PNG en niveaux de gris en Java

De même, le document PDF couleur peut également être converti en d'autres formats d'image en niveaux de gris. Les étapes suivantes montrent comment convertir un fichier PDF en PNG en niveaux de gris en Java.

* Chargez le document PDF à l'aide de la classe [Converter](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter).
* Préparez les options de conversion à l'aide de [ImageConvertOptions](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/ImageConvertOptions).
* Définissez le format du fichier de conversion sur **PNG**.
* Définissez l'option de niveaux de gris sur true.
* Convertir en image PNG en utilisant la méthode **convert()**.

Le code source Java suivant convertit le document PDF en une image PNG en niveaux de gris.

```
// Convertir un PDF en PNG en niveaux de gris en Java
Converter converter = new Converter("path/document.pdf");

ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Png);
options.setGrayscale(true);

converter.convert("path/grayscaleDocument.png", options);
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour résumer, nous avons appris comment les documents PDF peuvent être convertis en formats d'image PNG ou JPG en Java. Essayez de créer votre propre application de conversion. Vous pouvez en savoir plus sur les API Java low code et high code dans la [documentation](https://docs.groupdocs.com/conversion/net/) pour l'automatisation des conversions de documents.

Le moyen le plus simple consiste à découvrir les exemples de [GitHub](https://github.com/groupdocs-conversion). Contactez-nous pour toute question via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Convertir un PDF en niveaux de gris à l'aide de C#](https://blog.groupdocs.com/2022/03/16/convert-pdf-to-grayscale-jpg-png-images-in-csharp/)
* [Transformer des présentations en images en Java](https://blog.groupdocs.com/2022/01/18/convert-presentations-to-images-in-java/)
* [Convertir des images en PDF en Java](https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/)





