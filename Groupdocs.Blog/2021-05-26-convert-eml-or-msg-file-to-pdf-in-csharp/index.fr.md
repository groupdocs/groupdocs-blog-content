---
title: "Convertir un fichier EML ou MSG en PDF en C#"
date: Wed, 26 May 2021 12:50:00 +0000
draft: false
url: /fr/2021/05/26/convert-eml-or-msg-file-to-pdf-in-csharp/
aliases:
- /2019/12/06/convert-eml-or-msg-file-to-pdf-in-csharp/
author: 'Shoaib Khan'
summary: "For sharing and referencing the email content, you may need to convert your email message to PDF format. In this article, you will learn the **conversion of email message files like EML and MSG into PDF using C#**. In one of the other blog posts, we have already discussed the [conversion of emails to PDF using Java][1]. This will help to automate the email conversions within your desktop or web-based applications."
tags: ['document conversion', 'email to pdf', 'eml to pdf in csharp', 'msg to pdf in csharp']
categories: ['GroupDocs.Conversion Product Family']
---

Pour partager et référencer le contenu de l'e-mail, vous devrez peut-être convertir votre e-mail au format PDF. Dans cet article, vous apprendrez la **conversion de fichiers de messages électroniques tels que EML et MSG en PDF à l'aide de C#**. Dans l'un des autres articles du blog, nous avons déjà discuté de la [conversion d'e-mails en PDF à l'aide de Java][3]. Cela aidera à automatiser les conversions d'e-mails dans votre bureau ou vos applications Web.



{{< figure align=center src="images/convert-emails-to-pdf-in-dotnet.jpg" alt="Convertir des e-mails en PDF en C#">}}


Les sujets suivants sont traités ci-dessous :

