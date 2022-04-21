---
title: "Recherche de mots et remplacement de texte dans des documents Word à l'aide de Java"
date: Fri, 04 Feb 2022 15:24:00 +0000
draft: false
url: /fr/2022/02/04/trouver-et-remplacer-texte-dans-word-documents-en-utilisant-java/
author: 'Shoaib Khan'
summary: "Dans l'un des articles, nous avons déjà discuté de [comment expurger des mots dans des documents en tant que développeur .NET](https://blog.groupdocs.com/2022/02/15/find-and-replace-text-in-word-using-csharp/). La stratégie est utilisée de plusieurs façons pour effacer le contenu sensible, masquer ou supprimer des informations privées telles que les adresses e-mail ou les numéros d'identification. Cet article explique **comment effectuer une recherche de mots dans les documents Word DOC/DOCX en Java. **Nous discuterons séparément de la façon de** rechercher et remplacer le texte, les mots ou les phrases** avec différentes techniques utilisant l'API Java pour la rédaction."
tags: ['how to redact in word', 'how to redact PDF in Java', 'how to redact Word in Java', 'Java Redaction API', 'Redact in Java']
categories: ['GroupDocs.Redaction Product Family']
---

Dans l'un des articles, nous avons déjà discuté de [comment expurger des mots dans des documents en tant que développeur .NET](https://blog.groupdocs.com/2022/02/15/find-and-replace-text-in-word-using-csharp/). La stratégie est utilisée de plusieurs façons pour effacer le contenu sensible, masquer ou supprimer des informations privées telles que les adresses e-mail ou les numéros d'identification. Cet article explique **comment effectuer une recherche de mots dans les documents Word DOC/DOCX en Java.** Nous discuterons séparément de la façon de **rechercher et remplacer le texte, les mots ou les phrases** avec différentes techniques utilisant l'API Java pour la rédaction.

Les sujets suivants seront abordés ci-dessous:

