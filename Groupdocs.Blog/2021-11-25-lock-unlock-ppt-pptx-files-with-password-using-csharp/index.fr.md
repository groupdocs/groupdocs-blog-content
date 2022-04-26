---
title: "Verrouiller et déverrouiller les fichiers PowerPoint avec un mot de passe à l'aide de C#"
date: Thu, 25 Nov 2021 15:48:29 +0000
draft: false
url: /fr/2021/11/25/lock-unlock-ppt-pptx-files-with-password-using-csharp/
author: 'Shoaib Khan'
summary: 'Today, we will provide password protection to our presentation files programmatically. In this article, we will see **how to lock **PowerPoint presentation files** with password protection in C#**. Further, we will learn to unlock these by **removing the password** and also **how to change the existing password** of PPT & PPTX presentation files.

Les sujets suivants sont abordés dans cet article :

* API .NET pour protéger PowerPoint PPT/PPTX avec mot de passe
* Verrouillez les fichiers PowerPoint en ajoutant un mot de passe
* Changer le mot de passe PPT/PPTX en C#
* Comment supprimer le mot de passe de la présentation PowerPoint'
tags: ['Add Password to PPT in CSharp', 'Change PPT Password in CSharp', 'Lock PPT in CSharp', 'Remove Password in CSharp', 'Unlock Files in CSharp']
categories: ['GroupDocs.Merger Product Family']
---

Aujourd'hui, nous fournirons une protection par mot de passe à nos fichiers de présentation par programmation. Auparavant, nous avons appris quelque chose de similaire en discutant de [la protection par mot de passe des fichiers PDF en C#][1]. Dans cet article, nous verrons **comment verrouiller les **fichiers de présentation PowerPoint** avec une protection par mot de passe en C#**. De plus, nous apprendrons à les déverrouiller en ** supprimant le mot de passe ** et aussi ** comment changer le mot de passe existant ** des fichiers de présentation PPT & PPTX.



{{< figure align=center src="images/password-protect-lock-unlock-presentations.jpg" alt="Présentations protégées par mot de passe - Verrouiller Déverrouiller PPT-PPTX">}}


Les sujets suivants sont abordés ci-dessous :

* [API .NET pour protéger PowerPoint PPT/PPTX avec un mot de passe][2]
* [Verrouiller les fichiers PowerPoint en ajoutant un mot de passe][3]
* [Modifier le mot de passe PPT/PPTX en C#][4]
* [Comment supprimer le mot de passe de la présentation PowerPoint][5]

## API .NET pour verrouiller et déverrouiller les fichiers PowerPoint {#lock-unlock-ppt-dotnet-api}

Pour travailler avec la protection des fichiers de présentation, nous utiliserons [GroupDocs.Merger pour .NET][6]. Cette API permet d'ajouter, de modifier et de supprimer des fonctionnalités de sécurité par mot de passe pour la présentation et d'autres documents dans les applications .NET. Outre le verrouillage et le déverrouillage des fichiers PPT, l'API fournit de nombreuses autres fonctionnalités, notamment la fusion et le fractionnement des présentations mentionnées dans la [documentation][7].

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][8] ou installer l'API dans votre application .NET via [NuGet][9].

```
PM> Install-Package GroupDocs.Merger
```

## Ajouter un mot de passe aux fichiers PowerPoint en C# - Verrouiller PPT/PPTX {#lock-ppt-by-password}



{{< figure align=center src="images/locked-PPT.jpg" alt="Verrouiller PPT avec un mot de passe">}}


Nous pouvons verrouiller par programmation n'importe quel fichier de présentation en y ajoutant une protection par mot de passe. Les étapes suivantes montrent comment ajouter un mot de passe à une présentation PowerPoint (PPT/PPTX) à l'aide de C#.

* Définissez le mot de passe à l'aide de [AddPasswordOptions][10].
* Chargez le fichier PowerPoint en utilisant la classe [Merger][11].
* Appliquez la protection en ajoutant un mot de passe à l'aide de la méthode [AddPassword][12].
* Enregistrez le fichier de présentation protégé à l'aide de la méthode [Enregistrer][13].

L'extrait de code C# suivant verrouille le PPT en ajoutant un mot de passe pour un accès limité.

```
/*
 * Add password protection to the presentation files (PPT/PPTX) in C#
 */
string filePath = @"path/presentation.pptx";

AddPasswordOptions addOptions = new AddPasswordOptions("mySECRETpassWORD");

using (Merger merger = new Merger(filePath))
{
    merger.AddPassword(addOptions);
    merger.Save(@"path/protected-presentation.pptx");
}
```

Voici la sortie du code ci-dessus. Lorsque vous essayez d'ouvrir le fichier, l'éditeur ou le visualiseur vous demandera le mot de passe pour ouvrir la présentation.



