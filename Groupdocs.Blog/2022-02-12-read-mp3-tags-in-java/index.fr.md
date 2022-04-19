---
title: "Lire les balises MP3 en Java - (ID3, Paroles, APE)"
date: Sat, 12 Feb 2022 11:43:14 +0000
draft: false
url: /fr/2022/02/12/read-mp3-tags-in-java/
author: 'Shoaib Khan'
summary: "Des variantes de métadonnées sont jointes à des documents de différents formats de fichiers. Les fichiers MP3 contiennent généralement des balises de métadonnées ID3. Cet article explique **comment lire différentes balises MP3 en Java**. Un par un, nous verrons comment extraire les balises de métadonnées ID3 (IDEv1, ID3v2), Paroles et APEv2 des fichiers mp3 à l'aide de l'API Java Metadata."
tags: ['read ID3 tags', 'read mp3 lyrics', 'Read MP3 tags', 'Read MP3 Tags in Java']
categories: ['GroupDocs.Metadata Product Family']
---

Des variantes de métadonnées sont jointes à des documents de différents formats de fichiers. Les fichiers MP3 contiennent généralement des balises de métadonnées ID3. Cet article explique **comment lire différentes balises MP3 en Java**. Un par un, nous verrons comment extraire les balises de métadonnées ID3 (IDEv1, ID3v2), Paroles et APEv2 des fichiers mp3 à l'aide de l'API Java Metadata.

Les sujets suivants sont traités ci-dessous :

