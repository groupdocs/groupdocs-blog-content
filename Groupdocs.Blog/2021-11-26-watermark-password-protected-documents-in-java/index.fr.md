---
title: "Filigrane des documents protégés par mot de passe en Java"
date: Fri, 26 Nov 2021 09:36:00 +0000
draft: false
url: /fr/2021/11/26/watermark-password-protected-documents-in-java/
author: 'Shoaib Khan'
summary: ''
tags: ['Document Watermarking', 'Watermark Protected Documents using Java', 'Watermark Protected Files', 'Watermark Protected Files using Java', 'watermark using java', 'watermarking API for Java']
categories: ['GroupDocs.Watermark Product Family']
---



{{< figure align=center src="images/watermark-protected-files-using-java.jpg" alt="Documents protégés par filigrane à l'aide de Java">}}


Les filigranes peuvent être utilisés pour protéger le contenu et revendiquer la propriété de vos documents. De même, ceux-ci peuvent également être utilisés pour marquer ou étiqueter vos documents en tant que brouillons. Cet article explique **comment ajouter des filigranes aux fichiers protégés par mot de passe** en Java. Nous ajouterons du texte, ainsi que des filigranes d'image aux fichiers protégés à l'aide d'exemples de code.

Les sujets suivants sont abordés ici :

