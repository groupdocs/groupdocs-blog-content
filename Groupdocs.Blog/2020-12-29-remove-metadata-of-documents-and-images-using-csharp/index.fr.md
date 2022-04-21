---
title: "Suppresseur de métadonnées pour les documents et les images à l'aide de C#"
date: Tue, 29 Dec 2020 14:14:00 +0000
draft: false
url: /fr/2020/12/29/remove-metadata-of-documents-and-images-using-csharp/
author: 'Shoaib Khan'
summary: "Aujourd'hui, nous sommes sur le point d'apprendre quelques façons de ** supprimer par programme ou de nettoyer entièrement les métadonnées des documents ainsi que des images à l'aide de C # **. Dans un [article précédent][1], nous avons discuté de la suppression des propriétés sélectives ainsi que de toutes les propriétés de métadonnées disponibles des documents et des images à l'aide de Java. Il est parfois important de cacher au destinataire des informations personnelles qui sont jointes au document. Voici les rubriques qui vous aideront à nettoyer vos fichiers des métadonnées à l'aide de C#."
tags: ['metadata cleaner using csharp', 'remove metadata from documents in csharp', 'remove metadata from images in csharp', 'remove metadata using csharp']
categories: ['GroupDocs.Metadata Product Family']
---

Aujourd'hui, nous sommes sur le point d'apprendre quelques façons de ** supprimer par programme ou de nettoyer entièrement les métadonnées des documents ainsi que des images à l'aide de C # **. Dans un [article précédent][2], nous avons discuté de la suppression des propriétés sélectives ainsi que de toutes les propriétés de métadonnées disponibles des documents et des images à l'aide de Java. Il est parfois important de cacher au destinataire des informations personnelles qui sont jointes au document. Voici les rubriques qui vous aideront à nettoyer vos fichiers des métadonnées à l'aide de C#.

