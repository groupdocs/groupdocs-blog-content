---
title: 'Edit Watermark''s Text and Image using GroupDocs.Watermark for Java 18.3'
date: Fri, 06 Apr 2018 00:38:07 +0000
draft: false
url: /2018/04/06/edit-watermark-text-and-image-using-groupdocs.watermark-for-java-18.3/
author: 'Usman Aziz'
summary: ''
tags: ['document-watermark', 'Java document watermarking API', 'watermarking API for Java', 'GroupDocs.Watermark for Java', 'GroupDocs.Watermark for Java Releases']
categories: ['GroupDocs.Watermark Product Family']
---

[![GroupDocs Watermark for .NET](http://blog.groupdocs.com/wp-content/uploads/sites/4/2018/01/groupdocs-watermark-java.png)](https://products.groupdocs.com/watermark/java)We are excited to announce that we have released version 18.3 of [GroupDocs.Watermark for Java](https://products.groupdocs.com/watermark/java). The latest version supports replacing text and image for the found watermarks across all the supported formats. It also allows editing of the objects that can be considered as the watermark in **PDF** documents. Following are some salient features of GroupDocs.Watermark for Java 18.3

# Replacing Text and Image for Found Watermarks

The latest version allows replacing text and image for the found possible watermarks that we get in a search result. Following sections demonstrate how to replace text and image for the found watermarks.

## Replacing Text```
Document doc = Document.load("D:\\input.pptx");
 
TextSearchCriteria searchCriteria = new TextSearchCriteria("test", false);
PossibleWatermarkCollection watermarks = doc.findWatermarks(searchCriteria);
for (PossibleWatermark watermark : watermarks)
{
    try
    {
        watermark.setText("passed");
    }
    catch (Exception e)
    {
        // Found entity may not support text editing
        // Passed argument can have inappropriate value
        // Process such cases here
    }
}
 
doc.save("D:\\output.pptx");
doc.close();
```

## Replacing Image```
String imagePath = "D:\\test.png";
File imageFile = new File(imagePath);
byte[] imageBytes = new byte[(int)imageFile.length()];
InputStream imageInputStream = new FileInputStream(imageFile);
imageInputStream.read(imageBytes);
imageInputStream.close();
 
Document doc = Document.load("D:\\input.pdf");
 
SearchCriteria searchCriteria = new ImageDctHashSearchCriteria("D:\\logo.bmp");
PossibleWatermarkCollection watermarks = doc.findWatermarks(searchCriteria);
for (PossibleWatermark watermark : watermarks)
{
    try
    {
        watermark.setImageData(imageBytes);
    }
    catch (Exception e)
    {
        // Found entity may not support image replacing
        // Passed image can have inappropriate format
        // Process such cases here
    }
}
 
doc.save("D:\\output.pdf");
doc.close();
```For more details on this feature, please visit [this](https://docs.groupdocs.com/watermark/java/) documentation article.

# Editing Watermark Objects in PDF Documents

## Replacing Text for Particular ObjectsYou can now replace text for the particular XObjects, artifacts and the annotations in a PDF document. Furthermore, replacing text with formatting is also supported. Following sections demonstrate this feature with code samples.

### Replacing Text```
PdfDocument doc = Document.load(PdfDocument.class, "D:\\sample.pdf");
// Replace text for XObjects
for (PdfXObject xObject : doc.getPages().get_Item(0).getXObjects())
{
    if (xObject.getText().contains("Test"))
    {
        xObject.setText("Passed");
    }
}
// Replace text for artifacts
for (PdfArtifact artifact : doc.getPages().get_Item(0).getArtifacts())
{
    if (artifact.getText().contains("Test"))
    {
        artifact.setText("Passed");
    }
}   

// Replace text for annotations
for (PdfAnnotation annotation : doc.getPages().get_Item(0).getAnnotations())
{
    if (annotation.getText().contains("Test"))
    {
        annotation.setText("Passed");
    }
}
doc.save("D:\\output.pdf");
doc.close(); 
```

### Replacing Text with Formatting```
PdfDocument doc = Document.load(PdfDocument.class, "D:\\sample.pdf");

// Replace text for XObjects    
for (PdfXObject xObject : doc.getPages().get_Item(0).getXObjects())
{
    if (xObject.getText().contains("Test"))
    {
        xObject.getFormattedTextFragments().clear();
        xObject.getFormattedTextFragments().add("Passed", new Font("Calibri", 19, FontStyle.Bold), Color.getRed(), Color.getAqua());
    }
}
// Replace text for artifacts
for (PdfArtifact artifact : doc.getPages().get_Item(0).getArtifacts())
{
    if (artifact.getText().contains("Test"))
    {
        artifact.getFormattedTextFragments().clear();
        artifact.getFormattedTextFragments().add("Passed", new Font("Calibri", 19, FontStyle.Bold), Color.getRed(), Color.getAqua());
    }
}    
// Replace text for annotations
for (PdfAnnotation annotation : doc.getPages().get_Item(0).getAnnotations())
{
    if (annotation.getText().contains("Test"))
    {
        annotation.getFormattedTextFragments().clear();
        annotation.getFormattedTextFragments().add("Passed", new Font("Calibri", 19, FontStyle.Bold), Color.getRed(), Color.getAqua());
    }
}    

doc.save("D:\\output.pdf");
doc.close();
```

## Replacing Image for Particular ObjectsThe version 18.3 also supports replacing image for the particular XObjects, artifacts and the annotations as shown in the following code sample.```
String imagePath = "D:\\test.png";
File imageFile = new File(imagePath);
byte[] imageBytes = new byte[(int)imageFile.length()];
InputStream imageInputStream = new FileInputStream(imageFile);
imageInputStream.read(imageBytes);
imageInputStream.close();

PdfDocument doc = Document.load(PdfDocument.class, "D:\\sample.pdf");

// Replace image for XObjects
for (PdfXObject xObject : doc.getPages().get_Item(0).getXObjects())
{
    if (xObject.getImage() != null)
    {
        xObject.setImage(new PdfWatermarkableImage(imageBytes));
    }
}    
// Replace image for artifacts
for (PdfArtifact artifact : doc.getPages().get_Item(0).getArtifacts())
{
    if (artifact.getImage() != null)
    {
        artifact.setImage(new PdfWatermarkableImage(imageBytes));
    }
}
// Replace image for annotations
for (PdfAnnotation annotation : doc.getPages().get_Item(0).getAnnotations())
{
    if (annotation.getImage() != null)
    {
        annotation.setImage(new PdfWatermarkableImage(imageBytes));
    }
}

doc.save("D:\\output.pdf");
doc.close();
```For more details on this feature, please visit [this](https://docs.groupdocs.com/watermark/java/) documentation article.

# Available Channels and Resources

*   [Download](https://downloads.groupdocs.com/watermark/java "GroupDocs.Watermark MSI") - JAR
*   [Documentation](https://docs.groupdocs.com/watermark/java/ "Watermark API documentation") - API Documentation
*   [Examples](https://github.com/groupdocs-watermark/GroupDocs.Watermark-for-Java "How to use Watermark API") - Source Code Examples
*   [Product Support Forum](https://forum.groupdocs.com/c/watermark) - Technical Support Forum for GroupDocs.Watermark

# Feedback

As always, if you have any questions or suggestions, feel free to write on our [forum](https://forum.groupdocs.com/"Technical Support Forum").





