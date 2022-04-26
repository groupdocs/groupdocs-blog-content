---
title: "Fusionner des PDF, des documents Word, des feuilles de calcul, des fichiers de présentation en C#"
date: Wed, 19 Aug 2020 18:20:42 +0000
draft: false
url: /fr/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/
author: 'Shoaib Khan'
summary: "Aujourd'hui, nous allons apprendre à fusionner par programmation des documents PDF, Word, des feuilles de calcul et des présentations à l'aide de C#. Dans un article précédent, nous avons vu la [fusion et la division de documents à l'aide de Java][1]."
tags: ['Merge Documents in CSharp', 'Merge Excel Sheets in CSharp', 'Merge PDF Files in CSharp', 'Merge PPT PPTX in CSharp', 'Merge Word Docs in CSharp']
categories: ['GroupDocs.Merger Product Family']
---

Aujourd'hui, nous allons apprendre à fusionner par programmation des documents PDF, Word, des feuilles de calcul et des présentations à l'aide de C#. Dans un article précédent, nous avons vu la [fusion et la division de documents à l'aide de Java][2].



{{< figure align=center src="images/merge-documents-with-csharp-dotnet.png" alt="fusionner plusieurs fichiers pdf, word, excel, ppt en utilisant csharp dotnet">}}


Cet article vous montrera également les exemples de code concernant :

* [Fusionner des fichiers PDF][3]
* [Fusionner des documents Word][4]
* [Fusionner les pages sélectives][5]
* [Fusionner des feuilles de calcul et des présentations][6]

J'utiliserai [GroupDocs.Merger pour .NET][7] dans tous les exemples ci-dessous. Avant de continuer, vous pouvez obtenir l'API à partir de l'une des options suivantes :

* Installez le package à partir de [NuGet][8] Packages Gallery.
* [Téléchargez][9] le MSI ou les DLL à partir de la section des téléchargements de GroupDocs.

## Fusionner des fichiers PDF en C# {#merge-pdf-in-csharp}

Suivre 3 lignes de code simples combine 2 fichiers PDF en 1 document PDF.

* Commencez par le premier document en utilisant la classe [Merger][10].
* Appelez la méthode [Join][11] de la classe Merger et passez le deuxième document à fusionner.
* Appelez la méthode [Save][12] pour enregistrer le document combiné.

```
// Merge 2 PDF files in C#
using (Merger merger = new Merger(@"document1.pdf"))
{
    merger.Join(@"document2.pdf");
    merger.Save(@"merged.pdf");
}
```

La méthode [Join][13] a plusieurs méthodes surchargées qui permettent de fusionner des documents ou des pages sélectives de différents documents via le chemin du fichier, en utilisant un flux ou une URL distante.

## Fusionner plusieurs documents Word en C# {#merge-word-files-in-csharp}

Le code similaire ci-dessus permet de combiner deux ou plusieurs fichiers de formats MS Word et OpenDocument sans perdre le format. Juste pour donner une idée, vous pouvez fusionner .doc, .docx, .docm, .dot, .dotx, .dotm, .rtf, .odt, .ott etc. Ci-dessous le code à 3 lignes qui fusionne deux fichiers MS Word DOCX .

```
// Merge Word files in C#
using (Merger merger = new Merger(@"c:\\document1.docx"))
{
    merger.Join(@"c:\\document2.docx");
    merger.Save(@"c:\\merged.docx");
}
```

## Fusionner des pages de plusieurs fichiers - C# {#merge-pages-in-csharp}

Non seulement l'ensemble du document, mais nous pouvons également fusionner des pages sélectives de plusieurs documents pour obtenir un seul document combiné.

```
// Merge selective pages
string filePath = @"c:\\sample.docx";
string filePath2 = @"c:\\sample2.docx";
string filePathOut = @"c:\\output\\result.docx";

JoinOptions joinOptions = new JoinOptions(1, 4, RangeMode.OddPages);

using (Merger merger = new Merger(filePath, loadOptions))
{
    merger.Join(filePath2, joinOptions);
    merger.Save(filePathOut);
}
```

## Fusionner des feuilles de calcul, des présentations et d'autres documents en C# {#merge-documents-in-csharp}

