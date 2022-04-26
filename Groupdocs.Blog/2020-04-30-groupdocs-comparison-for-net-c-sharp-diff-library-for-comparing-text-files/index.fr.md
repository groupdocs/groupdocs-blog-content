---
title: "Bibliothèque C# Diff pour comparer des fichiers texte"
date: Thu, 30 Apr 2020 14:41:00 +0000
draft: false
url: /fr/2020/04/30/groupdocs-comparison-for-net-c-sharp-diff-library-for-comparing-text-files/
aliases:
- /2014/07/04/groupdocs-comparison-for-net-c-sharp-diff-library-for-comparing-text-files/
author: 'Muhammad Sohail'
summary: "Le [GroupDocs.Comparison pour .NET][1] est une bibliothèque C# qui vous permet de comparer des documents et de trouver des différences. Comparez et fusionnez Microsoft Word, Excel, PowerPoint, OpenDocument, PDF, Texte, HTML et [de nombreux autres documents][2], récupérez une liste des modifications entre les documents source et cible, appliquez ou rejetez les modifications et enregistrez les résultats avec GroupDocs .API de comparaison. En plus de cela, GroupDocs.Comparison peut identifier les changements de style et de formatage - comme le gras, l'italique, le soulignement, le barré, les types de police, etc."
tags: ['compare text files', 'diff view library', 'GroupDocs Comparison']
categories: ['GroupDocs.Comparison Product Family']
---



{{< figure align=center src="images/groupdocs-comparison-128x128-1.png" alt="">}}


Le [GroupDocs.Comparison pour .NET][3] est une bibliothèque C# qui vous permet de comparer des documents et de trouver des différences. Comparez et fusionnez Microsoft Word, Excel, PowerPoint, OpenDocument, PDF, Texte, HTML et [de nombreux autres documents][4], récupérez une liste des modifications entre les documents source et cible, appliquez ou rejetez les modifications et enregistrez les résultats avec GroupDocs .API de comparaison. En plus de cela, GroupDocs.Comparison peut identifier les changements de style et de mise en forme - comme le gras, l'italique, le soulignement, le barré, les types de police, etc.

Les algorithmes de détection des changements utilisés par [GroupDocs.Comparison][5] permettent de détecter les différences dans les différentes parties et blocs du document :

* Blocs de texte - paragraphes, mots et caractères ;
* Les tables;
* Images;
* Formes etc...

Voici quelques étapes simples pour comparer deux fichiers texte et montrer les différences :

* Instancier l'objet [Comparer][6] avec le chemin ou le flux du document source ;
* Appelez la méthode [Add][7] et spécifiez le chemin ou le flux du document cible ;
* Appelez la méthode [Comparer][8].

L'extrait de code suivant illustre le cas le plus simple de comparaison de documents à l'aide de quelques lignes de code.

### Comparer les documents du fichier local

```
using (Comparer comparer = new Comparer(“source.docx”))
{
    comparer.Add(“target.docx”);
    comparer.Compare(“result.docx”);
}
```

### Comparer les documents du flux
```
using (Comparer comparer = new Comparer(File.OpenRead(“source.docx”)))
{
    comparer.Add(File.OpenRead(“target.docx”));
    comparer.Compare(File.Create(“result.docx”));
}
```

Supposons que vous ayez deux contrats au format DOCX qui ont été conclus au cours d'années différentes. Si vous utilisez le code ci-dessus pour comparer ces contrats, vous obtenez un fichier DOCX où les éléments supprimés sont marqués en rouge, les ajoutés en bleu et les modifiés en vert comme indiqué ci-dessous :



{{< figure align=center src="images/FreelanceContract.png" alt="">}}


## Accepter ou rejeter les différences détectées

[GroupDocs.Comparison][9] offre la possibilité d'appliquer ou d'ignorer des modifications spécifiques entre les documents source et cible et d'enregistrer le document résultant avec (ou sans) les modifications sélectionnées.

Voici les étapes pour appliquer/rejeter les modifications apportées au document résultant.

* Instancier l'objet [Comparer][10] avec le chemin ou le flux du document source ;
* Appelez la méthode _[A][11]_[dd][12] et spécifiez le chemin ou le flux du document cible ;
* Appelez la méthode [Comparer][13] ;
* Appelez la méthode [GetChanges][14] et obtenez la liste des modifications détectées ;
* Définissez [ComparisonAction][15] de l'objet de modification nécessaire sur la valeur [ComparisonAction.Accept][16] ou [ComparisonAction.Reject][17] ;
* Appelez la méthode [ApplyChanges][18] et transmettez-lui la collection de modifications.

L'exemple de code suivant montre comment accepter/rejeter les différences détectées.

