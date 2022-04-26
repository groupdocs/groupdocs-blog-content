---
title: "Afficher les documents Word en tant que page HTML réactive à l'aide de C #"
date: Sat, 28 Aug 2021 12:35:45 +0000
draft: false
url: /fr/2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/
author: 'Shoaib Khan'
summary: "Les pages Web HTML Responsive sont conçues pour avoir une belle apparence sur différents appareils. Ces pages s'ajustent automatiquement en fonction des différentes tailles d'écran. Cet article vous guidera pour automatiser la conversion et afficher vos documents Word sous forme de pages HTML réactives dans vos applications .NET à l'aide de C#."
tags: ['convert docx to html in csharp', 'docx to html responsive', 'view word as html responsive', 'Word to HTML in CSharp']
categories: ['GroupDocs.Viewer Product Family']
---

Les pages Web HTML Responsive sont conçues pour avoir une belle apparence sur différents appareils. Ces pages s'ajustent automatiquement en fonction des différentes tailles d'écran. Cet article vous guidera pour automatiser la conversion et afficher vos documents Word sous forme de pages HTML réactives dans vos applications .NET à l'aide de C#.



{{< figure align=center src="images/word-to-responsive-html-layout-using-dotnet-1024x614.jpg" alt="Mise en page Word vers Responsive HTML à l'aide de l'API C# .NET">}}


Les sujets suivants seront abordés ci-dessous :

* [API .NET pour Word et visionneuse HTML réactive][1]
* [Afficher les documents Word en tant que HTML réactif à l'aide de C #][2]

## API .NET pour Word et lecteur HTML réactif {#html-viewer-dotnet-api}

J'utiliserai [GroupDocs.Viewer pour .NET][3] pour rendre les documents Word sous forme de pages HTML réactives dans les exemples ci-dessous. L'API est une puissante [API .NET de visionneuse de documents qui prend en charge le rendu d'un grand nombre de documents][4]. Il permet de créer une ** visionneuse HTML ** avec des ressources intégrées et externes, une ** visionneuse d'images ** en rendant au format JPG et PNG, et une ** visionneuse PDF ** idéale pour l'impression ou le partage avec d'autres.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][5] ou installer l'API en ajoutant son package à votre application .NET via [NuGet][6].

```
PM> Install-Package GroupDocs.Viewer
```

## Convertir des documents Word en HTML réactif à l'aide de C # {#word-to-html-responsive}

Si vous avez des documents MS Word DOC, DOCX et que vous souhaitez rendre ces documents dans des pages HTML réactives pour bien paraître sur toutes les différentes tailles d'écran, voici les étapes et le code C # pour vous.

Les étapes suivantes montrent comment convertir le document Word (DOC/DOCX) en HTML réactif à l'aide de l'API .NET.

* Chargez le document Word (DOC/DOCX) à l'aide de la classe [Viewer][7].
* Définissez les [HtmlViewOptions][8] pour les ressources intégrées ou externes pour la sortie html.
* Définissez [RenderResponsive][9] sur vrai.
* Appelez la méthode [View][10] de la classe Viewer pour générer les pages Web réactives du document Word chargé.

Le code source suivant à quatre lignes rend le document Word sous forme de code HTML réactif avec des ressources intégrées utilisant C#.

```
// Convertir des documents Word DOC/DOCX en HTML Responsive Page en C#
using (Viewer viewer = new Viewer(@"path/document.docx"))
{
    HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources("path/page_{0}.html");
    options.RenderResponsive = true; // Set the Responsive as true
    viewer.View(options);
}
```

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][11] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

En résumé, vous avez appris à rendre les documents Word sous forme de pages HTML réactives à l'aide de C#. De plus, vous pouvez générer les pages HTML avec des ressources intégrées et externes. Vous devez être confiant pour commencer à créer votre propre application .NET de visionneuse de documents comme celle [conçue par GroupDocs][12].

Pour en savoir plus sur l'API, vous pouvez consulter la [documentation][13] et le référentiel [GitHub][14]. En cas de questions supplémentaires et d'ambiguïtés, contactez le support gratuit sur le [forum][15].

## Voir également

* [Comment afficher des documents Word au format HTML réactif à l'aide de Java][16]
* [Afficher les documents CAO à l'aide de C#][17]
* [Lire et mettre en pause des images animées dans des pages Web à l'aide de C #][18]
* [Rendre les documents Word en HTML minifié à l'aide de C#][19]







[1]: #html-viewer-dotnet-api
[2]: #word-to-html-responsive
[3]: https://products.groupdocs.com/viewer/net/
[4]: https://docs.groupdocs.com/viewer/net/supported-document-formats/
[5]: https://downloads.groupdocs.com/viewer
[6]: https://www.nuget.org/packages/groupdocs.viewer
[7]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[8]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
[9]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions/properties/renderresponsive
[10]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view/index
[11]: https://purchase.groupdocs.com/temporary-license
[12]: https://products.groupdocs.app/viewer/total
[13]: https://docs.groupdocs.com/viewer/net/
[14]: https://github.com/groupdocs-viewer
[15]: https://forum.groupdocs.com/c/assembly
[16]: https://blog.groupdocs.com/2021/09/23/view-word-documents-as-responsive-html-page-using-java/
[17]: https://blog.groupdocs.com/2021/04/27/view-cad-documents-using-charp/
[18]: https://blog.groupdocs.com/2021/02/28/play-pause-animated-gif-and-apng-in-web-pages-using-csharp/
[19]: https://blog.groupdocs.com/2022/02/25/render-word-documents-as-clean-html-using-csharp/


