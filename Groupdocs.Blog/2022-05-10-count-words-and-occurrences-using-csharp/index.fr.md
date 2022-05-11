---
title: "Compter les mots et les occurrences de chaque mot dans un document à l'aide de C#"
seoTitle: "Compter les mots et les occurrences de chaque mot dans un document à l'aide de C# .NET"
description: "Comptez le nombre de mots et leurs occurrences dans les documents PDF, Word, Excel, PowerPoint et e-mail en C# à l'aide de l'API d'analyse de documents .NET."
date: Tue, 10 May 2022 16:33:57 +0000
draft: false
url: /fr/2022/05/10/count-words-and-occurrences-using-csharp
author: "Shoaib Khan"
summary: "Cet article montre comment compter par programme les mots et le nombre d'occurrences de mots de chaque mot dans les formats de document PDF, Word, Excel, PowerPoint, Ebook, Markup et Email à l'aide de C#."
tags: ['GroupDocs.Parser for .NET']
categories: ['GroupDocs.Parser Product Family']
---

La répétition des données peut diminuer la valeur du contenu. En tant qu'écrivain, vous devez suivre le principe [DRY][1] (ne vous répétez pas). Les statistiques telles que le nombre de mots ou le nombre d'occurrences de chaque mot peuvent vous permettre d'analyser le contenu, mais il est difficile de le faire manuellement pour plusieurs documents. Cet article montre donc comment ** compter les mots par programmation ** et le nombre d'occurrences de mots de chaque mot dans les formats de document PDF, Word, Excel, PowerPoint, eBook, Markup et Email à l'aide de C#.

## API .NET pour compter les mots et les occurrences

[GroupDocs.Parser][2] fournit la solution d'analyse de documents pour les développeurs. Pour l'extraction de texte à partir de documents et le comptage des occurrences, nous utiliserons son [GroupDocs.Parser for .NET][3]. L'API permet en outre l'extraction d'images et de métadonnées à partir d'une longue liste de formats de [document pris en charge][4] tels que des documents de traitement de texte, des présentations, des feuilles de calcul, des e-mails, des bases de données, des livres électroniques et bien d'autres.

Vous pouvez télécharger les DLL ou le programme d'installation MSI à partir de la [section téléchargements][5] ou installer l'API en ajoutant son package à votre application .NET via [NuGet][6].

```
PM> Install-Package GroupDocs.Parser
```

## Compter les mots en C# {#count-words}

Pour le comptage des mots, l'essentiel est d'analyser et d'extraire tout le contenu du document. Après l'extraction du texte, nous pouvons diviser son contenu en une collection de phrases et de mots. L'étape suivante permet de compter les mots dans le document en utilisant C#.

- Charger le document en utilisant la classe [Parser][7].
- Récupérer le texte du document chargé dans [TextReader][8].
- [Obtenir][9] le texte du document du TextReader sous forme de chaîne.
- Divisez le texte en mots et enregistrez-les dans un tableau de chaînes.
- Effectuer le comptage des mots.

Le code source C# suivant compte le nombre de mots dans un document.

```
// Compter les mots dans un document PDF à l'aide de C #
using (Parser parser = new Parser("path/document.pdf"))
{                
	// Extract a text into the reader
	using (TextReader reader = parser.GetText())
	{
		string text = reader.ReadToEnd();
		char[] chars = { ' ', '.', ',', ';', ':', '?', '\n', '\r' };
		// split words
		string[] words = text.Split(chars);
		// print total word count
		Console.WriteLine("Total word count: {0}", stats.Count);
	}
}
```

## Compter l'occurrence des mots en C # {#count-words-occurrences}

De même, nous pouvons compter combien de fois un mot ou une phrase particulière a été utilisée dans le document. En utilisant cette fonctionnalité, vous pouvez éviter la répétition excessive d'un mot dans un article. Les étapes suivantes comptent l'occurrence de chaque mot utilisé dans un document.

