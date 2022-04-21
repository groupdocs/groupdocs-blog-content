---
title: "Extraire les données des fichiers ZIP en C#"
date: Wed, 25 Aug 2021 12:43:51 +0000
draft: false
url: /fr/2021/08/25/extract-zip-files-data-in-csharp/
author: 'Shoaib Khan'
summary: "Les archives telles que **ZIP, RAR, TAR, GZIP, BZIP2** sont couramment utilisées pour stocker plusieurs fichiers et dossiers dans un même conteneur. Une autre raison principale pour les fichiers d'archives est de réduire la taille totale du fichier à l'aide d'algorithmes de compression. Tout comme l'analyse et l'extraction de données à partir de documents de différents formats de fichiers, vous pouvez traiter les fichiers d'archive de la même manière. Vous pouvez extraire le texte, les images et même les métadonnées des fichiers compressés dans les archives. Dans cet article, nous verrons **comment extraire les données des archives ZIP à l'aide de C#** avec vos applications .NET."
tags: ['Extract Archives in CSharp', 'Extract from ZIP in C#', 'unzip data in C#']
categories: ['GroupDocs.Parser Product Family']
---

Les archives telles que **ZIP, RAR, TAR, GZIP, BZIP2** sont couramment utilisées pour stocker plusieurs fichiers et dossiers dans un même conteneur. Une autre raison principale pour les fichiers d'archives est de réduire la taille totale du fichier à l'aide d'algorithmes de compression. Tout comme l'analyse et l'extraction de données à partir de documents de différents formats de fichiers, vous pouvez traiter les fichiers d'archive de la même manière. Vous pouvez extraire le texte, les images et même les métadonnées des fichiers compressés dans les archives. Dans cet article, nous verrons **comment extraire les données des archives ZIP à l'aide de C#** avec vos applications .NET.

Les sujets suivants sont traités ci-dessous :

* [API .NET pour l'extraction de données de fichiers ZIP][1]
* [Comment extraire les données des fichiers ZIP][2]

## API .NET pour extraire les données des fichiers ZIP {#dotnet-zip-files-extraction-api}

[GroupDocs.Parser][3] fournit la solution d'analyse de documents pour les développeurs. J'utiliserai son [API .NET pour extraire les données des fichiers ZIP][4] dans les exemples C# de cet article. L'API permet en outre d'extraire du texte, des images et des métadonnées à partir d'une longue liste de [formats de documents pris en charge][5] tels que des documents de traitement de texte, des présentations, des feuilles de calcul, des e-mails, des bases de données, des livres électroniques et bien d'autres.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][6] ou installer l'API en ajoutant son package à votre application .NET via [NuGet][7].

```
PM> Install-Package GroupDocs.Parser
```

## Comment extraire des données de fichiers ZIP en C# {#how-to-extract-zip-data}

Le [GroupDocs.Parser pour .NET][8] prend en charge l'extraction de données à partir de divers formats de fichiers de compression tels que ZIP, RAR, TAR, BZIP2 et GZIP. Après avoir récupéré la collection de fichiers à partir du fichier compressé, vous pouvez en outre extraire tout type de données de chaque fichier.

Les étapes suivantes montrent comment extraire les données des fichiers ZIP et récupérer le texte de chaque fichier joint en C#.

* Chargez l'archive ZIP en utilisant la classe **[Parser][9]**.
* Obtenez les pièces jointes à l'aide de la méthode **_[GetContainer][10]_**
* Parcourez la collection de pièces jointes.
* Pour chaque pièce jointe, vous pouvez obtenir ses différents types de données en utilisant les méthodes respectives de la classe **Parser**.

Le code source montre comment extraire les données des fichiers ZIP à l'aide de C#. Dans cet exemple, je vais extraire l'intégralité du texte de tous les fichiers de l'archive ZIP.

```
// Extraire les données des archives ZIP en C#
using (Parser parser = new Parser(@"path/sample.zip"))
{
    // Extract attachments from the container
    IEnumerable<ContainerItem> attachments = parser.GetContainer();

    // Iterate over collection of entities
    foreach (ContainerItem item in attachments)
    {
        // Print the FILE INFO
        Console.WriteLine("-----------------------------------");
        Console.WriteLine("Name: " + item.Name);
        Console.WriteLine("File Size: " + item.Size + " Bytes");
        Console.WriteLine("-----------------------------------");

        try
        {
            using (Parser attachmentParser = item.OpenParser())
            {
                // Extract the ZIP entity text
                using (TextReader reader = attachmentParser.GetText())
                {
                    Console.WriteLine(reader == null ? "No text" : reader.ReadToEnd());
                }
            }
        }
        catch (UnsupportedDocumentFormatException)
        {
            Console.WriteLine("Isn't supported.");
        }
    }
}
```

La sortie du code source ci-dessus montre le texte extrait de l'un des fichiers PDF dans le fichier ZIP.

```
 -----------------------------------
 Name: sample.pdf
 File Size: 33370 Bytes
 -----------------------------------

 Heading

 This is the first paragraph of the sample document that contains some sample
 text, bulleted list, numbered list and more.

    •  Bullet Item 1
    •  Bullet Item 2
    •  Bullet Item 3
 
 This is the second paragraph of the sample document and after this, there is a
 numbered list: 

    1. Numbered Item 1
    2. Numbered Item 2
    3. Numbered Item 3 
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][11] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

En résumé, vous avez appris à extraire des données d'archives ZIP à l'aide de C# dans votre application .NET. Plus précisément, vous pouvez désormais extraire des données de fichiers ZIP, RAR, TAR, GZIP et BZIP. Vous pouvez même créer votre propre application d'extraction de données .NET pour les fichiers compressés. Pour plus de détails ou en savoir plus sur l'API, consultez la [documentation][12]. Pour toute question, contactez-nous via le [forum][13].

## Voir également

* [Extraire des images de documents à l'aide de C #][14]
* [Extraire des images d'EPUB, FB2, CHM eBooks en C#][15]
* [Lire les champs de formulaire PDF à l'aide de C #][16]







[1]: #dotnet-zip-files-extraction-api
[2]: #how-to-extract-zip-data
[3]: https://products.groupdocs.com/parser/
[4]: https://products.groupdocs.com/parser/net/
[5]: https://docs.groupdocs.com/parser/net/supported-document-formats/
[6]: https://downloads.groupdocs.com/parser
[7]: https://www.nuget.org/packages/groupdocs.parser
[8]: https://products.groupdocs.com/parser/net/
[9]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser
[10]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/getcontainer
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://docs.groupdocs.com/parser/
[13]: https://forum.groupdocs.com/
[14]: https://blog.groupdocs.com/2020/10/28/extract-images-from-pdf-word-excel-ppt-using-csharp/
[15]: https://blog.groupdocs.com/2021/02/26/extract-images-from-ebooks-in-csharp/
[16]: https://blog.groupdocs.com/2020/12/23/parse-and-extract-data-from-pdf-forms-in-csharp/


