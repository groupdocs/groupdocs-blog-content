---
title: "Convertir des dessins CAO en PDF en C#"
date: Sun, 08 Nov 2020 04:03:43 +0000
draft: false
url: /fr/2020/11/08/convert-cad-drawings-to-pdf-in-csharp/
author: 'Shoaib Khan'
summary: "Aujourd'hui, nous allons apprendre à convertir par programmation les dessins CAO au format PDF en C#. Auparavant, dans un [article précédent][1], nous faisions la même chose mais en Java. Nous avons cherché à convertir les fichiers DWG, DGN et DWF en document PDF avec l'exemple de code. Faisons-le en C# en utilisant l'API de conversion de documents pour .NET."
tags: ['convert cad to pdf', 'convert cad to pdf in csharp', 'convert dgn to pdf in csharp', 'convert dwf to pdf in csharp', 'convert dwg to pdf in csharp']
categories: ['GroupDocs.Conversion Product Family']
---

Aujourd'hui, nous allons apprendre à convertir par programmation les dessins CAO au format PDF en C#. Auparavant, dans un [article précédent][2], nous faisions la même chose mais en Java. Nous avons cherché à convertir les fichiers DWG, DGN et DWF en documents PDF avec l'exemple de code. Faisons-le en C# en utilisant l'API de conversion de documents pour .NET.



{{< figure align=center src="images/convert-cad-drawings-to-pdf-using-dotnet.png" alt="Convertir des dessins CAO en PDF dans .NET">}}


Les sujets suivants seront abordés dans cet article :

