---
title: "Afficher des documents CAO à l'aide de C#"
date: Tue, 27 Apr 2021 20:23:00 +0000
draft: false
url: /fr/2021/04/27/view-cad-documents-using-csharp/
aliases:
- /2021/04/27/view-cad-documents-using-charp/
author: 'Shoaib Khan'
summary: '**CAD** (**C**omputer-**A**ided **D**esign) drawings are normally used to create architectural plans and models using CAD software programs. Some of the well-known AutoCAD file formats are **DWG, DXF, DGN, DWF**. We discussed [viewing the CAD drawings using Java][1] in a separate article. Today, in this article, we will discuss how to programmatically view CAD files using C# within .NET applications.

Les sujets suivants sont abordés brièvement dans cet article :

* API .NET pour rendre les fichiers CAO.
* Convertissez des fichiers CAO pour les rendre au format HTML, JPG, PNG ou PDF.
* Obtenez des mises en page et des couches de DWG.
* Rendre les couches CAO des dessins DWG.
* Rendre les mises en page CAO des dessins DWG.

[Continuer la lecture...][2]'
tags: ['CAD Viewer in CSharp', 'Convert DWG to HTML in CSharp', 'Convert DWG to JPG in CSharp', 'DWG Viewer using CSharp']
categories: ['GroupDocs.Viewer Product Family']
---

Les dessins **CAO** (_Conception assistée par ordinateur_) sont normalement utilisés pour créer des plans et des modèles architecturaux à l'aide de logiciels de CAO. Certains des formats de fichiers AutoCAD les plus connus sont **DWG, DXF, DGN, DWF**. Nous avons discuté de [l'affichage des dessins CAO à l'aide de Java][3] dans un article séparé. Aujourd'hui, dans cet article, nous expliquerons comment afficher par programmation des fichiers CAO à l'aide de C # dans des applications .NET.

Les sujets suivants sont brièvement abordés ci-dessous :

* [API .NET pour rendre les fichiers CAO][4].
* [Convertir les fichiers CAO pour les rendre au format HTML, JPG, PNG ou PDF][5].
* [Obtenir les mises en page et les calques de DWG][6].
* [Rendre les couches CAO des dessins DWG][7].
* [Rendre les mises en page CAO des dessins DWG][8].

## API de visualisation CAO .NET - DWG, DXF, DWF, DGN {#dotnet-api-to-render-cad-files}

Dans cet article, j'utiliserai [GroupDocs.Viewer pour .NET][9] qui permet de rendre par programme les fichiers CAO tels que DWG en PDF, JPG, PNG et HTML dans les applications .NET. En plus de DWG, l'API prend en charge les documents DWF, DGN, DWT, DXF, IFC, STL, Plotter et [beaucoup plus][10].

Outre les formats de fichiers CAO, l'API fournit les mêmes fonctionnalités de rendu pour les documents de traitement de texte, les feuilles de calcul, les présentations, les pages Web, les images, les vecteurs, les livres électroniques, les dessins Visio, de nombreux fichiers de code source de différents langages de programmation.

Téléchargez le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][11] ou installez l'API dans votre application .NET via [NuGet][12].

```
PM> Install-Package GroupDocs.Viewer
```

## Convertir des dessins CAO pour les afficher au format HTML, PNG, JPG ou PDF en C# {#convert-cad-to-html-jpg-jpg-pdf-in-csharp}

Dans cet article, j'utilise uniquement le format DWG pour la conversion et le rendu vers d'autres formats avec des exemples. Commençons par la conversion du fichier de conception DWG pour le rendre au format HTML avec des options de ressources intégrées et externes à l'aide de C#.

### Convertir DWG en HTML avec des ressources intégrées en C#

Voici les étapes de conversion du fichier DWG pour le rendre au format HTML.

* Chargez le fichier DWG à l'aide de la classe [Viewer][13].
* Créez [HtmlViewOptions][14] en utilisant la méthode _[forEmbeddedResources][15]_.
* Rendez .dwg en HTML en utilisant la méthode _[View][16]_.

Le code source suivant convertit le fichier DWG et le restitue au format HTML avec des ressources intégrées à l'aide de C#.

