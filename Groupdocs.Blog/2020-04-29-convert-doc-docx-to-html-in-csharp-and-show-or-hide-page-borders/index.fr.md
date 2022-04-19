---
title: "Afficher et masquer les bordures de page lors de la conversion de documents en HTML en C#"
date: Wed, 29 Apr 2020 20:18:10 +0000
draft: false
url: /fr/2020/04/29/convert-doc-docx-to-html-in-csharp-and-show-or-hide-page-borders/
author: 'Shoaib Khan'
summary: "Soit vous souhaitez convertir un document au format HTML pour obtenir le contenu de votre site Web, soit vous avez rencontré un site Web de soumission de documents en ligne qui exige que les documents soient soumis au format HTML. Dans les deux cas, vous avez besoin d'un **convertisseur DOC vers HTML**. Cependant, si vous avez besoin de convertir vos **documents en HTML par programmation**, cet article est pour vous uniquement. Cet article couvrira les manières suivantes de convertir des documents en HTML en C# :"
tags: ['convert document to html in csharp', 'convert docx to html', 'convert docx to html in csharp', 'convert to html', 'show or hide html page borders']
categories: ['GroupDocs.Conversion Product Family']
---



{{< figure align=center src="images/convert-doc-to-html-with-show-and-hide-borders.png" alt="Convertir DOCX en HTML dans CSharp">}}


Soit vous souhaitez convertir un document au format HTML pour obtenir le contenu de votre site Web, soit vous avez rencontré un site Web de soumission de documents en ligne qui exige que les documents soient soumis au format HTML. Dans les deux cas, vous avez besoin d'un **convertisseur DOC vers HTML**. Cependant, si vous avez besoin de convertir vos **documents en HTML par programmation**, cet article est pour vous uniquement. Cet article couvrira les manières suivantes de convertir des documents en HTML en C# :

* Conversion la plus simple de documents comme DOCX en HTML en C#.
* Convertir en HTML avec des options personnalisées.
* Convertir en utilisant l'option pour afficher ou masquer les bordures de page.

## Bibliothèque de conversion de documents C#

[GroupDocs.Conversion pour .NET][1] est une API puissante et facile à utiliser avec la possibilité de convertir n'importe quel document de la vaste liste de [formats de document pris en charge][2] dans n'importe quel format cible pris en charge. Vous pouvez télécharger l'API à partir de la section [téléchargements][3] ou l'installer à partir de [NuGet][4].

## Convertir DOCX en HTML en C# - Simple

C'est la conversion la plus simple et la plus utile. Je dirais plutôt que vous pouvez convertir n'importe lequel de vos documents au format HTML. Vérifiez simplement votre format dans la [liste des formats pris en charge][5] et lancez-vous pour le convertir.

* Créez l'instance de la classe [Converter][6] pour commencer avec votre document source.
* Instancier l'objet [MarkupConvertOptions][7].
* Appelez la méthode [Convert][8] de la classe Converter.
* C'est ça.

Votre document sera converti en HTML et le document résultant sera là dans votre référentiel. Le petit exemple de code suivant montre la conversion d'un fichier **DOCX en HTML** à l'aide de la classe Converter en C#.

```
// Converting DOCX to HTML in C#
using (Converter converter = new Converter("document.docx"))
{
    MarkupConvertOptions options = new MarkupConvertOptions();
    converter.Convert("converted.html", options);
}
```

## Convertir DOC/DOCX en HTML avec des options personnalisées

GroupDocs.Conversion fournit différentes autres options pour obtenir le résultat de conversion souhaité. Les options personnalisées incluent :

* Disposition fixe
* Disposition fixe - Afficher les bordures
*Format
* Numéro de page
* Pages
* Nombre de pages
* Utilisez PDF
* Filigrane
* Zoom

Vous pouvez consulter la [documentation][9] ou les [exemples GitHub][10] pour voir chaque option en détail. Je vais montrer certaines des personnalisations tout en convertissant à nouveau le format DOCX au format HTML dans l'exemple de code ci-dessous.

```
// Converting DOCX to HTML in C# with advance options.
using (Converter converter = new Converter("document.docx"))
{
    MarkupConvertOptions options = new MarkupConvertOptions
    { // Setting customized options
        PageNumber = 2,
        PagesCount = 1,
        FixedLayout = true
    };
    converter.Convert("converted.html", options);
}
```

## Convertir DOC/DOCX en HTML - Afficher ou masquer les bordures de page

Enfin, vous pouvez désormais contrôler la visibilité des bordures de page lors de la conversion de documents en HTML en C#. Le GroupDocs.Conversion pour .NET donne ce contrôle aux programmeurs C#. L'exemple ci-dessous montre qu'en définissant la propriété [FixedLayoutShowBorders][11] de la classe [MarkupConvertOptions][12] sur true ou false, vous pouvez afficher ou masquer les bordures de page dans le document HTML résultant.

```
// Converting DOCX to HTML in C# with show or hide borders control.
using (Converter converter = new Converter("document.docx"))
{
    MarkupConvertOptions options = new MarkupConvertOptions
    {
        PageNumber = 2,
        FixedLayout = true,
        PagesCount = 1,
        FixedLayoutShowBorders = false
    };
    converter.Convert("converted.html", options);
}
```

Images ci-dessous montrant le document DOCX original et le HTML converti avec et sans bordures de page.



{{< figure align=center src="images/word-docx-document-1-759x1024.png" alt="Document Docx à convertir en HTML" caption="Document DOCX original">}}




{{< figure align=center src="images/doc-to-html-file-with-borders-and-no-borders-1024x716.jpg" alt="Fichier HTML avec bordures de page et sans bordures." caption="<em>La figure ci-dessus montre les fichiers HTML qui sont convertis à partir de DOCX avec afficher les bordures et ne pas afficher les options de bordures.</em>">}}


## En savoir plus sur GroupDocs.Conversion

* [Documents][13]
* [Exemples de code source][14]
* [GroupDocs.Conversion - La solution de conversion de documents et d'images][15]

**Parlons plus @** [Forum d'assistance gratuit][16].







[1]: https://products.groupdocs.com/conversion/net
[2]: https://docs.groupdocs.com/display/conversionnet/Supported+Document+Formats
[3]: https://downloads.groupdocs.com/conversion/net
[4]: https://www.nuget.org/packages/groupdocs.conversion
[5]: https://docs.groupdocs.com/display/conversionnet/Supported+Document+Formats
[6]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[7]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/markupconvertoptions
[8]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.converter/convert/methods/4
[9]: https://docs.groupdocs.com/display/conversionnet/Convert+to+HTML+with+advanced+options
[10]: https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET/blob/master/Examples/GroupDocs.Conversion.Examples.CSharp/AdvancedUsage/Converting/ConvertToHtmlWithAdvancedOptions.cs
[11]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/markupconvertoptions/properties/fixedlayoutshowborders
[12]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/markupconvertoptions
[13]: https://docs.groupdocs.com/display/conversionnet/Getting+Started
[14]: https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET
[15]: https://products.groupdocs.com/conversion
[16]: https://forum.groupdocs.com/c/conversion