* [API C # pour convertir des dessins CAO][3]
* [Conversion de dessins CAO (DWG, DWF, DGN) en PDF en C#][4]

## API C# pour convertir des dessins CAO {#cad-conversion-dotnet-lib}



{{< figure align=center src="images/groupdocs-conversion-net.png" alt="Convertir des documents et des images à l'aide de .NET">}}


[GroupDocs.Conversion pour .NET][5] est l'API de conversion avancée pour les documents et les images dans n'importe quelle application .NET. Il prend en charge de nombreux formats de fichiers, notamment des documents de traitement de texte, des feuilles de calcul, des présentations, des images, des dessins CAO et bien d'autres.

Cet article utilisera GroupDocs.Conversion pour l'API .NET pour la **conversion de dessins CAO au format PDF en C#**. Vous pouvez [télécharger][6] la DLL ou l'installer à l'aide de [NuGet][7].

```
PM> Install-Package GroupDocs.Conversion
```

## Convertir des dessins CAO (DWG, DWF, DGN) en PDF en C# {#convert-cad-dwg-dwf-dgn-to-pdf-in-java}

Les étapes suivantes permettront une conversion facile des dessins CAO avec de nombreuses options en un fichier PDF personnalisé.

* **Charger** le dessin CAO.
* Spécifiez les **dispositions** et les **options**.
* **Convertir** CAO avec options en PDF.

### Charger les dessins CAO

Chargez le fichier CAO à l'aide de la classe [CadLoadOptions][8].

```
CadLoadOptions loadOptions =  new CadLoadOptions();
```

### Spécifier les mises en page et autres options

Vous pouvez spécifier certaines [propriétés][9] lors du chargement des fichiers CAO. Ces propriétés incluent **noms de mise en page**, **largeur**, **hauteur** et **format**. Spécifier des noms de mise en page vous permettra de convertir uniquement la mise en page mentionnée.

```
Contracts.Func<LoadOptions> getLoadOptions = () => new CadLoadOptions
{
    LayoutNames = new \[\]{ "Layout1", "Layout3" },
    Width = 1920,
    Height = 1080
};
```

### Convertir des dessins CAO - DWG, DWF en PDF en C#

Désormais, en utilisant la méthode Convert de la classe Converter, les fichiers DWG ou DWF peuvent être facilement convertis au format PDF à l'aide des options définies.

```
using (Converter converter = new Converter("with\_layers\_and\_layouts.dwf", getLoadOptions))
{
    PdfConvertOptions options = new PdfConvertOptions();
    converter.Convert("converted.pdf", options);
}
```

### Code complet

Voici le code C# complet, que vous pouvez utiliser pour convertir des fichiers DWG ou DWF en PDF en suivant les étapes, c'est-à-dire **Charger** -> Spécifier **Mise en page et options** -> **Convertir**.

```
// Convertir un dessin CAO - DWF en PDF en C# à l'aide de GroupDocs.Conversion pour .NET
// Options de chargement
Contracts.Func<LoadOptions> getLoadOptions = () => new CadLoadOptions
{
  LayoutNames = new []{ "Layout1", "Layout3" }, // Specifying Layouts
  // Width = 1920,
  // Height = 1080
};
using (Converter converter = new Converter("filePath/CAD-Drawing.dwf", getLoadOptions))
{
  PdfConvertOptions options = new PdfConvertOptions();
  converter.Convert("filePath/cadToPDF-NET.pdf", options);
}
```

Il existe de nombreuses autres options de personnalisation pour le format PDF résultant qui permettent de contrôler le résultat de sortie lors de la conversion de tout document au format PDF. Vous pouvez consulter ces options avancées dans l'article de documentation suivant.

[Convertir en PDF avec les options avancées dans .NET][10]

Avec une modification mineure, nous pouvons convertir d'autres fichiers CAO comme les fichiers DGN et DWG en conséquence. Il suffit de fournir le bon nom de fichier et son format dans le code ci-dessus. Pour un format de fichier qui ne prend pas en charge les mises en page, nous ne définirons pas **LayoutNames**. Pour de si petites modifications, vous pouvez consulter la [documentation][11].

## Conclusion

J'espère que vous êtes maintenant à l'aise avec la conversion de fichiers CAO tels que DWG, DGN et DWF en PDF en C # à l'aide de GroupDocs.Conversion dans vos applications .NET et Java. Vous pouvez désormais créer vos propres applications de conversion à l'aide de n'importe quelle plate-forme, tout comme les [applications gratuites][12] disponibles sur www.groupdocs.app.

Vous pouvez contacter l'**équipe d'assistance gratuite pour toute autre question**, qui est toujours disponible pour vous aider sur le [forum][13].

## Articles Liés

* [Convertir des dessins CAO en PDF en Java][14]
* [Feuilles de calcul Excel en PDF en utilisant C#][15]
* [Charger des documents CAO][16]
* [Convertir des documents et des images en PDF][17]







[1]: https://blog.groupdocs.com/2020/10/31/convert-cad-drawings-to-pdf-in-java/
[2]: https://blog.groupdocs.com/2020/10/31/convert-cad-drawings-to-pdf-in-java/
[3]: #cad-conversion-java-lib
[4]: #convert-cad-dwg-dwf-dgn-to-pdf-in-java
[5]: https://products.groupdocs.com/conversion/net
[6]: https://downloads.groupdocs.com/conversion/net
[7]: https://www.nuget.org/packages/groupdocs.conversion
[8]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.load/CadLoadOptions
[9]: https://apireference.groupdocs.com/conversion/net/groupdocs.conversion.options.load/cadloadoptions/properties/index
[10]: https://docs.groupdocs.com/conversion/net/convert-to-pdf-with-advanced-options/
[11]: https://docs.groupdocs.com/conversion/net/
[12]: https://products.groupdocs.app/conversion/total
[13]: https://forum.groupdocs.com/c/conversion
[14]: https://blog.groupdocs.com/2020/10/31/convert-cad-drawings-to-pdf-in-java/
[15]: https://blog.groupdocs.com/2021/11/14/convert-excel-spreadsheets-to-pdf-using-csharp/
[16]: https://docs.groupdocs.com/conversion/net/load-cad-document-with-options/
[17]: https://docs.groupdocs.com/conversion/net/convert/pdf/


