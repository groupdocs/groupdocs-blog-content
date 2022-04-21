---
title: "Générer un code-barres en C# - Ajouter un code-barres aux documents et aux images"
date: Wed, 14 Jul 2021 17:25:00 +0000
draft: false
url: /fr/2021/07/14/generate-barcode-in-csharp-to-sign-documents-and-images/
author: 'Shoaib Khan'
summary: 'Barcode is way to present the data in machine readable format. Barcodes are normally used for quick identification of large number of items. In this article, you will learn how to generate barcodes within .NET applications. Futher you will see, how the generated barcodes can be applied to any of your documents and images using C#.

Les sujets suivants sont traités dans cet article :

* API de générateur de codes à barres pour .NET
* Générer et appliquer un code-barres aux documents en C#
* Générer et appliquer un code-barres aux images en C#'
tags: ['Apply Barcode to Images in C#', 'Apply Barcode to PDF in C#', 'Generate Barcode in C#', 'Sign Documents with Barcode in C#', 'Sign Images with Barcode in C#']
categories: ['GroupDocs.Signature Product Family']
---

Le code-barres est un moyen de présenter les données dans un format lisible par machine. Les codes-barres sont normalement utilisés pour l'identification rapide d'un grand nombre d'articles. Dans cet article, vous apprendrez à générer des codes-barres dans les applications .NET. De plus, vous verrez comment les codes-barres générés peuvent être appliqués à n'importe lequel de vos documents et images à l'aide de C#.

Les sujets suivants sont traités ci-dessous :