```
using (Comparer comparer = new Comparer(“source.docx”))
{
    comparer.Add(“target.docx”);
    comparer.Compare();
    ChangeInfo[] changes = comparer.GetChanges();
    changes[0].ComparisonAction = ComparisonAction.Reject;
    comparer.ApplyChanges(File.Create(“result.docx”), new SaveOptions(), new ApplyChangeOptions() { Changes = changes });
}
```

## Générer un aperçu des pages du document

[GroupDocs.Comparison][19] permet de générer des aperçus de page pour les documents source, cible et résultant à l'aide de la méthode [GeneratePreview][20] d'une classe [Document][21].

La classe [PreviewOptions][22] est utilisée pour gérer le processus de génération d'aperçu - spécifiez les numéros de page souhaités, le format d'image, etc.

Voici les étapes pour générer un aperçu de document avec l'API GroupDocs.Comparison :

* Créez une nouvelle instance de la classe [Comparer][23] et transmettez le chemin du document source en tant que paramètre du constructeur ;
* Ajouter le(s) document(s) cible(s) à la comparaison à l'aide de la méthode [Ajouter][24] ;
* Les propriétés [Source][25] et [Targets][26] de l'objet [Comparer][27] permettent d'accéder aux documents source et cible et fournissent la méthode [GeneratePreview][28] ;
* Instanciez l'objet [PreviewOptions][29] avec :
    * délégué pour chaque création de flux de page (voir gestionnaire d'événement CreatePageStream) ;
    * format d'aperçu de l'image - PNG / JPG / BMP ;
    * numéros de page à traiter ;
    * taille personnalisée des images d'aperçu (si nécessaire).
* Appelez la méthode [GeneratePreview][30] du document [Source][31] et [Targets][32] et transmettez-lui [PreviewOptions][33].

### Obtenir des aperçus de page pour le document résultant

```
using (Comparer comparer = new Comparer(“source.docx”))
{
    comparer.Add(“target.docx”);
    comparer.Compare(“result.docx”);
    Document document = new Document(File.OpenRead(“result.docx”));
    PreviewOptions previewOptions = new PreviewOptions(pageNumber =>
    {
        var pagePath = Path.Combine(“C:\\”, $"result\_{pageNumber}.png");
        return File.Create(pagePath);
    });
    previewOptions.PreviewFormat = PreviewFormats.PNG;
    previewOptions.PageNumbers = new int[] { 1, 2 };
    document.GeneratePreview(previewOptions);
}
```

## Comparez plusieurs documents

[GroupDocs.Comparison][34] permet de comparer plus de deux documents. L'exemple de code suivant montre comment comparer plusieurs documents par programmation.

```
using (Comparer comparer = new Comparer(“source.docx”)
{
    comparer.Add(“target1.docx”);
    comparer.Add(“target2.docx”);
    comparer.Add(“target3.docx”);
    comparer.Compare(“result.docx”);
}
```

## Installation

[NuGet][35] est le moyen le plus simple de télécharger et d'installer GroupDocs.Comparison pour .NET. Veuillez [obtenir une licence temporaire][36] pour tester la bibliothèque sans aucune restriction fonctionnelle.

Veuillez consulter la [documentation][37] pour en savoir plus sur la bibliothèque. Nous proposons également une assistance technique gratuite, alors n'hésitez pas à [nous contacter][38] - nous serons heureux de vous aider.


[1]: https://products.groupdocs.com/comparison/net
[2]: https://docs.groupdocs.com/comparison/net
[3]: https://products.groupdocs.com/comparison/net
[4]: https://docs.groupdocs.com/comparison/net
[5]: https://apireference.groupdocs.com/comparison/net
[6]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[7]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[8]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/compare/index
[9]: https://products.groupdocs.com/comparison/net
[10]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[11]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[12]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[13]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/compare/index
[14]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/getchanges/index
[15]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.result/changeinfo/properties/comparisonaction
[16]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.result/comparisonaction
[17]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.result/comparisonaction
[18]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/applychanges/index
[19]: https://products.groupdocs.com/comparison/net
[20]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/document/methods/generatepreview
[21]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/document
[22]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.options/previewoptions
[23]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[24]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index
[25]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/properties/source
[26]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/properties/targets
[27]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer
[28]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/document/methods/generatepreview
[29]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.options/previewoptions
[30]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/document/methods/generatepreview
[31]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/properties/source
[32]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/properties/targets
[33]: https://apireference.groupdocs.com/net/comparison/groupdocs.comparison.options/previewoptions
[34]: https://products.groupdocs.com/comparison/net
[35]: https://www.nuget.org/packages/GroupDocs.Comparison/
[36]: https://purchase.groupdocs.com/temporary-license
[37]: https://docs.groupdocs.com/display/comparisonnet/Home
[38]: https://forum.groupdocs.com/