* [API de nettoyage de métadonnées .NET][3]
* [Supprimer les métadonnées des documents à l'aide de C #][4]
* [Nettoyer les métadonnées des images à l'aide de C#][5]
* [Supprimer les métadonnées sélectives des documents et des images à l'aide de C #][6]

## API de suppression des métadonnées .NET {#dotnet-metadata-removal-api}

Pour réaliser ce qui est prévu, j'utiliserai l'API [GroupDocs.Metadata for .NET][7] qui permet aux développeurs .NET d'ajouter, de modifier, d'extraire, de supprimer ou de compléter les métadonnées de nombreux [formats pris en charge][8] de documents, images et autres fichiers. L'API prend en charge les normes de métadonnées telles que EXIF, XMP, IPTC, balise ID3, etc. Vous pouvez [télécharger][9] les DLL ou le programme d'installation MSI, ou l'installer via [NuGet][10].

```
Install-Package GroupDocs.Metadata
```

## Supprimer les métadonnées des documents à l'aide de C # {#remove-documents-metadata-using-csharp}

Afin de supprimer toutes les propriétés des métadonnées sans appliquer de filtre spécifique, utilisez la méthode **Sanitize**. Voici les étapes pour nettoyer les métadonnées des documents tels que DOCX, PDF, XLSX, etc. à l'aide de GroupDocs.Metadata pour .NET.

* Commencez par créer l'objet de classe [Metadata][11] et passez le chemin du document cible en paramètre.
* Utilisez la méthode [Sanitize][12] pour effacer toutes les métadonnées disponibles. Il renvoie le nombre de propriétés de métadonnées supprimées.
* Appelez la méthode [Save][13] pour enregistrer le fichier de sortie avec les métadonnées supprimées.

L'exemple de code C# suivant montre comment supprimer et effacer les métadonnées d'un document PDF.

```
/*
* Nettoyez toutes les propriétés de métadonnées détectées de Word, Excel, 
* PowerPoint, PDF et autres documents utilisant C#
*/
using (Metadata metadata = new Metadata("filePath/document.pdf"))
{
	var affected = metadata.Sanitize();
	metadata.Save("filePath/output.pdf");
}
```

## Supprimer les métadonnées des images à l'aide de C# {#remove-images-metadata-using-csharp}

Que vous souhaitiez supprimer des métadonnées de vos documents ou de vos fichiers image, le processus restera le même. Seul le document source sera modifié en conséquence.

* Créez l'objet de la classe [Metadata][14] et passez le chemin du document en paramètre.
* Appelez la méthode [Sanitize][15] pour supprimer toutes les propriétés de métadonnées disponibles.
* Enregistrez le fichier de sortie à l'aide de la méthode [Save][16].

L'exemple de code C# suivant montre comment supprimer les métadonnées d'une image JPG.

```
/*
* Nettoyez ou supprimez toutes les propriétés de métadonnées détectées de PNG, JPG/JPEG,
* WebP, BMP, GIF, TIFF et autres images utilisant C#
*/
using (Metadata metadata = new Metadata("filePath/document.jpg"))
{
	var affected = metadata.Sanitize();
	metadata.Save("filePath/output.jpg");
}
```

## Supprimer les métadonnées sélectives des documents et des images à l'aide de C # {#remove-selective-metadata-using-csharp}

S'il n'est pas nécessaire de supprimer toutes les métadonnées disponibles des fichiers, et que nous voulons simplement supprimer uniquement les propriétés de métadonnées sélectives. Les étapes suivantes vous permettent de localiser et de supprimer les propriétés de métadonnées ciblées à l'aide du nom spécifique de la propriété.

* Créez un objet de la classe [Metadata][17] pour charger le document source ou le fichier image.
* Créez des spécifications personnalisées pour trouver les propriétés des métadonnées.
* Appelez la méthode [RemoveProperties][18] avec les spécifications personnalisées créées.
* Enregistrez le fichier de sortie à l'aide de la méthode [Save][19].

```
// Supprimez les propriétés de métadonnées des documents et des images qui satisfont le filtre personnalisé à l'aide de C#
using (Metadata metadata = new Metadata("filePath/document.docx"))
{
	// Remove all the properties that:
	// contains the name of the document author OR
	// it refers to the last editor OR 
	// the property value is a string AND equal to the given string "GroupDocs"
	var affected = metadata.RemoveProperties(
		p => p.Tags.Contains(Tags.Person.Creator) ||
			 p.Tags.Contains(Tags.Person.Editor) ||
			 p.Value.Type == MetadataPropertyType.String && p.Value.ToString().Contains("GroupDocs"));
	Console.WriteLine("Properties removed: {0}", affected);

	metadata.Save("outputPath/document.docx");
}
```

## Conclusion

Nous avons appris comment supprimer les métadonnées des documents et des images à l'aide de C#. Après avoir parcouru cet article, vous vous sentirez à l'aise pour créer votre propre application de nettoyage de métadonnées à l'aide de .NET. Il peut prendre en charge la suppression des métadonnées des formats de documents MS Word, des feuilles de calcul, des présentations, des fichiers PDF, des images, des e-mails, des livres électroniques, des dessins, des fichiers zip et bien d'autres [formats de fichiers pris en charge par l'API][20].

Vous pouvez explorer plus en détail l'[API de manipulation des métadonnées .NET][21] à partir de la [documentation][22].

## Voir également

* [Supprimer les métadonnées des documents et des images en Java][23]
* [Gérer les données EXIF des images en C#][24]
* [Gérer les données EXIF des images à l'aide de Java][25]







[1]: https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/
[2]: https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/
[3]: #dotnet-metadata-removal-api
[4]: #remove-documents-metadata-using-csharp
[5]: #remove-images-metadata-using-csharp
[6]: #remove-selective-metadata-using-csharp
[7]: https://products.groupdocs.com/metadata/net
[8]: https://docs.groupdocs.com/metadata/net/supported-document-formats/
[9]: https://downloads.groupdocs.com/metadata/net
[10]: https://www.nuget.org/packages/groupdocs.metadata
[11]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata
[12]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/sanitize
[13]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/save/index
[14]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata
[15]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/sanitize
[16]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/save/index
[17]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata
[18]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/removeproperties
[19]: https://apireference.groupdocs.com/metadata/net/groupdocs.metadata/metadata/methods/save/index
[20]: https://docs.groupdocs.com/metadata/net/supported-document-formats/
[21]: https://products.groupdocs.com/metadata/net
[22]: https://docs.groupdocs.com/metadata/net/
[23]: https://blog.groupdocs.com/2020/12/17/remove-metadata-from-documents-and-images-using-java/
[24]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/
[25]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/


