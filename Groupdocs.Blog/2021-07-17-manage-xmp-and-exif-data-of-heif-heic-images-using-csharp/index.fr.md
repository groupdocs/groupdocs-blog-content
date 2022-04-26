---
title: "Gérer les données XMP et EXIF des images HEIF/HEIC à l'aide de C#"
date: Sat, 17 Jul 2021 17:58:00 +0000
draft: false
url: /fr/2021/07/17/gérer-les-données-xmp-et-exif-des-images-heif-heic-en-utilisant-csharp/
author: 'Shoaib Khan'
summary: "**HEIC** (High-Efficiency Image Container) est un conteneur pouvant contenir des images **HEIF** au format d'image à haute efficacité. **XMP** est une norme de métadonnées basée sur XML, qui peut stocker des propriétés de métadonnées sous forme de paires nom/valeur. Cependant, **EXIF** (Exchangeable Image File Format) est la norme et définit comment stocker les propriétés des métadonnées dans les images et les formats audio les plus courants. Dans cet article, nous allons apprendre **comment extraire, mettre à jour et supprimer les métadonnées XMP et EXIP des images HEIF/HEIC** à l'aide de C# dans les applications .NET."
tags: ['exif data', 'exif data in CSharp', 'EXIF data of HEIC in CSharp', 'XMP data in CSharp', 'XMP data of HEIC in CSharp', 'XMP metadata']
categories: ['GroupDocs.Metadata Product Family']
---

**HEIC** (High-Efficiency Image Container) est un conteneur pouvant contenir des images **HEIF** au format d'image à haute efficacité. **XMP** est une norme de métadonnées basée sur XML, qui peut stocker des propriétés de métadonnées sous forme de paires nom/valeur. Cependant, **EXIF** (Exchangeable Image File Format) est la norme et définit comment stocker les propriétés des métadonnées dans les images et les formats audio les plus courants. Dans cet article, nous allons apprendre **comment extraire, mettre à jour et supprimer les métadonnées XMP et EXIP des images HEIF/HEIC** à l'aide de C# dans les applications .NET.

Les sujets suivants sont traités ci-dessous :

* [API .NET pour EXIF, métadonnées XMP][1]
* [Lire les données EXIF des images HEIC/HEIF][2]
* [Lire les données XMP des images HEIC/HEIF][3]

## API .NET pour les métadonnées XMP et EXIF {#dotnet-api-for-exif-and-xmp-metadata}

[GroupDocs.Metadata][4] fournit l'API .NET pour automatiser la gestion des métadonnées dans les applications .NET. L'API permet de lire, mettre à jour, ajouter, nettoyer/supprimer et parcourir les métadonnées pour de nombreux formats de fichiers. Diverses normes de métadonnées telles que EXIF, IPTC et XMP sont prises en charge par l'API. Vous pouvez également consulter la documentation pour la liste complète des [formats de fichiers pris en charge pour la manipulation des métadonnées][5].

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** depuis la [section téléchargements][6] ou installer l'API dans votre application .NET via [NuGet][7].

```
PM> Install-Package GroupDocs.Metadata
```

## Lire les données EXIF des images HEIC/HEIF en C# {#read-exif-of-heic-heif-images}

Voici les étapes pour lire et extraire les données EXIF des images HEIC et HEIF.

