---
title: "Comparer deux fichiers ou plus en C#"
date: Tue, 10 Mar 2020 22:25:55 +0000
draft: false
url: /fr/2020/03/10/compare-excel-word-pdf-files-in-csharp/
aliases:
- /2020/03/10/comparer-deux-fichiers-ou-plus-dans-csharp-word-document-excel-spreadsheet/
- /2015/01/14/groupdocs-comparsion-for-dot-net-sample-compare-two-documents-in-csharp-and-display-diffs-on-aps-net-sites/
author: 'Shoaib Khan'
summary: "La comparaison de documents est l'une des exigences les plus courantes dans le monde de la programmation d'aujourd'hui. Que ce soit pour comparer des fichiers Word, comparer des fichiers Excel, des documents PDF ou même comparer des fichiers texte ou tout autre format de document, la précision est le facteur clé lors de la comparaison."
tags: ['compare documents', 'compare excel files', 'compare PDF files', 'compare text files', 'compare two documents', 'compare two excel files', 'compare two files', 'compare two word documents', 'compare word documents', 'document comparison', 'file compare']
categories: ['GroupDocs.Comparison Product Family']
---

La comparaison de documents est l'une des exigences les plus courantes dans le monde de la programmation d'aujourd'hui. Que ce soit pour comparer des fichiers Word, comparer des fichiers Excel, des documents PDF ou même comparer des fichiers texte ou tout autre format de document, la précision est le facteur clé lors de la comparaison.



{{< figure align=center src="images/groupdocs-comparison-net-90x90-no-border.png" alt="Comparer des fichiers avec l'API de comparaison de documents pour les développeurs .NET">}}


Cet article vous donnera une idée de la façon dont **[GroupDocs.Comparison][1]** aide les programmeurs à comparer deux ou plusieurs documents de plusieurs façons. [On-Premise][2] Les API de GroupDocs.Comparison sont actuellement disponibles pour [.NET][3] et [Java][4], cependant, cet article s'adresse aux développeurs C#.

## Comparez Excel, des fichiers Word ou tout autre document en C#

