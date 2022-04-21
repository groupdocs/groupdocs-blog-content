---
title: "Nettoyeur de métadonnées pour les documents et les images à l'aide de Java"
date: Thu, 17 Dec 2020 10:02:00 +0000
draft: false
url: /fr/2020/12/17/remove-metadata-from-documents-and-images-using-java/
author: 'Shoaib Khan'
summary: "Les **métadonnées** sont les données qui fournissent des informations sur les données réelles. Il est communément décrit comme « **données sur les données** ». Lorsque vous envoyez un fichier à quelqu'un, ce n'est pas une bonne pratique d'envoyer des métadonnées. Il peut révéler au destinataire vos informations que vous ne souhaitez peut-être pas partager. Certains des exemples incluent; Nom, nom de l'entreprise, date de modification du document, marque et modèle de l'appareil photo, etc. Dans cet article, nous allons ** supprimer par programme les métadonnées des images et des documents à l'aide de Java **."
tags: ['metadata cleaner using Java', 'remove metadata from documents in Java', 'remove metadata from images in Java', 'remove metadata using Java']
categories: ['GroupDocs.Metadata Product Family']
---

Les **métadonnées** sont les données qui fournissent des informations sur les données réelles. Il est communément décrit comme « **données sur les données** ». Lorsque vous envoyez un fichier à quelqu'un, ce n'est pas une bonne pratique d'envoyer des métadonnées. Il peut révéler au destinataire vos informations que vous ne souhaitez peut-être pas partager. Certains des exemples incluent; Nom, nom de l'entreprise, date de modification du document, marque et modèle de l'appareil photo, etc. Dans cet article, nous allons ** supprimer par programme les métadonnées des images et des documents à l'aide de Java **.

* [API de nettoyage de métadonnées Java][1]
* [Supprimer les métadonnées des documents][2]
* [Nettoyer les métadonnées des images][3]
* [Supprimer les métadonnées sélectives des documents et des images][4]

## API de nettoyage de métadonnées Java {#java-metadata-cleaner-api}

[GroupDocs.Metadata for Java][5] est une API de métadonnées pour Java qui prend en charge la plupart des normes de métadonnées populaires telles que EXIF, XMP, IPTC, balise ID3, etc. Elle permet aux développeurs Java d'ajouter, de modifier, d'extraire et de supprimer des métadonnées. avec diverses options parmi une longue liste de [formats pris en charge][6] de documents, d'images et d'autres fichiers.

Les étapes de cet article et les exemples de code utilisent l'API GroupDocs.Metadata. Donc, avant de continuer, assurez-vous de préparer l'environnement de développement en utilisant l'une des options suivantes :

* Obtenez le fichier JAR à partir de la section [downloads][7].
* Ajoutez la configuration pom.xml suivante dans vos applications Java basées sur Maven

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
        <artifactId>groupdocs-metadata</artifactId>
        <version>20.11</version> 
