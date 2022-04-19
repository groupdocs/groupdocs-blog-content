---
title: "Extraire les données des factures et des reçus en Java"
date: Fri, 22 Jan 2021 16:48:00 +0000
draft: false
url: /fr/2021/01/22/extraire-les-données-des-factures-ou-des-reçus-en-java/
aliases:
- /2021/01/22/extraire-les-données-des-factures-ou-des-reçus-dans-csharp-2/
author: 'Shoaib Khan'
summary: 'In the era of online businesses, the use of digital invoices and receipts has largely increased. Similarly, the efficient data extraction from these digital invoices is also demanding. In this article, you will be knowing **how to extract data from PDF invoices or receipts programmatically in Java**.

[Continuer la lecture...][1]'
tags: ['data extraction from PDF invoices in Java', 'extract data from invoices in Java', 'extract data from PDF in Java', 'extract invoice data in Java']
categories: ['GroupDocs.Parser Product Family']
---

À l'ère des entreprises en ligne, l'utilisation des factures et des reçus numériques a largement augmenté. De même, l'extraction efficace des données de ces factures numériques est également exigeante. Dans cet article, vous saurez **comment extraire des données de factures ou de reçus PDF par programmation en Java**. Auparavant, nous avons vu [l'extraction des données de facturation à l'aide de C #][2] dans l'un des messages précédents.



{{< figure align=center src="images/Extract-Data-from-Invoices-using-GroupDocs.jpg" alt="Extraire des données de factures ou de reçus PDF">}}


## API Java d'analyse de documents et d'extraction de données

J'utiliserai [GroupDocs.Parser for Java][3] pour analyser les factures PDF et extraire les valeurs de données dans l'application Java. Cette API permet également d'extraire du texte, des images et des métadonnées à partir de documents, d'images, de présentations, d'archives, d'e-mails et de nombreux autres [formats de documents pris en charge][4].

### Télécharger ou configurer

À partir de la [section des téléchargements][5], vous pouvez télécharger le fichier **JAR** ou simplement obtenir les configurations du référentiel et des dépendances pour le pox.xml de vos applications Java **basées sur maven**.

## Comment extraire des données de facture PDF en Java

Les étapes suivantes vous permettront d'extraire facilement les données des factures PDF en utilisant Java.

* Créer un modèle.
* Analysez la facture PDF en fonction du modèle créé.
* Extraire les informations du PDF analysé.

### Créer un modèle pour la facture

Vous trouverez ci-dessous le modèle créé en fonction de la facture. Vous pouvez également télécharger la facture utilisée à partir des [exemples de fichiers][6] disponibles dans le référentiel GitHub.

```
// Créer un modèle pour analyser les données de la facture à l'aide de Java
// Créez d'abord des éléments de modèle
TemplateItem[] templateItems = new TemplateItem[]
{
    new TemplateField(new TemplateFixedPosition(new Rectangle(new Point(35, 135), new Size(100, 10))), "FromCompany"),
    new TemplateField(new TemplateFixedPosition(new Rectangle(new Point(35, 150), new Size(100, 35))), "FromAddress"),
    new TemplateField(new TemplateFixedPosition(new Rectangle(new Point(35, 190), new Size(150, 2))), "FromEmail"),
    new TemplateField(new TemplateFixedPosition(new Rectangle(new Point(35, 250), new Size(100, 2))), "ToCompany"),
    new TemplateField(new TemplateFixedPosition(new Rectangle(new Point(35, 260), new Size(100, 15))), "ToAddress"),
    new TemplateField(new TemplateFixedPosition(new Rectangle(new Point(35, 290), new Size(150, 2))), "ToEmail"),
    new TemplateField(new TemplateRegexPosition("Invoice Number"), "InvoiceNumber"),
    new TemplateField(new TemplateLinkedPosition(
            "InvoiceNumber",
            new Size(200, 15),
            new TemplateLinkedPositionEdges(false, false, true, false)),
            "InvoiceNumberValue"),
    new TemplateField(new TemplateRegexPosition("Order Number"), "InvoiceOrder"),
    new TemplateField(new TemplateLinkedPosition(
            "InvoiceOrder",
            new Size(200, 15),
            new TemplateLinkedPositionEdges(false, false, true, false)),
            "InvoiceOrderValue"),
    new TemplateField(new TemplateRegexPosition("Invoice Date"), "InvoiceDate"),
    new TemplateField(new TemplateLinkedPosition(
            "InvoiceDate",
            new Size(200, 15),
            new TemplateLinkedPositionEdges(false, false, true, false)),
            "InvoiceDateValue"),
    new TemplateField(new TemplateRegexPosition("Due Date"), "DueDate"),
    new TemplateField(new TemplateLinkedPosition(
            "DueDate",
            new Size(200, 15),
            new TemplateLinkedPositionEdges(false, false, true, false)),
            "DueDateValue"),
    new TemplateField(new TemplateRegexPosition("Total Due"), "TotalDue"),
    new TemplateField(new TemplateLinkedPosition(
            "TotalDue",
            new Size(200, 15),
            new TemplateLinkedPositionEdges(false, false, true, false)),
            "TotalDueValue")
};
// Transformer en modèle
Template template = new Template(Arrays.asList(templateItems));
```

