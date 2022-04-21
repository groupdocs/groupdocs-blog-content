---
title: "Convertir des présentations en images en Java"
date: Tue, 18 Jan 2022 09:02:01 +0000
draft: false
url: /fr/2022/01/18/convert-presentations-to-images-in-java/
author: 'Shoaib Khan'
summary: "Bienvenue développeur ! nous espérons que vous êtes ici pour convertir par programme certaines de vos diapositives de présentation en formats d'image. Cela peut être nécessaire lorsque nous voulons partager des diapositives spécifiques sous forme d'images ou si vous souhaitez créer des vignettes à partir des présentations. Dans cet article, vous apprendrez **comment convertir les diapositives de présentation PPT ou PPTX en images JPG et PNG** en Java.

Les sujets suivants sont abordés dans cet article :

* API Java pour la conversion de présentation
* Convertir PPT/PPTX en image JPG
* Convertir PPT/PPTX en image PNG"
tags: ['Convert PPT', 'Convert PPT to JPG in Java', 'Convert PPT to PNG in Java', 'Convert PPTX', 'PPT to JPG in Java', 'PPT to PNG in Java']
categories: ['GroupDocs.Conversion Product Family']
---

Bienvenue développeur ! nous espérons que vous êtes ici pour convertir par programme certaines de vos diapositives de présentation en formats d'image. Cela peut être nécessaire lorsque nous voulons partager des diapositives spécifiques sous forme d'images ou si vous souhaitez créer des vignettes à partir des présentations. Dans cet article, vous apprendrez **comment convertir les diapositives de présentation PPT ou PPTX en images JPG et PNG** en Java.

{{< figure align=center src="images/convert-ppt-to-jpg-png-image-in-java.jpg" alt="Convertir PPT en JPG ou PNG Image en Java">}}

Les sujets suivants sont abordés ici:

* [API Java pour la conversion de présentation](#ppt-convert-java-api)
* [Image PPT/PPTX vers JPG](#ppt-to-jpg)
* [Image PPT/PPTX vers PNG](#ppt-to-png)
* [Convertir en image avec effets](#convert-to-image-with-effects)

## API Java pour convertir des présentations {#ppt-convert-java-api}

[GroupDocs.Conversion](https://products.groupdocs.com/conversion/) fournit une API Java qui permet de convertir des présentations en images. Aujourd'hui, nous allons utiliser son [GroupDocs.Conversion pour Java](https://products.groupdocs.com/conversion/net/) pour convertir les présentations des formats PPT & PPTX en images JPG et PNG. L'API prend également en charge de nombreuses autres conversions de documents de traitement de texte, feuilles de calcul, présentations, livres électroniques, images, etc. qui sont mentionnés dans la [documentation](https://docs.groupdocs.com/conversion/java/supported-document-formats/).

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
        <version>21.10.1</version> 
</dependency>
```

## Convertir une présentation en image JPG en Java {#ppt-to-jpg}

Atteignons l'objectif en transformant la présentation au format d'image JPG. Les étapes suivantes expliquent comment convertir le format d'image Powerpoint PPT/PPTX au format JPG en Java.

* Chargez la présentation à l'aide de la classe [Converter](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter).
* Préparez les [Options de conversion d'image](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/ImageConvertOptions).
* Définissez le format de fichier de conversion comme **JPG**.
* Indiquez le numéro de la diapositive à convertir.
* Convertissez la diapositive de présentation en image JPG à l'aide de la méthode **convert()**.

Le code source Java suivant convertit la présentation PowerPoint au format JPG.

```
// Convertir des présentations PPT, PPTX en images JPG en Java
Converter converter = new Converter("path/presentation.pptx");            

ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Jpg);
options.setPageNumber(1);

converter.convert("path/ppt-to-image.jpg", options);
```

## Convertir une présentation en image PNG en Java {#ppt-to-png}

De même, vous pouvez convertir vers d'autres formats d'image populaires comme PNG. Convertissons n'importe quelle diapositive de la présentation en PNG. Les étapes suivantes montrent comment convertir la diapositive de présentation PPT/PPTX au format d'image PNG en Java.

* Chargez le fichier de présentation à l'aide de la classe [Converter](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion/Converter).
* Préparez les [Options de conversion d'image](https://apireference.groupdocs.com/conversion/java/com.groupdocs.conversion.options.convert/ImageConvertOptions).
* Définissez le format du fichier de conversion sur **PNG**.
* Définissez le nombre de diapositives sélectionnées à convertir.
* Convertissez la diapositive en image PNG à l'aide de la méthode **convert()**.

L'exemple de code source Java suivant convertit la présentation PowerPoint au format PNG.

```
// Convertir des présentations PPT, PPTX en images PNG en Java
Converter converter = new Converter("path/presentation.pptx");

ImageConvertOptions options = new ImageConvertOptions();
options.setFormat(ImageFileType.Png);
options.setPagesCount(1);

converter.convert("path/ppt-to-image.png", options);
```

## Convertir en image avec effets {#convert-to-image-with-effects}

Lors de la conversion des diapositives, vous pouvez appliquer de nombreuses variantes au fichier image de sortie. Vous pouvez en savoir plus à partir de l'un des articles suivants :

* [Convertir en image avec des options avancées en Java](https://blog.groupdocs.com/2021/01/18/convert-webp-to-jpg-png-and-pdf-in-java/)
* [Documentation API pour la conversion d'image avancée](https://docs.groupdocs.com/conversion/java/convert-to-image-with-advanced-options/)

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons appris comment les diapositives de présentation peuvent être converties en images JPG et PNG en Java. Pour créer vos applications de conversion, vous pouvez en savoir plus sur la [documentation](https://docs.groupdocs.com/conversion/java/) et sur les exemples en cours d'exécution sur [GitHub](https://github.com/groupdocs-conversion). Contactez-nous pour toute question via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Convertir des présentations en PDF en Java](https://blog.groupdocs.com/2021/02/15/convert-presentations-odp-pptx-ppt-to-pdf-in-java/)
* [Convertir des images en PDF en Java](https://blog.groupdocs.com/2021/04/21/convert-images-to-pdf-in-java/)
* [Conversion de feuilles de calcul Excel en PDF en Java](https://blog.groupdocs.com/2021/11/21/convert-excel-spreadsheets-to-pdf-in-java/)