</dependency>
```

## Supprimer les métadonnées des documents à l'aide de Java {#remove-documents-metadata}

Pour supprimer toutes les propriétés de métadonnées disponibles sans appliquer de filtre et pour rester en sécurité à l'ère du COVID-19, utilisez la méthode ** assainize **. Voici les étapes pour supprimer les métadonnées des documents à l'aide de GroupDocs.Metadata pour Java.

* Instanciez l'objet de la classe [Metadata][8], en passant le chemin du document cible en paramètre.
* Appelez la méthode [sanitize][9]. Il renvoie le nombre de propriétés de métadonnées supprimées.
* Enregistrez le fichier de sortie avec les métadonnées effacées à l'aide de la méthode [save][10].

L'exemple de code Java suivant montre comment supprimer et effacer les métadonnées du document.

```
/*
* Supprimez toutes les propriétés de métadonnées détectées de Word, Excel, 
* PowerPoint, PDF et autres documents utilisant Java
*/
Metadata metadata = new Metadata("filePath/document.pdf");
int affected = metadata.sanitize();
metadata.save("filePath/output.pdf"); // Save the output document with no metadata 
```

## Supprimer les métadonnées des images à l'aide de Java {#remove-images-metadata}

Si vous souhaitez supprimer toutes les métadonnées de vos images à l'aide de Java, vous pouvez utiliser la même méthode de nettoyage en suivant les mêmes étapes :

* Créez l'objet de la classe [Metadata][11], en passant le chemin du document cible comme paramètre.
* Appelez la méthode [sanitize][12].
* Enregistrez le fichier de sortie en utilisant la méthode [save][13].

```
/*
* Supprimez toutes les propriétés de métadonnées détectées de JPEG, PNG,
* WebP, BMP, GIF, TIFF et autres images utilisant Java
*/
Metadata metadata = new Metadata("filePath/document.jpg");
int affected = metadata.sanitize();
metadata.save("filePath/output.jpg"); // Save the output image having no metadata
```

## Supprimer les métadonnées sélectives des documents et des images à l'aide de Java {#remove-selective-metadata}

Il n'est pas toujours nécessaire de supprimer toutes les métadonnées disponibles des fichiers, cependant, nous souhaitons parfois supprimer les propriétés de métadonnées sélectives. Les étapes suivantes montrent comment localiser et supprimer les métadonnées à l'aide du nom spécifique de la propriété.

* Créez un objet [Metadata][14] pour charger le document ou le fichier image ciblé.
* Créez des spécifications personnalisées pour trouver les propriétés des métadonnées.
* Appelez la méthode [removeProperties][15] et transmettez les spécifications personnalisées.
* Enregistrez le fichier de sortie en utilisant la méthode [save][16].

```
// Supprimer les propriétés de métadonnées des documents et des images qui satisfont le filtre personnalisé à l'aide de Java
public class RemoveMetadataProperties {
	public static void removeMetadataProperties() {
		Metadata metadata = new Metadata("filePath/document.docx");
		/*
		 * Remove all the properties that: 
		 * contains the name of the document author OR
		 * it refers to the last editor OR 
		 * the property value is a string AND equal to the given string "GroupDocs"
		 */
		int affected = metadata.removeProperties(new ContainsTagSpecification(Tags.getPerson().getCreator())
				.or(new ContainsTagSpecification(Tags.getPerson().getEditor()))
				.or(new OfTypeSpecification(MetadataPropertyType.String)
						.and(new RemoveMetadataProperties().new WithValueSpecification("GroupDocs"))));

		System.out.println(String.format("Properties removed: %s", affected));

		metadata.save("outputPath/document.docx");
	}

	// Create personalized specifications to filter metadata properties
	public class WithValueSpecification extends Specification {
		public WithValueSpecification(Object value) {
			setValue(value);
		}

		public final Object getValue() {
			return auto_Value;
		}

		private void setValue(Object value) {
			auto_Value = value;
		}

		private Object auto_Value;

		public boolean isSatisfiedBy(MetadataProperty candidate) {
			return candidate.getValue().getRawValue().equals(getValue());
		}
	}
}
```

## Conclusion

Dans cet article, nous avons appris à nettoyer les métadonnées des documents et des images à l'aide de Java. Vous pouvez maintenant créer votre propre application Java de nettoyage de métadonnées. Il peut prendre en charge la suppression des métadonnées des documents de traitement de texte, des feuilles de calcul, des présentations, des fichiers PDF, des images, des e-mails, des livres électroniques, des dessins, des fichiers zip et bien d'autres. Vous pouvez en savoir plus sur l'API de métadonnées Java à partir de la [documentation][17].

## Voir également

* [Supprimer les métadonnées des documents et des images à l'aide de C #][18]
* [Gérer les données EXIF des images à l'aide de Java][19]
* [Gérer les données EXIF des images en C #][20]







[1]: #java-metadata-cleaner-api
[2]: #remove-documents-metadata
[3]: #remove-images-metadata
[4]: #remove-selective-metadata
[5]: https://products.groupdocs.com/metadata/java
[6]: https://docs.groupdocs.com/metadata/java/supported-document-formats/
[7]: https://downloads.groupdocs.com/metadata/java
[8]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata
[9]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#sanitize()
[10]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#save(java.lang.String)
[11]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata
[12]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#sanitize()
[13]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#save(java.lang.String)
[14]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata
[15]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#removeProperties(com.groupdocs.metadata.search.Specification)
[16]: https://apireference.groupdocs.com/metadata/java/com.groupdocs.metadata/Metadata#save(java.lang.String)
[17]: https://docs.groupdocs.com/metadata/java/
[18]: https://blog.groupdocs.com/2020/12/29/remove-metadata-of-documents-and-images-using-csharp/
[19]: https://blog.groupdocs.com/2020/05/12/handle-exif-data-of-jpg-png-webp-images-in-java/
[20]: https://blog.groupdocs.com/2020/05/13/manage-exif-data-in-csharp-net-for-jpeg-png-tiff-webp-images/