- Charger le document en utilisant la classe [Parser][7].
- Récupérer le texte du document chargé dans [TextReader][8].
- Lire et diviser l'ensemble du texte dans la collection de mots.
- Parcourez la collection de mots pour compter les mots.

L'extrait de code C# suivant compte l'occurrence de chaque mot unique dans le document.

```
// Compter les mots uniques et leurs occurrences dans un document PDF à l'aide de C#
using (Parser parser = new Parser("path/document.pdf"))
{                
	// Extract text into TextReader
	using (TextReader reader = parser.GetText())
	{
		Dictionary<string, int> stats = new Dictionary<string, int>();
		string text = reader.ReadToEnd();
		char[] chars = { ' ', '.', ',', ';', ':', '?', '\n', '\r' };
		// split words
		string[] words = text.Split(chars);
		int minWordLength = 2; // Consider a word having more than 2 characters

		// iterate over the words collection to count occurrences
		foreach (string word in words)
		{
			string w = word.Trim().ToLower();
			if (w.Length > minWordLength)
			{
				if (!stats.ContainsKey(w))
				{
					stats.Add(w, 1); // add new word to collection
				}
				else
				{
					stats[w] += 1; // update word occurrence count
				}
			}
		}
		// order the collection by word count
		var orderedStats = stats.OrderByDescending(x => x.Value);
		
    		// Print word count Results
		Console.WriteLine("Total word count: {0}", stats.Count);

    		foreach (var pair in orderedStats)
		{
			Console.WriteLine("Total occurrences of {0}: {1}", pair.Key, pair.Value);
		}
	}
}
```

Voici la sortie du code ci-dessus :

{{< figure align=center src="images/Word-Count.png" alt="Nombre d'occurrences de mots">}}

## Obtenez une licence API gratuite

Vous pouvez [obtenir une licence temporaire gratuite][10] afin d'utiliser l'API sans les limitations d'évaluation.

## Conclusion

Pour résumer, vous avez appris à compter les mots dans un document à l'aide de C#. De plus, nous avons discuté de la manière d'obtenir le nombre d'occurrences de mots pour chaque mot du document. Essayez de développer votre application .NET de compteur de mots en ligne. Pour plus de détails et en savoir plus sur l'API, consultez la [documentation][11]. Pour toute question, contactez-nous via le [forum][12].

## Voir également

- [Extraire les données des fichiers ZIP en C #][13]
- [Analyser des documents pour extraire des images à l'aide de C #][14]
- [Extraire des images d'EPUB, FB2, CHM eBooks en C #][15]
- [Lire les champs de formulaire PDF à l'aide de C #][16]

[1]: [https://en.wikipedia.org/wiki/Don%27t_repeat_yourself]
[2]: https://products.groupdocs.com/parser/
[3]: https://products.groupdocs.com/parser/net/
[4]: https://docs.groupdocs.com/parser/net/supported-document-formats/
[5]: https://downloads.groupdocs.com/parser
[6]: https://www.nuget.org/packages/groupdocs.parser
[7]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser
[8]: https://docs.microsoft.com/en-us/dotnet/api/system.io.textreader
[9]: https://apireference.groupdocs.com/parser/net/groupdocs.parser/parser/methods/gettext
[10]: https://purchase.groupdocs.com/temporary-license
[11]: https://docs.groupdocs.com/parser/
[12]: https://forum.groupdocs.com/
[13]: https://blog.groupdocs.com/2021/08/25/extract-zip-files-data-in-csharp/
[14]: https://blog.groupdocs.com/2020/10/28/extract-images-from-pdf-word-excel-ppt-using-csharp/
[15]: https://blog.groupdocs.com/2021/02/26/extract-images-from-ebooks-in-csharp/
[16]: https://blog.groupdocs.com/2020/12/23/parse-and-extract-data-from-pdf-forms-in-csharp/
