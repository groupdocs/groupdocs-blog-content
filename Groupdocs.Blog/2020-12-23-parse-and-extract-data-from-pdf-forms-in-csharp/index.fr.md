---
title: "Lire les champs de formulaire PDF à l'aide de C#"
date: Wed, 23 Dec 2020 12:39:01 +0000
draft: false
url: /fr/2020/12/23/analyser-et-extraire-les-donnees-des-formulaires-pdf-dans-csharp/
author: 'Shoaib Khan'
summary: "Dans cet article, nous allons apprendre **comment lire et analyser des documents PDF, puis extraire par programme les valeurs des champs de formulaire PDF en C#**. Plus tôt, nous avons vu [comment extraire des valeurs de formulaires PDF en Java][1]. Après avoir lu ces articles, si vous avez rempli des formulaires de commentaires, vous pouvez extraire les valeurs de vos applications .NET et Java pour les analyser ou les enregistrer dans la base de données."
tags: ['Extract Text from PDF Forms in CSharp', 'Parse PDF Forms in CSharp', 'Read PDF Form Fields in CSharp']
categories: ['GroupDocs.Parser Product Family']
---

Dans cet article, nous allons apprendre **comment lire et analyser des documents PDF, puis extraire par programme les valeurs des champs de formulaire PDF en C#**. Plus tôt, nous avons vu [comment extraire des valeurs de formulaires PDF en Java][2]. Après avoir lu ces articles, si vous avez rempli des formulaires de commentaires, vous pouvez extraire les valeurs de vos applications .NET et Java pour les analyser ou les enregistrer dans la base de données.



{{< figure align=center src="images/Extract-from-PDF-Form-in-csharp.jpeg" alt="Analyser des formulaires PDF pour extraire des valeurs en C#">}}


## API .NET pour analyser et extraire les valeurs des formulaires PDF

[GroupDocs.Parser for .NET][3] est une API d'analyse et d'extraction de données facile à utiliser et puissante pour les applications .NET. Il prend en charge l'extraction de texte, de métadonnées et d'images à partir de documents de traitement de texte et PDF, de feuilles de calcul, de présentations, d'e-mails, d'annotations, d'ebooks, d'archives et bien plus encore. L'une des fonctionnalités importantes et qui sera également présentée ci-dessous est l'analyse des formulaires PDF à remplir pour extraire les valeurs des champs du formulaire à l'aide d'un petit morceau de code C#.

Pour tester les exemples d'API mentionnés ci-dessous et d'autres, vous pouvez télécharger et installer l'API à partir de [NuGet][4] ou directement [télécharger][5] à partir des téléchargements GroupDocs.

```
PM> Install-Package GroupDocs.Parser
```

## Extraire des données d'un champ de formulaire PDF à l'aide de C#

Les étapes simples suivantes expliquent comment analyser un PDF, puis extraire des valeurs de champ de formulaire PDF en C#.

* Chargez le fichier PDF à l'aide de la classe [Parser][6].
* Analysez le formulaire PDF à l'aide de la méthode [ParseForm][7].
* Parcourez la collection analysée pour extraire les valeurs des champs de formulaire.

L'exemple de code C# suivant montre l'extraction des valeurs de champ des formulaires PDF remplis dans les applications .NET.

```
// Analyser le formulaire PDF rempli pour extraire les valeurs de champ en C #
using (Parser parser = new Parser("filePath/PDFForm.pdf"))
{
    // Extract data from PDF Form
    DocumentData data = parser.ParseForm();
    // Iterate over the extracted PDF Form fields data
    for (int i = 0; i < data.Count; i++)
    {
        Console.Write(data[i].Name + ": ");
        PageTextArea area = data[i].PageArea as PageTextArea;
        Console.WriteLine(area == null ? "Not a template field" : area.Text);
    }
}
```

```
COMPANY: GroupDocs
EMAIL: everything@groupdocs.com
COUNTRY: Australia
```

## Conclusion

Je suis convaincu que vous vous sentirez désormais à l'aise pour développer votre propre application basée sur .NET capable d'analyser des fichiers PDF et d'extraire rapidement et précisément des valeurs à partir de champs de formulaire PDF à remplir. Pour ajouter plus de fonctionnalités, vous pouvez en savoir plus sur l'API à partir des articles [documentation][8] et des exemples C# sur [GitHub][9].

Pour les questions et une réponse rapide, restez en contact sur le [forum][10].

## Voir également

* [Lire les champs de formulaire PDF en utilisant Java][11]
* [Extraire des images de documents en C#][12]







[1]: https://blog.groupdocs.com/2020/12/09/parse-and-extract-data-from-pdf-forms-in-java/
[2]: https://blog.groupdocs.com/2020/12/09/parse-and-extract-data-from-pdf-forms-in-java/
[3]: https://products.groupdocs.com/parser/net
[4]: https://www.nuget.org/packages/groupdocs.parser
[5]: https://downloads.groupdocs.com/parser/net
[6]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser
[7]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/parseform
[8]: https://docs.groupdocs.com/parser/net/
[9]: https://github.com/groupdocs-parser/GroupDocs.Parser-for-.NET
[10]: https://forum.groupdocs.com/c/parser
[11]: https://blog.groupdocs.com/2020/12/09/parse-and-extract-data-from-pdf-forms-in-java/
[12]: https://blog.groupdocs.com/2020/10/28/extract-images-from-pdf-word-excel-ppt-using-csharp/


