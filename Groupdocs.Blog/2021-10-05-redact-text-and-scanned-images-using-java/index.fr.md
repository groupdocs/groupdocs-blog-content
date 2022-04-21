---
title: "Masquer des documents PDF numérisés en Java"
date: Tue, 05 Oct 2021 04:21:00 +0000
draft: false
url: /fr/2021/10/05/redact-text-and-scanned-images-using-java/
author: 'Shoaib Khan'
summary: "Vous souhaitez sécuriser les informations secrètes ou sensibles contenues dans les documents ? C'est faisable même s'il s'agit d'informations textuelles régulières ou s'il s'agit de texte avec le document numérisé avec des images. Les articles précédents peuvent vous aider à affiner votre recherche, où nous avons discuté des [différentes stratégies pour rechercher des mots][1] et [rechercher des synonymes dans plusieurs documents][2]. Cet article vous explique **comment masquer du texte PDF et du texte dans des images dans un document à l'aide de Java**."
tags: ['Blackout Text', 'Blackout Text in PDF', 'redact documents', 'Redact in Java', 'Redact PDF files', 'Redact PDF in Java', 'Redact Text in Image', 'Redact Text in Java', 'Redact Text in PDF']
categories: ['GroupDocs.Redaction Product Family']
---

Vous souhaitez sécuriser les informations secrètes ou sensibles contenues dans les documents ? C'est faisable même s'il s'agit d'informations textuelles régulières ou s'il s'agit de texte avec le document numérisé avec des images. Les articles précédents peuvent vous aider à affiner votre recherche, où nous avons discuté des [différentes stratégies pour rechercher des mots][3] et [rechercher des synonymes dans plusieurs documents][4]. Cet article vous explique **comment masquer du texte PDF et du texte dans des images dans un document à l'aide de Java**.

Les sujets suivants seront abordés ci-dessous :