{{< figure align=center src="images/enter-pwd-to-protected-pptx-presentation.png" alt="Entrez le mot de passe pour le PPTX protégé">}}


## Mettre à jour le mot de passe existant des fichiers PPT/PPTX en C# {#change-ppt-password}

On dirait qu'il y a eu un aperçu de votre mot de passe. Changeons-le. Les étapes suivantes vous permettent de modifier le mot de passe du fichier de présentation existant à l'aide de C#.

* Préparez les [options de chargement][14] en utilisant le mot de passe actuel.
* Préparez les [options de mise à jour][15] en utilisant le nouveau mot de passe.
* Chargez la présentation en utilisant la classe [Merger][16].
* Modifiez le mot de passe à l'aide de la méthode [UpdatePassword][17].
* Appelez la méthode [Save][18] pour enregistrer le fichier verrouillé avec un nouveau mot de passe.

Voici l'extrait de code qui modifie le mot de passe existant d'une présentation PowerPoint PPT/PPTX.

```
/*
 * Update password of the protected presentation files (PPT/PPTX) in C#
 */
string filePath = @"path/protected-presentation.pptx";

LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");
UpdatePasswordOptions updateOptions = new UpdatePasswordOptions("TOPSECRET_pa22WORD");

using (Merger merger = new Merger(filePath, loadOptions))
{
    merger.UpdatePassword(updateOptions);
    merger.Save(@"path/pwd-changed-presentation.pptx");
}
```

## Supprimer le mot de passe du fichier PowerPoint en C# - Déverrouiller PPT/PPTX {#remove-password-to-unlock-ppt}



{{< figure align=center src="images/unlocked-PPT.jpg" alt="Déverrouiller PPT - Mot de passe supprimé">}}


Maintenant, retirons le couvercle et laissons tout le monde profiter de votre présentation. Commencez par ouvrir le fichier, puis supprimez son mot de passe pour un accès facile. Les étapes suivantes montrent comment déverrouiller le fichier PPT en supprimant son mot de passe à l'aide de C#.

* Utilisez le mot de passe du fichier pour préparer les [options de chargement][19].
* **Chargez** le document de présentation PowerPoint en utilisant la classe [Merger][20].
* **Supprimez** le mot de passe à l'aide de la méthode [RemovePassword][21].
* **Enregistrer** le fichier déverrouillé en utilisant la méthode [Save][22].

L'exemple de code C# suivant déverrouille le fichier de présentation PowerPoint en supprimant son mot de passe.

```
/*
 * Remove password protection of presentation files (PPT/PPTX) in C#
 */
string filePath = @"path/protected-presentation.pptx";

LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");

using (Merger merger = new Merger(filePath, loadOptions))
{
    merger.RemovePassword();
    merger.Save(@"path/no-pwd-presentation.pptx");
}
```

## Conclusion

Terminons par un aperçu de ce que nous avons appris aujourd'hui. Nous avons utilisé une simple présentation PowerPoint (PPTX) et d'abord, nous l'avons verrouillée simplement en ajoutant un mot de passe. Ensuite, nous avons changé le mot de passe existant du fichier de présentation. Enfin, nous avons appris comment supprimer le mot de passe des présentations PowerPoint.

Pour en savoir plus sur GroupDocs.Merger pour .NET, consultez la [documentation][23] et commencez à créer votre propre application pour verrouiller et déverrouiller les fichiers de présentation. Pour toute question, contactez-nous via le [forum][24].

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][25] pour utiliser l'API sans les limitations d'évaluation.

## Voir également

* [Verrouiller et déverrouiller les fichiers PDF avec mot de passe à l'aide de C #][26]
* [Convertir des présentations PPT, PPTX en PDF en C#][27]
* [Fichiers PDF en filigrane à l'aide de C #][28]
* [Comment diviser des fichiers PDF à l'aide de C #][29]



[1]: https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/
[2]: #lock-unlock-ppt-dotnet-api
[3]: #lock-ppt-by-password
[4]: #change-ppt-password
[5]: #remove-password-to-unlock-ppt
[6]: https://products.groupdocs.com/merger/net/
[7]: https://docs.groupdocs.com/merger/net/
[8]: https://downloads.groupdocs.com/merger
[9]: https://www.nuget.org/packages/groupdocs.merger
[10]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/addpasswordoptions
[11]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[12]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/addpassword
[13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/loadoptions
[15]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/updatepasswordoptions
[16]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[17]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/updatepassword
[18]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[19]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/loadoptions
[20]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[21]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/removepassword
[22]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[23]: https://docs.groupdocs.com/merger
[24]: https://forum.groupdocs.com/
[25]: https://purchase.groupdocs.com/temporary-license
[26]: https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/
[27]: https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/
[28]: https://blog.groupdocs.com/2021/07/27/watermark-pdf-files-using-csharp/
[29]: https://blog.groupdocs.com/2021/10/11/split-pdf-files-in-csharp/


