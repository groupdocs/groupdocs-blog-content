---
title: "Extraire les informations RIFF et les métadonnées des fichiers WAV en Java"
date: Mon, 22 Mar 2021 16:37:44 +0000
draft: false
url: /fr/2021/03/22/extract-riff-info-and-metadata-of-wav-files-in-java/
author: 'Shoaib Khan'
summary: "**RIFF** Format de conteneur de fichiers utilisé pour stocker des fichiers multimédias audio et vidéo. Ces données stockées en morceaux peuvent inclure de nombreuses informations telles que la date de création, les informations de copyright, les artistes, les commentaires, etc. Vous pouvez manipuler par programme les métadonnées ainsi que RIFF INFO. Cet article guide les développeurs pour **extraire par programmation les métadonnées et RIFF INFO des fichiers audio WAV en Java**."
tags: ['extract metadata in java', 'Extract Metadata of WAV file in Java', 'Extract RIFF INFO of WAV in Java']
categories: ['GroupDocs.Metadata Product Family']
---

**RIFF** Format de conteneur de fichiers utilisé pour stocker des fichiers multimédias audio et vidéo. Ces données stockées en morceaux peuvent inclure de nombreuses informations telles que la date de création, les informations de copyright, les artistes, les commentaires, etc. Vous pouvez manipuler par programme les métadonnées ainsi que RIFF INFO. Cet article guide les développeurs pour **extraire par programmation les métadonnées et RIFF INFO des fichiers audio WAV en Java**.

Les sujets suivants sont abordés dans l'article en bref:

* [API Java pour la gestion des métadonnées][2]
* [Extraire les métadonnées des fichiers WAV en Java][3]
* [Extraire les informations RIFF des fichiers WAV en Java][4]

## API Java pour la gestion des métadonnées et RIFF INFO {#metadata-management-java-api}

[GroupDocs.Metadata for Java][5] est l'API d'automatisation et de manipulation des métadonnées pour divers formats de documents et de fichiers image. J'utiliserai cette API pour extraire les métadonnées et les RIFF INFO des fichiers WAV. En plus des fichiers audio WAV, l'API prend en charge l'ajout, la suppression, la mise à jour et l'extraction de métadonnées à partir de **fichiers MP3** et de **vidéos**. En outre, il prend également en charge les formats de fichiers **Microsoft Office** et **Open Office**, **eBooks**, **images** et de nombreux autres formats de documents.

### Télécharger et configurer

[Obtenez la bibliothèque][6] à partir des téléchargements ou ajoutez simplement la configuration pom.xml suivante dans vos applications Java basées sur Maven pour essayer les exemples mentionnés ci-dessous. Pour plus de détails, vous pouvez visiter la [API Reference][7].

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
        <version>21.2</version> 
</dependency>
```

## Extraire les métadonnées des fichiers WAV en Java {#extract-metadata-of-wav-audio-in-java}

Les étapes suivantes et l'exemple de code Java mentionné ci-dessous extraient les métadonnées des fichiers WAV.

* Chargez le fichier audio WAV.
* Obtenez le [WavRootPackage][8] de métadonnées.
* Extrayez le [WavPackage][9] en utilisant la méthode _getWavPackage_.
* Vous pouvez maintenant accéder à toutes les propriétés de l'audio WAV.

```
// Extraire les métadonnées des fichiers WAV en Java
try (Metadata metadata = new Metadata("audio.wav"))
{
    WavRootPackage root = metadata.getRootPackageGeneric();
    System.out.println(root.getWavPackage().getBitsPerSample()); // Bits per Sample
    System.out.println(root.getWavPackage().getBlockAlign()); // Block Align
    System.out.println(root.getWavPackage().getByteRate()); // Byte Rate
    System.out.println(root.getWavPackage().getNumberOfChannels()); // No. of Channels
    System.out.println(root.getWavPackage().getAudioFormat()); // Audio Format
    System.out.println(root.getWavPackage().getSampleRate()); // Sample Rate
}
```

Le code ci-dessus produit la sortie suivante avec le fichier wav fourni :

```
Bits per Sample: 16
Block Align: 4
Byte Rate: 176400
Number of Channels: 2
Audio Format: 1
Sample Rate: 44100
```

## Extraire les informations RIFF des fichiers WAV en Java {#extract-riff-info-of-wav-audio-in-java}

Si vous souhaitez extraire les informations RIFF des fichiers WAV, vous pouvez les obtenir dans votre application Java en suivant ces étapes. Ceci est similaire à la façon dont nous avons extrait les métadonnées présentées ci-dessus.

* Chargez le fichier WAV.
* Obtenez le [WavRootPackage][10] de métadonnées.
* Extrayez le [RiffInfoPackage][11] du package racine.
* Maintenant, les propriétés de l'audio WAV sont accessibles.

L'exemple de code suivant extrait les propriétés de métadonnées du package RIFF INFO du fichier WAV en Java.

```
// Extraire RIFF INFO des fichiers WAV en Java
try (Metadata metadata = new Metadata("audio.wav"))
{
    WavRootPackage root = metadata.getRootPackageGeneric();
    System.out.println(root.getRiffInfoPackage().getArtist()); // Artist
    System.out.println(root.getRiffInfoPackage().getComment()); // Comment
    System.out.println(root.getRiffInfoPackage().getCopyright()); // Copyright
    System.out.println(root.getRiffInfoPackage().getCreationDate()); // Creation Date
    System.out.println(root.getRiffInfoPackage().getSoftware()); // Software
    System.out.println(root.getRiffInfoPackage().getEngineer()); // Engineer
    System.out.println(root.getRiffInfoPackage().getGenre()); // Genre
} 
```

Voici la sortie du code ci-dessus :

```
Artist: GroupDocs 
Comment: Sample WAV File
Copyright: 
CreationDate: 2020-12-03
Software: Sound Forge
Engineer: SGEFFNER
Genre: Mystery
```

## Conclusion

Dans cet article, nous avons expliqué comment extraire par programme les métadonnées et les informations RIFF des fichiers audio WAV en Java. J'espère que vous le trouverez assez simple. Vous pouvez désormais créer votre propre application Java d'extraction de métadonnées à l'aide de GroupDocs.Metadata for Java.

## En savoir plus sur l'API

* [Documents][12]
* [Exemples de code source][13]
* [Référence API][14]

** Dissipons tous les doutes @ ** [Forum d'assistance gratuit.][15]

## Voir également

* [Extraire les informations RIFF et les métadonnées des fichiers WAV en C #][16]
* [Gérer les données EXIF des images en Java][17]







[1]: https://blog.groupdocs.com/2021/03/22/extract-riff-info-and-metadata-of-wav-files-in-java
[2]: #metadata-management-java-api
[3]: #extract-metadata-of-wav-audio-in-java
[4]: #extract-riff-info-of-wav-audio-in-java
[5]: https://products.groupdocs.com/metadata/java
[6]: https://downloads.groupdocs.com/metadata/java
[7]: https://apireference.groupdocs.com/metadata/java
[8]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/WavRootPackage
[9]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/WavPackage
[10]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/WavRootPackage
[11]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata.core/RiffInfoPackage
[12]: https://docs.groupdocs.com/metadata/java/
[13]: https://github.com/groupdocs-metadata/GroupDocs.Metadata-for-Java
[14]: https://apireference.groupdocs.com/metadata/java
[15]: https://forum.groupdocs.com/c/metadata
[16]: https://blog.groupdocs.com/2021/03/05/extract-riff-info-and-metadata-of-wav-files-in-csharp/
[17]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/


