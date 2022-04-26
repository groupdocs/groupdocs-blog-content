---
title: "Convertir WebP en JPG, PNG et PDF en Java"
date: Mon, 18 Jan 2021 22:52:00 +0000
draft: false
url: /fr/2021/01/18/convertir-webp-en-jpg-png-et-pdf-en-java/
aliases:
- /2020/01/26/convert-webp-to-png-jpg-and-pdf-in-java/
- /2020/01/26/convert-webp-to-jpg-png-and-pdf-in-java/
author: 'Shoaib Khan'
summary: "Les images WebP **donnent de la transparence comme PNG**, **s'animent comme GIF**, et le plus important pour tout développeur Web est la **taille plus petite que le format JPG de qualité comparative**. Cependant, en raison de problèmes d'incompatibilité ou de toute autre exigence, il est parfois nécessaire de convertir l'image WebP en JPG, PNG ou d'autres formats."
tags: ['convert WebP to JPG in java', 'Convert WebP to PNG in Java', 'Java Convert WebP', 'Java WebP to JPG', 'Java WebP to PDF', 'Java WebP to PNG']
categories: ['GroupDocs.Conversion Product Family']
---

WebP est le format d'image introduit par [Google][1] qui fournit une compression sans perte et avec perte pour les images sur le Web. Les images WebP sont plus petites que les formats d'image bien connus et largement utilisés comme PNG et JPG, offrant ainsi une expérience Web plus rapide.



{{< figure align=center src="images/webp-to-jpg-converter-free-online.jpg" alt="Convertisseur WebP en JPG en ligne gratuit">}}


_Si vous êtes ici uniquement pour convertir en ligne vos fichiers WebP en documents JPG, PNG ou PDF, utilisez [l'outil de conversion WebP en ligne gratuit de GroupDocs][2] développé à l'aide de l'API GroupDocs.Conversion. Cependant, si vous voulez réaliser la chose exacte par programmation en Java, continuez à lire._

Les images WebP **donnent de la transparence comme PNG**, **s'animent comme GIF**, et le plus important pour tout développeur Web est la **taille plus petite que le format JPG de qualité comparative**. Cependant, en raison de problèmes d'incompatibilité ou de toute autre exigence, il est parfois nécessaire de convertir l'image WebP en JPG, PNG ou d'autres formats.

* [API Java pour convertir des images WebP][3]
* [Convertir WebP en JPG en Java][4]
* [Convertir WebP en JPG, PNG, TIFF avec des options avancées en Java][5]
* [Conversion WebP en PDF en Java][6]



{{< figure align=center src="images/convert-webp-to-jpg-png-tiff-with-options.jpg" alt="Convertir une image WebP aux formats JPG, PNG ou PDF en Java et C#" caption="** L'image WebP d'origine est modifiée au format JPG avec des ajustements et des options de couleur. ** Image utilisée : [Un cerisier sauvage (Prunus avium) en fleur][7]. Auteur de l'image : Benjamin Gimmel. Photo sous licence [Creative Commons][8] [Attribution-Share Alike 3.0 Unported][9].">}}


## API Java pour convertir des images WebP {#image-conversion-java-api}

GroupDocs fournit la [solution][10] pour convertir plus de 50 formats de documents et de fichiers image. En tant que développeur Java, vous pouvez utiliser [GroupDocs.Conversion for Java][11] pour convertir des images WebP dans vos applications Java.

Vous pouvez télécharger le fichier **JAR** à partir de la [section téléchargements][12] ou simplement ajouter les configurations de référentiel et de dépendance suivantes dans le fichier pox.xml de vos applications Java **basées sur maven**.

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
        <version>20.10.3</version> 
</dependency>
```

Lors de l'utilisation de l'API GroupDocs.Conversion, vous pouvez obtenir les formats de conversion possibles du document source ou de l'image en utilisant la méthode [getPossibleConversions()][13] de la classe [Converter][14]. Il existe plusieurs façons d'obtenir les conversions possibles, vous pouvez consulter la [documentation][15] ou la [référence API][16] pour cela.

## Convertir WebP en JPG en Java {#convert-webp-to-jpg-in-java}

Les étapes suivantes vous aident à convertir l'image WebP au format JPG ou à d'autres formats :

* Initialisez l'objet de classe [Converter][17] avec le fichier image WebP.
* Définissez le format de conversion sur JPG à l'aide de la méthode **setFormat** de [ImageConvertOptions][18].
* Convertissez le WebP en JPG en utilisant la méthode de conversion.

Le code source Java ci-dessous montre à quel point la conversion WebP au format JPG est facile. Pour la conversion vers d'autres formats pris en charge, il vous suffit de modifier le format de sortie de l'image en définissant le ImageFileType approprié. Par exemple, pour convertir WebP en PNG, changez simplement le ImageFileType ci-dessous de JPG en PNG.

```
// Convertir WebP en JPG en Java à l'aide de l'API GroupDocs.Conversion
Converter converter = new Converter("filePath/WebPImage.webp");
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Jpg);
converter.convert("path/WebPToJPG.jpg", options);
```

## Convertir WebP en JPG, PNG, TIFF avec des options avancées en Java {#convert-webp-with-advanced-options-in-java}

Lors de la conversion du WebP en JPG, PNG ou d'autres formats, vous pouvez également appliquer des ajustements de couleur aux images de sortie. Vous pouvez modifier le contraste, la luminosité et le gamma de l'image résultante. L'image peut être retournée, pivotée, appliquer des filigranes ou obtenir l'image en niveaux de gris comme sortie.

Ci-dessus, j'ai montré les images résultantes qui sont converties du format WebP au format JPG après avoir appliqué différentes variantes à l'aide du code Java mentionné ci-dessous.

```
// Convertissez WebP en JPG, PNG, GIF, TIFF en Java et appliquez des filtres tels que Retourner, Luminosité, Contraste, Gamma, Rotation, Filigrane 
Converter converter = new Converter("filePath/WebPImage.webp");

