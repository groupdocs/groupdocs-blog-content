---
title: "Gérer les données XMP et EXIF des images HEIF/HEIC à l'aide de Java"
date: Mon, 10 May 2021 08:20:00 +0000
draft: false
url: /fr/2021/05/10/données-xmp-et-exif-des-images-heif-heic-utilisant-java/
author: 'Shoaib Khan'
summary: "**HEIC** signifie High-Efficiency Image Container. Il s'agit de l'extension de fichier pour les images capturées pour certains appareils Apple. Il s'agit d'un conteneur pouvant contenir des images au format d'image **HEIF** à haute efficacité. Dans cet article, nous expliquerons **comment extraire, mettre à jour et supprimer les métadonnées EXIF et XMP des images HEIF/HEIC** dans les applications Java."
tags: ['exif data', 'exif data in Java', 'exif data of heic in java', 'XMP data in Java', 'xmp data of heic in java', 'XMP metadata']
categories: ['GroupDocs.Metadata Product Family']
---

**HEIC** signifie High-Efficiency Image Container. Il s'agit de l'extension de fichier pour les images capturées pour certains appareils Apple. Il s'agit d'un conteneur pouvant contenir des images au format d'image **HEIF** à haute efficacité. Dans cet article, nous expliquerons **comment extraire, mettre à jour et supprimer les métadonnées EXIF et XMP des images HEIF/HEIC** dans les applications Java.

**EXIF**, le format de fichier d'image échangeable est la norme qui définit comment stocker les propriétés des métadonnées dans les images et les formats audio les plus courants. **XMP** est une norme de métadonnées basée sur XML, qui peut stocker n'importe quel ensemble de propriétés de métadonnées sous forme de paires nom/valeur.

Les sujets suivants sont traités ci-dessous

* [API Java de métadonnées pour les données EXIF, XMP][2]
* [Lire les données EXIF des images HEIC/HEIF][3]
* [Lire les données XMP des images HEIC/HEIF][4]

## API Java pour les métadonnées EXIF et XMP {#java-api-for-exif-and-xmp-metadata}

[GroupDocs.Metadata][5] fournit l'API de manipulation des métadonnées pour vos applications Java. L'API permet de lire, mettre à jour, ajouter, nettoyer/supprimer et traverser des fonctionnalités pour de nombreux formats de fichiers. Il prend en charge diverses normes de métadonnées telles que EXIF, IPTC et XMP. Les documents de traitement de texte, les feuilles de calcul, les présentations, les messages électroniques, les livres électroniques, les images, les dessins AutoCAD, les fichiers audio et vidéo, les torrents font partie des formats de document pris en charge. Plus précisément, vous pouvez consulter la documentation pour la liste complète des [formats de fichiers pris en charge pour la manipulation des métadonnées][6].

### Télécharger et configurer

Obtenez la bibliothèque de métadonnées à partir de la section [téléchargements][7]. Pour votre application Java basée sur Maven, ajoutez simplement la configuration pom.xml suivante. Après cela, vous pouvez essayer les exemples de cet article ainsi que les nombreux autres exemples disponibles sur [GitHub][8]. Pour plus de détails, vous pouvez visiter la [API Reference][9].

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
        <artifactId>groupdocs-metadata</artifactId>
        <version>21.4</version> 
</dependency>
```

## Lire les données EXIF des images HEIF / HEIC en Java {#read-exif-of-heic-heif-images}

Voici les étapes pour lire et extraire les données EXIF des images HEIC et HEIF.

* Chargez l'image HEIF ou HEIC en utilisant la classe Metadata.
* Obtenez le package racine.
* Récupérez le package EXIF à partir du package racine.
* À partir du package EXIF, vous pouvez parcourir les propriétés des données EXIF.
* De plus, vous pouvez obtenir les informations IFD (répertoire de fichiers d'images) et GPS à partir du package EXIF.

Le code suivant montre comment obtenir les données EXIF, les informations de métadonnées IFD et GPS de l'image HEIC à l'aide de Java.

```
// Lire EXIF, EXIF IFD, EXIF GPS Package d'images HEIF / HEIC en Java
Metadata metadata = new Metadata("image.heic");
IExif root = (IExif) metadata.getRootPackage();
if (root.getExifPackage() != null) {
    String pattern = "%s : %s";
    // Get EXIF Package information
    for (TiffTag tag : root.getExifPackage().toList()) {
        System.out.println(String.format(pattern, tag.getName(), tag.getInterpretedValue()));
    }
    // Get EXIF IFD Package Information
    for (TiffTag tag : root.getExifPackage().getExifIfdPackage().toList()) {
        System.out.println(String.format(pattern, tag.getName(), tag.getInterpretedValue()));
    }
    // Get GPS information
    for (TiffTag tag : root.getExifPackage().getGpsPackage().toList()) {
        System.out.println(String.format(pattern, tag.getName(), tag.getInterpretedValue()));
    }
}
```

## Lire les données XMP des images HEIC / HEIF en Java {#read-xmp-of-heic-heif-images}

Les étapes suivantes lisent les métadonnées XMP des images HEIC ou HEIF.

* Chargez l'image HEIF ou HEIC en utilisant la classe Metadata.
* Obtenez le package racine à l'aide de la méthode getRootPackage.
* À partir du package racine, vous pouvez obtenir les informations de base XMP.
* De plus, vous pouvez obtenir les informations DCMI Dublin Core.
* De plus, vous pouvez obtenir des informations sur Photoshop à l'aide de la méthode getPhotoshop.

Le code source suivant montre comment obtenir des informations XMP basic, DCMI et Photoshop en Java.

```
// Extraire les données XMP Basic, DublinCore et Photoshop des images heic et heif en Java
Metadata metadata = new Metadata("image.heic");
IXmp root = (IXmp) metadata.getRootPackage();

