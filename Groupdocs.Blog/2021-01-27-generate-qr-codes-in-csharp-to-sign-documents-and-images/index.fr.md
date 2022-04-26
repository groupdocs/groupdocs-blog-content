---
title: "Générer un code QR en C# pour signer des documents et des images"
date: Wed, 27 Jan 2021 22:39:00 +0000
draft: false
url: /fr/2021/01/27/generate-qr-codes-in-csharp-to-sign-documents-and-images/
aliases:
- /2019/09/07/sign-documents-with-qr-code/
- /2019/09/07/sign-documents-with-qr-code-in-csharp-and-java
- /2019/09/07/sign-documents-with-qr-code-in-csharp-and-java/
- /2020/11/18/sign-documents-and-images-with-qr-code-in-csharp/
author: 'Shoaib Khan'
summary: "Dans cet article, nous verrons **comment ajouter par programmation des codes QR pour signer électroniquement des documents et des images à l'aide de C#**. GroupDocs.Signature pour .NET est l'API permettant d'ajouter des codes QR dans des fichiers PDF, des documents de traitement de texte, des feuilles de calcul, des présentations et des images. Il prend en charge diverses signatures électroniques pour une grande liste de formats de fichiers pris en charge. Parmi les codes QR, il prend en charge le code aztèque, le code DataMatrix, GS1 DataMatrix, GS1 QR, les types QR. L'API nous permet d'ajouter des codes QR aux images JPG/JPEG, PNG, WebP, BMP, GIF, SVG, CMX et TIFF ainsi qu'à d'autres formats de fichiers image."
tags: ['Add QR code in CSharp', 'Attach QR code with Images in CSharp', 'eSign in CSharp', 'generate qr code in csharp', 'Sign documents with QR code in CSharp']
categories: ['GroupDocs.Signature Product Family']
---

Les codes QR ont gagné en popularité ces dernières années. En tant que développeur, voyons **comment générer par programmation des codes QR en C#** pour signer électroniquement des documents et des images. Dans le post précédent, nous avons discuté [attacher des codes QR avec des documents et des images en utilisant Java][1].



{{< figure align=center src="images/add-qr-code-to-docs-and-images-using-dotnet.png" alt="Générez des codes QR en C# .NET pour signer des documents et des images à l'aide de GroupDocs.">}}


Les sujets suivants seront convertis dans cet article :

