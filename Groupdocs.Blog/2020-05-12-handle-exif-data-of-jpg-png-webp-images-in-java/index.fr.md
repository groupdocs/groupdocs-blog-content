---
title: "Gérer les données EXIF des images JPEG, PNG, TIFF et WebP en Java"
date: Tue, 12 May 2020 07:09:04 +0000
draft: false
url: /fr/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/
author: 'Shoaib Khan'
summary: "**EXIF** (_Exchangeable Image File Format_) est la norme pour spécifier les formats d'image et de son principalement utilisés par les appareils photo numériques et les scanners. Les données EXIF incluent les informations de marquage et de métadonnées sur le fichier image capturé. Les métadonnées peuvent contenir des informations telles que la marque de l'appareil photo, le modèle, la vitesse d'obturation, la date et l'heure, l'ouverture, le temps d'exposition, la résolution X, la résolution Y. etc."
tags: ['exif data', 'exif data of jpeg in java', 'exif metadata', 'exif metadata in java', 'extract exif data', 'extract exif data in java', 'remove exif data from images', 'remove exif metadata', 'update exif']
categories: ['GroupDocs.Metadata Product Family']
---

**EXIF** (_Exchangeable Image File Format_) est la norme pour spécifier les formats d'image et de son principalement utilisés par les appareils photo numériques et les scanners. Les données EXIF incluent les informations de marquage et de métadonnées sur le fichier image capturé. Les métadonnées peuvent contenir des informations telles que la marque de l'appareil photo, le modèle, la vitesse d'obturation, la date et l'heure, l'ouverture, le temps d'exposition, la résolution X, la résolution Y. etc.

Si vous souhaitez **gérer, extraire, mettre à jour ou supprimer les données EXIF de vos images par programmation**, cet article est pour vous. Cet article couvrira les manières suivantes de manipuler les données EXIF en Java :

* [Extraire les données EXIF - Visualiseur de données EXIF][1]
* [Extraire toutes les balises EXIF des images][2]
* [Mettre à jour les propriétés EXIF][3]
* [Supprimer les métadonnées EXIF][4]

## Bibliothèque de manipulation de métadonnées Java



{{< figure align=center src="images/GroupDocs.MetaData_for_Java.png" alt="API Java de métadonnées par GroupDocs">}}


[GroupDocs.Metadata for Java][5] est une API Java de gestion des métadonnées facile à utiliser. Il a la capacité non seulement d'extraire des métadonnées d'images telles que JPG, PNG ou WebP, mais également d'ajouter, de modifier, de mettre à jour et de supprimer des métadonnées d'images et d'autres documents avec différentes options.

J'utilise cette API dans cet article, alors assurez-vous de [télécharger][6] ou de l'intégrer dans vos applications basées sur Maven en ajoutant simplement les configurations suivantes au fichier pom.xml.

### Référentiel```
<repository>
<id>GroupDocsJavaAPI</id>
<name>API Java GroupDocs</name>
<url>http://repository.groupdocs.com/repo/</url>
</repository>
```

### Dependency```
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-metadata</artifactId>
    <version>20.5</version>
    <classifier>javadoc</classifier>