* [API du générateur de code-barres pour .NET][1]
* [Générer et appliquer un code-barres aux documents en C#][2]
* [Générer et appliquer un code-barres aux images en C#][3]

## API .NET pour la génération de codes-barres {#barcode-generator-dotnet-api}

[GroupDocs.Signature][4] possède l'API .NET qui vous permet de signer vos documents, images ou fichiers de différents formats de fichiers. En utilisant cette API, vous pouvez facilement appliquer différents types de signatures comme les codes QR, les codes-barres, le texte, l'image, les métadonnées, les signatures numériques, les tampons, les signatures électroniques. De plus, vous pouvez personnaliser l'apparence de la signature de plusieurs façons.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** depuis la [section téléchargements][5] ou installer l'API pour votre application .NET via [NuGet][6]. Vous pouvez également utiliser la commande suivante du gestionnaire de packages.

```
PM> Install-Package GroupDocs.Signature
```

## Codes à barres pour les documents et les images à l'aide de C # {#generate-barcode-in-csharp}

Les codes-barres peuvent être générés par programmation avec le texte personnalisé, l'apparence et différents types d'encodage. Certains des types de codes-barres pris en charge incluent le Code 32, le Code 128, le DotCode, le GS1, l'ISBN, le PDF417, le Pharmacode, le Postnet, l'UPCA et bien d'autres. Ces codes-barres peuvent être appliqués à une grande liste de [formats de documents et d'images pris en charge][7].

Voici l'étape principale pour appliquer des codes-barres sur n'importe quel document ou image.

* Charger le document ou l'image.
* Générez le code-barres avec le texte, l'apparence, l'encodage et d'autres propriétés.
* Appliquez-le sur le fichier chargé.



{{< figure align=center src="images/Generate-Barcode-using-GroupDocs.jpg" alt="Générer un code-barres en C#">}}


## Générer un code-barres et l'appliquer aux documents en C# {#apply-barcode-to-documents}

Voici l'étape pour générer des codes-barres et les appliquer à n'importe quel document. Que les documents cibles soient un document MS Word, un fichier PDF, une feuille de calcul Excel ou une présentation, les étapes pour ajouter un code-barres seraient les mêmes pour tous les différents formats.

* Chargez le document (PDF, Word Doc, Tableur, PPT, ...) en utilisant la classe [Signature][8].
* Configurez les options de code-barres à l'aide de la classe [BarcodeSignOptions][9].
* Définissez les propriétés du code-barres telles que le type d'encodage, la position, la taille, etc.
* Appelez la méthode [Sign][10] pour appliquer le code-barres et signer le document chargé.

Le code source suivant génère un code-barres et le joint à un document PDF à l'aide de C#.

```
// Générez et appliquez des codes-barres aux documents (DOC, DOCX, PDF, PPT, XLS, XLSX, ...)
using (Signature signature = new Signature("path/document.pdf"))
{
    // Create barcode options with the barcode text
    BarcodeSignOptions options = new BarcodeSignOptions("Signed by GroupDocs using GroupDocs.Signature.")
    {
        // Set the Barcode Encoding Ttype
        EncodeType = BarcodeTypes.Code128,

        // Set Signature Position
        Left = 205,
        Top = 170,
        Width = 200,
        Height = 50
    };
    // Apply Barcode on document to Sign.
    SignResult result = signature.Sign("path/document-with-barcode.pdf", options);
}
```

## Générer un code-barres et appliquer aux images en C # {#apply-barcode-to-images}

De même, la façon d'appliquer des codes-barres sur les images n'est pas différente. Chargez simplement la bonne image, le reste des étapes et le code resteront les mêmes que ceux utilisés pour appliquer des codes-barres aux documents ci-dessus.

Voici l'étape pour générer des codes-barres et les appliquer à n'importe quelle image.

* Chargez l'image (JPG, PNG, WebP, ...) en utilisant [Signature][11].
* Préparez les options de code-barres à l'aide de [BarcodeSignOptions][12].
* Personnalisez le code-barres en définissant le texte, le type d'encodage, la position, la taille, l'apparence, etc.
* Appliquez le code-barres pour signer l'image à l'aide de la méthode [Sign][13].

Le code source suivant génère un code-barres et l'attache à une image JPG à l'aide de C#.

```
// Générez et appliquez des codes-barres aux images (JPG, PNG, BMP, ...)
using (Signature signature = new Signature("path/image.jpg"))
{
    // Create barcode options with the barcode text
    BarcodeSignOptions options = new BarcodeSignOptions("Signed by GroupDocs using GroupDocs.Signature.")
    {
        // Set the Barcode Encoding Ttype
        EncodeType = BarcodeTypes.Code128,

        // Set Signature Position
        Left = 20,
        Top = 150,
        Width = 160,
        Height = 30
    };
    // Apply Barcode on document to Sign.
    SignResult result = signature.Sign("path/document-with-barcode.jpg", options);
}
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][14] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, vous avez appris à générer le code-barres en C#. De plus, vous avez vu comment ajouter ces codes-barres générés à vos images et documents. Vous pouvez maintenant développer votre propre application .NET de générateur de codes-barres.

Vous pouvez en savoir plus sur l'API de signature .NET en utilisant la [documentation][15], ou par des exemples disponibles sur [GitHub][16]. Contactez-nous sur le [forum][17].

## Voir également

* [Générer des codes QR en C# et les appliquer aux documents et images en tant que signature][18]
* [Générer et appliquer des codes QR sur des images et des documents en Java][19]







[1]: #barcode-generator-dotnet-api
[2]: #apply-barcode-to-documents
[3]: #apply-barcode-to-images
[4]: https://products.groupdocs.com/signature/
[5]: https://downloads.groupdocs.com/signature
[6]: https://www.nuget.org/packages/groupdocs.signature
[7]: https://docs.groupdocs.com/signature/net/supported-document-formats/
[8]: https://apireference.groupdocs.com/signature/net/groupdocs.signature/signature
[9]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.options/barcodesignoptions
[10]: https://apireference.groupdocs.com/signature/net/groupdocs.signature/signature/methods/sign
[11]: https://apireference.groupdocs.com/signature/net/groupdocs.signature/signature
[12]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.options/barcodesignoptions
[13]: https://apireference.groupdocs.com/signature/net/groupdocs.signature/signature/methods/sign
[14]: https://purchase.groupdocs.com/temporary-license
[15]: https://docs.groupdocs.com/signature/net/
[16]: https://github.com/groupdocs-signature
[17]: https://forum.groupdocs.com/
[18]: https://blog.groupdocs.com/2021/01/27/generate-qr-codes-in-csharp-to-sign-documents-and-images/
[19]: https://blog.groupdocs.com/2021/02/19/generate-qr-codes-in-java-to-sign-documents-and-images/