* Chargez l'image HEIF ou HEIC en utilisant la classe Metadata.
* Obtenez le package racine.
* Récupérez le package EXIF à partir du package racine.
* Parcourez les propriétés des données EXIF.
* De plus, vous pouvez obtenir les informations IFD (répertoire de fichiers d'images) et GPS à partir du package EXIF.

Le code suivant montre comment obtenir les données EXIF, les informations de métadonnées IFD et GPS de l'image HEIC à l'aide de C#.

```
// Lire EXIF, EXIF IFD, EXIF GPS Package d'images HEIF / HEIC en C #
using (Metadata metadata = new Metadata(@"image.heic"))
{
    IExif root = metadata.GetRootPackage() as IExif;
    if (root != null && root.ExifPackage != null)
    {
        const string pattern = "{0} = {1}";

        foreach (TiffTag tag in root.ExifPackage.ToList())
        {
            Console.WriteLine(pattern, tag.TagID, tag.Value);
        }

        foreach (TiffTag tag in root.ExifPackage.ExifIfdPackage.ToList())
        {
            Console.WriteLine(pattern, tag.TagID, tag.Value);
        }

        foreach (TiffTag tag in root.ExifPackage.GpsPackage.ToList())
        {
            Console.WriteLine(pattern, tag.TagID, tag.Value);
        }
    }
}
```

## Lire les données XMP des images HEIC/HEIF en C# {#read-xmp-of-heic-heif-images}

Les étapes suivantes lisent les métadonnées XMP des images HEIC ou HEIF.

* Chargez l'image HEIF ou HEIC en utilisant la classe Metadata.
* Obtenez le package racine à l'aide de la méthode getRootPackage.
* À partir du package racine, vous pouvez obtenir les informations de base XMP.
* De plus, vous pouvez obtenir les informations DCMI Dublin Core.
* De plus, vous pouvez obtenir des informations sur Photoshop à l'aide de la méthode getPhotoshop.

Le code source suivant montre comment obtenir des informations XMP basic, DCMI et Photoshop en C#.

```
// Extraire les données XMP Basic, DublinCore et Photoshop des images HEIC et HEIF en C#
using (Metadata metadata = new Metadata(@"xmp.heic"))
{
    IXmp root = metadata.GetRootPackage() as IXmp;
    if (root != null && root.XmpPackage != null)
    {
        if (root.XmpPackage.Schemes.XmpBasic != null)
        {
            Console.WriteLine(root.XmpPackage.Schemes.XmpBasic.CreatorTool);
            Console.WriteLine(root.XmpPackage.Schemes.XmpBasic.CreateDate);
            Console.WriteLine(root.XmpPackage.Schemes.XmpBasic.ModifyDate);
            Console.WriteLine(root.XmpPackage.Schemes.XmpBasic.Label);
            Console.WriteLine(root.XmpPackage.Schemes.XmpBasic.Nickname);
            // ...
        }
        if (root.XmpPackage.Schemes.DublinCore != null)
        {
            Console.WriteLine(root.XmpPackage.Schemes.DublinCore.Format);
            Console.WriteLine(root.XmpPackage.Schemes.DublinCore.Coverage);
            Console.WriteLine(root.XmpPackage.Schemes.DublinCore.Identifier);
            Console.WriteLine(root.XmpPackage.Schemes.DublinCore.Source);
            // ...
        }
        if (root.XmpPackage.Schemes.Photoshop != null)
        {
            Console.WriteLine(root.XmpPackage.Schemes.Photoshop.ColorMode);
            Console.WriteLine(root.XmpPackage.Schemes.Photoshop.IccProfile);
            Console.WriteLine(root.XmpPackage.Schemes.Photoshop.Country);
            Console.WriteLine(root.XmpPackage.Schemes.Photoshop.City);
            Console.WriteLine(root.XmpPackage.Schemes.Photoshop.DateCreated);
            // ... 
        }
        // ...
    }
}
```

De même, il existe de nombreuses méthodes de définition pour définir ou mettre à jour différentes propriétés XMP. Vous pouvez même [fournir votre propre paire clé-valeur pour définir la propriété de package XMP personnalisée][8].

## Supprimer les métadonnées EXIF et XMP des images HEIC/HEIF en C#

Vous pouvez simplement définir le package EXIF ou le package XMP respectif sur null pour supprimer toutes les propriétés de métadonnées.

Le code suivant supprime les données EXIF des images HEIC en C#.

```
using (Metadata metadata = new Metadata("image.heic"))
{
	IExif root = metadata.GetRootPackage() as IExif;
	if (root != null)
	{
		root.ExifPackage = null;
		metadata.Save("no-exif-image.heic");
	}
}
```

Le code suivant supprime les données XMP des images HEIC en C#.

```
using (Metadata metadata = new Metadata("image.heic"))
{
	IXmp root = metadata.GetRootPackage() as IXmp;
	if (root != null)
	{
		root.XmpPackage = null;
		metadata.Save("no-xmp-image.heic");
	}
}
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][9] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour résumer, nous avons appris à extraire, mettre à jour, supprimer les métadonnées EXIF et XMP des images HEIF/HEIC en C#. De plus, vous avez vu comment obtenir des informations IFD et GPS à partir de ces images. Désormais, vous pouvez facilement obtenir ces informations et commencer à créer vos propres applications telles que [GroupDocs.Metadata App Product Family][10] pour automatiser les informations de métadonnées.

Pour plus d'informations, d'options et d'exemples, vous pouvez consulter la [documentation][11] et le référentiel [GitHub][12]. Pour toute autre question, contactez-nous sur le support [forum][13].

## Voir également

* [Extraire les informations RIFF et les métadonnées des fichiers WAV en C #][14]
* [Supprimer les métadonnées des fichiers de document et d'image à l'aide de C #][15]







[1]: #dotnet-api-for-exif-and-xmp-metadata
[2]: #read-exif-of-heic-heif-images
[3]: #read-xmp-of-heic-heif-images
[4]: https://products.groupdocs.com/metadata
[5]: https://docs.groupdocs.com/metadata/net/supported-document-formats/
[6]: https://downloads.groupdocs.com/metadata
[7]: https://www.nuget.org/packages/groupdocs.metadata
[8]: https://docs.groupdocs.com/metadata/net/working-with-xmp-metadata/
[9]: https://purchase.groupdocs.com/temporary-license
[10]: https://products.groupdocs.app/metadata/family
[11]: https://docs.groupdocs.com/metadata/
[12]: https://github.com/groupdocs-metadata
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2021/03/05/extract-riff-info-and-metadata-of-wav-files-in-csharp/
[15]: https://blog.groupdocs.com/2020/12/29/remove-metadata-of-documents-and-images-using-csharp/


