---
title: "Signer des documents avec un certificat numérique à l'aide de C#"
date: Thu, 11 Mar 2021 07:36:00 +0000
draft: false
url: /fr/2021/03/11/sign-documents-with-digital-certificate-using-csharp/
author: 'Shoaib Khan'
summary: "La **signature numérique** est un système fiable de vérification de l'authenticité de vos documents. Les signatures numériques sont souvent utilisées pour mettre en œuvre des signatures électroniques. Dans cet article, vous apprendrez à signer électroniquement des documents PDF et Word avec des certificats numériques à l'aide de C#."
tags: ['Digital Certificate in CSharp', 'Digital Signature in CSharp', 'Sign PDF in CSharp', 'Sign with Digital Certificate in CSharp', 'Sign Word in CSharp']
categories: ['GroupDocs.Signature Product Family']
---

La **signature numérique** est un système fiable de vérification de l'authenticité de vos documents. Les signatures numériques sont souvent utilisées pour mettre en œuvre des signatures électroniques. Dans cet article, vous apprendrez à signer électroniquement des documents PDF et Word avec des certificats numériques à l'aide de C#.

## API .NET pour les signatures numériques et les certificats

Pour signer des documents avec le certificat numérique, j'utiliserai l'API [GroupDocs.Signature pour .NET][2] dans les exemples C# de cet article. Outre la signature de documents PDF, cette API prend en charge les signatures numériques pour les documents de traitement de texte et les formats de feuille de calcul.

Téléchargez les DLL ou le programme d'installation MSI à partir de la [section des téléchargements][3] ou installez l'API dans votre application .NET via [NuGet][4].

```
PM> Install-Package GroupDocs.Signature
```

## Signer un PDF avec un certificat numérique en C#

Après la mise en place de l'environnement, vous êtes à quelques lignes de la signature réussie de vos documents. Suivez les étapes suivantes pour faire signer votre document avec le certificat numérique disponible à l'aide de C#.

* Initialiser l'objet [Signature][5] avec le document à signer.
* Initialiser l'objet [DigitalSignOptions][6] avec le fichier de certificat.
* Définissez les options de signe requises telles que le mot de passe et la position.
* Appelez la méthode [Sign][7] pour signer le document avec le certificat numérique.

L'exemple de code suivant signe les documents PDF avec le certificat en C#.

```
// Signer un PDF avec un certificat numérique en C#
using (Signature signature = new Signature("document.pdf"))
{
    DigitalSignOptions options = new DigitalSignOptions("certificate.pfx");
    {
        ImageFilePath = "sampleImage.jpg", // Optional - Set image file path
        Left = 50,                    // Set signature position
        Top = 50,
        Password = "GroupDocs"       // Set Password
    };
    signature.Sign("signedDocument.pdf", options);
}
```

## Signer avec une signature numérique à l'aide d'une apparence personnalisée en C#

La signature numérique peut être personnalisée pour avoir différentes présentations. Pour l'apparence personnalisée, les options suivantes peuvent être personnalisées à l'aide de la classe [PdfDigitalSignatureAppearance][8].

* Arrière-plan
* Informations de contact
* Date de signature à
* Signé numériquement
* Emplacement
* Raison
* Famille de polices
* Taille de police

De plus, vous pouvez modifier les propriétés suivantes :

* Hauteur
* Largeur
* Style de bordure
* Afficher sur **Toutes les pages** ou **Non**



{{< figure align=center src="images/programmatically-sign-pdf-with-digital-certificate.jpg" alt="Signer un PDF avec un certificat numérique" caption="<em>Document PDF signé avec certificat numérique à l'aide de GroupDocs.Signature pour .NET en C#</em>">}}


Dans l'exemple suivant, j'utilise presque toutes les propriétés mentionnées ci-dessus. Cet exemple personnalise l'apparence de la signature numérique dans un document PDF à l'aide de C#.

