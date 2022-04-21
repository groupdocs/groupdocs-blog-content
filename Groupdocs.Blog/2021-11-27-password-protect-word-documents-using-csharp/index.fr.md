---
title: "Comment protéger par mot de passe et supprimer la protection des documents Word à l'aide de C #"
date: Sat, 27 Nov 2021 04:30:16 +0000
draft: false
url: /fr/2021/11/27/password-protect-word-documents-using-csharp/
author: 'Shoaib Khan'
summary: "Voyons comment nous pouvons restreindre l'accès aux documents Word en les protégeant par mot de passe. Nous avons déjà appris à verrouiller et déverrouiller les fichiers PDF et PowerPoint. Dans cet article, nous verrons **comment protéger par mot de passe un document Word en utilisant C#**. De plus, nous apprendrons à **supprimer le mot de passe pour déverrouiller les documents Word**, et enfin, **comment changer le mot de passe existant des fichiers DOC et DOCX** dans les applications .NET."
tags: ['add password in csharp', 'Change Doc Password in C#', 'Lock Files in CSharp', 'Lock Word Files in CSharp', 'Remove Password in CSharp', 'Unlock Files in CSharp']
categories: ['GroupDocs.Merger Product Family']
---

Voyons comment nous pouvons restreindre l'accès aux documents Word en les protégeant par mot de passe. Nous avons déjà appris à [verrouiller et déverrouiller les fichiers PDF][1] et [PowerPoint][2]. Dans cet article, nous verrons **comment protéger par mot de passe un document Word en utilisant C#**. De plus, nous apprendrons à **supprimer le mot de passe pour déverrouiller les documents Word**, et enfin, **comment changer le mot de passe existant des fichiers DOC et DOCX** dans les applications .NET.



{{< figure align=center src="images/lock-unlock-word-documents-in-dotnet.jpg" alt="Mot de passe Protéger les documents Word à l'aide de C#">}}


Les sujets suivants sont abordés ci-dessous :

