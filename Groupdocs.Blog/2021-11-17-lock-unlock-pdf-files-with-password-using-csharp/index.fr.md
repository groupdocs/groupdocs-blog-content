---
title: "Verrouiller et déverrouiller des fichiers PDF avec un mot de passe à l'aide de C#"
date: Wed, 17 Nov 2021 12:28:00 +0000
draft: false
url: /fr/2021/11/17/verrouiller-déverrouiller-les-fichiers-pdf-avec-mot-de-passe-en-utilisant-csharp/
aliases:
- /2021/11/17/password-protection-to-pdf-files-in-csharp/
- /2019/09/25/add-password-protection-to-word-or-pdf-files-in-csharp/
- /2019/09/25/add-password-protection-to-word-or-pdf-files-in-c/
author: 'Shoaib Khan'
summary: 'Let us learn to secure our documents from unauthorized access. Previously we discussed [adding text and image watermarks to the documents][1] to avoid and illegal use. In this article, we will see **how to add password protection to PDF documents to get them locked using C#**. Additionally, we will **change the existing password** and also learn to **remove the password** to make the PDF unlocked.

Les sujets suivants sont abordés dans cet article :

* API .NET pour la protection par mot de passe des fichiers PDF
* Verrouillez les fichiers PDF en ajoutant un mot de passe
* Changer le mot de passe PDF en C #
* Comment supprimer le mot de passe PDF - Déverrouiller PDF'
tags: ['add password to PDF in csharp', 'Change PDF Password in CSharp', 'Lock PDF in CSharp', 'Remove PDF Password in CSharp', 'Unlock PDF in CSharp']
categories: ['GroupDocs.Merger Product Family']
---

Apprenons à sécuriser nos documents contre tout accès non autorisé. Auparavant, nous avons discuté [d'ajouter des filigranes de texte et d'image aux documents][2] pour éviter toute utilisation illégale. Dans cet article, nous verrons **comment ajouter une protection par mot de passe aux documents PDF pour les verrouiller à l'aide de C#**. De plus, nous allons **changer le mot de passe existant** et également apprendre à **supprimer le mot de passe** pour déverrouiller le PDF.



{{< figure align=center src="images/password-protect-lock-unlock-pdf.jpg" alt="Protéger les fichiers PDF par programme avec un mot de passe - Verrouiller Déverrouiller">}}


Les sujets suivants sont abordés ci-dessous :

* [API .NET pour la protection par mot de passe des fichiers PDF][3]
* [Verrouiller les fichiers PDF en ajoutant un mot de passe][4]
* [Modifier le mot de passe PDF en C #][5]
* [Comment supprimer le mot de passe PDF - Déverrouiller PDF][6]

## API .NET pour verrouiller et déverrouiller les fichiers PDF {#lock-unlock-pdf-dotnet-api}

Pour verrouiller et déverrouiller des documents, nous utiliserons [GroupDocs.Merger pour .NET][7]. Cette API permet d'ajouter, de modifier et de supprimer des fonctionnalités de sécurité par mot de passe pour les documents dans les applications .NET. Outre la protection et la déprotection des documents PDF, l'API fournit de nombreuses autres fonctionnalités telles que la fusion et le fractionnement qui sont mentionnées dans la [documentation][8].

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][9] ou installer l'API dans votre application .NET via [NuGet][10].

```
PM> Install-Package GroupDocs.Merger
```

## Ajouter un mot de passe au PDF en C# - Verrouiller le PDF {#lock-pdf-by-password}



{{< figure align=center src="images/locked-PDF.jpg" alt="Verrouiller le PDF avec un mot de passe">}}


Commençons par ajouter une protection au fichier en le verrouillant avec le mot de passe. Les étapes suivantes montrent comment ajouter une sécurité par mot de passe aux documents PDF à l'aide de C#.

* Définissez le mot de passe à l'aide de la classe [AddPasswordOptions][11].
* Chargez le fichier PDF en utilisant la classe [Merger][12].
* Verrouillez le fichier en ajoutant un mot de passe à l'aide de la méthode [AddPassword][13].
* Enregistrez le fichier protégé à l'aide de la méthode [Save][14].

Le code C# suivant ajoute le mot de passe au fichier PDF pour des raisons de sécurité.

```
/*
 * Add password protection to the PDF document using C#
 */
string filePath = @"path/document.pdf";

AddPasswordOptions addOptions = new AddPasswordOptions("mySECRETpassWORD");

using (Merger merger = new Merger(filePath))
{
    merger.AddPassword(addOptions);
    merger.Save(@"path/protected-document.pdf");
}
```

Voici la sortie du code ci-dessus. Lorsque vous essayez d'ouvrir le fichier PDF, l'éditeur ou le visualiseur vous demandera le mot de passe pour prouver votre autorité.



