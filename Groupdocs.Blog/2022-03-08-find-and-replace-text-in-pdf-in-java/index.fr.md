---
title: "Recherche de mots et remplacement de texte dans un PDF en Java"
date: Tue, 08 Mar 2022 10:10:00 +0000
draft: false
url: /fr/2022/03/08/trouver-et-remplacer-texte-en-pdf-en-java/
author: 'Shoaib Khan'
summary: "Les modèles sont largement utilisés pour générer des documents personnalisés en remplaçant les clés de modèle par les valeurs respectives. Cet article explique **comment rechercher et remplacer du texte et des mots dans des documents PDF en Java**. Nous discuterons séparément de la manière d'effectuer une recherche de mots et de phrases, une recherche de mots sensible à la casse, en remplaçant le texte trouvé à l'aide d'expressions régulières. Enfin, nous apprendrons à masquer la partie de texte recherchée à l'aide de Java."
tags: ['Blackout Text', 'Blackout Text in PDF', 'Find &amp; Replace Text in PDF', 'Find Text in PDF', 'Hide Text in PDF', 'Redact PDF files', 'Word Search in Java']
categories: ['GroupDocs.Redaction Product Family']
---

Les modèles sont largement utilisés pour générer des documents personnalisés en remplaçant les clés de modèle par les valeurs respectives. Cet article explique **comment rechercher et remplacer du texte et des mots dans des documents PDF en Java**. Nous discuterons séparément de la manière d'effectuer une recherche de mots et de phrases, une recherche de mots sensible à la casse, en remplaçant le texte trouvé à l'aide d'expressions régulières. Enfin, nous apprendrons à masquer la partie de texte recherchée à l'aide de Java.

Les sujets suivants seront abordés ci-dessous :