if (root.getXmpPackage() != null) {
    // XMP Basic    
    if (root.getXmpPackage().getSchemes().getXmpBasic() != null) {
        XmpBasicPackage xmpBasicPackage = root.getXmpPackage().getSchemes().getXmpBasic();
	System.out.println("Creator Tool : " + xmpBasicPackage.getCreatorTool());
	System.out.println("Create Date : " + xmpBasicPackage.getCreateDate());
	System.out.println("Modify Date : " + xmpBasicPackage.getModifyDate());
	System.out.println("Label : " + xmpBasicPackage.getLabel());
	System.out.println("Nick Name: " + xmpBasicPackage.getNickname());
	// ...
    }
    // DublinCore information
    if (root.getXmpPackage().getSchemes().getDublinCore() != null) {
	XmpDublinCorePackage xmpDublinCorePackage = root.getXmpPackage().getSchemes().getDublinCore();
	System.out.println("Format : " + xmpDublinCorePackage.getFormat());
	System.out.println("Coverage :" + xmpDublinCorePackage.getCoverage());
	System.out.println("Identifier : " + xmpDublinCorePackage.getIdentifier());
	System.out.println("Source : " + xmpDublinCorePackage.getSource());
	// ...
    }
    // Photoshop Information
    if (root.getXmpPackage().getSchemes().getPhotoshop() != null) {
	XmpPhotoshopPackage xmpPhotoshopPackage = root.getXmpPackage().getSchemes().getPhotoshop();
	System.out.println("Color Mode : " + xmpPhotoshopPackage.getColorMode());
	System.out.println("ICC Profile : " + xmpPhotoshopPackage.getIccProfile());
	System.out.println("Country : " + xmpPhotoshopPackage.getCountry());
	System.out.println("City : " + xmpPhotoshopPackage.getCity());
	System.out.println("Date Created : " + xmpPhotoshopPackage.getDateCreated());
	// ...
    }
}
```

De même, il existe de nombreuses méthodes de définition pour définir ou mettre à jour différentes propriétés XMP. Vous pouvez même fournir votre propre paire clé-valeur pour [définir la propriété de package XMP personnalisée][10].

## Supprimer les métadonnées EXIF et XMP des images HEIC/HEIF en Java

Vous pouvez simplement définir le package EXIF ou le package XMP respectif sur null pour supprimer toutes les propriétés de métadonnées.

Le code suivant supprime les données EXIF des images HEIC.

```
try (Metadata metadata = new Metadata("image.heic")) {
	IExif root = (IExif) metadata.getRootPackage();
	root.setExifPackage(null);
	metadata.save("no-exif-image.heic");
}
```

Le code suivant supprime les données XMP des images HEIC.

```
try (Metadata metadata = new Metadata("image.heic")) {
	IXmp root = (IXmp) metadata.getRootPackage();
	root.setXmpPackage(null);
	metadata.save("no-xmp-image.heic");
}
```

## Conclusion

En résumé, nous avons appris à extraire, mettre à jour, supprimer les métadonnées EXIF et XMP des images HEIF/HEIC en Java. De plus, vous avez vu comment obtenir des informations IFD et GPS à partir de ces images. Désormais, vous pouvez facilement obtenir ces informations et continuer à créer vos propres applications telles que GroupDocs.Metadata App Product Family pour automatiser les informations de métadonnées.

Pour plus d'informations, d'options et d'exemples, vous pouvez consulter la [documentation][11] et le référentiel [GitHub][12]. Pour toute autre question, contactez-nous sur le support [forum][13].

## Voir également

* [Extraire les informations RIFF et les métadonnées des fichiers WAV en Java][14]
* [Nettoyer les métadonnées des documents et des images à l'aide de Java][15]







[1]: https://blog.groupdocs.com/2021/05/10/xmp-and-exif-data-of-heif-heic-images-using-java
[2]: #java-api-for-exif-and-xmp-metadata
[3]: #read-exif-of-heic-heif-images
[4]: #read-xmp-of-heic-heif-images
[5]: https://products.groupdocs.com/metadata
[6]: https://docs.groupdocs.com/metadata/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/metadata/java
[8]: https://github.com/groupdocs-metadata
[9]: https://apireference.groupdocs.com/metadata/java
[10]: https://docs.groupdocs.com/metadata/java/working-with-xmp-metadata/
[11]: https://docs.groupdocs.com/metadata/
[12]: https://github.com/groupdocs-metadata
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2021/03/22/extract-riff-info-and-metadata-of-wav-files-in-java/
[15]: https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/