[GroupDocs.Comparison][5] permet aux développeurs de comparer deux documents ([en fait plus de 2][6]. Le document résultant montre les changements entre les deux fichiers en comparaison. Le code mentionné ci-dessous montre comment vous pouvez comparer deux fichiers Excel en seulement 3 lignes de code en C#.

1. Instanciez l'objet [Comparer][7] avec le chemin du document source.
2. Appelez la méthode [Add][8] pour spécifier le chemin du document cible.
3. Appelez la méthode [Comparer][9].
4. C'est ça.

```
using (Comparer comparer = new Comparer(“source.xlsx”))
{
    comparer.Add(“target.xlsx”);
    comparer.Compare(“result.xlsx”);
}
```

La comparaison de feuilles de calcul Excel ou de documents Microsoft Word fait partie du sous-ensemble de comparaisons prises en charge par l'API .NET de GroupDocs.Comparison. Vous trouverez ci-dessous la liste des formats pris en charge. Vous pouvez consulter la [documentation][10] pour rester à jour.

<figure class="wp-block-table is-style-stripes"><table class=""><tbody><tr><td>**Type de document</td><td> <strong>Formats de fichiers**</strong></td></tr><tr><td> <a href="https://wiki.fileformat.com/word-processing/">Traitement de texte</a></td><td> DOC, DOCX, DOCM, POINT, DOTX, DOTM, RTF, TXT</td></tr><tr><td> <a href="https://wiki.fileformat.com/spreadsheet/">Feuilles de calcul</a></td><td> XLS, XLSX, XLSM, XLT, XLTM, XLSB, XLSM, CSV</td></tr><tr><td> <a href="https://wiki.fileformat.com/presentation/">Présentations</a></td><td> PPT, PPTX, PPS, PPSX, POT, POTX</td></tr><tr><td> <a href="https://wiki.fileformat.com/word-processing/">OuvrirDocument</a></td><td> ODT, ODP, OTP, ODS, OTT</td></tr><tr><td> <a href="https://wiki.fileformat.com/view/pdf/">Portable</a></td><td> PDF</td></tr><tr><td> <a href="https://docs.fileformat.com/visio/">Dessins Microsoft Visio</a></td><td> VSD, VSDX, VSS, VST, VDX</td></tr><tr><td> <a href="https://wiki.fileformat.com/note-taking/">Prendre des notes</a></td><td> UNE</td></tr><tr><td> <a href="https://wiki.fileformat.com/web/">la toile</a></td><td> HTML, HTML, MHT, MHTML</td></tr><tr><td> <a href="https://wiki.fileformat.com/ebook/">livres électroniques</a></td><td> MOBI</td></tr><tr><td> <a href="https://wiki.fileformat.com/image/">Images</a></td><td> BMP, GIF, JPG, JPEG, PNG, DICOM, DJVU, DWG, DXF</td></tr><tr><td> <a href="https://wiki.fileformat.com/email/">E-mails</a></td><td> EML, EMLX, MSG</td></tr></tbody></table></figure>

## Comparez deux ou plusieurs feuilles de calcul ou documents OneNote en C #

Après la sortie de GroupDocs.Comparison pour .NET 20.2, l'API prend désormais en charge :

* Comparaison de plus de deux **feuilles de calcul **Microsoft Excel** et **OpenOffice** (XLS, XLSX, ODS, CSV, ...)
* Comparez plusieurs documents Microsoft OneNote.

L'API prend déjà en charge la comparaison de plusieurs fichiers pour différents formats de documents. L'extrait de code suivant montre à quelle vitesse plusieurs fichiers Excel peuvent être comparés en C#.

```
using (Comparer comparer = new Comparer(“source.xlsx”)
{
    comparer.Add(“target1.xlsx”);
    comparer.Add(“target2.xlsx”);
    comparer.Add(“target3.xlsx”);
    comparer.Compare(“result.xlsx”);
}
```

## Comparer des documents à partir de Stream en C#

En tant que programmeur, vous n'êtes pas seulement autorisé à comparer des documents disponibles sur le stockage local, en fait, nous pouvons comparer des documents à partir du flux.

1. Initialisez simplement l'objet [Comparer][11] avec le flux de document source.
2. Appelez la méthode [Add][12] et spécifiez le flux cible.
3. Appelez la méthode [Comparer][13]

```
using (Comparer comparer = new Comparer(File.OpenRead(“source.docx”))
{
    comparer.Add(File.OpenRead(“target1.docx”));
    comparer.Add(File.OpenRead(“target2.docx”));
    comparer.Add(File.OpenRead(“target3.docx”));
    comparer.Compare(File.Create(“result.docx”));
}
```

## Comparer des documents Word protégés par mot de passe/feuille de calcul Excel en C#

La protection par mot de passe est courante dans la documentation officielle. En utilisant l'API .NET de comparaison de documents, il permet à ses utilisateurs/développeurs de comparer des documents protégés par mot de passe.

Juste un petit changement dans le code par rapport au code de comparaison des documents qui ne sont pas protégés par mot de passe. Lors du chargement du document, utilisez [LoadOptions][14] pour spécifier le mot de passe du document. Vous trouverez ci-dessous l'exemple de code de comparaison pour votre aide.

```
using (Comparer comparer = new Comparer("source.docx", new LoadOptions() { Password = "1234" }))
{
    comparer.Add("target1.docx", new LoadOptions() { Password = "5678" });
    comparer.Add("target2.docx", new LoadOptions() { Password = "5678" });
    comparer.Add("target3.docx", new LoadOptions() { Password = "5678" });
    comparer.Compare("result.docx");
}
```

## Comparaison de documents avec des paramètres spécifiques

Une longueur d'avance sur la simple comparaison, en utilisant le code similaire à celui mentionné ci-dessous, vous pouvez comparer plusieurs documents avec vos paramètres de comparaison personnalisés.

[CompareOptions][15] vous offre la possibilité de spécifier vos options de comparaison comme le style de police pour les changements détectés, etc.

```
using (Comparer comparer = new Comparer(“source.docx”)
{
    comparer.Add(“target1.docx”);
    comparer.Add(“target2.docx”);
    comparer.Add(“target3.docx”);
    CompareOptions compareOptions = new CompareOptions()
    {
        InsertedItemStyle = new StyleSettings()
        {
            FontColor = System.Drawing.Color.Yellow
        }
    };
    comparer.Compare(“result.docx”, compareOptions);
}
```

## Comparer les fichiers de langage de programmation en C#

GroupDocs augmente continuellement la prise en charge pour comparer davantage de formats de fichiers. Après la version v 20.2, vous pouvez désormais également comparer les fichiers JSON à l'aide de l'API .NET. Voici les formats de fichiers de langage de programmation récemment ajoutés à la [liste des formats de documents pris en charge][16] :

<figure class="wp-block-table is-style-stripes"><table class="has-fixed-layout"><tbody><tr><td> ActionScript</td><td> Objectif C/C++</td></tr><tr><td> Assembleur</td><td> perle</td></tr><tr><td> Basé sur C</td><td> PHP</td></tr><tr><td> CSharp</td><td> Python</td></tr><tr><td> Sensationnel</td><td> Rubis</td></tr><tr><td> Javascript</td><td> Scala</td></tr><tr><td> Java</td><td> Script Shell/Batch, Log, Diff, Config, MOINS</td></tr><tr><td> JSON</td><td> SQL</td></tr></tbody></table></figure>

## Parlons

Vous pouvez créer votre propre application en utilisant les fonctionnalités mises en évidence ci-dessus. Nous serons ravis si vous nous contactez sur le [forum][17] pour discuter, résoudre un problème ou partager vos commentaires.







[1]: https://products.groupdocs.com/comparison
[2]: https://products.groupdocs.com/comparison/family
[3]: https://products.groupdocs.com/comparison/net
[4]: https://products.groupdocs.com/comparison/java
[5]: https://products.groupdocs.com/comparison/family
[6]: https://docs.groupdocs.com/display/comparisonnet/Compare+multiple+documents)
[7]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[8]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[9]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/compare/index
[10]: https://docs.groupdocs.com/comparison/net
[11]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[12]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[13]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/compare/index
[14]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.options/loadoptions
[15]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.options/compareoptions
[16]: https://docs.groupdocs.com/comparison/net
[17]: https://forum.groupdocs.com/c/comparison


