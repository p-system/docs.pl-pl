---
title: Serializacja na element XmlReader (wywoływanie XSLT) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 8b64f95a-e8f6-40f7-99f9-a8002c63af96
ms.openlocfilehash: 05754593f4f30683ffabecaa8e16c35bf836a3f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33645593"
---
# <a name="serializing-to-an-xmlreader-invoking-xslt-visual-basic"></a>Serializacja na element XmlReader (wywoływanie XSLT) (Visual Basic)
Jeśli używasz <xref:System.Xml?displayProperty=nameWithType> możliwości współdziałania [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], można użyć <xref:System.Xml.Linq.XNode.CreateReader%2A> do utworzenia <xref:System.Xml.XmlReader>. Moduł odczytujący tego <xref:System.Xml.XmlReader> odczytuje węzły drzewa XML i odpowiednio je przetwarza.  
  
## <a name="invoking-an-xslt-transformation"></a>Wywoływanie transformacji XSLT  
 Jedno możliwe użycie tej metody jest wywoływanie transformację XSLT. Można utworzyć drzewa XML, Utwórz <xref:System.Xml.XmlReader> z drzewa XML, Utwórz nowy dokument, a następnie utwórz <xref:System.Xml.XmlWriter> zapis do nowego dokumentu. Następnie można wywołać przekształcenia XSLT, przekazując <xref:System.Xml.XmlReader> i <xref:System.Xml.XmlWriter>. Po pomyślnym zakończeniu transformacja, nowe drzewo XML jest wypełniana wyniki przekształcenia.  
  
```vb  
Dim xslMarkup As XDocument = _  
    <?xml version='1.0'?>  
    <xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
        <xsl:template match='/Parent'>  
            <Root>  
                <C1>  
                    <xsl:value-of select='Child1'/>  
                </C1>  
                <C2>  
                    <xsl:value-of select='Child2'/>  
                </C2>  
            </Root>  
        </xsl:template>  
    </xsl:stylesheet>  
  
Dim xmlTree As XDocument = _  
    <?xml version='1.0'?>  
    <Parent>  
        <Child1>Child1 data</Child1>  
        <Child2>Child2 data</Child2>  
    </Parent>  
  
Dim newTree As XDocument = New XDocument()  
Using writer As XmlWriter = newTree.CreateWriter()  
    ' Load the style sheet.  
    Dim xslt As XslCompiledTransform = New XslCompiledTransform()  
    xslt.Load(xslMarkup.CreateReader())  
  
    ' Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer)  
End Using  
  
Console.WriteLine(newTree)  
```  
  
 Ten przykład generuje następujące wyniki:  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja drzewa XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