```
// Rendre le dessin CAO DWG pour l'afficher au format HTML avec des ressources intégrées à l'aide de C#
using (Viewer viewer = new Viewer("drawing.dwg"))
{
    HtmlViewOptions viewOptions = HtmlViewOptions.ForEmbeddedResources("page_{0}.html");
    viewer.View(viewOptions);
}
```

### Convertir DWG en HTML avec des ressources externes en C#

Voici les étapes pour convertir le fichier DWG et le rendre sous forme de fichier(s) HTML avec des ressources externes.

* Chargez le fichier DWG à l'aide de la classe [Viewer][17].
* Créez [HtmlViewOptions][18] en utilisant la méthode _[forExternalResources][19]_.
* Rendu .dwg au format HTML en utilisant la méthode _[View][20]_.

Le code source suivant affiche le fichier DWG au format HTML avec des ressources externes en C#.

```
// Rendre le dessin CAO C# pour l'afficher au format HTML avec des ressources externes à l'aide de C#
using (Viewer viewer = new Viewer("drawing.dwg"))
{
    HtmlViewOptions viewOptions = HtmlViewOptions.ForExternalResources(
        "page_{0}.html","page_{0}/resource_{1}","page_{0}/resources");

    viewer.View(viewOptions);
}
```

### Convertir DWG en PDF, JPG et PNG en C#

Tout comme la conversion au format HTML, les fichiers DWG peuvent être rendus au format PDF, PNG et JPG à l'aide des [ViewOptions][21] respectifs comme suit :

* Rendu **HTML** à l'aide de [HtmlViewOptions][22].
* Rendu **JPG** à l'aide de [JpgViewOptions][23].
* Rendu **PNG** avec [PngViewOptions][24].
* Rendu **PDF** à l'aide de [PdfViewOptions][25].

## Obtenir des mises en page et des calques de DWG en C # {#get-layout-and-layers-of-dwg-in-csharp}

Les fichiers CAO peuvent contenir plusieurs mises en page et couches, vous pouvez obtenir ces mises en page et couches en suivant les étapes suivantes.

* Chargez le fichier DWG à l'aide de la classe [Viewer][26].
* Créez les [ViewInfoOptions][27] pour le rendu de vue HTML.
* À l'aide de Viewer, obtenez le [CadViewInfo][28] qui a des mises en page.
* Obtenez les mises en page de CadViewInfo et parcourez-les.
* De même, récupérez les calques de CadViewInfo et parcourez-les.

Le code suivant montre comment obtenir les mises en page et les calques du fichier ا DWG à l'aide de C#.

```
// Obtenir des mises en page et des calques de dessin CAO DWG en C#
using (Viewer viewer = new Viewer("drawing.dwg"))
{
    ViewInfoOptions viewInfoOptions = ViewInfoOptions.ForHtmlView();
    CadViewInfo viewInfo = viewer.GetViewInfo(viewInfoOptions) as CadViewInfo;

    Console.WriteLine("File type: " + viewInfo.FileType);
    Console.WriteLine("Pages count: " + viewInfo.Pages.Count);

    foreach (Layout layout in viewInfo.Layouts)
        Console.WriteLine(layout);

    foreach (Layer layer in viewInfo.Layers)
        Console.WriteLine(layer);
}
```

## Rendre les couches CAO du fichier DWG en C# {#render-layers-of-dwg-in-csharp}

Si vous ne souhaitez pas rendre tous les calques mais seulement certains calques spécifiques du DWG, vous pouvez le faire en définissant des noms de calques.

* Chargez le dessin DWG à l'aide de la classe [Viewer][29].
* Créer des options d'affichage.
* **Ajouter des couches CAO aux options d'affichage**
* Rendez DWG en HTML en utilisant la méthode _[View][30]_.

Le code suivant rend les calques d'un fichier CAO au format DWG en C#.

```
// Rendre les couches du dessin CAO .dwg en C#
using (Viewer viewer = new Viewer("drawing.dwg"))
{
    HtmlViewOptions viewOptions = HtmlViewOptions.ForEmbeddedResources();
    viewOptions.CadOptions.Layers = new List<Layer>
    {
        new Layer("Walls"),
        new Layer("Windows")
    };
    viewer.View(viewOptions);
}
```