* [API Java pour gérer les balises MP3](#mp3-tags-java-api)
* [Lire les balises MP3 ID3 - ID3v1 et ID3v2](#read-mp3-id3-tags)
* [Obtenir les balises de paroles MP3](#read-mp3-lyrics-tags)
* [Récupérer les balises MP3 APEv2](#read-mp3-ape-tags)

## API Java pour les balises de métadonnées MP3 {#mp3-tags-java-api}

[GroupDocs.Metadata](https://products.groupdocs.com/metadata) est équipé d'API pour automatiser la gestion des métadonnées de [divers formats de fichiers](https://docs.groupdocs.com/metadata/net/supported-document-formats/) dans les applications. Son API Java vous permet de lire, mettre à jour, ajouter, nettoyer et supprimer les métadonnées pour de nombreux formats de fichiers dans l'application Java. Nous l'utiliserons pour travailler avec les balises de métadonnées MP3.

### Télécharger et configurer

Obtenez la bibliothèque de métadonnées à partir de la section [downloads](https://downloads.groupdocs.com/metadata/java). Pour votre application Java basée sur Maven, ajoutez simplement la configuration pom.xml suivante. Après cela, vous pouvez essayer les exemples de cet article ainsi que les nombreux autres exemples disponibles sur [GitHub](https://github.com/groupdocs-metadata). Pour plus de détails, vous pouvez visiter la [API Reference](https://apireference.groupdocs.com/metadata/java).

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-metadata</artifactId>
        <version>22.2</version> 
</dependency>
```

## Lire les balises MP3 ID3 en Java - ID3v1 & ID3v2 {#read-mp3-id3-tags}

Les étapes suivantes montrent comment lire les balises MP3 ID3v1 à l'aide de Java.

* Chargez le fichier MP3 à l'aide de la classe [Metadata](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata).
* Récupérez le [MP3RootPackage](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MP3RootPackage) en utilisant la méthode **getRootPackageGeneric()**.
* À partir du package racine, récupérez chacune des propriétés ID3v1.

Le code source Java suivant lit certaines des balises MP3 ID3v1 du fichier MP3.

```
// Lire les balises ID3V1 des fichiers MP3
try (Metadata metadata = new Metadata("path/audio-ID3V1.mp3")) {
	MP3RootPackage root = metadata.getRootPackageGeneric();
	if (root.getID3V1() != null) {

		System.out.println(root.getID3V1().getAlbum());
		System.out.println(root.getID3V1().getArtist());
		System.out.println(root.getID3V1().getTitle());
		System.out.println(root.getID3V1().getVersion());
		System.out.println(root.getID3V1().getComment());
		// ...
	}
}
```

Vous pouvez extraire les balises ID3v2 de la même manière. Les étapes suivantes montrent comment récupérer les balises MP3 ID3v2 en Java.

* Chargez le fichier MP3 à l'aide de la classe [Metadata](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata).
* Obtenez le [paquet racine](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MP3RootPackage).
* À partir de la racine, vous pouvez facilement récupérer toutes les balises ID3v2 telles que Artiste, Compositeurs, Éditeur, Titre, etc.
* Les détails des images jointes peuvent être récupérés à partir des propriétés de [Cadres d'image attachés](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/ID3V2AttachedPictureFrame).

L'exemple de code source Java suivant lit certaines des balises MP3 ID3v2 et les détails des images jointes du fichier MP3.

```
// Lire les balises ID3V2 des fichiers MP3
try (Metadata metadata = new Metadata("path/audio-ID3V2.mp3")) {
    MP3RootPackage root = metadata.getRootPackageGeneric();
 
    if (root.getID3V2() != null) {
        System.out.println(root.getID3V2().getAlbum());
        System.out.println(root.getID3V2().getArtist());
        System.out.println(root.getID3V2().getBand());
        System.out.println(root.getID3V2().getTitle());
        System.out.println(root.getID3V2().getComposers());
        System.out.println(root.getID3V2().getCopyright());
        System.out.println(root.getID3V2().getPublisher());
        System.out.println(root.getID3V2().getOriginalAlbum());
        System.out.println(root.getID3V2().getMusicalKey());
 
        if (root.getID3V2().getAttachedPictures() != null) {
            for (ID3V2AttachedPictureFrame attachedPicture : root.getID3V2().getAttachedPictures()) {
                System.out.println(attachedPicture.getAttachedPictureType());
                System.out.println(attachedPicture.getMimeType());
                System.out.println(attachedPicture.getDescription()); 
            }
        }
    }
}
```

## Lire les balises de paroles MP3 en Java {#read-mp3-lyrics-tags}

Les étapes suivantes expliquent comment lire les balises MP3 Lyrics en Java.

* Chargez le fichier MP3 à l'aide de la classe [Metadata](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata).
* Récupérez le [paquet racine](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MP3RootPackage).
* À partir de la racine, vous pouvez obtenir des balises de paroles et ses propriétés comme les paroles, l'artiste, la piste, etc.

L'extrait de code Java suivant récupère les balises de paroles MP3 et certaines des propriétés du fichier MP3.

```
// Lire les balises de paroles de fichiers MP3
try (Metadata metadata = new Metadata("path/audio-Lyrics.mp3")) {
	MP3RootPackage root = metadata.getRootPackageGeneric();
	if (root.getLyrics3V2() != null) {
		System.out.println(root.getLyrics3V2().getLyrics());
		System.out.println(root.getLyrics3V2().getAlbum());
		System.out.println(root.getLyrics3V2().getArtist());
		System.out.println(root.getLyrics3V2().getTrack());
		// ...

    // Similarly, you can traverse the tag fields
		for (LyricsField field : root.getLyrics3V2().toList()) {
			System.out.println(String.format("%s = %s", field.getID(), field.getData()));
		}
	}
}
```

## Lire les balises MP3 APEv2 en Java {#read-mp3-ape-tags}

Les étapes suivantes montrent comment nous pouvons extraire les balises MP3 APEv2 dans l'application Java.

* Chargez le fichier MP3 à l'aide de la classe [Metadata](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata).
* Récupérez le **[paquet racine](https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/MP3RootPackage)** en utilisant la méthode **getRootPackageGeneric()**.
* À partir de la racine, vous pouvez récupérer les balises APEv2 telles que Album, Genre, Copyrights, Language, etc.

Les exemples de code Java suivants lisent certaines des propriétés des balises MP3 APE d'un fichier MP3.

```
// Lire les balises APE des fichiers MP3
try (Metadata metadata = new Metadata("path/audio-APE.mp3")) {
	MP3RootPackage root = metadata.getRootPackageGeneric();

	if (root.getApeV2() != null) {
		System.out.println(root.getApeV2().getAlbum());
		System.out.println(root.getApeV2().getTitle());
		System.out.println(root.getApeV2().getArtist());
		System.out.println(root.getApeV2().getComposer());
		System.out.println(root.getApeV2().getCopyright());
		System.out.println(root.getApeV2().getGenre());
		System.out.println(root.getApeV2().getLanguage());
		// ...
	}
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour résumer, nous avons appris à extraire les balises de métadonnées des fichiers MP3 en Java. Un par un, nous lisons les balises ID3v1, ID3v2, Paroles et APE et leurs propriétés à partir des fichiers MP3. Pensez à créer votre propre éditeur de balises MP3 en ligne et visualiseur de métadonnées, tout comme [Online Metadata App](https://products.groupdocs.app/metadata/total).

Apprenez-en plus sur l'API dans la [documentation](https://docs.groupdocs.com/metadata/java/) et contactez-nous pour toute question via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Nettoyeur de métadonnées pour les documents et les images utilisant Java](https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/)
* [Supprimer les balises MP3 en Java](https://blog.groupdocs.com/2022/01/30/remove-mp3-tags-in-java/)
* [Gérer les données XMP et EXIF des images HEIF/HEIC à l'aide de Java](https://blog.groupdocs.com/2021/05/10/xmp-and-exif-data-of-heif-heic-images-using-Java/)
* [Extraire les informations RIFF et les métadonnées des fichiers WAV en Java](https://blog.groupdocs.com/2021/03/22/extract-riff-info-and-metadata-of-wav-files-in-java/)





