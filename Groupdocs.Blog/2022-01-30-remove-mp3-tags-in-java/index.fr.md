---
title: "Supprimer les balises MP3 en Java"
date: Sun, 30 Jan 2022 05:05:23 +0000
draft: false
url: /fr/2022/01/30/remove-mp3-tags-in-java/
author: 'Shoaib Khan'
summary: "Lorsque les métadonnées ne sont pas vraiment nécessaires, vous pouvez les éliminer. Dans cet article, nous apprendrons **comment supprimer par programmation différentes balises MP3 en Java.** Précisément, nous verrons la suppression des balises de métadonnées ID3v1, ID3v2, Paroles et APEv2 des fichiers mp3 dans l'application Java.

Les sujets suivants sont traités ci-dessous :

* API Java pour les balises MP3
* Supprimer les balises MP3 ID3 - ID3, Paroles, APE
* Code Java - Supprimer l'exemple de métadonnées MP3"
tags: ['Remove APE', 'Remove Metadata in Java', 'Remove MP3 ID3', 'Remove MP3 Metadata', 'Remove MP3 Tags', 'Remove MP3 Tags in Java']
categories: ['GroupDocs.Metadata Product Family']
---

Lorsque les métadonnées ne sont pas vraiment nécessaires, vous pouvez les éliminer. Dans cet article, nous apprendrons **comment supprimer par programmation différentes balises MP3 en Java.** Précisément, nous verrons la suppression des balises de métadonnées ID3v1, ID3v2, Paroles et APEv2 des fichiers mp3 dans l'application Java.

Les sujets suivants sont traités ci-dessous :

* [API Java pour les balises MP3](#mp3-tags-java-api)
* [Supprimer les balises MP3 ID3 - ID3, Paroles, APE](#remove-mp3-tags)
* [Code Java - Exemple de suppression de métadonnées MP3](#source-code-remove-mp3-tags)

## API Java pour la suppression des balises MP3 {#mp3-tags-java-api}

[GroupDocs.Metadata](https://products.groupdocs.com/metadata) fournit une [API Java de gestion des métadonnées](https://products.groupdocs.com/metadata/java/) pour gérer les métadonnées de différents formats de fichiers. **GroupDocs.Metadata for Java** permet de lire, mettre à jour, ajouter, nettoyer et supprimer totalement les métadonnées pour [divers formats de fichiers](https://docs.groupdocs.com/metadata/java/supported-document-formats/). Je vais utiliser cette API pour supprimer les balises de métadonnées des fichiers MP3.

### Télécharger ou configurer

Vous pouvez télécharger le fichier **JAR** à partir de la [section des téléchargements](https://downloads.groupdocs.com/metadata), ou simplement obtenir les configurations du référentiel et des dépendances pour le pox.xml de votre **Maven-based** Applications Java.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-metadata</artifactId>
        <version>21.8</version> 
</dependency>
```

## Supprimer les balises MP3 en Java - ID3v1, ID3v2, Paroles, APE {#remove-mp3-tags}

Les étapes suivantes vous permettront de supprimer rapidement les balises de métadonnées MP3 de vos fichiers MP3 en Java.

1. **Chargez** le fichier MP3.
2. Obtenez le **paquet racine MP3**.
3. **Supprimez** le(s) tag(s) MP3 concerné(s).
4. **Enregistrer** le fichier MP3 mis à jour.

### 1\. **Charger MP3**

Sélectionnez le fichier MP3 et chargez-le à l'aide de la classe [Metadata](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata).

```
Metadata metadata = new Metadata("path/mp3File.mp3");
```

### 2\. Obtenir le package racine MP3

Obtenez le [paquet racine MP3](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MP3RootPackage) du fichier MP3 à l'aide de [getRootPackageGeneric()](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#getRootPackageGeneric()).

```
MP3RootPackage root = metadata.getRootPackageGeneric();
```

### 3\. Supprimer les balises MP3

Voici des façons de supprimer différentes balises de métadonnées. Vous pouvez utiliser la méthode de suppression appropriée pour vos fichiers MP3.

#### **ID3v**1

Pour supprimer les balises de métadonnées **ID3v1**, définissez la propriété [ID3V1](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ID3V1Tag) du package racine sur null.

```
root.setID3V1(null);
```

#### **ID3v2**

Définissez la propriété [ID3V2](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ID3V2Tag) sur null pour supprimer les balises de métadonnées **ID3v2**.

```
root.setID3V2(null);
```

#### **Paroles**

Supprimez les balises **Lyrics** en définissant [Lyrics Tag](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/LyricsTag) sur null.

```
root.setLyrics3V2(null);
```

#### ****APE****

Utilisez la méthode [removeApeV2()](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MP3RootPackage#removeApeV2()) du package racine pour éliminer les balises **APEv2**.

```
root.removeApeV2();
```

### 4\. Enregistrer le fichier

Enfin, **enregistrez** le fichier MP3 mis à jour à l'aide de la méthode [save()](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#save()).

```
metadata.save("path/mp3TagsRemoved.mp3");
```

## Code complet - Supprimer les balises MP3 {#source-code-remove-mp3-tags}

L'exemple de code source Java suivant montre comment supprimer les balises MP3 pertinentes des fichiers MP3.

```
// Supprimer les balises de métadonnées MP3 des fichiers MP3 en C# - ID3v1, ID3v2, Paroles, APE
Metadata metadata = new Metadata("path/mp3File.mp3")

MP3RootPackage root = metadata.getRootPackageGeneric();
root.setID3V1(null); // delete ID3v1
root.setID3V2(null); // delete ID3v2
root.setLyrics3V2(null); // delete Lyrics3v2
root.removeApeV2(); // delete APE

metadata.save("path/mp3TagsRemoved.mp3");
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons appris à supprimer les balises de métadonnées des fichiers MP3 en Java à l'aide de l'API de métadonnées. Un par un, nous avons examiné comment supprimer les balises ID3v1, ID3v2, Paroles et APE des fichiers MP3.

Vous pouvez en savoir plus sur l'API dans la [documentation](https://docs.groupdocs.com/metadata/java/). Contactez-nous pour toute question via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Nettoyeur de métadonnées pour les documents et les images utilisant Java](https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/)
* [Extraire les informations RIFF et les métadonnées des fichiers WAV en Java](https://blog.groupdocs.com/2021/03/22/extract-riff-info-and-metadata-of-wav-files-in-java/)
* [Gérer les données XMP et EXIF des images HEIF/HEIC à l'aide de Java](https://blog.groupdocs.com/2021/05/10/xmp-and-exif-data-of-heif-heic-images-using-Java/)