En plus des documents tels que PDF et Word, nous pouvons fusionner les présentations, les feuilles de calcul et de nombreux autres formats sans aucune différence. Changez simplement le nom du fichier et tapez en conséquence dans le code ci-dessus, vous obtiendrez votre document fusionné.

```
using (Merger merger = new Merger(@"filepath1.xxx"))
{
    merger.Join(@"filepath2.xxx");
    merger.Save(@"xyz.xxx");
}
```

## Vérifiez d'abord la prise en charge du format de fichier

Votre besoin peut être d'un type de fichier un peu différent, il est donc préférable de savoir d'abord si le document requis est pris en charge pour la fusion par l'API ou non. Le code suivant obtient tous les types de fichiers pris en charge par l'API Merger.

```
foreach (FileType fileType in FileType
        .GetSupportedFileTypes()
        .OrderBy(fileType => fileType.Extension))
{
    Console.WriteLine(fileType);
}
```

Voici la sortie du code ci-dessus qui affiche les formats de fichiers.

```
Bitmap Image File (.bmp)
Comma Separated Values File (.csv)
Excel Binary Spreadsheet (.xlsb)
Excel Macro-Enabled Add-In (.xlam)
Excel Open XML Macro-Enabled Spreadsheet (.xlsm)
Excel Open XML Macro-Enabled Spreadsheet Template (.xltm)
Excel Open XML Spreadsheet (.xlsx)
Excel Open XML Spreadsheet Template (.xltx)
Excel Spreadsheet (.xls)
Excel Template File (.xlt)
Hypertext Markup Language File (.html)
JPEG Image (.jpeg)
LaTeX Source Document (.tex)
MHTML Web Archive (.mht)
MIME HTML File (.mhtml)
OneNote Document (.one)
Open eBook File (.epub)
OpenDocument Document Template (.ott)
OpenDocument Presentation (.odp)
OpenDocument Presentation Template (.otp)
OpenDocument Spreadsheet (.ods)
OpenDocument Text Document (.odt)
Plain Text File (.txt)
Portable Document Format File (.pdf)
Portable Network Graphic (.png)
PostScript File (.ps)
PowerPoint Open XML Presentation (.pptx)
PowerPoint Open XML Slide Show (.ppsx)
PowerPoint Presentation (.ppt)
PowerPoint Slide Show (.pps)
Rich Text Format File (.rtf)
Tab Separated Values File (.tsv)
Visio Drawing (.vsdx)
Visio Drawing Template (.vstx)
Visio Drawing XML File (.vdx)
Visio Macro-Enabled Drawing (.vsdm)
Visio Macro-Enabled Drawing Template (.vstm)
Visio Macro-Enabled Stencil File (.vssm)
Visio Stencil File (.vssx)
Visio Stencil XML File (.vsx)
Visio Template XML File (.vtx)
Word Document (.doc)
Word Document Template (.dot)
Word Open XML Document (.docx)
Word Open XML Document Template (.dotx)
Word Open XML Macro-Enabled Document (.docm)
Word Open XML Macro-Enabled Document Template (.dotm)
XML Paper Specification File (.xps)
```

## En savoir plus sur l'API .NET Merger

Si vous souhaitez en savoir plus sur l'API .NET Merger de GroupDocs, veuillez consulter la [documentation][14] ou nous contacter sur le [forum][15] pour toute question.

Merci.







[1]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/
[2]: https://blog.groupdocs.com/2020/05/20/merge-pdf-word-excel-powerpoint-documents-in-java/
[3]: https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/#merge-pdf-in-csharp
[4]: https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/#merge-word-files-in-csharp
[5]: https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/#merge-pages-in-csharp
[6]: https://blog.groupdocs.com/2020/08/19/merge-pdf-word-excel-ppt-files-in-csharp/#merge-documents-in-csharp
[7]: https://products.groupdocs.com/merger/net
[8]: https://www.nuget.org/packages/GroupDocs.Merger/
[9]: https://downloads.groupdocs.com/merger/net
[10]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger
[11]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/join/index
[12]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/save/index
[13]: https://apireference.groupdocs.com/merger/net/groupdocs.merger/merger/methods/join/index
[14]: https://docs.groupdocs.com/merger/net/getting-started/
[15]: https://forum.groupdocs.com/c/merger


