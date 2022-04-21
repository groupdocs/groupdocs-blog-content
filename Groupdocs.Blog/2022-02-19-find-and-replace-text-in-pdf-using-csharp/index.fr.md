---
title: "Rechercher et remplacer du texte dans un PDF à l'aide de C#"
date: Sat, 19 Feb 2022 04:42:16 +0000
draft: false
url: /fr/2022/02/19/trouver-et-remplacer-texte-dans-pdf-en-utilisant-csharp/
author: 'Shoaib Khan'
summary: "Les modèles sont largement utilisés pour générer des documents personnalisés. Cet article explique **comment rechercher et remplacer du texte et des mots dans des documents PDF à l'aide de C#**. Nous discuterons séparément de la manière de remplacer par programmation des mots et des phrases, de remplacer des mots par une recherche sensible à la casse, de remplacer à l'aide d'expressions régulières. Enfin, nous apprendrons également à masquer la chaîne recherchée à l'aide de C#."
tags: ['Blackout Text in PDF', 'Find &amp; Replace Text in PDF', 'Find Text in PDF', 'Hide Text in PDF', 'Redact PDF files']
categories: ['GroupDocs.Redaction Product Family']
---

Les modèles sont largement utilisés pour générer des documents personnalisés. Cet article explique **comment rechercher et remplacer du texte et des mots dans des documents PDF à l'aide de C#**. Nous discuterons séparément de la manière de remplacer par programmation des mots et des phrases, de remplacer des mots par une recherche sensible à la casse, de remplacer à l'aide d'expressions régulières. Enfin, nous apprendrons également à masquer la chaîne recherchée à l'aide de C#.

Les sujets suivants seront abordés ci-dessous :