* [API Java pour filigraner les fichiers protégés par mot de passe][1]
* [Ajouter un filigrane aux fichiers protégés à l'aide de Java][2]
    * [Insérer un filigrane textuel][3]
    * [Insérer un filigrane d'image][4]

## API Java pour filigraner les fichiers protégés par mot de passe {#watermarking-java-api}

[GroupDocs.Watermark][5] présente [l'API Java de filigrane qui permet de travailler avec des filigranes][6] dans vos applications. Nous utiliserons cette API pour insérer des filigranes de texte et d'image dans les documents protégés par mot de passe.

Vous pouvez télécharger le fichier **JAR** à partir de la [section des téléchargements][7] ou utiliser les dernières configurations de référentiel et de dépendance [Maven][8] dans vos applications Java.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-watermark</artifactId>
        <version>21.3</version> 
</dependency>
```

## Ajouter un filigrane aux fichiers protégés par mot de passe à l'aide de Java {#add-watermark-to-protected-files}

Quelques lignes de code vous permettent de personnaliser le filigrane selon vos besoins et de l'appliquer à vos fichiers. Suivez les étapes suivantes pour ajouter les deux types de filigrane.

* **Charger** le fichier protégé.
* **Appliquer** filigrane.
* **Enregistrer** le fichier en filigrane.

Maintenant, nous allons ajouter des filigranes de texte, puis des filigranes d'image, un par un.

## Ajouter un filigrane de texte aux fichiers protégés en Java {#text-watermark-to-protected-files}

Des filigranes de texte peuvent être utilisés pour mentionner les documents comme BROUILLON ou CONFIDENTIEL ; ou à des fins similaires. Les étapes suivantes montrent comment ajouter un filigrane de texte aux documents protégés par mot de passe en Java.

* Préparez l'[option de chargement][9] en utilisant le mot de passe existant.
* Utilisez les options de chargement pour charger le fichier protégé avec la classe [Watermarker][10].
* Définissez le filigrane à l'aide de la classe [TextWatermark][11].
* Définissez le texte, l'apparence, la rotation, l'opacité, la couleur et d'autres propriétés du filigrane.
* Ajoutez le filigrane au document en utilisant la méthode [add()][12].
* Enregistrez le fichier filigrané à l'aide de la méthode [save()][13].

L'extrait de code Java suivant insère un filigrane de texte dans un document PDF protégé.

```
/*
 * Apply Text Watermark to document (PDF, Word, PPT, Excel, ...) in Java
 */
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("P@$$w0rd");

String filePath = "path/document.pdf";
Watermarker watermarker = new Watermarker(filePath, loadOptions);

TextWatermark watermark = new TextWatermark("Watermark", new Font("Arial", 36));
watermark.setForegroundColor(Color.getRed());
watermark.setOpacity(0.3);
watermark.setRotateAngle(-45);

watermarker.add(watermark);
watermarker.save("path/watermark-document.pdf");
```

## Ajouter un filigrane d'image aux fichiers protégés en Java {#image-watermark-to-protected-files}

Vous pouvez également insérer n'importe quelle image ou logo en filigrane. Pour ajouter l'image, utilisez la classe **ImageWatermark**. Les étapes suivantes permettent d'ajouter un filigrane d'image à vos documents protégés par mot de passe en Java.

* Préparez l'[option de chargement][14] pour le fichier protégé en utilisant le mot de passe existant.
* Chargez le fichier à l'aide de la classe [Watermarker][15] et de l'**option de chargement**.
* Chargez le fichier image à l'aide de la classe [ImageWatermark][16].
* Définissez l'apparence, l'alignement, les coordonnées, la rotation, l'opacité et d'autres propriétés du filigrane.
* Maintenant, ajoutez un filigrane au document en utilisant la méthode [add()][17].
* Enfin, enregistrez le fichier filigrané en utilisant la méthode [save()][18].

L'exemple de code Java suivant insère un filigrane d'image dans le fichier PDF protégé.

```
/*
 * Apply Image Watermark to document (PDF, Word, PPT, Excel, ...) in Java
 */
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("P@$$w0rd");

String filePath = "path/document.docx";
Watermarker watermarker = new Watermarker(filePath, loadOptions);

ImageWatermark watermark = new ImageWatermark("path/watermark-image.png");
watermark.setOpacity(0.7);
watermark.setX(70);
watermark.setY(350);

watermarker.add(watermark);
watermarker.save("path/watermark-document.docx");
```

## Obtenez une licence API gratuite

Vous pouvez utiliser les API gratuitement en [obtenant une licence temporaire][19].

## Conclusion

Pour résumer, nous avons discuté de l'ajout de filigranes de texte, ainsi que des filigranes d'image aux fichiers protégés par mot de passe dans les applications Java. De plus, nous avons personnalisé l'apparence des filigranes lorsqu'ils sont appliqués aux documents.

Dans le même ordre d'idées, vous pouvez insérer des filigranes dans les **pages, diapositives et feuilles de documents**, **présentations** et **classeurs** spécifiques, respectivement.

Voir les [articles connexes][20] pour plus de détails et en savoir plus sur sa [documentation][21]. Pour toute question, contactez-nous via le [forum][22].

## Articles Liés {#releated-articles}

* [Rechercher et **Supprimer les filigranes** des documents en Java][23]
* [Ajouter un filigrane à **Images** en Java][24]
* [Présentations protégées par mot de passe en Java][25]
* [Ajouter un filigrane aux **diapositives de présentation** à l'aide de Java][26]
* [Filigrane **PDF** Fichiers en Java][27]







[1]: #watermarking-java-api
[2]: #add-watermark-to-protected-files
[3]: #text-watermark-to-protected-files
[4]: #image-watermark-to-protected-files
[5]: https://products.groupdocs.com/watermark/
[6]: https://products.groupdocs.com/watermark/java/
[7]: https://downloads.groupdocs.com/watermark
[8]: https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo/com/groupdocs
[9]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.options/LoadOptions
[10]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[11]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/TextWatermark
[12]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[13]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String)
[14]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.options/LoadOptions
[15]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker
[16]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark.watermarks/ImageWatermark
[17]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#add(com.groupdocs.watermark.Watermark)
[18]: https://apireference.groupdocs.com/watermark/java/com.groupdocs.watermark/Watermarker#save(java.lang.String)
[19]: https://purchase.groupdocs.com/temporary-license
[20]: #releated-articles
[21]: https://docs.groupdocs.com/watermark/
[22]: https://forum.groupdocs.com/
[23]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/
[24]: https://blog.groupdocs.com/2020/09/15/add-watermark-to-images-in-java/
[25]: https://blog.groupdocs.com/2022/02/10/lock-unlock-ppt-pptx-files-with-password-in-java/
[26]: https://blog.groupdocs.com/2021/06/09/watermark-presentation-slides-using-java/
[27]: https://blog.groupdocs.com/2021/06/26/add-watermark-to-pdf-in-java/