// Définissez les options de conversion d'image. Vous pouvez appliquer un filtre à la fois.
ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Jpg);
options.setFlipMode(ImageFlipModes.FlipX);
options.setBrightness(50);
options.setContrast(50);
options.setGamma(0.5F);
options.setGrayscale(true);
options.setRotateAngle(90);

// Définir le texte et l'apparence du filigrane 
WatermarkOptions watermark = new WatermarkOptions();
watermark.setText("GroupDocs");
watermark.setFont(new Font("Arial", Font.BOLD, 130));
watermark.setColor(Color.WHITE);
watermark.setBackground(false);
watermark.setRotationAngle(-45);
watermark.setTop(70);
watermark.setLeft(150);
watermark.setTransparency(0.2);
options.setWatermark(watermark);

converter.convert("filePath/WebPToJPG.jpg", options);
```

## Conversion WebP en PDF en Java {#webp-to-pdf-conversion-in-java}

Parallèlement à la conversion de WebP vers d'autres formats d'image, l'API GroupDocs.Conversion permet également de convertir WebP en formats de document tels que PDF. L'exemple suivant montre comment convertir rapidement des images WebP en PDF (Portable Document Format). Vous pouvez en outre appliquer différentes personnalisations pour le fichier PDF résultant à l'aide des [Options de conversion][19] pertinentes.

```
// Convertir WebP en PDF en Java à l'aide de l'API GroupDocs.Conversion
Converter converter = new Converter("filePath/WebPImage.webp");
PdfConvertOptions options = new PdfConvertOptions();
converter.convert("filePath/WebPToPDF.pdf", options);
```

Il existe de nombreux autres exemples open source accessibles au public sur [GitHub Repository][20]. Téléchargez le code source et exécutez rapidement les exemples à l'aide du guide [de démarrage][21]. En cas de difficulté, consultez la [documentation][22] ou rejoignez-nous à tout moment sur le [forum][23].

## Conclusion

Je pense qu'en tant que développeur Java, vous êtes maintenant sûr de convertir par programmation les images WebP en JPG, PNG, GIF, TIFF, PDF et autres formats en Java. Vous pouvez désormais modifier facilement le réglage des couleurs (luminosité du contraste, gamma, niveaux de gris) aux formats convertis et retourner, faire pivoter ou appliquer des filigranes.

Pourquoi ne pas créer votre propre application basée sur Java ? Il peut convertir le format d'image pris en charge et appliquer différents filtres et variations de couleur.

Bonne journée de codage !

## Voir également

* [Convertir WebP en JPG, PNG, TIFF et PDF en C#][24]







[1]: https://developers.google.com/speed/webp
[2]: https://products.groupdocs.app/conversion/webp-to-jpg
[3]: #image-conversion-java-api
[4]: #convert-webp-to-jpg-in-java
[5]: #convert-webp-with-advanced-options-in-java
[6]: #webp-to-pdf-conversion-in-java
[7]: http://commons.wikimedia.org/wiki/File:Fr%C3%BChling_bl%C3%BChender_Kirschenbaum.jpg
[8]: http://en.wikipedia.org/wiki/en:Creative_Commons
[9]: http://creativecommons.org/licenses/by-sa/3.0/deed.en
[10]: https://products.groupdocs.com/conversion
[11]: https://products.groupdocs.com/conversion/java
[12]: https://downloads.groupdocs.com/conversion/java
[13]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#getAllPossibleConversions()
[14]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[15]: https://docs.groupdocs.com/conversion/java/get-possible-conversions/
[16]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter#getPossibleConversions()
[17]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter
[18]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/ImageConvertOptions
[19]: https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/package-frame
[20]: https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-Java
[21]: https://docs.groupdocs.com/display/conversionjava/Getting+Started
[22]: https://docs.groupdocs.com/display/conversionjava/Home
[23]: https://forum.groupdocs.com/c/conversion
[24]: https://blog.groupdocs.com/2020/06/30/convert-webp-to-jpg-png-tiff-and-pdf-in-csharp/


