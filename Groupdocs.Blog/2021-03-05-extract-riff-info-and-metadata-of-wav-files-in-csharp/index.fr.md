---
title: "Extraire les informations RIFF et les métadonnées des fichiers WAV en C #"
date: Fri, 05 Mar 2021 17:58:00 +0000
draft: false
url: /fr/2021/03/05/extract-riff-info-and-metadata-of-wav-files-in-csharp/
author: 'Shoaib Khan'
summary: "**RIFF** (Resource Interchange File Format) est un format de conteneur de fichiers permettant de stocker des données sous forme de blocs balisés. Il est principalement utilisé pour stocker du multimédia comme la vidéo et l'audio. Le bloc peut inclure des informations telles que l'artiste, la date de création et les informations de copyright, etc. Cet article guidera les développeurs pour **extraire les métadonnées et les informations RIFF des fichiers audio WAV en C#**."
tags: ['Extract Metadata in CSharp', 'Extract Metadata of WAV file in CSharp', 'Extract RIFF INFO of WAV in CSharp']
categories: ['GroupDocs.Metadata Product Family']
---

**RIFF** (Resource Interchange File Format) est un format de conteneur de fichiers permettant de stocker des données sous forme de blocs balisés. Il est principalement utilisé pour stocker du multimédia comme la vidéo et l'audio. Le bloc peut inclure des informations telles que l'artiste, la date de création et les informations de copyright, etc. Cet article guidera les développeurs pour **extraire les métadonnées et les informations RIFF des fichiers audio WAV en C#**.

Les sujets suivants seront abordés dans l'article en bref:

* [API .NET pour la gestion des métadonnées][2]
* [Extraire les métadonnées des fichiers WAV en C#][3]
* [Extraire les informations RIFF des fichiers WAV en C #][4]

## API .NET pour la gestion des métadonnées {#metadata-management-dotnet-api}

Dans cet article, j'utiliserai l'API [GroupDocs.Metadata for .NET][5] dans les exemples C# pour extraire les métadonnées des fichiers WAV. En plus des fichiers audio WAV, l'API prend en charge l'ajout, la suppression, la mise à jour et l'extraction de métadonnées à partir de fichiers MP3 et de vidéos. En outre, il prend en charge les formats de fichiers Microsoft Office et Open Office, les livres électroniques, les images et de nombreux autres formats de documents.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** depuis la [section téléchargements][6] ou installer l'API dans votre application .NET via [NuGet][7].

```
PM> Install-Package GroupDocs.Metadata
```

## Extraire les métadonnées des fichiers WAV en C# {#extract-metadata-of-wav-audio-in-csharp}

Commençons par l'extraction des métadonnées des fichiers WAV. Suivez les étapes et l'exemple de code ci-dessous pour extraire les propriétés de métadonnées du package WAV des fichiers WAV en C#.

* Chargez le fichier audio WAV.
* Obtenez le [WavRootPackage][8] de métadonnées.
* Extrayez le [WavPackage][9] du package racine.
* Vous pouvez maintenant accéder à toutes les propriétés de l'audio WAV.

```
// Extraire les métadonnées des fichiers WAV en C#
using (Metadata metadata = new Metadata("audio.wav"))
{
    var root = metadata.GetRootPackage<WavRootPackage>();
    Console.WriteLine("Bits per Sample: "   + root.WavPackage.BitsPerSample); // Bits per Sample
    Console.WriteLine("Block Align: "       + root.WavPackage.BlockAlign); // Block Align
    Console.WriteLine("Byte Rate: "         + root.WavPackage.ByteRate); // Byte Rate
    Console.WriteLine("Number of Channels: " + root.WavPackage.NumberOfChannels); // Number of Channels
    Console.WriteLine("Audio Format: "      + root.WavPackage.AudioFormat); // Audio Format 
    Console.WriteLine("Sample Rate: "       + root.WavPackage.SampleRate); // Sample Rate
}
```

Voici la sortie du code ci-dessus :

```
Bits per Sample: 16
Block Align: 4
Byte Rate: 176400
Number of Channels: 2
Audio Format: 1
Sample Rate: 44100
```

## Extraire les informations RIFF des fichiers WAV en C# {#extract-riff-info-of-wav-audio-in-csharp}

Les informations RIFF des fichiers WAV peuvent également être extraites de la même manière que l'extraction des propriétés WavPackage illustrée précédemment. En suivant les étapes suivantes, vous pouvez extraire les RIFF INFO du fichier audio au format de fichier WAV dans votre application .NET.

* Chargez le fichier audio WAV.
* Obtenez le [WavRootPackage][10] de métadonnées.
* Extrayez le [RiffInfoPackage][11] du package racine.
* Accédez maintenant aux propriétés de l'audio WAV.

L'exemple de code suivant extrait les propriétés de métadonnées du package RIFF INFO du fichier WAV en C#.

```
// Extraire RIFF INFO des fichiers WAV en C#
using (Metadata metadata = new Metadata("audio.wav"))
{
    var root = metadata.GetRootPackage<WavRootPackage>();
    Console.WriteLine("Artist: "      + root.RiffInfoPackage.Artist); // Artist
    Console.WriteLine("Comment: "     + root.RiffInfoPackage.Comment); // Comment
    Console.WriteLine("Copyright: "   + root.RiffInfoPackage.Copyright); // Copyright
    Console.WriteLine("CreationDate: " + root.RiffInfoPackage.CreationDate); // Creation Date
    Console.WriteLine("Software: "    + root.RiffInfoPackage.Software); // Software
    Console.WriteLine("Engineer: "    + root.RiffInfoPackage.Engineer); // Engineer
    Console.WriteLine("Genre: "       + root.RiffInfoPackage.Genre); // Genre
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

En bref, il est très facile de retirer les métadonnées et les RIFF INFO des fichiers WAV en C#. Après avoir essayé les exemples ci-dessus, pensez à développer votre propre application .NET d'extraction de métadonnées comme [GroupDocs.Metadata App][12].

Il existe de nombreux autres exemples open source disponibles sur [GitHub Repository][13]. Téléchargez le code source et exécutez rapidement les exemples à l'aide du guide [de démarrage][14]. En cas de difficulté, visitez la [documentation][15] ou contactez l'équipe d'assistance à tout moment sur le [forum][16].

## Voir également

* [Gérer les données EXIF des images en C #][17]
* [Gérer les données EXIF des images en Java][18]







[1]: https://blog.groupdocs.com/2021/03/05/extract-riff-info-and-metadata-of-wav-files-in-csharp
[2]: #metadata-management-dotnet-api
[3]: #extract-metadata-of-wav-audio-in-csharp
[4]: #extract-riff-info-of-wav-audio-in-csharp
[5]: https://products.groupdocs.com/metadata/net
[6]: https://downloads.groupdocs.com/metadata/net
[7]: https://www.nuget.org/packages/groupdocs.metadata
[8]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/wavrootpackage/properties/index
[9]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/wavrootpackage/properties/wavpackage
[10]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/wavrootpackage/properties/index
[11]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/wavrootpackage/properties/riffinfopackage
[12]: https://products.groupdocs.app/metadata/family
[13]: https://github.com/groupdocs-metadata
[14]: https://docs.groupdocs.com/metadata/net/getting-started/
[15]: https://docs.groupdocs.com/metadata/net
[16]: https://forum.groupdocs.com/c/metadata
[17]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/
[18]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/