* [API .NET pour la génération de codes QR et la signature][2]
* [Générer des codes QR - Signer des documents en C#][3]
* [Générer des codes QR - Ajouter à une image JPG, PNG ou WebP en C#][4]

## API .NET pour la génération de codes QR {#dotnet-api-for-qr-codes}



{{< figure align=center src="images/groupdocs-signature-net-90x90-no-border.png" alt="GroupDocs.Signature pour .NET">}}


Dans cet article, j'utiliserai l'API [GroupDocs.Signature pour .NET][5] pour générer des codes QR. Cette API prend en charge le code aztèque, le code DataMatrix, GS1 DataMatrix, GS1 QR, les types QR. Il prend également en charge les fichiers PDF, les documents de traitement de texte, les feuilles de calcul, les présentations, les images et bien plus encore [formats de fichiers de documents pour ajouter des codes QR][6].

Pour les exemples ci-dessous, je vous recommande d'installer l'API à partir du gestionnaire de packages [NuGet][7] ou d'obtenir le programme d'installation MSI et les DLL de la section [downloads][8]. Vous pouvez également utiliser la commande suivante dans votre console du gestionnaire de packages.

```
PM> Install-Package GroupDocs.Signature
```

Pour plus de détails, vous pouvez visiter la [API Reference][9].

## Générer des codes QR en C# - Ajouter aux fichiers PDF, Word, Excel, PPT {#add-qr-code-to-documents-in-csharp}

Les classes **Signature** et **QrCodeSignOptions** permettent de créer rapidement différents types de codes QR et de signer des documents et des images dans l'application .NET. Les étapes suivantes montrent comment générer des codes QR à l'aide de C#, puis les joindre à un document PDF :

1. Initialisez l'objet de classe **Signature** avec le document source.
2. Définissez les propriétés du code QR à l'aide de la classe **QrCodeSignOptions**.
3. Plus important encore, sélectionnez le type de code QR approprié parmi les types de code QR disponibles. (Aztèque, DataMatrix, GS1 DataMatrix, GS1 QR, QR)
4. Appelez la méthode **Sign**, en transmettant le chemin du document résultant et les options de code QR.

Le code C# suivant implémente les étapes ci-dessus. De même, vous pouvez fournir un document Word, une feuille de calcul, une présentation ou tout autre [format de document pris en charge][10] pour joindre les codes QR générés.

```
// Signez électroniquement des documents PDF, Excel, PPT, Word et des images avec un code QR à l'aide de GroupDocs.Signature pour l'API .NET
using (Signature signature = new Signature("filePath/document.pdf")) // Provide any DOC, PDF, XLS, PPT, PNG, JPG, WebP file.
{
    // Create QR Code option with predefined text
    QrCodeSignOptions options = new QrCodeSignOptions("Signed by GroupDocs")
    {
        EncodeType = QrCodeTypes.QR,
        // Set QR Code position & appearance
        Left = 50,
        Top = 50,
        Width = 90,
        Height = 90
    };
    // Sign document and save file
    SignResult result = signature.Sign("filePath/document-with-qr-code.pdf", options);
}
```

Il s'agit du fichier PDF avec le code QR en sortie du code ci-dessus.



{{< figure align=center src="images/Added-QR-Code-in-PDF-using-GroupDocs.Signature-APIs.png" alt="Ajouter le code QR généré au PDF à l'aide de l'API Signature" caption="Fichier PDF avec code QR ajouté à l'aide de GroupDocs.Signature pour l'API .NET">}}


## Générer des codes QR en C# - Joindre avec des images JPG, PNG ou WebP {#add-qr-code-to-images-in-csharp}



{{< figure align=center src="images/image-with-qr-code.png" alt="Ajoutez le code QR généré à Image.">}}


Vous pouvez également utiliser le même code ci-dessus pour joindre les codes QR générés aux images. L'API vous permet d'ajouter des codes QR aux images JPG/JPEG, PNG, WebP, BMP, GIF, SVG, CMX et TIFF, ainsi qu'à d'autres formats de fichiers image.

Lors de la génération de codes QR, vous pouvez également modifier la couleur d'arrière-plan, la première couleur, la transparence et d'autres propriétés pour modifier leur apparence. Le code C# ci-dessous change la couleur d'arrière-plan du code QR en **noir** et définit la première couleur sur **blanc**.

```
// Modifier l'apparence du code QR en C #
// Réglage de la couleur d'arrière-plan, de la première couleur, de la transparence, etc.
Background = new Background()
{
    Color = Color.Black,
    Transparency = 0.5
},
//définir la couleur et la police du texte
ForeColor = Color.White
```

## Conclusion

Je crois que vous savez maintenant comment créer des codes QR en C # pour signer vos documents et images électroniquement dans les applications .NET. Vous pouvez encore modifier l'apparence des codes QR qui convient à votre marque.

## Voir également

* [Générer des codes QR pour signer des documents et des images en Java][11]

* [Documents][12]
* [Équipe d'assistance gratuite][13]
* [Exemples sur GitHub][14]







[1]: https://blog.groupdocs.com/2021/02/19/generate-qr-codes-in-java-to-sign-documents-and-images/
[2]: #dotnet-api-for-qr-codes
[3]: #add-qr-code-to-documents-in-csharp
[4]: #add-qr-code-to-images-in-csharp
[5]: https://products.groupdocs.com/signature/net
[6]: https://docs.groupdocs.com/signature/net/supported-document-formats/
[7]: https://www.nuget.org/packages/groupdocs.signature
[8]: https://downloads.groupdocs.com/signature/net
[9]: https://apireference.groupdocs.com/signature/net
[10]: https://docs.groupdocs.com/signature/net/supported-document-formats/
[11]: https://blog.groupdocs.com/2021/02/19/generate-qr-codes-in-java-to-sign-documents-and-images/
[12]: https://docs.groupdocs.com/signature/net/
[13]: https://forum.groupdocs.com/c/signature
[14]: https://github.com/groupdocs-signature/GroupDocs.Signature-for-.NET