### Analyser la facture/le reçu PDF pour l'extraction de données

Les lignes suivantes analyseront la facture PDF en fonction du modèle créé et extrairont les données de la facture à l'aide d'un simple code Java.

```
// Analyser la facture PDF à l'aide du modèle défini en Java
Parser parser = new Parser("filePath/invoice.pdf");
DocumentData data = parser.parseByTemplate(template);
// Imprimer les données extraites
for (int i = 0; i < data.getCount(); i++) {
    // Printing Field Name
    System.out.print(data.get(i).getName() + ": ");
    // Cast PageArea property value to PageTextArea
    // as we have defined only text fields in the template
    PageTextArea area = data.get(i).getPageArea() instanceof PageTextArea
            ? (PageTextArea) data.get(i).getPageArea()
            : null;
    System.out.println(area == null ? "Not a template field" : area.getText());
}
```

### Le résultat

Voici la sortie du code ci-dessus après extraction des données de la facture.

```
**FROMCOMPANY:**    DEMO - Sliced Invoices
**FROMADDRESS:**    Suite 5A-1204
123 Somewhere Street
Your City AZ 12345
**FROMEMAIL:**     admin@slicedinvoices.com
**TOCOMPANY:**    Test Business
**TOADDRESS:**    123 Somewhere St
Melbourne, VIC 3000
**INVOICENUMBER:**             Invoice Number
**INVOICENUMBERVALUE:** NV-3337
**INVOICEORDER:**                Order Number
**INVOICEORDERVALUE:**    12345
**INVOICEDATE:**                    Invoice Date
**INVOICEDATEVALUE:**        January 25, 2016
**DUEDATE:**                           Due Date
**DUEDATEVALUE:**               January 31, 2016
**TOTALDUE:**                         Total Due
**TOTALDUEVALUE:**             $93.50
```

Il existe de nombreux autres exemples open source disponibles sur [GitHub Repository][7]. Vous pouvez télécharger le code et exécuter rapidement les exemples. Pour plus de conseils et d'autres façons d'[utiliser des modèles pour l'analyse et l'extraction de données en Java][8], consultez le guide du développeur dans la [documentation][9]. En cas de difficulté supplémentaire, contactez gratuitement l'équipe d'assistance à tout moment sur le [forum][10].

## Voir également

* [En savoir plus sur l'analyse des factures PDF en Java à l'aide de modèles][11]
* [Extraire les données des factures ou des reçus en C #][12]







[1]: https://blog.groupdocs.com/2021/01/22/extract-data-from-invoices-or-receipts-in-java/
[2]: https://blog.groupdocs.com/2019/10/24/extract-data-from-invoices-or-receipts-in-csharp/
[3]: https://products.groupdocs.com/parser/java
[4]: https://docs.groupdocs.com/parser/java/supported-document-formats/
[5]: https://downloads.groupdocs.com/parser/java
[6]: https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java/tree/master/Examples/Resources/SampleFiles
[7]: https://github.com/groupdocs-parser/GroupDocs.Parser-for-Java
[8]: https://docs.groupdocs.com/parser/java/working-with-templates/
[9]: https://docs.groupdocs.com/parser/java/introducing-groupdocs-parser-for-java/
[10]: https://forum.groupdocs.com/c/parser
[11]: https://docs.groupdocs.com/parser/java/working-with-templates/
[12]: https://blog.groupdocs.com/2019/10/24/extract-data-from-invoices-or-receipts-in-csharp/


