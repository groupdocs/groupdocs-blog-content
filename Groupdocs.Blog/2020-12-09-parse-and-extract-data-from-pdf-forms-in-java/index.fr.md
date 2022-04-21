---
title: "Lire les champs de formulaire PDF en Java"
date: Wed, 09 Dec 2020 15:43:10 +0000
draft: false
url: /fr/2020/12/09/analyser-et-extraire-les-données-des-formulaires-pdf-en-java/
aliases:
- /2018/09/13/extract-data-from-pdf-forms-using-groupdocs.parser-for-java-18.9/
author: 'Shoaib Khan'
summary: "Dans cet article, nous discuterons de **comment analyser un document PDF et extraire des valeurs de formulaires PDF par programmation en Java**. Il existe de nombreuses situations où nous avons plusieurs formulaires d'enquête remplis ou des commentaires au format PDF d'un large public. Nous pouvons facilement extraire les valeurs de données remplies et les utiliser pour l'analyse. Passons maintenant directement à la lecture de ces formulaires PDF et extrayons les valeurs des champs de données remplis dans les applications Java."
tags: ['Extract Text from PDF Forms', 'Extract Text from PDF Forms in Java', 'Parse PDF Forms in Java']
categories: ['GroupDocs.Parser Product Family']
---

Dans cet article, nous discuterons de **comment analyser un document PDF et extraire des valeurs de formulaires PDF par programmation en Java**. Il existe de nombreuses situations où nous avons plusieurs formulaires d'enquête remplis ou des commentaires au format PDF d'un large public. Nous pouvons facilement extraire les valeurs de données remplies et les utiliser pour l'analyse. Passons maintenant directement à la lecture de ces formulaires PDF et extrayons les valeurs des champs de données remplis dans les applications Java.



{{< figure align=center src="images/Extract-from-PDF-Form-in-java.jpeg" alt="Analyser un formulaire PDF pour extraire des valeurs en Java">}}


## API Java pour analyser et extraire des valeurs à partir de formulaires PDF

**GroupDocs** propose une [API Java d'analyse de documents et d'extraction de données][1] qui prend en charge bien plus que les formats de traitement de texte, de présentations, de feuilles de calcul, d'e-mails, de PDF, de balisage, de livres électroniques et d'archives. Outre l'extraction de texte et d'images, l'API prend également en charge l'extraction de métadonnées à partir des [formats de documents pris en charge][2]. L'une des principales fonctionnalités de l'API consiste à ** analyser les documents PDF à remplir et à extraire les valeurs des champs du formulaire ** avec un code Java simple.

Dans les exemples à venir, j'utiliserai l'API mentionnée, c'est-à-dire **[GroupDocs.Parser pour Java][3]**, je vous recommande donc de préparer votre environnement pour implémenter la fonctionnalité. Vous pouvez télécharger le dernier fichier JAR à partir de la section [downloads][4] ou simplement ajouter les configurations suivantes dans vos applications Java basées sur Maven. Pour plus de détails sur l'API, consultez [API Reference][5].

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
	<artifactId>groupdocs-parser</artifactId>
	<version>20.8</version> 
</dependency>
```

## Extraire des données d'un champ de formulaire PDF en Java

Les étapes simples suivantes pour savoir comment extraire les valeurs de champ du formulaire PDF.

* Initialisez l'objet **[Parser][6]** avec le formulaire PDF cible.
* Appelez la méthode **[parseForm][7]** pour obtenir toutes les données du formulaire PDF.
* Parcourez les données collectées pour obtenir les valeurs de champ souhaitées.

Le code suivant montre comment analyser un document PDF et obtenir des valeurs à partir des champs de formulaire PDF remplis en Java.

```
// Analysez le formulaire PDF rempli pour extraire les valeurs de champ à l'aide de l'API Java de GroupDocs.Parser
Parser parser = new Parser("filePath/PDFForm.pdf"); 
// Extraire les données du formulaire PDF
DocumentData data = parser.parseForm();
// Itérer sur les données extraites du formulaire PDF
for (int i = 0; i < data.getCount(); i++) {
    System.out.print(data.get(i).getName() + ": ");
    PageTextArea area = (data.get(i).getPageArea() instanceof PageTextArea)
            ? (PageTextArea) data.get(i).getPageArea()
            : null;
    System.out.println(area == null ? "Not a template field" : area.getText());
}
```

```
COMPANY: GroupDocs
EMAIL: everything@groupdocs.com
COUNTRY: Australia
```

## Conclusion

J'espère que les développeurs Java sont maintenant familiarisés avec le moyen simple, précis et efficace d'analyser les documents PDF pour extraire les valeurs de texte des champs de formulaire PDF. Si vous souhaitez en savoir plus sur les fonctionnalités de base et avancées de l'API, vous pouvez explorer la [documentation][8].

En cas de questions, contactez le support @ [forum][9].

## Voir également

* [Lire les champs de formulaire PDF à l'aide de C #][10]
* [Extraire des images de documents à l'aide de Java][11]







[1]: https://products.groupdocs.com/parser/java
[2]: https://docs.groupdocs.com/parser/java/supported-document-formats/
[3]: https://products.groupdocs.com/parser/java
[4]: https://downloads.groupdocs.com/parser/java
[5]: https://apireference.groupdocs.com/parser/java
[6]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser
[7]: https://apireference.groupdocs.com/parser/java/com.groupdocs.parser/Parser#parseForm()
[8]: https://docs.groupdocs.com/parser/java/
[9]: https://forum.groupdocs.com/c/parser
[10]: https://blog.groupdocs.com/2020/12/23/parse-and-extract-data-from-pdf-forms-in-csharp/
[11]: https://blog.groupdocs.com/2020/10/27/extract-images-from-pdf-word-excel-ppt-using-java/