</dependency>
```

## Extraire des données EXIF à partir d'images en Java - Visualiseur de métadonnées {#extract-exif-data-from-images}

Vous pouvez lire les propriétés des données EXIF en suivant des étapes simples. Commençons par l'extraction des données EXIF de cette photo de la Tour Eiffel. J'ai sélectionné un fichier JPG comme exemple d'image, vous pouvez utiliser n'importe lequel de vos fichiers, qu'il s'agisse d'un PNG, WebP, BMP, GIF ou TIFF.



{{< figure align=center src="images/eiffel-tower.jpg" alt="Image de la Tour Eiffel pour les données EXIF">}}


* Chargez le fichier source de l'image contenant les informations de données EXIF à l'aide du constructeur de classe [Metadata][7].
* Obtenez son **paquet racine** en appelant la méthode [getRootPackage()][8].
* À partir du package racine, obtenez son **package EXIF** en appelant la méthode [getExifPackage()][9].
* Une fois que vous avez le package EXIF, vous pouvez obtenir des propriétés EXIF d'image telles que **Make**, **Model**, **Width**, **Length**, **Date-Time**, etc., comme indiqué dans l'exemple de code Java ci-dessous.

```
// Extract EXIF Data Package Information from image in Java
try (Metadata metadata = new Metadata("eiffel-tower.jpg")) {
	IExif root = (IExif) metadata.getRootPackage();
	if (root.getExifPackage() != null) {
		// Extract EXIF Package
		ExifPackage exifPackage = root.getExifPackage();
		System.out.println("Make : " + exifPackage.getMake());
		System.out.println("Model : " + exifPackage.getModel());
		System.out.println("Width : " + exifPackage.getImageWidth());
		System.out.println("Length : " + exifPackage.getImageLength());
		System.out.println("DateTime : " + exifPackage.getDateTime());					
	} 
}
```

Voici les informations EXIF que vous obtiendrez à la suite du code ci-dessus.

```
Make : NIKON CORPORATION
Model : NIKON D3000
Width : 640
Length : 424
DateTime : 2014:08:09 10:35:13
```

Pour plus d'informations sur les packages **IFD** (Image File Directory) et **GPS** (Global Positioning System), il vous suffit d'appeler les méthodes respectives du **EXIF package**, c'est-à-dire [getExifIfdPackage()][10] ou [getGpsPackage()][11]. À partir de ces packages, vous pouvez extraire plus d'informations telles que;

* Appareil de capture d'image **numéro de série**
* Caméra **Nom du propriétaire**
* **Commentaires des utilisateurs**
* **Altitude**
* **Latitude**
* **Longitude**
* etc.

Voici le code que vous pouvez ajouter dans votre méthode ci-dessus pour afficher les données EXIF avec les informations IFD et GPS.

```
// EXIF IFD Package
ExifIfdPackage exifIfdPackage = exifPackage.getExifIfdPackage();
System.out.println("BodySerialNumber : " + exifIfdPackage.getBodySerialNumber());
System.out.println("CameraOwnerName : " + exifIfdPackage.getCameraOwnerName());
System.out.println("UserComment : " + exifIfdPackage.getUserComment());
// EXIF GPS Information Package
ExifGpsPackage exifGpsPackage = exifPackage.getGpsPackage();
System.out.println("getAltitude : " + exifGpsPackage.getAltitude());
System.out.println("Latitude Ref : " + exifGpsPackage.getLatitudeRef());
System.out.println("LongitudeRef : " + exifGpsPackage.getLongitudeRef());
```

## Lire toutes les balises EXIF des images à l'aide de Java {#extract-all-exif-tags-from-images}

Si vous souhaitez afficher ou extraire toutes les propriétés EXIF d'une image ou d'un fichier, vous pouvez le faire en suivant des étapes similaires aux exemples ci-dessus :

* Chargez simplement le fichier avec le constructeur [Metadata][12].
* Obtenez le **package racine EXIF** en appelant la méthode [getRootPackage()][13].
* Obtenez le **package EXIF** en appelant la méthode [getExifPackage()][14].
* Parcourez le package EXIF pour obtenir les paires nom-valeur souhaitées.
* De même, récupérez les packages IFD et GPS et affichez ses clés et ses valeurs.

```
try (Metadata metadata = new Metadata("eiffel-tower.jpg")) {
	IExif root = (IExif) metadata.getRootPackage();
	if (root.getExifPackage() != null) {
		String pattern = "%s = %s";
		// Reading all EXIF tags.
		for (TiffTag tag : root.getExifPackage().toList()) {
			System.out.println(String.format(pattern, tag.getName(), tag.getValue()));
		}
		// Extract all EXIF IFD tags.
		for (TiffTag tag : root.getExifPackage().getExifIfdPackage().toList()) {
			System.out.println(String.format(pattern, tag.getName(), tag.getValue()));
		}
		// Extract all EXIF GPS tags
		for (TiffTag tag : root.getExifPackage().getGpsPackage().toList()) {
			System.out.println(String.format(pattern, tag.getName(), tag.getValue()));
		}
	}
}
```

## Mettre à jour les propriétés EXIF en Java {#update-exif-properties}

Vous pouvez même modifier facilement les données EXIF existantes de n'importe quelle image ou de n'importe quel document. Les étapes sont simples :

### **Mettre à jour le package EXIF**

* Obtenez le package EXIF en appelant la méthode [getExifPackage()][15].
* Utilisez les méthodes de setter comme;
    * [setCopyright()][16] - pour définir les informations de copyright mises à jour.
    * [setImageDescription()][17] - pour définir la description de l'image.
* De même, vous pouvez définir les valeurs pour l'artiste, la marque, le modèle, le logiciel, la largeur et la hauteur de l'image, la date, l'heure, etc.

### **Mettre à jour le package EXIF IFD**

Tout comme la mise à jour du package EXIF, vous pouvez mettre à jour les propriétés des packages EXIF IFD et GPS. Veuillez visiter la classe [ExifIfdPackage][18] ou [ExifGpsPackage][19] pour savoir combien vous pouvez personnaliser pour vos images et documents précieux.

```
// Update/Set new values in EXIF Data (EXIF Package and EXIF IFD Package).
try (Metadata metadata = new Metadata("eiffel-tower.jpg")) {
    IExif root = (IExif) metadata.getRootPackage();
    // Set the EXIF package if it's missing
    if (root.getExifPackage() == null) {
        root.setExifPackage(new ExifPackage());
    }
    ExifPackage exifPackage = root.getExifPackage();
    // Setting the desired values in EXIF Package and EXIF IFD Package.
    exifPackage.setCopyright("Copyright (C) 2011-2020 GroupDocs. All Rights Reserved.");
    exifPackage.setImageDescription("Eiffel Tower for EXIF");
    exifPackage.setSoftware("GroupDocs.Metadata");
    exifPackage.getExifIfdPackage().setBodySerialNumber("GD-2020");
    exifPackage.getExifIfdPackage().setCameraOwnerName("GroupDocs");
    exifPackage.getExifIfdPackage().setUserComment("Nice image captured in 2014");
    metadata.save("eiffel-tower-updated.jpg");
}
```

## Supprimer les métadonnées EXIF des images en Java {#remove-exif-metadata}

C'est très simple si vous souhaitez supprimer le package EXIF de n'importe quel fichier, définissez simplement son package EXIF sur null en appelant [setExifPackage(null)][20] du package racine.

```
// Removing the EXIF data from an image.
try (Metadata metadata = new Metadata("eiffel-tower.jpg")) {
    IExif root = (IExif) metadata.getRootPackage();
    root.setExifPackage(null);
    metadata.save("eiffel-tower-no-exif.jpg");
}
```

## Images et autres formats pris en charge

Voici les formats de fichiers actuellement pris en charge par GroupDocs.Metadata. Vous pouvez toujours visiter la [documentation][21] pour les informations mises à jour.

<figure class="wp-block-table is-style-stripes"><table class="has-fixed-layout"><tbody><tr><td> **Type de document</td><td> <strong>Formats de fichiers**</strong></td></tr><tr><td> <a href="https://wiki.fileformat.com/image/">Images</a></td><td> BMP, GIF, JPG, JPEG, JPE, JP2, PNG, DJVU, DWG, DXF, WebP, TIFF, PSD, EMF, WMF</td></tr><tr><td> <a href="https://wiki.fileformat.com/audio">Audio</a> et <a href="https://wiki.fileformat.com/video/">vidéo</a></td><td> MP3, WAV, AVI, MOV/QT, FLV, ASF, DICOM</td></tr></tbody></table></figure>

## En savoir plus sur GroupDocs.Metadata

* [Documents][22]
* Exemples de code source. [Java][23] | [.NET][24]
* GroupDocs.Metadata - [La solution de gestion des métadonnées][25]

**Parlons plus @** [Forum d'assistance gratuit.][26]

## Article associé

* [Gérer les données EXIF des images en C#][27]







[1]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/#update-exif-properties
[2]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/#extract-all-exif-tags-from-images
[3]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/#update-exif-properties
[4]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/#remove-exif-metadata
[5]: https://products.groupdocs.com/metadata/java
[6]: https://downloads.groupdocs.com/metadata/java
[7]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata
[8]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#getRootPackage()
[9]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/IExif#getExifPackage()
[10]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifIfdPackage
[11]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifPackage#getGpsPackage()
[12]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata
[13]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#getRootPackage()
[14]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifIfdPackage
[15]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifIfdPackage
[16]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifPackage#setCopyright(java.lang.String)
[17]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifPackage#setImageDescription(java.lang.String)
[18]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifIfdPackage
[19]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ExifGpsPackage
[20]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/IExif#setExifPackage(com.groupdocs.metadata.core.ExifPackage)
[21]: https://docs.groupdocs.com/display/metadatajava/Supported+File+Formats
[22]: https://docs.groupdocs.com/display/metadatajava/Getting+Started
[23]: https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java
[24]: https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-.NET
[25]: https://products.groupdocs.com/metadata
[26]: https://forum.groupdocs.com/c/metadata
[27]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/


