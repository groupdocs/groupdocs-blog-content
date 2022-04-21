---
title: "'Lire les balises MP3 à l'aide de C# - (ID3, Paroles, APE)'"
date: Sat, 22 Jan 2022 12:49:38 +0000
draft: false
url: /fr/2022/01/22/read-mp3-tags-using-csharp/
author: 'Shoaib Khan'
summary: "Il existe différentes normes de métadonnées utilisées avec les fichiers MP3. Différents types de données peuvent être stockés en utilisant différentes normes. Dans cet article, nous verrons comment lire différentes balises MP3 à l'aide de C#. Plus précisément, nous apprendrons à extraire les balises de métadonnées ID3v1, ID3v2, Paroles et APEv2 des fichiers mp3 dans l'application .NET.

Les sujets suivants sont traités dans cet article :

* API .NET pour gérer les balises MP3
* Lire les balises MP3 ID3 - ID3v1 et ID3v2
* Obtenez des balises de paroles MP3
* Récupérer les balises MP3 APEv2"
tags: ['read ID3 tags', 'read mp3 lyrics', 'Read MP3 tags', 'Read MP3 Tags CSharp']
categories: ['GroupDocs.Metadata Product Family']
---



{{< figure align=center src="images/mp3-icon.png" alt="mp3 - extraire ses balises mp3 de métadonnées">}}


Il existe différentes normes de métadonnées utilisées avec les fichiers MP3. Différents types de données peuvent être stockés en utilisant différentes normes. Dans cet article, nous expliquerons **comment lire différentes balises MP3 à l'aide de C#**. Plus précisément, nous apprendrons à extraire les balises de métadonnées ID3v1, ID3v2, Paroles et APEv2 des fichiers mp3 dans l'application .NET.

Les sujets suivants sont traités ci-dessous:

* [API .NET pour gérer les balises MP3](#mp3-tags-dotnet-api)
* [Lire les balises MP3 ID3 - ID3v1 et ID3v2](#read-mp3-id3-tags)
* [Obtenir les balises de paroles MP3](#read-mp3-lyrics-tags)
* [Récupérer les balises MP3 APEv2](#read-mp3-ape-tags)

## API .NET pour l'éditeur de balises MP3 {#mp3-tags-dotnet-api}

[GroupDocs.Metadata](https://products.groupdocs.com/metadata) fournit l'API .NET pour automatiser la gestion des métadonnées de [divers formats de fichiers](https://docs.groupdocs.com/metadata/net/supported-document-formats/) dans les applications .NET. L'API permet de lire, mettre à jour, ajouter, nettoyer et supprimer les métadonnées pour de nombreux formats de fichiers. Nous utiliserons cette API pour traiter les balises de métadonnées des fichiers MP3.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements](https://downloads.groupdocs.com/metadata) ou installer l'API dans votre application .NET via [NuGet](https://www.nuget.org/packages/groupdocs.metadata).

```
PM> Install-Package GroupDocs.Metadata
```

## Lire les balises MP3 ID3 à l'aide de C# - ID3v1 et ID3v2 {#read-mp3-id3-tags}

Les étapes suivantes montrent comment lire les balises MP3 ID3v1 à l'aide de C#.

* Chargez le fichier MP3 à l'aide de la classe [Metadata](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata).
* Récupérez le [paquet racine](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage) à l'aide de la méthode **GetRootPackage()**.
* Depuis la racine, vous pouvez récupérer chacun des ID3v1.

Le code source C# suivant lit certaines des balises MP3 ID3v1 du fichier MP3.

```
// Lire les balises ID3V1 des fichiers MP3
using (Metadata metadata = new Metadata(Constants.MP3WithID3V1))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();

    if (root.ID3V1 != null)
    {
        Console.WriteLine(root.ID3V1.Album);
        Console.WriteLine(root.ID3V1.Artist);
        Console.WriteLine(root.ID3V1.Title);
        Console.WriteLine(root.ID3V1.Version);
        Console.WriteLine(root.ID3V1.Comment);
    }
}
```

De même, vous pouvez extraire les balises ID3v2. Les étapes suivantes montrent comment récupérer les balises MP3 ID3v2 à l'aide de C#.

* Chargez le fichier MP3 à l'aide de la classe [Metadata](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata).
* Obtenez le [paquet racine](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage).
* À partir de la racine, vous pouvez récupérer toutes les balises ID3v2 telles que Groupe, Artiste, Compositeurs, etc.
* Pour les images jointes et leurs détails, utilisez les propriétés AttachedPictures.

L'exemple de code source C# suivant lit certaines des balises MP3 ID3v2 et les détails des images jointes du fichier MP3.

```
// Lire les balises ID3V2 des fichiers MP3
using (Metadata metadata = new Metadata(Constants.MP3WithID3V2))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();

    if (root.ID3V2 != null)
    {
        Console.WriteLine(root.ID3V2.Album);
        Console.WriteLine(root.ID3V2.Artist);
        Console.WriteLine(root.ID3V2.Band);
        Console.WriteLine(root.ID3V2.Title);
        Console.WriteLine(root.ID3V2.Composers);
        Console.WriteLine(root.ID3V2.Copyright);
        Console.WriteLine(root.ID3V2.Publisher);
        Console.WriteLine(root.ID3V2.OriginalAlbum);
        Console.WriteLine(root.ID3V2.MusicalKey);

        if (root.ID3V2.AttachedPictures != null)
        {
            foreach (var attachedPicture in root.ID3V2.AttachedPictures)
            {
                Console.WriteLine(attachedPicture.AttachedPictureType);
                Console.WriteLine(attachedPicture.MimeType);
                Console.WriteLine(attachedPicture.Description);
            }
        }
    }
}
```

## Lire les balises de paroles MP3 en C# {#read-mp3-lyrics-tags}

Les étapes suivantes vous guident pour lire les balises MP3 Lyrics à l'aide de C#.

* Chargez le fichier MP3 à l'aide de la classe [Metadata](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata).
* Récupérez le [paquet racine](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage).
* À partir de la racine, vous pouvez obtenir des balises de paroles et ses propriétés telles que Paroles, artiste, etc.

L'extrait de code C# suivant récupère les balises de paroles MP3 et certaines de ses propriétés à partir du fichier MP3.

```
// Lire les balises de paroles de fichiers MP3
using (Metadata metadata = new Metadata(Constants.MP3WithLyrics))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();

    if (root.Lyrics3V2 != null)
    {
        Console.WriteLine(root.Lyrics3V2.Lyrics);
        Console.WriteLine(root.Lyrics3V2.Album);
        Console.WriteLine(root.Lyrics3V2.Artist);
        Console.WriteLine(root.Lyrics3V2.Track);

        // Alternatively, you can loop through a full list of tag fields
        foreach (var field in root.Lyrics3V2.ToList())
        {
            Console.WriteLine("{0} = {1}", field.ID, field.Data);
        }
    }
}
```

## Lire les balises MP3 APEv2 en C# {#read-mp3-ape-tags}

Les étapes suivantes montrent comment nous pouvons extraire les balises MP3 APEv2 à l'aide de C#.

* Chargez le fichier MP3 à l'aide de la classe [Metadata](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata).
* Récupérez le **paquet racine** à l'aide de la méthode **GetRootPackage()**.
* À partir de la racine, vous pouvez récupérer toutes les balises APEv2 telles que Album, Genre, Copyrights, Language, etc.

Les exemples de code C# suivants lisent certaines des propriétés des balises MP3 APE d'un fichier MP3.

```
// Lire les balises APE des fichiers MP3
using (Metadata metadata = new Metadata(Constants.MP3WithApe))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();

    if (root.ApeV2 != null)
    {
        Console.WriteLine(root.ApeV2.Album);
        Console.WriteLine(root.ApeV2.Title);
        Console.WriteLine(root.ApeV2.Artist);
        Console.WriteLine(root.ApeV2.Composer);
        Console.WriteLine(root.ApeV2.Copyright);
        Console.WriteLine(root.ApeV2.Genre);
        Console.WriteLine(root.ApeV2.Language);
    }
}
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons appris à extraire les balises de métadonnées des fichiers MP3 à l'aide de C#. Nous lisons les balises ID3v1, ID3v2, Paroles et APE et leurs propriétés à partir des fichiers MP3. Vous pouvez en savoir plus sur l'API à partir de la [documentation](https://docs.groupdocs.com/metadata/net/) et nous contacter pour toute question via le [forum](https://forum.groupdocs.com/) .

## Voir également

* [Suppression de métadonnées pour les documents et les images à l'aide de C#](https://blog.groupdocs.com/2020/12/29/remove-metadata-of-documents-and-images-using-csharp/)
* [Extraire les informations RIFF et les métadonnées des fichiers WAV en C#](https://blog.groupdocs.com/2021/03/05/extract-riff-info-and-metadata-of-wav-files-in-csharp/)
* [Gérer les données XMP et EXIF des images HEIF/HEIC à l'aide de C#](https://blog.groupdocs.com/2021/07/17/manage-xmp-and-exif-data-of-heif-heic-images-using-csharp/)
* [Gérer les données EXIF des images en C# .NET](https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/)