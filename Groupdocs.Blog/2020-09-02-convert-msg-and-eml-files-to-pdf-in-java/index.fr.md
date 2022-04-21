---
title: "Convertir des fichiers MSG et EML en PDF en Java"
date: Wed, 02 Sep 2020 14:04:02 +0000
draft: false
url: /fr/2020/09/02/convertir-les-fichiers-msg-et-eml-en-pdf-en-java/
author: 'Shoaib Khan'
summary: "Les conversions d'e-mails en PDF sont souvent nécessaires pour le référencement et les exigences telles que le partage du contenu de l'e-mail. Dans cet article, nous allons découvrir **comment convertir des fichiers de messages électroniques tels que MSG et EML en PDF à l'aide de Java**. Auparavant, dans l'un des [articles de blog précédents][1], nous avons déjà appris à convertir des fichiers MSG et EML à l'aide de C# dans une application .NET. Cela aidera à automatiser la conversion des e-mails dans les applications de bureau ou Web."
tags: ['convert emails to pdf', 'Convert MSG or EML to PDF in Java', 'eml to pdf in java', 'MSG to PDF in Java']
categories: ['GroupDocs.Conversion Product Family']
---



{{< figure align=center src="images/Convert-Emails-to-PDF-in-Java.png" alt="Convertir des e-mails en PDF en Java">}}


Les conversions d'e-mails en PDF sont souvent nécessaires pour le référencement et les exigences telles que le partage du contenu de l'e-mail. Dans cet article, nous allons découvrir **comment convertir des fichiers de messages électroniques tels que MSG et EML en PDF à l'aide de Java**. Auparavant, dans l'un des [articles de blog précédents][2], nous avons déjà appris à convertir des fichiers MSG et EML à l'aide de C# dans une application .NET. Cela aidera à automatiser la conversion des e-mails dans les applications de bureau ou Web.

Voici les sujets abordés dans cet article :

* [Bibliothèque de conversion Java][3]
* [Conversion de MSG en PDF à l'aide de Java][4]
* [Conversion d'EML en PDF à l'aide de Java][5]

## Bibliothèque de conversion Java {#java-conversion-library}

Dans cet article, j'utiliserai l'API [GroupDocs.Conversion for Java][6] pour les conversions. En l'utilisant, vous pouvez convertir des formats de documents de courrier électronique tels que MSG et EML en PDF et en d'autres formats sans perdre le format de courrier électronique.

Vous pouvez obtenir le fichier JAR à partir de la section [downloads][7]. Pour les applications basées sur maven, voici la configuration pom.xml :

```
<repository>
	<id>GroupDocsJavaAPI</id>
	<name>GroupDocs Java API</name>
	<url>http://repository.groupdocs.com/repo/</url>
</repository>
```
```
<dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-conversion</artifactId>
        <version>20.6</version> 
</dependency>
```

## Convertir MSG en PDF en utilisant Java {#convert-msg-to-pdf-in-java}

Voici les étapes pour convertir les fichiers Outlook MSG en PDF avec seulement quelques lignes de code. Des liens intégrés dans les étapes permettront d'explorer davantage les classes et les méthodes.

1. Créez une instance de la classe [Converter][8] et transmettez le fichier MSG au constructeur.
2. Instanciez la classe [PdfConvertOptions][9].
3. Appelez la méthode [convert][10] pour obtenir le fichier PDF converti.

```
import com.groupdocs.conversion.Converter;
import com.groupdocs.conversion.options.convert.PdfConvertOptions;

public class EmailMessagesConverter 
{
	// Convert MSG message to PDF
	public void convertMsgtoPDF(String filePath) 
	{
		Converter converter = new Converter(filePath + "emailMessage.msg");
		PdfConvertOptions options = new PdfConvertOptions();
		converter.convert(filePath + "msg-Message.pdf", options);
	}
}
```

Voici l'exemple de fichier MSG créé à l'aide de Microsoft Outlook. Plus bas se trouve le fichier PDF, obtenu en convertissant le fichier MSG à l'aide du code Java mentionné ci-dessus.



{{< figure align=center src="images/MSG-message.png" alt="Fichier MSG à convertir en PDF" caption="Fichier MSG">}}




{{< figure align=center src="images/converted-msg-to-pdf-in-java.png" alt="Fichier PDF converti à partir de MSG" caption="Fichier PDF converti à partir du format MSG à l'aide du code Java ci-dessus.">}}


## Convertir EML en PDF en utilisant Java {#convert-eml-to-pdf-in-java}

Nous pouvons convertir par programmation nos e-mails stockés au format EML, au format PDF avec des lignes de code Java similaires très facilement et efficacement. Les étapes suivantes guideront pour atteindre l'objectif.

1. Initialisez l'objet [Converter][11] fournissant le chemin du fichier EML source.
2. Initialisez les [PDFConvertOptions][12]. Vous pouvez définir une personnalisation supplémentaire pour le fichier PDF résultant.
3. Appelez simplement la méthode [convert][13] de la classe Converter et transmettez-lui le chemin du fichier PDF résultant et les PDFConvertOptions déjà définis en tant que paramètres.

```
// Convertir un message EML en PDF
public void convertEmltoPDF(String filePath) 
{
	Converter converter = new Converter(filePath + "emailMessage.eml");
	PdfConvertOptions options = new PdfConvertOptions();
	converter.convert(filePath + "eml-Message.pdf", options);
}
```

Vous trouverez ci-dessous le fichier EML source et les captures d'écran du fichier PDF converti, qui ont été convertis à l'aide du code Java ci-dessus.



{{< figure align=center src="images/EML-message.png" alt="Fichier EML à convertir en PDF" caption="Fichier EML">}}




{{< figure align=center src="images/converted-eml-to-pdf-in-java.png" alt="Fichier PDF converti à partir d'EML" caption="Fichier PDF converti à partir du format EML à l'aide de Java.">}}


## Conclusion

Dans cet article, nous avons appris à convertir les fichiers MSG et EML en PDF à l'aide de l'API de conversion Java. De plus, nous pouvons appliquer par programme la personnalisation sur les fichiers PDF pour obtenir le résultat dans le style souhaité. Vous pouvez en savoir plus sur GroupDocs.Conversion pour Java dans la documentation.

## Voir également

* [Convertir un fichier EML ou MSG en PDF en C#][14]







[1]: https://blog.groupdocs.com/2019/12/06/convert-eml-or-msg-file-to-pdf-in-csharp/
[2]: https://blog.groupdocs.com/2019/12/06/convert-eml-or-msg-file-to-pdf-in-csharp/
[3]: https://blog.groupdocs.com/2020/09/02/convert-msg-and-eml-files-to-pdf-in-java/#java-conversion-library
[4]: https://blog.groupdocs.com/2020/09/02/convert-msg-and-eml-files-to-pdf-in-java/#convert-msg-to-pdf-in-java
[5]: https://blog.groupdocs.com/2020/09/02/convert-msg-and-eml-files-to-pdf-in-java/#convert-eml-to-pdf-in-java
[6]: https://products.groupdocs.com/conversion/java
[7]: https://downloads.groupdocs.com/conversion/java
[8]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion/Converter
[9]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/PdfConvertOptions
[10]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[11]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion/Converter
[12]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/PdfConvertOptions
[13]: https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)
[14]: https://blog.groupdocs.com/2019/12/06/convert-eml-or-msg-file-to-pdf-in-csharp/


