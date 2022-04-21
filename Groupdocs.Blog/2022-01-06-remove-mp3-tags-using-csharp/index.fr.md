---
title: "Supprimer les balises MP3 à l'aide de C#"
date: Thu, 06 Jan 2022 05:27:00 +0000
draft: false
url: /fr/2022/01/06/remove-mp3-tags-using-csharp/
author: 'Shoaib Khan'
summary: "Les fichiers [MP3](https://docs.fileformat.com/audio/mp3/) peuvent contenir des métadonnées de différentes normes. Parfois, vous n'avez pas besoin de certaines informations de métadonnées. Nous pouvons rapidement supprimer ces balises MP3 de métadonnées par programmation. Dans cet article, nous expliquerons **comment supprimer différentes balises MP3 à l'aide de C#**. Plus précisément, nous apprendrons à supprimer les balises de métadonnées ID3v1, ID3v2, Paroles et APEv2 des fichiers mp3 dans l'application .NET.

Les sujets suivants sont traités dans cet article :

* API .NET pour supprimer les balises MP3
* Supprimer les balises MP3 ID3 - ID3, Paroles, APE
* Exemple de code C#"
tags: ['Remove APE', 'Remove Metadata in CSharp', 'Remove MP3 ID3', 'Remove MP3 Metadata', 'Remove MP3 Tags', 'Remove MP3 Tags in CSharp']
categories: ['GroupDocs.Metadata Product Family']
---

Les fichiers [MP3](https://docs.fileformat.com/audio/mp3/) peuvent contenir des métadonnées de différentes normes. Parfois, vous n'avez pas besoin de certaines informations de métadonnées. Nous pouvons rapidement supprimer ces balises MP3 de métadonnées par programmation. Dans cet article, nous expliquerons **comment supprimer différentes balises MP3 à l'aide de C#**. Plus précisément, nous apprendrons à supprimer les balises de métadonnées ID3v1, ID3v2, Paroles et APEv2 des fichiers mp3 dans l'application .NET.

Les sujets suivants sont traités ci-dessous :

* [API .NET pour supprimer les balises MP3](#mp3-tags-dotnet-api)
* [Supprimer les balises MP3 ID3 - ID3, Paroles, APE](#remove-mp3-tags)
* [Exemple de code C#](#source-code-remove-mp3-tags)

## API .NET pour la suppression des balises MP3 {#mp3-tags-dotnet-api}

[GroupDocs.Metadata](https://products.groupdocs.com/metadata) présente [l'API .NET de gestion des métadonnées](https://products.groupdocs.com/metadata/net/) pour gérer divers formats de fichiers dans . applications NET. L'API permet de lire, mettre à jour, ajouter, nettoyer et supprimer totalement les métadonnées pour de nombreux formats de fichiers. Nous utiliserons cette API pour supprimer les balises de métadonnées des fichiers MP3.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements](https://downloads.groupdocs.com/metadata) ou installer l'API dans votre application .NET via [NuGet](https://www.nuget.org/packages/groupdocs.metadata).

```
PM> Install-Package GroupDocs.Metadata
```

## Supprimer les balises MP3 à l'aide de C# - ID3v1, ID3v2, Paroles, APE {#remove-mp3-tags}

Les étapes suivantes vous permettront de supprimer rapidement les balises de métadonnées MP3 de vos fichiers MP3 en C#.

1. **Chargez** le fichier MP3.
2. Obtenez le **paquet racine MP3**.
3. **Supprimez** le(s) tag(s) MP3 concerné(s).
4. **Enregistrer** le fichier MP3 mis à jour.

### 1\. **Charger MP3**

Sélectionnez le fichier MP3 et chargez-le à l'aide de la classe [Metadata](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata).

```
Metadata metadata = new Metadata("path/mp3File.mp3");
```

### 2\. Obtenir le package racine MP3

Obtenez le [paquet racine MP3](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage) du fichier MP3 à l'aide de [GetRootPackage()](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/getrootpackage/index).

```
var root = metadata.GetRootPackage();
```

### 3\. Supprimer les balises MP3

Parmi les manières suivantes de supprimer différentes balises de métadonnées, vous pouvez utiliser votre stratégie de suppression appropriée.

#### **ID3v**1

Pour supprimer les balises de métadonnées **ID3v1**, définissez la propriété [ID3V1](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage/properties/id3v1) du package racine comme nul.

```
root.ID3V1 = null;
```

#### **ID3v2**

Pour supprimer les balises de métadonnées **ID3v2**, annulez la propriété [ID3V2](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage/properties/id3v2).

```
root.ID3V2 = null;
```

#### **Paroles**

Supprimez les balises **Lyrics** en définissant la propriété [Lyrics3V2](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage/properties/lyrics3v2) sur null.

```
root.Lyrics3V2 = null;
```

#### **APE**

Utilisez la méthode [RemoveApeV2()](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.formats.audio/mp3rootpackage/methods/removeapev2) du package racine pour éliminer les balises **APEv2**.

```
root.RemoveApeV2();
```

### 4\. Enregistrer le fichier

Enfin, **enregistrez** le fichier MP3 mis à jour à l'aide de la méthode [Save()](https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/save/index).

```
metadata.Save("path/mp3TagsRemoved.mp3");
```

## Code complet - Supprimer {#source-code-remove-mp3-tags}

L'exemple de code source suivant montre comment supprimer les balises MP3 pertinentes du fichier MP3 en C#.

```
// Supprimer les balises de métadonnées MP3 des fichiers MP3 en C# - ID3v1, ID3v2, Paroles, APE
using (Metadata metadata = new Metadata("path/mp3File.mp3"))
{
    var root = metadata.GetRootPackage<MP3RootPackage>();
    // Use the relevant MP3 Tag propertie(s)
    root.ID3V1 = null;
    root.ID3V2 = null;
    root.Lyrics3V2 = null;
    root.RemoveApeV2();

    metadata.Save("path/mp3TagsRemoved.mp3");
}
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour résumer, nous avons appris à supprimer les balises de métadonnées des fichiers MP3 à l'aide de C#. Nous avons spécifiquement supprimé les balises ID3v1, ID3v2, Paroles et APE des fichiers MP3. Vous pouvez en savoir plus sur l'API à partir de la [documentation](https://docs.groupdocs.com/metadata/net/) et nous contacter pour toute question via le [forum](https://forum.groupdocs.com/) .

## Voir également

* [Lire les balises MP3 en utilisant C# - (ID3, Paroles, APE)](https://blog.groupdocs.com/2022/01/22/read-mp3-tags-using-csharp/)
* [Extraire les informations RIFF et les métadonnées des fichiers WAV en C#](https://blog.groupdocs.com/2021/03/05/extract-riff-info-and-metadata-of-wav-files-in-csharp/)
* [Gérer les données XMP et EXIF des images HEIF/HEIC à l'aide de C#](https://blog.groupdocs.com/2021/07/17/manage-xmp-and-exif-data-of-heif-heic-images-using-csharp/)