* [API Java pour remplacer du texte](#java-redaction-api)
* [Rechercher et remplacer des mots ou une expression](#replace-word-or-phrase)
* [Recherche et remplacement de mots sensibles à la casse](#case-sensitive-text-redaction)
* [Remplacer par des expressions régulières (RegEx)](#replace-text-using-regex)
* [Masquer le texte avec une boîte de couleur](#hide-text-with-colored-box)

## API Java Redaction pour le remplacement de texte {#java-redaction-api}

GroupDocs fournit une API Java pour appliquer différents types de suppressions. Il permet de caviarder, de masquer ou de supprimer le contenu et même les métadonnées des documents, des présentations, des feuilles de calcul, des fichiers PDF et des images dans l'application. Pour plus de détails sur l'API, consultez sa [documentation](https://docs.groupdocs.com/redaction/java/).

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
        <artifactId>groupdocs-redaction</artifactId>
        <version>21.12</version> 
</dependency>
```

L'une des bonnes choses est qu'il n'est pas nécessaire d'installer un éditeur de PDF ou tout autre logiciel tiers pour la rédaction de PDF. Voici le contenu du document PDF utilisé dans les exemples ci-dessous pour la rédaction. La même approche fonctionnera pour d'autres formats de document avec pratiquement aucune différence dans le code source.



{{< figure align=center src="images/original-doc.png" alt="">}}


## Rechercher et remplacer un mot ou une phrase dans un PDF en Java {#replace-word-or-phrase}

Vous pouvez utiliser cette fonctionnalité pour masquer toutes les données privées et également pour créer un nouveau document personnalisé à partir de n'importe quel modèle. L'étape suivante explique comment rechercher un mot/phrase dans un document PDF et le remplacer par un autre texte dans l'application Java.

* **Chargez** le fichier PDF à l'aide de la classe [Redactor](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor).
* **Trouvez la phrase ou le mot exact**, en utilisant [ExactPhraseRedaction](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ExactPhraseRedaction) et [ReplacementOptions](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ReplacementOptions).
* **Appliquez la rédaction** en utilisant la méthode apply().
* **Enregistrer** le nouveau document avec les modifications à l'aide de la méthode save().

Le code suivant recherche et remplace les mots dans un fichier PDF à l'aide de Java. Plus précisément, il cache toutes les occurrences de "John Doe" en le remplaçant par le mot "\[censored\]".

```
// Trouvez la phrase exacte dans le PDF et remplacez-la par un autre texte en utilisant Java
final Redactor redactor  = new Redactor("path/document.pdf");
redactor.apply(new ExactPhraseRedaction("John Doe", new ReplacementOptions("[censored]")));
// Enregistrez le fichier expurgé à un emplacement différent avec un nom différent.
FileOutputStream stream = new FileOutputStream("path/exactPhrase.pdf");
RasterizationOptions rasterOptions = new RasterizationOptions();
rasterOptions.setEnabled(false);
redactor.save(stream, rasterOptions);
```

La sortie du code ci-dessus est la suivante.



{{< figure align=center src="images/Exact-Phrase-Replacement.png" alt="">}}


## Rechercher et remplacer du texte ou une phrase sensible à la casse dans un PDF à l'aide de Java {#case-sensitive-text-redaction}

Vous pouvez effectuer la recherche et la rédaction sensibles à la casse. Le code suivant remplace l'occurrence sensible à la casse du mot "John Doe" mais pas "john doe" dans un document PDF utilisant Java.

```
// Trouvez la phrase exacte dans le PDF (sensible à la casse) et remplacez-la par un autre texte en utilisant Java
final Redactor redactor  = new Redactor("path/document.pdf");
redactor.apply(new ExactPhraseRedaction("John Doe", true /*isCaseSensitive*/, new ReplacementOptions("[censored]")));
redactor.save();
```

La sortie du code est la suivante.



{{< figure align=center src="images/Case-Sensitive-Exact-Phrase-Redaction.png" alt="">}}


## Remplacer le texte en PDF par des expressions régulières (RegEx) en Java {#replace-text-using-regex}

De même, vous pouvez remplacer n'importe quel modèle de texte spécifique à l'aide d'expressions régulières. Les étapes suivantes vous permettent de biffer un PDF après une recherche à l'aide d'une expression régulière (RegEx) dans vos applications Java.

* **Chargez** le document PDF à l'aide de la classe [Redactor](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor).
* **Trouvez la correspondance de regex** en utilisant la classe [RegexRedaction](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/RegexRedaction) avec [ReplacementOptions](https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ReplacementOptions).
* Appliquez les modifications au document à l'aide de la méthode apply().
* **Enregistrer** le document expurgé en utilisant la méthode save() appropriée.

Le code Java suivant montre comment trouver un certain modèle de texte dans un document PDF à l'aide de RegEx et le remplacer/masquer ultérieurement par un autre texte.

```
// Rechercher du texte dans un PDF à l'aide d'une expression régulière et le remplacer par un autre texte à l'aide de Java
final Redactor redactor  = new Redactor("path/document.pdf");
redactor.apply(new RegexRedaction("\\d{2}\\s*\\d{2}[^\\d]*\\d{6}", new ReplacementOptions("[censored]")));
redactor.save();
```

La sortie du code ci-dessus est la suivante.



{{< figure align=center src="images/Regex-Redaction.png" alt="">}}


## Remplacer le texte par une boîte colorée en Java {#hide-text-with-colored-box}

Si vous souhaitez simplement masquer les informations confidentielles recherchées dans votre fichier PDF, vous pouvez simplement y mettre une couverture. L'API vous permet de masquer le texte recherché. Le code suivant place le rectangle noir sur le texte privé mentionné en Java.

```
// Trouvez du texte dans un PDF et masquez-le en dessinant un rectangle dessus à l'aide de Java
final Redactor redactor  = new Redactor("path/document.pdf");
redactor.apply(new ExactPhraseRedaction("John Doe", true, new ReplacementOptions(java.awt.Color.BLACK)));
redactor.save();
```

La sortie du code ci-dessus est la suivante.



{{< figure align=center src="images/Colored-Box-Redaction.png" alt="">}}


## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite](https://purchase.groupdocs.com/temporary-license) afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour résumer, nous avons appris à trouver certains textes dans des fichiers PDF en utilisant différentes techniques de recherche. Plus tard, nous avons rédigé les fichiers PDF en remplaçant ou en masquant le texte dans les applications en Java. Plus précisément, nous avons effectué une recherche simple sur les mots, les phrases, en respectant la casse et en utilisant RegEx en Java. Enfin, nous avons modifié les résultats de la recherche avec un autre texte ou en le masquant simplement avec de la couleur dessus.

Pour plus de détails sur l'API, consultez la [documentation](https://docs.groupdocs.com/redaction). Pour toute question, contactez-nous via le [forum](https://forum.groupdocs.com/).

## Voir également

* [Masquer les documents PDF numérisés en Java](https://blog.groupdocs.com/2021/10/05/redact-text-and-scanned-images-using-java/)
* [Rechercher des synonymes dans plusieurs fichiers à l'aide de Java](https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/)
* [Créer une solution de recherche en texte intégral en Java](https://blog.groupdocs.com/2021/08/07/build-full-text-search-solution-in-java/)





