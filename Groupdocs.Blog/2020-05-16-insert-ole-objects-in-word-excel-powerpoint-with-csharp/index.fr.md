---
title: "Insérer des objets OLE dans Word, Excel, PowerPoint avec C#"
date: Sat, 16 May 2020 13:06:31 +0000
draft: false
url: /fr/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/
author: 'Shoaib Khan'
summary: "**OLE** signifie [Liaison et incorporation d'objets][1]. Il est fourni par Microsoft et vous permet de créer et de modifier des documents contenant des éléments ou des objets créés par diverses applications."
tags: ['embed OLE object in word in csharp', 'Insert OLE objects in csharp', 'insert OLE objects in excel in csharp', 'insert OLE objects in presentations in csharp']
categories: ['GroupDocs.Merger Product Family']
---

**OLE** signifie [Liaison et incorporation d'objets][2]. Il est fourni par Microsoft et vous permet de créer et de modifier des documents contenant des éléments ou des objets créés par diverses applications.

Par exemple, vous pouvez incorporer des feuilles de calcul, des images et des clips audio en tant qu'objets OLE dans un document Word. Vous pouvez utiliser ces objets OLE dans le document Word et ne vous inquiétez pas de basculer encore et encore vers plusieurs applications. Vous pouvez incorporer ou insérer de tels objets par programmation à l'aide d'OLE en C#.

Cet article vous guidera sur la façon dont vous pouvez :

* [Insérer un objet OLE dans des documents MS Word][3]
* [Insérer un objet OLE dans des feuilles de calcul Excel][4]
* [Ajouter un objet OLE dans les présentations PowerPoint][5]

Les étapes de cet article et les exemples de code utilisent [GroupDocs.Merger pour .NET][6]. Assurez-vous donc d'installer l'API à partir de l'une des méthodes suivantes :

* Installez à l'aide de [NuGet][7] Gestionnaire de packages.
* [Téléchargez][8] la DLL et référencez-la dans le projet.

## Insérer un PDF en tant qu'objet OLE dans un document MS Word en C# {#insert-ole-obj-into-word-in-csharp}



{{< figure align=center src="images/PDF-in-Word.png" alt="Insérer un PDF en tant qu'OLE dans un document Word en C #">}}


Voici les étapes et un exemple de code C# pour montrer **comment intégrer un fichier PDF dans un document Word en tant qu'objet OLE** :

1. Instanciez [OleWordProcessingOptions][9] avec les options d'incorporation et le document à incorporer dans un document Word.
2. Instanciez maintenant l'objet [Merger][10] avec le chemin ou le flux du **document Word source**.
3. Appelez la méthode [ImportDocument][11] et transmettez l'objet des **Options de traitement de texte OLE** définies à l'étape 1.
4. C'est ça. Appelez la méthode [Save][12] pour obtenir le document Word résultant ayant un document PDF comme objet OLE.

```
// Embed a PDF file into a Word document as an OLE Object in C#
int pageNumber = 2;
OleWordProcessingOptions oleWordProcessingOptions = new OleWordProcessingOptions(@"embedded-doc.pdf", pageNumber)
{ 
    Width = 300, // Just setting the height & width, you have more options.
    Height = 300
};
// Use Merger class to start with source Word document and embed PDF as OLE object.
using (Merger merger = new Merger(@"source-doc.docx"))
{
    merger.ImportDocument(oleWordProcessingOptions);
    merger.Save(@"word-document-with-OLE.docx");
}
```

## Insérer un document Word en tant qu'objet OLE dans une feuille de calcul Excel en C# {#insert-ole-obj-into-excel-in-csharp}



{{< figure align=center src="images/Word-in-Excel.png" alt="Insérer un fichier Word s OLE dans une feuille de calcul Excel en C#">}}


Nous pouvons intégrer des objets OLE dans des feuilles de calcul Excel. Exemple de code CSharp et étapes ci-dessous expliquant **comment ajouter un document Word dans une feuille de calcul Excel en tant qu'objet OLE** :

1. Instanciez [OleSpreadsheetOptions][13] avec les options d'intégration et le document à intégrer dans une feuille de calcul Excel.
2. Instanciez maintenant l'objet [Merger][14] avec le chemin ou le flux **source Spreadsheet**.
3. Appelez maintenant la méthode [ImportDocument][15] et transmettez l'objet **OLE Spreadsheet Options** défini à l'étape 1.
4. Enfin, appelez la méthode [Save][16] pour obtenir la feuille de calcul Excel résultante ayant un document Word comme objet OLE.

```
// Embed a Word file into an Excel Spreadsheet as an OLE Object in C#
int pageNumber = 2;
OleSpreadsheetOptions oleSpreadsheetOptions = new OleSpreadsheetOptions(@"embedded-doc.docx", pageNumber)
{
    RowIndex = 2, // Setting the Row & height Index, you have more options.
    ColumnIndex = 2
};
// Using Merger class with source spreadsheet and embedding a Word document as an OLE object.
using (Merger merger = new Merger(@"sample-doc.xlsx"))
{
    merger.ImportDocument(oleSpreadsheetOptions);
    merger.Save(@"excel-sheet-with-ole.xlsx");
}
```

## Ajouter un PDF en tant qu'objet OLE à une présentation PowerPoint en C # {#insert-ole-obj-into-presentation-in-csharp}



{{< figure align=center src="images/PDF-in-PPT.png" alt="Insérer un PDF en tant qu'OLE dans une présentation PowerPoint en C#">}}


De même, nous insérons ici des objets dans une présentation PowerPoint.

1. Instanciez [OlePresentationOptions][17] avec les options d'intégration et le document à intégrer dans une présentation PowerPoint.
2. Instanciez maintenant l'objet [Merger][18] avec le chemin ou le flux **source Presentation**.
3. Appelez la méthode [ImportDocument][19] et transmettez l'objet des **Options de présentation OLE** définies à l'étape 1.
4. Enfin, appelez la méthode [Save][20] pour obtenir la présentation PowerPoint résultante avec un document PDF en tant qu'objet OLE.

```
// Embed a PDF file into an Excel Spreadsheet as an OLE Object in C#
int pageNumber = 2;
OlePresentationOptions olePresentationOptions = new OlePresentationOptions(@"embedded.pdf", pageNumber)
{
    X = 10, // Setting only X & Y coordinates, you can customize more.
    Y = 10
};
// Using Merger class to embed a PDF file as an OLE object in the PowerPoint presentation.
using (Merger merger = new Merger(@"sample-presentation.ppt"))
{
    merger.ImportDocument(olePresentationOptions);
    merger.Save(@"powerpoint-presentation-with-ole.ppt");
}
```

## Conclusion

Nous avons discuté de la facilité et de la rapidité avec lesquelles nous pouvons insérer des objets OLE dans des documents Word, Excel ou PowerPoint par programme en C#. Il n'y a qu'une petite différence de code pour chaque objectif, c'est-à-dire une classe d'options OLE différente et ses options pour chaque format de fichier :

* **OleWordProcessingOptions** pour incorporer des objets OLE dans un **document Word**.
* **OleSpreadsheetOptions** pour incorporer des objets OLE dans **Excel Spreadsheets**.
* **OlePresentationOptions** pour incorporer des objets OLE dans la **présentation PowerPoint**.

Vous pouvez en savoir plus sur l'API à partir de la [documentation][21] ou **Parlons plus @** [Forum de support gratuit.][22]







[1]: https://docs.microsoft.com/en-us/cpp/mfc/ole-background
[2]: https://docs.microsoft.com/en-us/cpp/mfc/ole-background
[3]: https://blog.groupdocs.com/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/#insert-ole-obj-into-word-in-csharp
[4]: https://blog.groupdocs.com/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/#insert-ole-obj-into-excel-in-csharp
[5]: https://blog.groupdocs.com/2020/05/16/insert-ole-objects-in-word-excel-powerpoint-with-csharp/#insert-ole-obj-into-presentation-in-csharp
[6]: https://products.groupdocs.com/merger/net
[7]: https://www.nuget.org/packages/GroupDocs.Merger
[8]: https://downloads.groupdocs.com/merger/net
[9]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/olewordprocessingoptions
[10]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[11]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/importdocument
[12]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.merger/save/methods/1
[13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/olespreadsheetoptions
[14]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[15]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/importdocument
[16]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.merger/save/methods/1
[17]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.domain.options/olepresentationoptions
[18]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[19]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/importdocument
[20]: https://apireference.groupdocs.com/merger/net/groupdocs.merger.merger/save/methods/1
[21]: https://docs.groupdocs.com/merger/net/import-documents/
[22]: https://forum.groupdocs.com/c/merger