{{< figure align=center src="images/enter-pwd-to-protected-pdf-1024x298.png" alt="Entrez le mot de passe pour le PDF protégé">}}


## Mettre à jour le mot de passe existant des fichiers PDF en C # {#change-pdf-password}

Oups! votre mot de passe est probablement exposé. Changeons-le rapidement par programmation avec le nouveau et difficile. Les étapes suivantes vous permettent de modifier le mot de passe actuel de vos fichiers PDF dans votre application .NET en C#.

* Préparez les [options de chargement][15] en utilisant le mot de passe actuel.
* Préparez les [options de mise à jour][16] en utilisant le nouveau mot de passe.
* Chargez le document PDF à l'aide de la classe [Merger][17] et des options de chargement.
* Modifiez le mot de passe existant à l'aide de la méthode [UpdatePassword][18].
* Enregistrez le fichier verrouillé ayant changé de mot de passe en utilisant la méthode [Save][19].

Voici l'extrait de code qui change le mot de passe actuel du document PDF.

```
/*
 * Update password of the protected PDF document using C#
 */
string filePath = @"path/protected-document.pdf";

LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");
UpdatePasswordOptions updateOptions = new UpdatePasswordOptions("TOPSECRET_pa22WORD");

using (Merger merger = new Merger(filePath, loadOptions))
{
    merger.UpdatePassword(updateOptions);
    merger.Save(@"path/pwd-changed-document.pdf");
}
```

## Supprimer le mot de passe des fichiers PDF en C # - Déverrouiller PDF {#remove-password-to-unlock-pdf}



{{< figure align=center src="images/unlocked-PDF.jpg" alt="PDF déverrouillé - Mot de passe supprimé">}}


Maintenant, je pense que vous n'avez pas besoin de sécurité, c'est pourquoi vous voulez supprimer le mot de passe. Ouvrons d'abord le fichier, puis supprimons son mot de passe afin que tout le monde puisse y accéder facilement. Les étapes suivantes montrent comment déverrouiller le fichier PDF en supprimant son mot de passe à l'aide de C#.

* Préparez les [options de chargement][20] en utilisant le mot de passe du fichier.
* Chargez le document PDF à l'aide de la classe [Merger][21] et des options de chargement.
* Supprimez le mot de passe existant à l'aide de la méthode [RemovePassword][22].
* Enregistrez le fichier déverrouillé en utilisant la méthode [Save][23].

L'extrait de code C# suivant déverrouille le fichier PDF en supprimant son mot de passe existant, ainsi n'importe qui peut y accéder sans autorisation.

```
/*
 * Remove password protection of PDF document using C#
 */
string filePath = @"path/protected-document.pdf";

LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");

using (Merger merger = new Merger(filePath, loadOptions))
{
    merger.RemovePassword();
    merger.Save(@"path/no-pwd-document.pdf");
}
```

## Conclusion

Résumons ce que nous avons appris aujourd'hui. Nous avons commencé avec le simple document PDF et avons ajouté une protection par mot de passe. Ensuite, nous avons changé le mot de passe existant de ce fichier PDF. Au final, nous avons appris à supprimer le mot de passe de nos documents PDF. Vous pouvez maintenant créer votre propre application de protection de mot de passe ou de suppression de mot de passe à l'aide de l'API .NET.

Pour en savoir plus sur GroupDocs.Merger pour .NET, consultez la [documentation][24]. Pour toute question, contactez-nous via le [forum][25].

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][26] pour utiliser l'API sans les limitations d'évaluation.

## Voir également

* [Fichiers PDF en filigrane avec C#][27]
* [Comment diviser des fichiers PDF à l'aide de C #][28]
* [Ajouter ou supprimer la protection par mot de passe des fichiers PDF en Java][29]







[1]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[2]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[3]: #lock-unlock-pdf-dotnet-api
[4]: #lock-pdf-by-password
[5]: #change-pdf-password
[6]: #remove-password-to-unlock-pdf
[7]: https://products.groupdocs.com/merger/net/
[8]: https://docs.groupdocs.com/merger/net/
[9]: https://downloads.groupdocs.com/merger
[10]: https://www.nuget.org/packages/groupdocs.merger
[11]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/addpasswordoptions
[12]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/addpassword
[14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[15]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/loadoptions
[16]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/updatepasswordoptions
[17]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[18]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/updatepassword
[19]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[20]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/loadoptions
[21]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[22]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/removepassword
[23]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[24]: https://docs.groupdocs.com/merger
[25]: https://forum.groupdocs.com/
[26]: https://purchase.groupdocs.com/temporary-license
[27]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[28]: https://blog.groupdocs.com/2021/10/11/split-pdf-files-in-csharp/
[29]: https://blog.groupdocs.com/2021/12/07/password-protect-pdf-files-in-java/