## Rendu des mises en page CAO du fichier DWG en C # {#render-layouts-of-dwg-in-csharp}

Par défaut, nous n'obtenons la présentation du modèle que lorsque nous rendons un fichier CAO. Nous pouvons définir des propriétés pour rendre toutes les mises en page non vides avec le modèle.

* Chargez le dessin DWG à l'aide de la classe [Viewer][31].
* Créer des options d'affichage.
* **Définissez la propriété Render Layouts sur true.**
* Rendre DWG en HTML en utilisant la méthode _[View][32]_.

Le code suivant restitue toutes les mises en page non vides avec le modèle d'un dessin CAO au format DWG en C#.

```
// Dispositions de rendu du dessin CAO .dwg en C#
using (Viewer viewer = new Viewer("drawing.dwg"))
{
   HtmlViewOptions viewOptions = HtmlViewOptions.ForEmbeddedResources();
   viewOptions.CadOptions.RenderLayouts = true;
   viewer.View(viewOptions);
}
```

## Obtenez une licence API gratuite {#Get-a-Free-API-License}

Vous pouvez [obtenir une licence temporaire gratuite][33] afin d'utiliser l'API sans limitation d'évaluation.

## Conclusion

Pour conclure, j'espère que vous avez appris à visualiser les fichiers CAO en C # dans les applications .NET. De plus, vous avez vu comment obtenir et afficher des modèles, des mises en page et des couches de fichiers CAO dans votre application. Vous devez être sûr de pouvoir créer votre propre visionneuse CAO à l'aide de C#. Vous pouvez [faire l'expérience des applications en ligne pour afficher n'importe lequel de vos fichiers][34]. Ceux-ci sont construits à l'aide de GroupDocs.Viewer.

Vous pouvez en savoir plus sur GroupDocs.Viewer pour .NET en utilisant la [documentation][35]. Si vous avez des questions, n'hésitez pas à nous le faire savoir via notre [forum][36].

## Voir également

* [Afficher les documents CAO à l'aide de Java][37]
* [Convertir des dessins CAO en PDF en C#][38]
* [Rendre les documents Word en HTML propre à l'aide de C#][39]







[1]: https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/
[2]: https://blog.groupdocs.com/2021/04/27/view-cad-documents-using-charp/
[3]: https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/
[4]: #dotnet-api-to-render-cad-files
[5]: #convert-cad-to-html-jpg-jpg-pdf-in-csharp
[6]: #get-layout-and-layers-of-dwg-in-csharp
[7]: #render-layers-of-dwg-in-csharp
[8]: #render-layouts-of-dwg-in-csharp
[9]: https://products.groupdocs.com/conversion/net
[10]: https://docs.groupdocs.com/viewer/net/supported-document-formats/
[11]: https://downloads.groupdocs.com/viewer/net
[12]: https://www.nuget.org/packages/groupdocs.viewer
[13]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[14]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
[15]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions/methods/forembeddedresources/index
[16]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view/index
[17]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[18]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
[19]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions/methods/forexternalresources/index
[20]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view/index
[21]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/viewoptions
[22]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
[23]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/jpgviewoptions
[24]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pngviewoptions
[25]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
[26]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[27]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/viewinfooptions
[28]: https://apireference.groupdocs.com/viewer/java/com.groupdocs.viewer.results/CadViewInfo
[29]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[30]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view/index
[31]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[32]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view/index
[33]: https://purchase.groupdocs.com/temporary-license
[34]: https://products.groupdocs.app/viewer/family
[35]: https://docs.groupdocs.com/viewer/net/
[36]: https://forum.groupdocs.com/
[37]: https://blog.groupdocs.com/2021/04/05/viewing-cad-documents-using-java/
[38]: https://blog.groupdocs.com/2020/11/08/convert-cad-drawings-to-pdf-in-csharp/
[39]: https://blog.groupdocs.com/2022/02/25/render-word-documents-as-clean-html-using-csharp/


