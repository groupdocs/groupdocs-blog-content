---
title: "Visionneuse de fichiers STL utilisant C#"
date: Tue, 28 Dec 2021 11:00:00 +0000
draft: false
url: /fr/2021/12/28/stl-file-viewer-using-csharp/
author: 'Shoaib Khan'
summary: 'STL (STereoLithography) file format is used for 3D CAD drawings and 3D printing. There are several requirements when the developers are required to programmatically render STL files into various other formats. One of the reasons for conversion is better portability. In this article, you will learn how to render the STL files into PDF format using C#. Additionally, we will convert the STL files to HTML, JPG, and PNG format within .NET application using examples.

Les sujets suivants sont abordés dans cet article :

* API .NET de la visionneuse STL
* Voir STL au format PDF
* Afficher STL au format HTML, JPG, PNG'
tags: ['STL as HTML', 'STL as JPG', 'STL as PNG', 'STL Viewer', 'STL Viewer using C#', 'View STL', 'View STL as PDF']
categories: ['GroupDocs.Viewer Product Family']
---

Le format de fichier STL (**ST**ereo**L**ithography) est utilisé pour les dessins CAO 3D et l'impression 3D. Il existe plusieurs exigences lorsque les développeurs doivent restituer par programmation des fichiers STL dans divers autres formats. L'une des raisons de la conversion est une meilleure portabilité. Dans cet article, vous apprendrez **comment rendre les fichiers STL au format PDF à l'aide de C#**. De plus, nous convertirons les **fichiers STL au format HTML, JPG et PNG** dans l'application .NET à l'aide d'exemples.

Les sujets suivants sont abordés ci-dessous :

* [API .NET de la visionneuse STL][1]
* [Voir STL au format PDF][2]
* [Afficher STL au format HTML, JPG, PNG][3]

## API .NET pour afficher les fichiers STL {#stl-viewer-dotnet-api}

[GroupDocs.Viewer][4] présente [l'API .NET de la visionneuse de documents][5] qui permet de rendre les documents au format PDF, HTML et images dans l'application .NET. Dans cet article, nous l'utiliserons dans des exemples pour convertir les fichiers STL en différents autres formats de fichiers.

Vous pouvez télécharger les DLL ou le programme d'installation MSI à partir de la [section des téléchargements][6] ou installer l'API dans votre application .NET via [NuGet][7].

```
PM> Install-Package GroupDocs.Viewer
```

## Afficher le fichier STL au format PDF à l'aide de C# {#stl-to-pdf}

Il est souvent nécessaire de convertir le format stéréolithographique STL au format PDF en raison de sa grande portabilité. Les étapes suivantes montrent comment convertir les fichiers STL au format PDF à l'aide de C#.

* Chargez le fichier STL à l'aide de la classe [Viewer][8].
* Préparez les options de rendu PDF à l'aide de la classe [PdfViewOptions][9].
* Utilisez la méthode [View()][10] pour rendre le fichier STL au format PDF.

L'exemple de code C# suivant rend les fichiers STL au format PDF.

```
using (Viewer viewer = new Viewer("path/input.stl"))
{
    PdfViewOptions options = new PdfViewOptions("path/stl-output.pdf");
    viewer.View(options);
}
```

## Afficher le fichier STL au format HTML, JPG ou PNG à l'aide de C # {#convert-stl-using-csharp}

De même, vous pouvez convertir les fichiers STL dans d'autres formats selon les besoins. Les étapes suivantes vous aident à rendre les fichiers STL dans divers autres formats à l'aide de C#.

* Chargez le fichier **STL** à l'aide de la classe [Viewer][11].
* Préparez les options de rendu en fonction du format de conversion :
    * Le rendu **HTML** nécessite la classe [](https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions)[HtmlViewOptions][12]. (Vous pouvez utiliser des ressources intégrées ou externes)
    * Le rendu **JPG** utilise la classe [JpgViewOptions][13].
    * Le rendu **PNG** nécessite la classe [PngViewOptions][14].
* Utilisez la méthode [View()][15] pour rendre le fichier STL au format HTML, JPG ou PNG.

Vous trouverez ci-dessous les exemples C# qui restituent séparément les fichiers STL dans chaque format à l'aide des options de format respectives.

### STL vers HTML en utilisant C# {#stl-to-html}

Le code C# suivant convertit le fichier STL en HTML avec des ressources intégrées. De même, vous pouvez convertir en HTML avec des ressources externes.

```
using (Viewer viewer = new Viewer("path/input.stl"))
{
    HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources("path/stl-output.html");
    viewer.View(options);
}
```

### STL en JPG en utilisant C# {#stl-to-jpg}

Le code C# suivant convertit le fichier STL au format d'image JPG.

```
using (Viewer viewer = new Viewer("path/input.stl"))
{
    JpgViewOptions options = new JpgViewOptions("path/stl-output.jpg");
    viewer.View(options);
}
```

### STL vers PNG en utilisant C# {#stl-to-png}

Le code C# suivant convertit le fichier STL au format d'image PNG.

```
using (Viewer viewer = new Viewer("path/input.stl"))
{
    PngViewOptions options = new PngViewOptions("path/stl-output.png");
    viewer.View(options);
}
```

## Obtenez une licence API gratuite

Vous pouvez utiliser les API gratuitement en [obtenant une licence temporaire][16].

## Conclusion

Pour conclure, nous avons appris à rendre les fichiers STL dans d'autres formats. Plus précisément, nous avons converti les fichiers STL aux formats PDF, HTML, JPG et PNG à l'aide de l'exemple C#. Vous pouvez créer votre propre application de visualisation STL comme [Groupdocs.Viewer Online App][17].

Pour en savoir plus sur [GroupDocs.Viewer pour .NET][18], consultez sa [documentation][19]. Pour toute question, contactez-nous via le [forum][20].

## Voir également

* [Code source en PDF en C#][21]
* [Afficher les documents CAO à l'aide de C#][22]
* [Documents Word en tant que page HTML réactive à l'aide de C #][23]


[1]: #stl-viewer-dotnet-api
[2]: #stl-to-pdf
[3]: #convert-stl-using-csharp
[4]: https://products.groupdocs.com/viewer/
[5]: https://products.groupdocs.com/viewer/net/
[6]: https://downloads.groupdocs.com/viewer/net
[7]: https://www.nuget.org/packages/groupdocs.viewer
[8]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[9]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pdfviewoptions
[10]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
[11]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[12]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
[13]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/jpgviewoptions
[14]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/pngviewoptions
[15]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view
[16]: https://purchase.groupdocs.com/temporary-license
[17]: https://products.groupdocs.app/viewer
[18]: https://products.groupdocs.com/viewer/net/
[19]: https://docs.groupdocs.com/viewer/
[20]: https://forum.groupdocs.com/
[21]: https://blog.groupdocs.com/2021/12/03/convert-source-code-to-pdf-in-csharp/
[22]: https://blog.groupdocs.com/2021/04/27/view-cad-documents-using-csharp/
[23]: https://blog.groupdocs.com/2021/08/28/view-word-documents-as-html-responsive-page-using-csharp/


