---
title: "Gérer les données EXIF des images JPEG, PNG, TIFF et WebP en C# .NET"
date: Wed, 13 May 2020 21:06:49 +0000
draft: false
url: /fr/2020/05/13/gérer-les-données-exif-dans-csharp-net-pour-jpeg-png-tiff-webp-images/
author: 'Shoaib Khan'
summary: "Dans le [article précédent][1], nous avons expliqué comment traiter les données EXIF des images en Java. Ici, aujourd'hui, nous allons chercher à obtenir la même chose mais en C#. Si vous n'avez pas consulté le dernier article, mais que vous souhaitez **extraire, mettre à jour, ajouter ou supprimer des données EXIF ​​de vos images par programmation en C# **, cet article vous guidera à travers cela."
tags: ['change exif data of images', 'extract exif data', 'extract exif data in csharp', 'extract metadata from images', 'remove exif data from images']
categories: ['GroupDocs.Metadata Product Family']
---

Dans le [post précédent][2], nous avons expliqué comment traiter les données EXIF des images en Java. Ici, aujourd'hui, nous allons chercher à obtenir la même chose mais en C#. Si vous n'avez pas consulté le dernier article, mais que vous souhaitez **extraire, mettre à jour, ajouter ou supprimer des données EXIF de vos images par programmation en C # **, cet article vous guidera à travers cela. Nous couvrirons les manières suivantes de manipuler les données EXIF en C# :