```
// Signer un PDF avec un certificat numérique en C# avec une apparence et des paramètres personnalisés
using (Signature signature = new Signature("document.pdf"))
{
    DigitalSignOptions options = new DigitalSignOptions("certificate.pfx")
    {
        Password = "GroupDocs",
        // digital certificate details
        Reason = "Approved",
        Location = "New York",

        // Custom PDF signature appearance
        Appearance = new PdfDigitalSignatureAppearance()
        {
            // Do not show contact details
            ContactInfoLabel = string.Empty,
            // Simplify Reason Label
            ReasonLabel = "?",
            // Change Location Label
            LocationLabel = "From",
            DigitalSignedLabel = "By",
            DateSignedAtLabel = "On",
            Background = Color.Red
        },
        AllPages = true,
        Width = 160,
        Height = 80,
        // Set signature border
        Border = new Border()
        {
            Visible = true,
            Color = Color.Red,
            DashStyle = DashStyle.DashDot,
            Weight = 2
        }
    };
    SignResult signResult = signature.Sign("signedDocument.pdf", options);
}
```

## Signer des documents Word avec un certificat numérique en C#

De même, vous pouvez signer des documents Word à l'aide du certificat. Fournissez simplement le bon document lorsque vous commencez à initialiser l'objet Signature.

* Initialiser l'objet [Signature][9] avec le document Word à signer.
* Initialiser l'objet [DigitalSignOptions][10] avec le fichier de certificat.
* Définissez les options de signe telles que le mot de passe et la position.
* Signez le document avec le certificat numérique en utilisant la méthode [Sign][11].

L'exemple signe les documents Word à l'aide du certificat en C#.

```
// Signer un document Word avec un certificat numérique en C#
using (Signature signature = new Signature("document.docx"))
{
    DigitalSignOptions options = new DigitalSignOptions("certificate.pfx");
    {
        ImageFilePath = "sampleImage.jpg", // Optional - Set image file path
        Left = 50,                    // Set signature position
        Top = 50,
        Password = "GroupDocs"       // Set Password
    };
    signature.Sign("signedDocument.docx", options);
}
```

## Conclusion

Dans cet article, vous avez appris à signer électroniquement des documents PDF et Word avec le certificat numérique à l'aide de C#. De plus, vous pouvez facilement personnaliser l'apparence de la signature. Vous pouvez maintenant essayer de créer votre propre application .NET pour signer des documents PDF et Word avec des certificats numériques ayant une apparence personnalisée en C#.

## Liens rapides pour en savoir plus sur l'API Signature

* Exemples sur [GitHub][12]
* [Guide du développeur et documentation][13]
* [Forum][14] pour une assistance rapide

## Voir également

* [Vérifier la signature numérique dans les documents à l'aide de C#][15]
* [Vérifier la signature numérique dans les documents à l'aide de Java][16]







[1]: https://blog.groupdocs.com/2021/03/11/sign-documents-with-digital-certificate-using-csharp/
[2]: https://products.groupdocs.com/signature/net
[3]: https://downloads.groupdocs.com/signature/net
[4]: https://www.nuget.org/packages/groupdocs.signature
[5]: https://apireference.groupdocs.com/net/signature/groupdocs.signature/signature
[6]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.options/digitalsignoptions
[7]: https://apireference.groupdocs.com/signature/net/groupdocs.signature/signature/methods/sign/index
[8]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.options.appearances/pdfdigitalsignatureappearance
[9]: https://apireference.groupdocs.com/net/signature/groupdocs.signature/signature
[10]: https://apireference.groupdocs.com/signature/net/groupdocs.signature.options/digitalsignoptions
[11]: https://apireference.groupdocs.com/signature/net/groupdocs.signature/signature/methods/sign/index
[12]: https://github.com/groupdocs-signature/GroupDocs.Signature-for-.NET
[13]: https://docs.groupdocs.com/signature/net
[14]: https://forum.groupdocs.com/c/signature
[15]: https://blog.groupdocs.com/2019/09/25/verify-digital-signature-in-documents-using-csharp/
[16]: https://blog.groupdocs.com/2020/10/06/verify-digital-signature-in-documents-using-java/


