---
title: "Rechercher et remplacer des mots dans des documents Word à l'aide de C#"
date: Tue, 15 Feb 2022 10:41:00 +0000
draft: false
url: /fr/2022/02/15/trouver-et-remplacer-du-texte-dans-un-mot-en-utilisant-csharp/
author: 'Shoaib Khan'
summary: "Il peut y avoir de nombreuses raisons de remplacer un mot ou une phrase dans le document. Que vous souhaitiez effacer le contenu sensible avant de partager publiquement le document ou que vous souhaitiez masquer/supprimer toutes les informations privées telles que les identifiants de messagerie ou les numéros de sécurité sociale, vous devez expurger le contenu du document. Cet article vous explique **comment expurger des documents Word par programmation** dans vos applications .NET à l'aide de C#. Nous verrons séparément comment expurger en masquant le texte et comment **rechercher et remplacer le texte, les mots ou les phrases** en utilisant différentes techniques."
tags: ['case sensitive find and replace', 'Find &amp; Replace in Word', 'Find and replace text', 'Redact in CSharp', 'Redact Word in CSharp', 'Replace words in CSharp', 'text redaction']
categories: ['GroupDocs.Redaction Product Family']
---

Il peut y avoir de nombreuses raisons de remplacer un mot ou une phrase dans le document. Que vous souhaitiez effacer le contenu sensible avant de partager publiquement le document ou que vous souhaitiez masquer/supprimer toutes les informations privées telles que les identifiants de messagerie ou les numéros de sécurité sociale, vous devez expurger le contenu du document. Cet article vous explique **comment expurger des documents Word par programmation** dans vos applications .NET à l'aide de C#. Nous verrons séparément comment expurger en masquant le texte et comment **rechercher et remplacer le texte, les mots ou les phrases** en utilisant différentes techniques.

Les sujets suivants seront abordés ci-dessous :