* [Bibliothèque de conversion d'e-mails pour .NET][4]
* [Conversion de MSG en PDF][5]
* [Conversion d'EML en PDF][6]

## API .NET pour la conversion par e-mail {#dotnet-email-conversion-library}

GroupDocs.Conversion pour .NET est l'API qui permet la conversion des messages électroniques vers d'autres formats. Dans cet article, nous utiliserons cette API pour convertir les messages MSG et EML au format PDF à l'aide de C#. De plus, l'API permet la conversion dans les deux sens de documents de traitement de texte, de feuilles de calcul, de présentations, de livres électroniques, d'images et de nombreux autres formats de fichiers dans vos applications .NET.

Vous pouvez télécharger le programme d'installation **DLLs** ou **MSI** à partir de la [section téléchargements][7] ou installer l'API dans votre application .NET via [NuGet][8].

```
PM> Install-Package GroupDocs.Conversion
```

## Convertir MSG en PDF en C# {#msg-to-pdf-in-csharp}

Voici les étapes pour convertir les fichiers Outlook MSG au format PDF.

1. Chargez le fichier MSG à l'aide de la classe [Converter][9].
2. Créez des options de conversion PDF à l'aide de la classe [PdfConvertOptions][10].
3. Appelez la méthode [Convert][11] pour convertir le fichier MSG au format PDF.

Le code source suivant convertit le fichier MSG en PDF à l'aide de C#.

```
// Convertir un message MSG en PDF en C#
using (Converter converter = new Converter("emailMessage.msg"))
{
    PdfConvertOptions options = new PdfConvertOptions();
    converter.Convert("msg-Message.pdf", options);
}
```

Vous trouverez ci-dessous le fichier Microsoft Outlook MSG. De plus, le fichier PDF est également affiché ici, qui est obtenu après conversion du fichier MSG à l'aide du code ci-dessus.



{{< figure align=center src="images/MSG-message.png" alt="Fichier MSG à convertir en PDF" caption="Fichier MSG">}}




{{< figure align=center src="images/converted-msg-to-pdf-in-java.png" alt="Fichier PDF converti à partir de MSG" caption="Fichier PDF converti à partir du format MSG à l'aide du code C# ci-dessus.">}}


## Convertir EML en PDF en utilisant C# {#eml-to-pdf-in-csharp}

Si vous souhaitez convertir vos e-mails stockés au format EML au format PDF, cela peut être fait efficacement en utilisant des lignes de code similaires. Voici les étapes pour convertir des fichiers EML en PDF.

1. Chargez le fichier de message EML à l'aide de la classe [Converter][12].
2. À l'aide de la classe [PdfConvertOptions][13], créez des options de conversion pour le fichier PDF.
3. Appelez la méthode [Convert][14] pour convertir les fichiers EML au format PDF. Passez le chemin du fichier PDF résultant et les options de conversion en tant que paramètres.

```
// Convertir un message EML en PDF en C#
using (Converter converter = new Converter("emailMessage.eml"))
{
    PdfConvertOptions options = new PdfConvertOptions();
    converter.Convert("eml-Message.pdf", options);
}
```

Vous trouverez ci-dessous le fichier EML et les captures d'écran du fichier PDF converti, qui ont été convertis à l'aide du code ci-dessus.



{{< figure align=center src="images/EML-message.png" alt="Fichier EML à convertir en PDF" caption="Fichier EML">}}




{{< figure align=center src="images/converted-eml-to-pdf-in-java.png" alt="Fichier PDF converti à partir d'EML" caption="Fichier PDF converti à partir du format EML à l'aide de C#.">}}


De plus, vous pouvez modifier l'apparence des fichiers PDF de sortie selon vos besoins. Vous pouvez visiter [documentation][15] à ces fins et pour de nombreuses autres fonctionnalités.

## Obtenez une licence API gratuite {#Get-a-Free-API-License}

Vous pouvez [obtenir une licence temporaire gratuite][16] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour conclure, nous avons appris à convertir les fichiers EML et MSG en PDF à l'aide de l'API de conversion .NET. De plus, nous pouvons appliquer par programmation la personnalisation sur les fichiers PDF pour obtenir le résultat dans le style souhaité.

Vous pouvez en savoir plus sur GroupDocs.Conversion pour .NET en utilisant [documentation][17]. De nombreux autres exemples sont disponibles sur [GitHub][18]. Pour toute question, contactez-nous via le [forum][19].

## Voir également

* [Feuilles de calcul Excel en PDF en C#][20]
* [Images en PDF en C#][21]
* [Présentations au format PDF en C#][22]
* [](https://blog.groupdocs.com/2019/12/06/convert-eml-or-msg-file-to-pdf-in-csharp/)[E-mails en PDF en Java][23]







[1]: https://blog.groupdocs.com/2020/09/02/convert-msg-and-eml-files-to-pdf-in-java/
[2]: https://blog.groupdocs.com/2021/05/26/convert-eml-or-msg-file-to-pdf-in-csharp/
[3]: https://blog.groupdocs.com/2020/09/02/convert-msg-and-eml-files-to-pdf-in-java/
[4]: #dotnet-email-conversion-library
[5]: #msg-to-pdf-in-csharp
[6]: #eml-to-pdf-in-csharp
[7]: https://downloads.groupdocs.com/conversion
[8]: https://www.nuget.org/packages/groupdocs.conversion
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[10]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[11]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[12]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter
[13]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.convert/pdfconvertoptions
[14]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion/converter/methods/convert/index
[15]: https://docs.groupdocs.com/conversion/
[16]: https://purchase.groupdocs.com/temporary-license
[17]: https://docs.groupdocs.com/conversion/
[18]: https://github.com/groupdocs-conversion
[19]: https://forum.groupdocs.com/
[20]: https://blog.groupdocs.com/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/
[21]: https://blog.groupdocs.com/2021/05/19/convert-images-to-pdf-in-csharp/
[22]: https://blog.groupdocs.com/2020/03/05/convert-presentations-pptx-ppt-to-pdf-in-csharp/
[23]: https://blog.groupdocs.com/2020/09/02/convert-msg-and-eml-files-to-pdf-in-java/