* [API Java pour la recherche de mots et le remplacement de texte](#word-search-java-api)
* [Rechercher et remplacer des mots ou une expression](#replace-word-or-phrase)
* [Recherche de mots sensibles à la casse et remplacement de texte](#case-sensitive-text-redaction)
* [Remplacer le texte à l'aide d'expressions régulières (RegEx)](#replace-text-using-regex)
* [Remplacer le texte par une boîte de couleur](#hide-text-with-colored-box)

## API Java pour la recherche de mots et le remplacement de texte {#word-search-java-api}

**GroupDocs** fournit une [API de rédaction Java](https://products.groupdocs.com/redaction/java/) qui permet de rechercher et de remplacer le contenu des fichiers pris en charge par MS Word et d'autres documents de divers autres formats de fichiers. En plus de la rédaction et de la rastérisation du texte, l'API prend en charge les métadonnées, les annotations, les feuilles de calcul, ainsi que les fonctionnalités de rédaction des images. Les [formats de fichiers pris en charge](https://docs.groupdocs.com/redaction/java/supported-document-formats/) des documents Word, feuilles de calcul, présentations, images et documents PDF sont disponibles dans la documentation.

### Télécharger ou configurer

Vous pouvez télécharger le fichier **JAR** à partir de la [section des téléchargements](https://downloads.groupdocs.com/redaction), ou simplement obtenir les dernières configurations de référentiel et de dépendance pour le pox.xml de votre **maven- applications basées** sur Java.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>

<dependency>
	<groupId>com.groupdocs</groupId>
	<artifactId>groupdocs-rédaction</artifactId>
	<version>21.12</version>
</dependency>
```

MS Word ou tout autre logiciel tiers n'est pas requis pour le processus de rédaction. Commençons maintenant par différentes approches pour gérer la recherche et le remplacement de texte. Voici la capture d'écran d'un document Word utilisé dans les exemples ci-dessous. Vous pouvez également utiliser les mêmes méthodes pour d'autres formats de document avec très peu ou pas de changement dans le code source.

{{< figure align=center src="images/original-doc.png" alt="Document to redact text">}}


## Rechercher et remplacer des mots ou des phrases à l'aide de Java {#replace-word-or-phrase}

Les étapes suivantes expliquent comment rechercher puis remplacer les occurrences d'un mot/d'une phrase dans un document Word dans l'application Java.

*   Chargez le fichier DOC/DOCX à l'aide de la classe [Redactor](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor).
*   Recherchez l'expression ou le mot exact à l'aide des classes [ExactPhraseRedaction](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ExactPhraseRedaction) et [ReplacementOptions](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ReplacementOptions).
*   Utilisez la méthode d'application de Redactor pour appliquer la rédaction.
*   Pour enregistrer le fichier à un emplacement différent après avoir apporté des modifications, utilisez le flux de sortie.
*   Enregistrez les modifications de rédaction à l'aide de la méthode [save](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor#save(java.io.OutputStream,%20com.groupdocs.redaction.options.RasterizationOptions)).

Le code suivant recherche et remplace le mot "John Doe" dans le document Word ci-dessus à l'aide de Java. Il remplace toutes les occurrences de "John Doe" par le mot "\[censored\]".

```
// Trouver la phrase exacte et la remplacer par un autre texte en utilisant Java
final Redactor redactor  = new Redactor("path/document.docx");
redactor.apply(new ExactPhraseRedaction("John Doe", new ReplacementOptions("[censored]")));
// Si vous souhaitez enregistrer le fichier expurgé à un emplacement différent avec un nom différent.
FileOutputStream stream = new FileOutputStream("path/exactPhrase.docx");
RasterizationOptions rasterOptions = new RasterizationOptions();
rasterOptions.setEnabled(false);
redactor.save(stream, rasterOptions);
```

La sortie du code est la suivante.

{{< figure align=center src="images/Exact-Phrase-Replacement.png" alt="Redact using Exact Phrase">}}


## Recherche de mots sensibles à la casse et remplacement de texte en Java {#case-sensitive-text-redaction}

Vous semblez prudent quant à la casse exacte du mot et souhaitez uniquement remplacer le mot qui correspond uniquement à votre recherche sensible à la casse. Le code suivant remplace l'existence de la correspondance de casse exacte du mot "John Doe" en Java.


```
// Trouvez la phrase exacte (sensible à la casse) et remplacez-la par un autre texte en utilisant Java
final Redactor redactor  = new Redactor("path/document.docx");
redactor.apply(new ExactPhraseRedaction("John Doe", true /*isCaseSensitive*/, new ReplacementOptions("[censored]")));
redactor.save();
```

La sortie du code est la suivante.

{{< figure align=center src="images/Case-Sensitive-Exact-Phrase-Redaction.png" alt="Caviardage sensible à la casse">}}


## Remplacer du texte à l'aide d'expressions régulières (RegEx) en Java {#replace-text-using-regex}

Si vous ne voulez pas changer le mot exact mais un modèle qui existe dans votre document, vous pouvez utiliser les expressions régulières. Les étapes suivantes vous permettent de rechercher et de remplacer n'importe quel modèle de texte à l'aide d'expressions régulières (RegEx) dans vos applications Java.

*   Chargez le document à l'aide de la classe [Redactor](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor).
*   Créez le RegEx à l'aide de [RegexRedaction](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/RegexRedaction).
*   Fournissez le texte à l'aide de [ReplacementOptions](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ReplacementOptions) pour remplacer la correspondance RegEx.
*   Utilisez la méthode apply pour remplacer toutes les correspondances d'expression régulière.
*   Utilisez la méthode d'enregistrement pour obtenir le document expurgé.

Le code suivant montre comment effectuer la recherche de mots dans un fichier Word à l'aide de RegEx et le remplacer par un autre texte à l'aide de Java.

```
// Rechercher du texte à l'aide d'une expression régulière et le remplacer par un autre texte à l'aide de Java
final Redactor redactor  = new Redactor("path/document.docx");
redactor.apply(new RegexRedaction("\\d{2}\\s*\\d{2}[^\\d]*\\d{6}", new ReplacementOptions("[censored]")));
redactor.save();
```

Voici la sortie du code ci-dessus :

{{< figure align=center src="images/Regex-Redaction.png" alt="RegEx Redaction">}}

## Remplacer le texte par une boîte colorée en Java {#hide-text-with-colored-box}

Si vous ne souhaitez pas remplacer votre contenu et souhaitez simplement le masquer, l'API vous permet de couvrir la correspondance du texte en traçant un cadre dessus. Le code Java suivant masque le texte avec le rectangle noir.

```
// Trouvez du texte et masquez-le en dessinant un rectangle dessus à l'aide de Java
final Redactor redactor  = new Redactor("path/document.docx");
redactor.apply(new ExactPhraseRedaction("John Doe", true, new ReplacementOptions(java.awt.Color.BLACK)));
redactor.save();
```

La sortie du code ci-dessus est la suivante.

{{< figure align=center src="images/Colored-Box-Redaction.png" alt="Hide Text using Box">}}


## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour résumer, vous avez appris à effectuer une recherche de mots pour trouver du texte dans des documents Word à l'aide d'une recherche par expression de texte exacte, d'une recherche sensible à la casse, d'une recherche à l'aide d'expressions régulières et, enfin et surtout, du masquage du texte au lieu de le remplacer. Vous pouvez utiliser ces différentes techniques pour remplacer les résultats de différentes manières dans les documents MS Word.

Pour plus de détails et en savoir plus sur l'API, consultez la [documentation](https://docs.groupdocs.com/redaction). Pour toute question, contactez-nous via le [forum](https://forum.groupdocs.com/).

## See Also

*   [Créer une solution de recherche en texte intégral en Java](https://blog.groupdocs.com/2021/08/07/build-full-text-search-solution-in-java/)
*   [Comparaison d'images en Java pour repérer les différences](https://blog.groupdocs.com/2021/06/16/compare-images-in-java/)
*   [Réorganiser les pages dans Word à l'aide de Java](https://blog.groupdocs.com/2022/03/01/move-word-pages-using-java/)
*   [Rechercher et remplacer du texte dans un PDF à l'aide de C#](https://blog.groupdocs.com/2022/02/19/find-and-replace-text-in-pdf-using-csharp/)