* [API .NET pour remplacer le texte](#dotnet-redaction-api)
* [Rechercher et remplacer des mots ou des phrases](#replace-word-or-phrase)
* [Recherche sensible à la casse et remplacement de mots ou d'expressions](#case-sensitive-text-redaction)
* [Remplacer le texte à l'aide d'expressions régulières (RegEx)](#replace-text-using-regex)
* [Masquer le texte avec une boîte de couleur](#hide-text-with-colored-box)

## API de rédaction .NET pour le remplacement de texte {#dotnet-redaction-api}

GroupDocs.Redaction pour .NET est l'API de rédaction de documents qui permet de rechercher puis de remplacer les données prévues à partir de documents de différents formats de fichiers. Outre la rédaction et la rastérisation du texte, l'API fournit des fonctionnalités de métadonnées, d'annotation, de feuille de calcul et de rédaction d'images. Les [formats de fichiers pris en charge](https://docs.groupdocs.com/redaction/net/supported-document-formats/) des documents Word, feuilles de calcul, présentations, images et documents PDF sont disponibles dans la documentation.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements](https://downloads.groupdocs.com/redaction) ou installer l'API dans votre application .NET via [NuGet](https://www.nuget.org/packages/groupdocs.redaction).

```
PM> Install-Package GroupDocs.Redaction
```

Il n'est pas nécessaire d'installer MS Office ou tout autre logiciel tiers dans ce processus. Commençons maintenant et examinons différentes approches pour gérer la recherche et le remplacement de texte dans les documents. Voici la capture d'écran d'un document Word utilisé dans les exemples de démonstration. Les mêmes méthodes fonctionneront pour d'autres formats de document sans aucune modification du code.



{{< figure align=center src="images/original-doc.png" alt="">}}


## Rechercher et remplacer des mots ou des phrases dans un document Word à l'aide de C# {#replace-word-or-phrase}

L'étape suivante explique comment rechercher un mot/une phrase dans un document Word, puis remplace toutes les occurrences par un autre texte dans l'application C#.

* Chargez le document Word (DOC/DOCX) à l'aide de la classe [Redactor](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor).
* Trouvez la phrase ou le mot exact à l'aide de la classe [ExactPhraseRedaction](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/exactphraseredaction) avec [ReplacementOptions](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/replacementoptions).
* Utilisez la méthode [Apply](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/apply/index) de Redactor pour appliquer la rédaction.
* Enregistrez les modifications à l'aide de la méthode [Save](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/save/index).

Le code suivant recherche et remplace le mot en C#. Plus précisément, il remplace toutes les occurrences de "John Doe" par "\[censored\]".

```
// Trouvez la phrase exacte et remplacez-la par un autre texte en utilisant C#
using (Redactor redactor = new Redactor(@"path/document.docx"))
{
  redactor.Apply(new ExactPhraseRedaction("John Doe", new ReplacementOptions("[censored]")));
  redactor.Save();
}
```

La sortie du code est la suivante.



{{< figure align=center src="images/Exact-Phrase-Replacement.png" alt="">}}


## Recherche et remplacement sensibles à la casse dans les fichiers Word à l'aide de C# {#case-sensitive-text-redaction}

De même, vous pouvez effectuer la rédaction sensible à la casse d'un document Word en trouvant le mot exact et en le remplaçant par un autre. Le code suivant remplace l'existence du mot "John Doe" dans un fichier DOCX utilisant C#, mais cette fois, la recherche sera sensible à la casse.

```
// Trouvez la phrase exacte (sensible à la casse) et remplacez-la par un autre texte en utilisant C#
using (Redactor redactor = new Redactor(@"path/document.docx"))
{
  redactor.Apply(new ExactPhraseRedaction("John Doe", true /*isCaseSensitive*/, new ReplacementOptions("[censored]")));
  redactor.Save();
}
```

La sortie du code est la suivante.



{{< figure align=center src="images/Case-Sensitive-Exact-Phrase-Redaction.png" alt="">}}


## Remplacer du texte dans des fichiers Word à l'aide d'expressions régulières (RegEx) à l'aide de C# {#replace-text-using-regex}

Pour rechercher et remplacer n'importe quel modèle de texte dans les fichiers Word (DOC, DOCX), vous pouvez utiliser des expressions régulières. Les étapes suivantes vous permettent de rédiger un document Word avec RegEx à l'aide de C#.

* Chargez le document Word à l'aide de la classe [Redactor](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor).
* Trouvez la correspondance d'expression régulière à l'aide de la classe [RegexRedaction](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/regexredaction) avec [ReplacementOptions](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction.redactions/replacementoptions).
* Utilisez la méthode [Apply](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/apply/index) pour remplacer tous les textes de correspondance de regex.
* Utilisez la méthode [Save](https://apireference.groupdocs.com/redaction/net/groupdocs.redaction/redactor/methods/save/index) pour obtenir le fichier Word expurgé.

Le code suivant montre comment rechercher un modèle de texte dans un fichier Word à l'aide de RegEx, puis le remplacer/masquer par un autre texte à l'aide de C#.

```
// Rechercher du texte à l'aide d'une expression régulière et le remplacer par un autre texte à l'aide de C#
using (Redactor redactor = new Redactor(@"path/document.docx"))
{
  redactor.Apply(new RegexRedaction("\\d{2}\\s*\\d{2}[^\\d]*\\d{6}", new ReplacementOptions("[censored]")));
  redactor.Save();
}
```

La sortie du code ci-dessus est la suivante.



{{< figure align=center src="images/Regex-Redaction.png" alt="">}}


## Masquer le texte confidentiel dans les documents Word avec une boîte colorée à l'aide de C# {#hide-text-with-colored-box}

Si vous ne souhaitez pas remplacer votre contenu privé mais souhaitez simplement le couvrir, l'API vous permet de masquer ce contenu en traçant un cadre dessus. Le code suivant place le rectangle noir sur le texte prévu pour masquer le texte à l'aide de C#.

```
// Trouvez du texte et masquez-le en dessinant un rectangle dessus à l'aide de C#
using (Redactor redactor = new Redactor(@"path/document.docx"))
{
  redactor.Apply(new ExactPhraseRedaction("John Doe", new ReplacementOptions(System.Drawing.Color.Black)));
  redactor.Save();
}
```

La sortie du code ci-dessus est la suivante.



{{< figure align=center src="images/Colored-Box-Redaction.png" alt="">}}


## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, vous avez appris à rechercher du texte dans des fichiers Word (DOC, DOCX) à l'aide de différentes techniques et à remplacer les résultats de différentes manières. Plus précisément, nous avons expliqué comment rechercher du texte, un mot ou une phrase même s'il s'agit d'une recherche sensible à la casse ou en utilisant une expression régulière en C#. Plus tard, nous avons remplacé les résultats de la recherche par un autre texte ou en plaçant le rectangle coloré sur le texte recherché.

Pour en savoir plus sur l'API, consultez la [documentation](https://docs.groupdocs.com/redaction). Pour toute question, contactez-nous via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Créez votre solution de recherche en texte intégral en C#](https://blog.groupdocs.com/2021/06/03/build-your-full-text-search-solution-in-csharp/)
* [Trouvez les différences en comparant deux images en C#](https://blog.groupdocs.com/2021/01/06/compare-images-in-csharp-dotnet/)