* [API .NET pour protéger par mot de passe les documents Word][3]
* [Ajouter un mot de passe au document Word][4]
* [Modifier le mot de passe du document Word][5]
* [Comment supprimer le mot de passe d'un document Word][6]

## API .NET pour protéger par mot de passe les documents Word {#dotnet-api-lock-unlock-documents}

[GroupDocs.Merger][7] fournit l'API .NET qui permet de verrouiller et de déverrouiller des documents Word dans les applications .NET. Nous utiliserons [GroupDocs.Merger pour .NET][8] pour ajouter, modifier et supprimer la protection par mot de passe. Outre la protection et la déprotection des documents Word, vous pouvez faire bien plus avec les documents Word à l'aide de l'API. [Documentation][9] est disponible qui explique les fonctionnalités détaillées, les formats de fichiers pris en charge et bien plus encore.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][10] ou installer l'API dans votre application .NET via [NuGet][11].

```
PM> Install-Package GroupDocs.Merger
```

## Mot de passe protéger le document Word en C# {#password-protect-document}

{{< figure align=center src="images/locked-doc.jpg" alt="Doc Word verrouillé par programme">}}


Voyons comment ajouter un mot de passe aux documents Word et les protéger par mot de passe. Les étapes suivantes montrent comment verrouiller un document Word (DOC/DOCX) avec un mot de passe à l'aide de C#.

* Définissez les options de mot de passe à l'aide de [AddPasswordOptions][12].
* **Chargez** le document en utilisant la classe [Merger][13].
* **Ajoutez** le mot de passe pour verrouiller le document Word chargé à l'aide de la méthode [AddPassword][14].
* **Enregistrer** le fichier protégé par mot de passe en utilisant la méthode [Save][15].

L'extrait de code suivant montre comment protéger par mot de passe un document Word à l'aide de C#.

```
/*
 * Password Protect Word Documents using C#
 */
string filePath = @"path/document.docx";

AddPasswordOptions addOptions = new AddPasswordOptions("mySECRETpassWORD");

using (Merger merger = new Merger(filePath))
{
    merger.AddPassword(addOptions);
    merger.Save(@"path/protected-document.docx");
}
```

Désormais, lorsque vous essayez d'ouvrir le document protégé par mot de passe, la visionneuse et l'éditeur de documents vous demanderont le mot de passe pour ouvrir le fichier.



{{< figure align=center src="images/enter-pwd-to-open-protected-word-doc.jpg" alt="Entrez le mot de passe pour ouvrir le document Word protégé">}}


## Modifier le mot de passe existant du document Word en C# {#change-password}

Votre ancien mot de passe était peut-être trop commun pour avoir été deviné. Changeons-le et soyons plus prudents la prochaine fois. Les étapes suivantes expliquent comment modifier le mot de passe existant du document Word à l'aide de C#.

* Préparez les [LoadOptions][16] en utilisant le mot de passe actuel.
* Définissez les [UpdatePasswordOptions][17] en utilisant le nouveau mot de passe.
* **Chargez** le fichier DOC/DOCX en utilisant la classe [Merger][18].
* **Changez** le mot de passe en utilisant la méthode [UpdatePassword][19].
* **Enregistrer** le document protégé avec un nouveau mot de passe en utilisant la méthode [Enregistrer][20].

Voici l'extrait de code C# qui modifie le mot de passe existant d'un fichier DOCX.

```
/*
 * Change password of the protected DOC/DOCX documents in C#
 */
string filePath = @"path/protected-document.docx";

LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");
UpdatePasswordOptions updateOptions = new UpdatePasswordOptions("TOPSECRET_pa22WORD");

using (Merger merger = new Merger(filePath, loadOptions))
{
    merger.UpdatePassword(updateOptions);
    merger.Save(@"path/pwd-changed-document.docx");
}
```

## Supprimer le mot de passe du document Word en C # {#remove-password-to-unlock}



{{< figure align=center src="images/unlocked-DOC.jpg" alt="Document Word déverrouillé par programmation">}}


Enlevons maintenant la protection des documents qui ne sont plus confidentiels. Commencez par ouvrir le document Word, puis supprimez le mot de passe pour le déverrouiller. Les étapes suivantes montrent comment déverrouiller le document Word en supprimant le mot de passe à l'aide de C#.

* Utilisez le mot de passe existant du document pour préparer [LoadOptions][21].
* **Chargez** le document Word en utilisant la classe [Merger][22].
* **Supprimer** son mot de passe en utilisant la méthode [RemovePassword][23].
* **Enregistrer** le fichier déverrouillé au format DOC/DOCX en appelant la méthode [Save][24].

L'exemple de code suivant déverrouille le document Word au format DOCX en supprimant son mot de passe à l'aide de C#

```
/*
 * Remove password from Word document using C#
 */
string filePath = @"path/protected-document.docx";

LoadOptions loadOptions = new LoadOptions("mySECRETpassWORD");

using (Merger merger = new Merger(filePath, loadOptions))
{
    merger.RemovePassword();
    merger.Save(@"path/no-pwd-document.docx");
}
```

## Conclusion

Résumons ce que nous avons appris aujourd'hui. À l'aide d'un simple document Word, nous l'avons d'abord protégé par un mot de passe à l'aide de C#. Ensuite, nous avons appris à changer le mot de passe existant d'un document Word. Enfin, nous avons appris à supprimer le mot de passe du fichier Word pour le déverrouiller dans n'importe quelle application .NET.

Pour en savoir plus sur **GroupDocs.Merger pour .NET**, consultez sa [documentation][25] pour commencer à créer vos propres applications de protection de document ou de suppression de mot de passe pour divers [formats de document pris en charge][26]. Pour toute question, contactez-nous via le [forum][27].

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][28] pour utiliser l'API sans les limitations d'évaluation.

## Voir également

* [Ajouter et supprimer la protection par mot de passe des fichiers PDF][29]
* [Protéger et déprotéger les fichiers PowerPoint][30]
* [Afficher les documents Word en tant que page HTML réactive][31]
* [Fusionner des fichiers Word, PDF, Excel, PowerPoint][32]
* [Insérer des objets OLE dans des fichiers Word, Excel, PowerPoint][33]







[1]: https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/
[2]: https://blog.groupdocs.com/2021/11/25/lock-unlock-ppt-pptx-files-with-password-using-csharp/
[3]: #dotnet-api-lock-unlock-documents
[4]: #password-protect-document
[5]: #change-password
[6]: #remove-password-to-unlock
[7]: https://products.groupdocs.com/merger/
[8]: https://products.groupdocs.com/merger/net/
[9]: https://docs.groupdocs.com/merger/net/
[10]: https://downloads.groupdocs.com/merger
[11]: https://www.nuget.org/packages/groupdocs.merger
[12]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/addpasswordoptions
[13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/addpassword
[15]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[16]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/loadoptions
[17]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/updatepasswordoptions
[18]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[19]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/updatepassword
[20]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[21]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/loadoptions
[22]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[23]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/removepassword
[24]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[25]: https://docs.groupdocs.com/merger
[26]: https://docs.groupdocs.com/merger/net/supported-document-formats/
[27]: https://forum.groupdocs.com/
[28]: https://purchase.groupdocs.com/temporary-license
[29]: https://blog.groupdocs.com/2021/11/17/lock-unlock-pdf-files-with-password-using-csharp/
[30]: https://blog.groupdocs.com/2021/11/25/lock-unlock-ppt-pptx-files-with-password-using-csharp/
[31]: https://blog.groupdocs.com/2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/
[32]: https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/
[33]: https://blog.groupdocs.com/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/