* [API .NET pour remplacer le texte](#dotnet-redaction-api)
* [Rechercher et remplacer des mots ou une expression](#replace-word-or-phrase)
* [Recherche et remplacement de mots sensibles à la casse](#case-sensitive-text-redaction)
* [Remplacer par des expressions régulières (RegEx)](#replace-text-using-regex)
* [Masquer le texte avec une boîte de couleur](#hide-text-with-colored-box)

## API de rédaction .NET pour le remplacement de texte {#dotnet-redaction-api}

GroupDocs présente GroupDocs.Redaction pour .NET, l'API permettant de biffer, masquer ou supprimer le contenu et même les métadonnées des documents, présentations, feuilles de calcul, fichiers PDF et images dans l'application .NET. Pour plus de détails sur l'API, consultez sa documentation.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements](https://downloads.groupdocs.com/redaction) ou installer l'API dans votre application .NET via [NuGet](https://www.nuget.org/packages/groupdocs.redaction).

```
PM> Install-Package GroupDocs.Redaction
```

Pas besoin d'installer un éditeur de PDF ou tout autre logiciel tiers pour la rédaction. Voici la capture d'écran d'un document PDF utilisé dans les exemples ci-dessous. La même approche fonctionnera pour d'autres formats de document avec très peu ou pas de changement dans le code.



{{< figure align=center src="images/original-doc.png" alt="">}}


## Rechercher et remplacer un mot ou une phrase dans un PDF à l'aide de C# {#replace-word-or-phrase}

Vous pouvez utiliser cette fonctionnalité pour masquer toutes les données confidentielles et également pour créer un nouveau document personnalisé à partir du modèle. L'étape suivante explique comment rechercher un mot/une phrase dans un document PDF avec un autre texte dans l'application C#.

* **Chargez** le fichier PDF à l'aide de la classe [Redactor](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor).
* **Trouvez la phrase ou le mot exact**, en utilisant [ExactPhraseRedaction](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/exactphraseredaction) et [ReplacementOptions](https://apireference .groupdocs.com/redaction/net/groupdocs.redaction.redactions/replacementoptions).
* **Appliquez la rédaction** en utilisant la méthode [Apply()](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/apply/index).
* **Enregistrer** le nouveau document avec les modifications à l'aide de la méthode [Save()](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/save/index).

Le code suivant recherche et remplace le mot en C#. Plus précisément, il cache toutes les occurrences de "John Doe" en le remplaçant par le mot "\[censored\]".

```
// Trouvez la phrase exacte et remplacez-la par un autre texte en utilisant C#
using (Redactor redactor = new Redactor(@"path/document.pdf"))
{
  redactor.Apply(new ExactPhraseRedaction("John Doe", new ReplacementOptions("[censored]")));
  redactor.Save(new SaveOptions() { AddSuffix = true, RasterizeToPDF = false });
}
```

La sortie du code est la suivante.



{{< figure align=center src="images/Exact-Phrase-Replacement.png" alt="">}}


## Rechercher et remplacer du texte ou une phrase sensible à la casse dans un PDF à l'aide de C# {#case-sensitive-text-redaction}

Vous pouvez effectuer la recherche et la rédaction sensibles à la casse. Le code suivant remplace l'existence sensible à la casse du mot "John Doe" mais pas "john doe" en C#.

```
// Trouvez la phrase exacte (sensible à la casse) et remplacez-la par un autre texte en utilisant C#
using (Redactor redactor = new Redactor(@"path/document.pdf"))
{
  redactor.Apply(new ExactPhraseRedaction("John Doe", true /*isCaseSensitive*/, new ReplacementOptions("[censored]")));
  redactor.Save(new SaveOptions() { AddSuffix = true, RasterizeToPDF = false });
}
```

La sortie du code est la suivante.



{{< figure align=center src="images/Case-Sensitive-Exact-Phrase-Redaction.png" alt="">}}


## Remplacer le texte d'un PDF par des expressions régulières (RegEx) à l'aide de C# {#replace-text-using-regex}

Vous pouvez également remplacer n'importe quel modèle de texte spécifique à l'aide d'expressions régulières. Les étapes suivantes vous permettent de biffer le PDF après la recherche à l'aide d'une expression régulière (RegEx) dans votre application .NET.

* **Chargez** le document PDF à l'aide de la classe [Redactor](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor).
* **Trouvez la correspondance de regex** en utilisant la classe [RegexRedaction](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/regexredaction) avec [ReplacementOptions](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/replacementoptions).
* Introduisez les modifications dans le document à l'aide de la méthode [Apply()](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/apply/index).
* **Enregistrer** le document expurgé en utilisant la méthode [Save()](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/save/index) appropriée.

Le code suivant montre comment rechercher un certain modèle de texte dans un document PDF à l'aide de RegEx, puis le remplacer/masquer ultérieurement par un autre texte à l'aide de C#.

```
// Rechercher du texte à l'aide d'une expression régulière et le remplacer par un autre texte à l'aide de C#
using (Redactor redactor = new Redactor(@"path/document.pdf"))
{
  redactor.Apply(new RegexRedaction("\\d{2}\\s*\\d{2}[^\\d]*\\d{6}", new ReplacementOptions("[censored]")));
  redactor.Save(new SaveOptions() { AddSuffix = true, RasterizeToPDF = false });
}
```

La sortie du code ci-dessus est la suivante.



{{< figure align=center src="images/Regex-Redaction.png" alt="">}}


## Remplacer le texte par une boîte colorée en C# {#hide-text-with-colored-box}

Si vous souhaitez simplement masquer le contenu recherché (informations privées) de votre fichier PDF, vous pouvez simplement y mettre une couverture. L'API vous permet de masquer le texte recherché. Le code C# suivant place le rectangle noir sur le texte privé mentionné.

```
// Recherchez du texte dans un PDF et masquez-le en dessinant un rectangle dessus à l'aide de C#
using (Redactor redactor = new Redactor(@"path/document.pdf"))
{
  redactor.Apply(new ExactPhraseRedaction("John Doe", new ReplacementOptions(System.Drawing.Color.Black)));
  redactor.Save(new SaveOptions() { AddSuffix = true, RasterizeToPDF = false });
}
```

La sortie du code ci-dessus est la suivante.



{{< figure align=center src="images/Colored-Box-Redaction.png" alt="">}}


## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons appris à trouver certains textes dans des fichiers PDF en utilisant différentes techniques de recherche. Plus tard, nous avons expliqué comment expurger des fichiers PDF en remplaçant ou en masquant le texte dans l'application .NET à l'aide de C#. Plus précisément, nous avons simplement recherché les mots, les phrases, la recherche avec sensibilité à la casse et en utilisant des expressions régulières en C#. Enfin, nous avons remplacé les résultats de la recherche par un autre texte ou en le masquant avec un rectangle au-dessus.

Pour plus de détails sur l'API, consultez la [documentation](https://docs.groupdocs.com/redaction). Pour toute question, contactez-nous via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Masquer les documents PDF numérisés en C#](https://blog.groupdocs.com/2021/09/25/redact-text-and-scanned-images-using-csharp/)
* [Rechercher des synonymes dans plusieurs fichiers à l'aide de C#](https://blog.groupdocs.com/2021/09/17/find-synonyms-in-multiple-files-using-csharp/)
* [Créez votre solution de recherche de texte intégral en C#](https://blog.groupdocs.com/2021/06/03/build-your-full-text-search-solution-in-csharp/)