* [Caviardage de texte et d'image – API Java][5]
* [Expurger le texte PDF et les informations numérisées à l'aide de Java][6]

## API Java pour la rédaction de texte et d'image {#redaction-java-api}

GroupDocs.Redaction fournit la [solution de rédaction pour sécuriser les informations classifiées][7]. Son API Java vous permet de supprimer ou de supprimer des informations confidentielles dans des documents de différents formats de fichiers à partir de vos applications Java. En plus de la rédaction et de la rastérisation simples du texte, l'API permet également d'identifier le texte dans les images qui peuvent avoir été à l'intérieur de n'importe quel document, comme les fichiers PDF numérisés les plus couramment utilisés. La liste complète des [formats de fichiers pris en charge][8] est disponible dans la documentation.

### Télécharger ou configurer

Vous pouvez télécharger le fichier **JAR** à partir de la [section téléchargements][9], ou simplement obtenir les dernières configurations de référentiel et de dépendance pour le pox.xml de vos applications Java **basées sur maven**.

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>https://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-redaction</artifactId>
        <version>21.6</version> 
</dependency>
```

## Masquer le texte PDF et le texte de l'image numérisée à l'aide de Java {#redact-text-and-scanned-text}

Nous avons déjà discuté des différentes [façons de rechercher et de remplacer du texte dans des documents][10]. Cependant, nous pouvons également expurger le texte dans les images. J'utiliserai le document PDF suivant, qui contient du texte et également une image avec du texte. Pour cela, nous devons combiner l'OCR avec le processus de rédaction. Premièrement, nous identifierons le texte dans le document et également le texte qui se trouve à l'intérieur de l'image du document. Ensuite, nous le couvrirons d'une boîte noire pour masquer par programmation toute information légale, confidentielle ou secrète, même si elle est sous forme de texte dans une image de document numérisée.



{{< figure align=center src="images/PDF-with-text-and-scanned-image.jpg" alt="PDF avec texte et image numérisée">}}


Les étapes suivantes détecteront et remplaceront le texte dans les documents PDF, qui contient du texte normal ou tout texte dans les images incorporées.

* Préparez les paramètres du rédacteur à l'aide de n'importe quel connecteur OCR.
* Chargez votre fichier PDF en utilisant la classe [Redactor][11] et également si des options de chargement spécifiques sont requises.
* Définissez vos [options de remplacement][12]. Je choisis de noircir le texte.
* Préparer les rédactions; utilisez la stratégie de masquage appropriée comme [Phrase Redaction][13] ou [RegEx redaction][14].
* Appliquez les caviardages en utilisant la méthode [apply][15].
* Enregistrez le document expurgé en utilisant la méthode [save][16].

Le code source suivant expurge le texte sélectionné dans un document PDF à l'aide de Java.

```
// Masquer le texte en PDF et le texte en image comme un document numérisé à l'aide de Java
RedactorSettings settings = new RedactorSettings(new AsposeCloudOcrConnector());
try (Redactor redactor = new Redactor("path/document.pdf", new LoadOptions(), settings))
{
    ReplacementOptions marker = new ReplacementOptions(java.awt.Color.BLACK);
    Redaction redactions[] = new Redaction[] {
            new RegexRedaction("(?<=Dear\\s)([^,]+)", marker), // cardholder name
            new RegexRedaction("\\d{2}/\\d{2}", marker), // valid thru
            new RegexRedaction("\\d{4}", marker)  // card number parts
        };
    RedactorChangeLog result = redactor.apply(redactions);
    if (result.getStatus() != RedactionStatus.Failed)
    {
        redactor.save(new SaveOptions(false, "redacted"));
    }
}
```

La sortie du code ci-dessus est la suivante avec le texte sélectionné noirci du document PDF.



{{< figure align=center src="images/Redacted-PDF-with-text-and-scanned-image.jpg" alt="Masquer le texte du PDF et le texte de l'image numérisée">}}


## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][17] pour utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, vous avez appris à biffer du texte dans des documents. De plus, nous avons discuté de la façon de biffer du texte dans les images d'un document PDF à l'aide de Java. De même, vous pouvez biffer du texte et des images avec des documents de tout autre format. Nous avons utilisé la rédaction des expressions régulières, cependant, cela peut également être fait de différentes manières. Plus tard, nous avons masqué les résultats de la recherche à l'aide d'une boîte noire.

Pour plus de détails sur l'API, consultez la [documentation][18]. Pour toute question, contactez-nous via le [forum][19].

## Voir également

* [Rechercher et remplacer des mots dans des documents à l'aide de Java][20]
* [Rechercher et supprimer des filigranes de documents en Java][21]
* [Ajouter ou supprimer des annotations de fichiers PDF en Java][22]







[1]: https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/
[2]: https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/
[3]: https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/
[4]: https://blog.groupdocs.com/2021/10/03/find-synonyms-in-multiple-files-using-java/
[5]: #redaction-java-api
[6]: #redact-text-and-scanned-text
[7]: https://products.groupdocs.com/redaction/
[8]: https://docs.groupdocs.com/redaction/java/supported-document-formats/
[9]: https://downloads.groupdocs.com/redaction
[10]: https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/
[11]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor
[12]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ReplacementOptions
[13]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/ExactPhraseRedaction
[14]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction.redactions/RegexRedaction
[15]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor#apply(com.groupdocs.redaction.Redaction)
[16]: https://apireference.groupdocs.com/redaction/java/com.groupdocs.redaction/Redactor#save()
[17]: https://purchase.groupdocs.com/temporary-license
[18]: https://docs.groupdocs.com/redaction
[19]: https://forum.groupdocs.com/
[20]: https://blog.groupdocs.com/2021/09/01/find-and-replace-text-in-documents-using-java/
[21]: https://blog.groupdocs.com/2020/11/30/find-and-remove-watermarks-from-documents-in-java/
[22]: https://blog.groupdocs.com/2021/04/18/annotate-pdf-files-using-java/