* [Lire les données EXIF][3]
* [Lire toutes les balises EXIF d'une image][4]
* [Mettre à jour les propriétés EXIF][5]
* [Supprimer les métadonnées EXIF][6]

## Bibliothèque C# de gestion des métadonnées



{{< figure align=center src="images/GroupDocs.MetaData_for_NET.png" alt="API de métadonnées .NET par GroupDocs">}}


[GroupDocs.Metadata for .NET][7] est l'API .NET de gestion des métadonnées. Il a une longue liste de [fonctionnalités][8] pour une grande variété de formats de fichiers pris en charge. Il a la capacité non seulement d'extraire les métadonnées des images, mais également d'ajouter, de modifier, de mettre à jour et de supprimer les métadonnées des images et des documents avec diverses options.

Dans cet article, nous utiliserons cette API, alors assurez-vous de [télécharger][9] ses binaires ou d'installer l'API à partir de [NuGet][10].

## Lire les données EXIF à partir d'images en C# {#extract-exif-data-from-images}

Vous pouvez facilement lire les propriétés des données EXIF en suivant les étapes mentionnées. A commencer par l'extraction des données EXIF de cette image, Statue de la Liberté haute de 93m. Ici, nous utiliserons un fichier JPG comme exemple d'image, cependant, nous pouvons utiliser n'importe quel fichier, qu'il s'agisse d'un PNG, WebP, BMP, GIF, TIFF ou de tout autre parmi les [formats de fichiers pris en charge][11] mentionnés à la fin de Cet article.



{{< figure align=center src="images/statue-of-liberty.jpg" alt="Image Liberty JPG pour les données EXIF">}}


* Chargez le fichier source de l'image contenant les informations de données EXIF à l'aide du constructeur de classe [Metadata][12].
* Obtenez son **paquet racine** en appelant la méthode [GetRootPackage()][13].
* À partir du package racine, obtenez son [ExifPackage][14] à partir de sa [propriété ExifPackage][15].
* Une fois que vous avez le package EXIF, vous pouvez maintenant accéder aux propriétés EXIF de l'image ; comme **Make**, **Model**, **Width**, **Length**, **DateTime**, Copyright, Software, etc. comme indiqué ci-dessous dans l'exemple de code C#.

```
// Extract EXIF Data Package Information from image in C#
using (Metadata metadata = new Metadata("statue-of-liberty.jpg"))
{
    IExif root = metadata.GetRootPackage() as IExif;
    if (root != null && root.ExifPackage != null)
    {
        Console.WriteLine(root.ExifPackage.Make);
        Console.WriteLine(root.ExifPackage.Model);
        Console.WriteLine(root.ExifPackage.ImageWidth);
        Console.WriteLine(root.ExifPackage.ImageLength);
        Console.WriteLine(root.ExifPackage.DateTime);
     }
}
```

Le code ci-dessus affichera les informations EXIF disponibles suivantes de l'image JPG fournie.

```
Make : NIKON CORPORATION
Model : NIKON D7200 
Width : 640
Length : 384
DateTime : 2018:07:06 19:31:05
```

### Lecture des informations EXIF IFD et GPS de l'image

Les données EXIF incluent également les informations Exif **IFD** (Répertoire de fichiers d'images) et **GPS** (Global Positioning System). Désormais, pour les informations sur les packages IFD et GPS, il vous suffit d'accéder aux propriétés respectives du ** package EXIF **, c'est-à-dire [ExifIfdPackage][16] ou [GpsPackage][17]. À partir de ces packages, vous pouvez extraire beaucoup plus d'informations que celles mentionnées ci-dessous :

* Numéro de série de l'appareil
* Nom du propriétaire de la caméra
* Modèle CFA
* La vitesse
* Sens de l'image
* Timbre dateur
* Informations sur la région
* Altitude
* Latitude
*Longueur
* etc.

Le code mentionné ci-dessous peut être ajouté dans votre méthode ci-dessus pour afficher les données EXIF avec les informations IFD et GPS.

```
// Display EXIF IFD Package Properties like Serial Number and Camera Owner.
Console.WriteLine(root.ExifPackage.ExifIfdPackage.BodySerialNumber);
Console.WriteLine(root.ExifPackage.ExifIfdPackage.CameraOwnerName);
Console.WriteLine(root.ExifPackage.ExifIfdPackage.UserComment);
// Display EXIF GPS Information like Latitude, Longitude, etc.
Console.WriteLine(root.ExifPackage.GpsPackage.Altitude);
Console.WriteLine(root.ExifPackage.GpsPackage.LatitudeRef);
Console.WriteLine(root.ExifPackage.GpsPackage.LongitudeRef);
```

## Lire toutes les balises EXIF des images en C# {#extract-all-exif-tags-from-images}

Vous pouvez extraire toutes les propriétés EXIF de n'importe quelle image, vous pouvez le faire d'une manière presque similaire à celle ci-dessus :

* Chargez l'image avec le constructeur [Metadata][18].
* Obtenez le **paquet racine** en appelant la méthode [GetRootPackage()][19].
* Obtenez le **package EXIF** à partir de la [propriété ExifPackage][20] du package racine.
* Itérez le package EXIF et obtenez les paires nom-valeur souhaitées.
* De même, obtenez les packages IFD et GPS pour afficher ses clés et ses valeurs.

```
// Extract all EXIF Metadata from the image
using (Metadata metadata = new Metadata("statue-of-liberty.jpg"))
{
    IExif root = metadata.GetRootPackage() as IExif;
    if (root != null && root.ExifPackage != null)
    {
        const string pattern = "{0} = {1}";
        // Read all EXIF Package Tags and values.
        foreach (TiffTag tag in root.ExifPackage.ToList()) {
            Console.WriteLine(pattern, tag.Name, tag.Value);
        }
        // Read all EXIF IFD Package Tags and values.
        foreach (TiffTag tag in root.ExifPackage.ExifIfdPackage.ToList()) {
            Console.WriteLine(pattern, tag.Name, tag.Value);
        }
         // Read all EXIF GPS Package Tags and values.
        foreach (TiffTag tag in root.ExifPackage.GpsPackage.ToList()) {
            Console.WriteLine(pattern, tag.Name, tag.Value);
        }
    }
}
```

## Mettre à jour les propriétés EXIF en C# {#update-exif-properties}

Vous pouvez facilement modifier les données EXIF existantes de n'importe quelle image. Voici les étapes que vous pouvez suivre :

### **Mettre à jour le package EXIF**

* Obtenez le **paquet racine** en appelant la méthode [GetRootPackage()][21].
* Définissez les propriétés ExifPackage en attribuant les nouvelles valeurs aux propriétés correspondantes, comme attribuer une nouvelle valeur à :
    * **root.ExifPackage.Copyright** - pour définir les informations de copyright mises à jour.
* De même, vous pouvez définir les valeurs de l'artiste, de la marque, du modèle, du logiciel, de la largeur et de la hauteur de l'image, de la date et de l'heure, etc.

### **Mettre à jour le package EXIF IFD**

Semblable aux propriétés de réglage du package EXIF, nous pouvons mettre à jour les propriétés des packages EXIF IFD et GPS.

* Attribuez une valeur à **root.ExifPackage.ExifIfdPackage.CameraOwnerName** pour définir le propriétaire de la caméra.

Vous pouvez visiter les classes [ExifIfdPackage][22] ou [ExifGpsPackage][23] pour avoir une idée de ce que vous pouvez personnaliser pour vos images.

```
// Update or change new values in EXIF Data (EXIF Package & EXIF IFD Package).
using (Metadata metadata = new Metadata("statue-of-liberty.jpg"))
{
    IExif root = metadata.GetRootPackage() as IExif;
    if (root != null)
    {
        // Set the EXIF package if it is missing
        if (root.ExifPackage == null) {
            root.ExifPackage = new ExifPackage();
        }
       // Setting the desired values in EXIF Package and EXIF IFD Package.
        root.ExifPackage.Copyright = "Copyright (C) 2011-2020 GroupDocs. All Rights Reserved.";
        root.ExifPackage.ImageDescription = "Statue of Liberty for EXIF Data";
        root.ExifPackage.Software = "GroupDocs.Metadata for .NET"; 
        root.ExifPackage.ExifIfdPackage.BodySerialNumber = "GD-2020";
        root.ExifPackage.ExifIfdPackage.CameraOwnerName = "GroupDocs";
        root.ExifPackage.ExifIfdPackage.UserComment = "Nice image captured in 2018";
        metadata.Save("statue-of-liberty-updated.jpg");
    }
}
```

## Supprimer les métadonnées EXIF des images en C # {#remove-exif-metadata}

Si vous souhaitez supprimer le package EXIF de n'importe quel fichier, définissez simplement sa propriété ExifPackage sur ** null **.

```
// Removing the EXIF data from an image.
using (Metadata metadata = new Metadata("statue-of-liberty.jpg"))
{
    IExif root = metadata.GetRootPackage() as IExif;
    if (root != null)
    {
        root.ExifPackage = null;
        metadata.Save("statue-of-liberty-no-exif.jpg");
    }
}
```

## Images et autres formats pris en charge {#exif-supported-formats}

Ce sont les formats de fichiers actuellement pris en charge par GroupDocs.Metadata pour les informations de données EXIF des images, audios et vidéos. Vous pouvez toujours visiter la [documentation][24] pour les informations mises à jour.

<figure class="wp-block-table is-style-stripes"><table class="has-fixed-layout"><tbody><tr><td> **Type de document</td><td> <strong>Formats de fichiers**</strong></td></tr><tr><td> <a href="https://wiki.fileformat.com/image/">Images</a></td><td> BMP, GIF, JPG, JPEG, JPE, JP2, PNG, DJVU, DWG, DXF, WebP, TIFF, PSD, EMF, WMF</td></tr><tr><td> <a href="https://wiki.fileformat.com/audio">Audio</a> et <a href="https://wiki.fileformat.com/video/">vidéo</a></td><td> MP3, WAV, AVI, MOV/QT, FLV, ASF, DICOM</td></tr></tbody></table></figure>

## En savoir plus sur GroupDocs.Metadata

* Documentation ([.NET][25] | [Java][26]
* [Exemples de code source][27]
* [Référence API][28]
* GroupDocs.Metadata - [La solution de gestion des métadonnées][29]

**Parlons plus @** [Forum d'assistance gratuit.][30]

## Article associé

* [Gérer les données EXIF des images en Java][31]







[1]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/
[2]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/
[3]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/#extract-exif-data-from-images
[4]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/#extract-all-exif-tags-from-images
[5]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/#update-exif-properties
[6]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/#remove-exif-metadata
[7]: https://products.groupdocs.com/metadata/net
[8]: https://docs.groupdocs.com/display/metadatanet/Features+Overview
[9]: https://downloads.groupdocs.com/metadata/net
[10]: https://www.nuget.org/packages/groupdocs.metadata
[11]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/#exif-supported-formats
[12]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata
[13]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/getrootpackage
[14]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/exifpackage
[15]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/iexif/properties/exifpackage
[16]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/exifpackage/properties/exififdpackage
[17]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/exifpackage/properties/gpspackage
[18]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata
[19]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/getrootpackage
[20]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/iexif/properties/exifpackage
[21]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/getrootpackage
[22]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/exififdpackage
[23]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata.standards.exif/exifgpspackage
[24]: https://docs.groupdocs.com/display/metadatanet/Supported+File+Formats
[25]: https://docs.groupdocs.com/display/metadatanet/Getting+Started
[26]: https://docs.groupdocs.com/display/metadatajava/Getting+Started)
[27]: https://github.com/groupdocs-metadata/
[28]: https://apireference.groupdocs.com/metadata
[29]: https://products.groupdocs.com/metadata
[30]: https://forum.groupdocs.com/c/metadata
[31]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/


