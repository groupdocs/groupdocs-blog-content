---
title: "Rechercher des signatures d'image dans Word, Excel, PowerPoint, documents PDF en C#"
date: Mon, 06 Apr 2020 02:26:52 +0000
draft: false
url: /fr/2020/04/06/search-image-signatures-in-word-excel-ppt-pdf-using-csharp/
aliases:
- /2020/04/06/search-image-signatures-in-word-excel-ppt-pdf-documents/
author: 'Shoaib Khan'
summary: "La **signature électronique** est la donnée numérique jointe à un document transmis électroniquement. Il vérifie l'intention de l'expéditeur de signer le document."
tags: ['Search Barcode in CSharp', 'Search Electronic Signature in CSharp', 'Search QR code in CSharp', 'Search Signatures in CSharp']
categories: ['GroupDocs.Signature Product Family']
---

La **signature électronique** est la donnée numérique jointe à un document transmis électroniquement. Il vérifie l'intention de l'expéditeur de signer le document.



{{< figure align=center src="images/groupdocs-signature-net-90x90-no-border.png" alt="GroupDocs.Signature pour .NET. Rechercher des signatures d'image dans des documents">}}


En tant que développeur, vous pouvez signer des documents par programmation et également vérifier si le document est correctement signé avec la bonne signature. [**GroupDocs.Signature pour .NET**][1] L'API fournit de nombreuses fonctionnalités de ce type et vous donne un contrôle total sur le processus de signature électronique. Il fournit différentes implémentations de signature électronique, telles que :

* Signatures de texte (texte, annotations, filigranes, autocollants)
* Signature d'image - avec des options telles que les effets d'image et la rotation.
* Signature numérique - basée sur des certificats numériques.
* Signature de code-barres
* Signature du code QR
* Signature du cachet
* Signature des métadonnées
* Signature du champ de formulaire

Cet article montre comment les développeurs peuvent rechercher des signatures électroniques de différents types dans n'importe quel document avec C# à l'aide de l'API GroupDocs.Signature pour .NET.

## Rechercher des signatures de code QR en C#

Voici la méthode de recherche la plus simple qui montre comment rechercher des signatures de code QR dans un document PDF. Vous pouvez utiliser la même ligne de code pour effectuer une recherche dans n'importe quel format de fichier pris en charge.

```
// Search QR Code Signatures in PDF document using C#
using (Signature signature = new Signature("signed.pdf"))
{
    // search for signatures in document
    List<QrCodeSignature> signatures = signature.Search<QrCodeSignature>(SignatureType.QrCode);
 
    Console.WriteLine($"\\nSource document contains following signatures.");
    foreach (var qrCodeSignature in signatures)
    {
        Console.WriteLine($"QRCode signature found at page {qrCodeSignature.PageNumber} with type {qrCodeSignature.EncodeType.TypeName} and text {qrCodeSignature.Text}");
    }
}
```

## Rechercher des codes-barres, des codes QR et d'autres signatures en C#

Il est assez simple de trouver la signature de code-barres, la signature de code QR, la signature de texte ou même la signature de métadonnées cachée dans le document. Le code mentionné ci-dessous montre comment différents types de signature peuvent être extraits de n'importe quel document en C#.

```
using (Signature signature = new Signature("signed.pdf"))
{
    // search for signatures in document
    SearchResult result = signature.Search(SignatureType.Text, SignatureType.Barcode, SignatureType.QrCode, SignatureType.Metadata);
    if (result.Signatures.Count > 0)
    {
        Console.WriteLine($"\\nSource document contains following signatures.");
        foreach (var resSignature in result.Signatures)
        {
            Console.WriteLine($"Signature found at page {resSignature.PageNumber} with type {resSignature.SignatureType} and Id#: {resSignature.SignatureId}");
        }
    }
    else
    {
        Console.WriteLine("No signature was found.");
    }                
}
```

## Rechercher une signature d'image dans un PDF et saisir du contenu dans C#

L'API de signature .NET permet non seulement d'obtenir toutes les signatures de différents types, mais elle récupère également le contenu des données d'image pour les présentations, les feuilles de calcul, le traitement de texte et les documents PDF. Voici le code source montrant comment récupérer le contenu de l'image après la recherche réussie de signature d'image à partir d'un document PDF en C#.

```
using (Signature signature = new Signature("signed.pdf"))
{
    // setup search options
    ImageSearchOptions searchOptions = new ImageSearchOptions()
    {
        // enable grabbing image content feature
        ReturnContent = true,
        // set minimum size if needed
        MinContentSize = 0,
        // set maximum size if needed
        MaxContentSize = 0,                    
        // specify exact image type to be returned
        ReturnContentType = FileType.JPEG,                                   
    };
    // search document
    List<ImageSignature> signatures = signature.Search<ImageSignature>(searchOptions);
    Console.WriteLine($"\\nSource document contains following image signature(s).");
    // output signatures
    foreach (ImageSignature imageSignature in signatures)
    {
        Console.Write($"Found Image signature at page {imageSignature.PageNumber} and size {imageSignature.Size}.");
        Console.WriteLine($"Location at {imageSignature.Left}-{imageSignature.Top}. Size is {imageSignature.Width}x{imageSignature.Height}.");
    }
    //Save signature images
    string outputPath = "Output";
    if (!Directory.Exists(outputPath))
    {
        Directory.CreateDirectory(outputPath);
    }
    foreach (ImageSignature imageSignature in signatures)
    {
        Console.Write($"Found Image signature at page {imageSignature.PageNumber} and size {imageSignature.Size}.");
        Console.WriteLine($"Location at {imageSignature.Left}-{imageSignature.Top}. Size is {imageSignature.Width}x{imageSignature.Height}.");
        string outputFilePath = System.IO.Path.Combine(outputPath, $"image{i}{imageSignature.Format.Extension}");
        using (FileStream fs = new FileStream(outputFilePath, FileMode.Create))
        {
            fs.Write(imageSignature.Content, 0, imageSignature.Content.Length);
        }
    }
}
```

## Ressources clés pour GroupDocs.Signature pour .NET

En savoir plus sur l'API GroupDocs.Signaure pour .NET. Vous pouvez librement contacter le support si vous avez besoin d'aide :

* [Documents][2]
* [Exemples de code source][3] - GitHub
* [Forum][4]







[1]: https://products.groupdocs.com/signature/net
[2]: https://docs.groupdocs.com/display/signaturenet/Home
[3]: https://github.com/groupdocs-signature/GroupDocs.Signature-for-.NET
[4]: https://forum.groupdocs.com/c/signature


