---
title: "Lire et mettre en pause des images GIF et APNG animées dans des pages Web à l'aide de C#"
date: Sun, 28 Feb 2021 12:52:00 +0000
draft: false
url: /fr/2021/02/28/play-pause-animated-gif-and-apng-in-web-pages-using-csharp/
author: 'Shoaib Khan'
summary: "**GIF** et **APNG** font partie de la liste des formats d'images animées les plus courants. GIF signifie **G**raphics **I**nterchange **F**ormat et les fichiers APNG sont les **A**nimated **P**ortable **N**etwork **G**raphics . Si l'on compare des fichiers GIF et APNG de même qualité, on remarque que les fichiers APNG sont de taille plus petite. Cet article discutera de **lire et mettre en pause les fichiers GIF et APNG animés dans une page Web HTML à l'aide de C#**."
tags: ['Play and Pause Animated Images', 'Play and Pause APNG in CSharp', 'Play and Pause GIF in CSharp', 'Render APNG to HTML in CSharp', 'Render GIF to HTML in CSharp']
categories: ['GroupDocs.Viewer Product Family']
---

**GIF** et **APNG** font partie de la liste des formats d'images animées les plus courants. GIF signifie **G**raphics **I**nterchange **F**ormat et les fichiers APNG sont les **A**nimated **P**ortable **N**etwork **G**raphics . Si l'on compare des fichiers GIF et APNG de même qualité, on remarque que les fichiers APNG sont de taille plus petite. Cet article discutera de **lire et mettre en pause les fichiers GIF et APNG animés dans une page Web HTML à l'aide de C#**.

Les sujets suivants seront abordés ci-dessous :

* [API .NET pour les images animées][1]
* [Lire et mettre en pause l'image APNG animée en HTML à l'aide de C #][2]
* [Lire et mettre en pause l'image GIF animée en HTML à l'aide de C #][3]

## API .NET pour les images animées {#dotnet-api-for-animated-images}

Pour les images animées, j'utiliserai l'API [GroupDocs.Viewer for .NET][4] dans les exemples C# de cet article. Outre le rendu des images GIF et APNG, cette API prend en charge le rendu des documents de traitement de texte, des feuilles de calcul, des PDF, des présentations, des e-mails, des archives ZIP, des dessins Visio et CAO, des images de livres électroniques, des fichiers de code source de programmation et de nombreux autres formats de document.

Vous pouvez télécharger les DLL ou le programme d'installation MSI à partir de la [section des téléchargements][5] ou installer l'API dans votre application .NET via [NuGet][6].

```
PM> Install-Package GroupDocs.Viewer
```

## Lire et mettre en pause des images APNG animées en C # {#play-pause-animated-apng-in-csharp}

Pour afficher le fichier image APNG sur une page HTML, suivez les étapes ci-dessous. Le code source C# et la sortie sont également disponibles ci-dessous.

* Créez un objet de classe [Viewer][7] avec le fichier image APNG.
* Créez l'objet [HTMLViewOptions][8] à l'aide de la méthode **ForEmbeddedResources** et fournissez-lui le fichier HTML de sortie.
* Appelez la méthode [View][9] de l'objet spectateur pour créer la vue de l'image animée APNG.

Voici le code C # qui affiche l'image APNG sur une page Web HTML. Il fournit également l'option de lecture et de pause pour le fichier PNG animé.

```
// Rendre APNG en HTML avec l'option de lecture et de pause
using (Viewer viewer = new Viewer("animation.apng"))
{
    HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources("Web-Page-with-APNG.html");
    viewer.View(options);
}
```

Voici la vue de la page HTML de sortie avec le fichier APNG. À partir de ce lien, vous pouvez également [faire l'expérience de la lecture et de la pause de l'animation APNG][10] créée à l'aide du code C # ci-dessus.



{{< figure align=center src="images/play-pause-APNG-in-CSharp.gif" alt="Pause APNG PNG animé en C #">}}


## Lire et mettre en pause des images GIF animées en C # {#play-pause-animated-gif-in-csharp}

Si vous souhaitez rendre les images GIF sur une page Web HTML, vous pouvez le faire en utilisant le code similaire ci-dessus. L'option de lecture et de pause sera également disponible pour les animations GIF comme pour les animations APNG. L'exemple de code C# suivant restitue le fichier d'animation GIF au format HTML avec l'option de lecture et de pause.

```
// Rendu GIF en HTML avec l'option Lecture et Pause
using (Viewer viewer = new Viewer("animation.gif"))
{
    HtmlViewOptions options = HtmlViewOptions.ForEmbeddedResources("Web-Page-with-gif.html");
    viewer.View(options);
}
```

## Conclusion

Je suis sûr que vous serez sûr d'essayer de rendre des fichiers GIF et APNG animés sur des pages Web HTML à l'aide de C#. Vous pouvez créer votre propre application .NET avec la fonctionnalité de lecture et de pause des animations GIF et APNG en C#.

Pour en savoir plus sur l'API et les images animées, consultez la [documentation][11] ou les exemples open source sur [GitHub][12]. En cas de question ou de confusion, n'hésitez pas à contacter l'assistance sur le [forum][13].

Bonne journée d'animation avec C#.

## Voir également

* [Visionneuse de documents CAO utilisant C# et Java][14]







[1]: #dotnet-api-for-animated-images
[2]: #play-pause-animated-apng-in-csharp
[3]: #play-pause-animated-gif-in-csharp
[4]: https://products.groupdocs.com/viewer/net
[5]: https://downloads.groupdocs.com/viewer/net
[6]: https://www.nuget.org/packages/groupdocs.viewer
[7]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer
[8]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer.options/htmlviewoptions
[9]: https://apireference.groupdocs.com/viewer/net/groupdocs.viewer/viewer/methods/view/index
[10]: https://blog.groupdocs.com/play-pause-apng.html
[11]: https://docs.groupdocs.com/viewer/net
[12]: https://github.com/groupdocs-viewer/GroupDocs.Viewer-for-.NET
[13]: https://forum.groupdocs.com/c/viewer
[14]: https://blog.groupdocs.com/2019/07/13/viewing-cad-documents/


