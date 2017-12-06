---
title: "Prognozowanie XML w różnych kształtu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2da7ec97-34f7-443d-9a48-b162ac58236b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2cf5f963b8675f22c9cab0297d8f48eb68f5aefb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="projecting-xml-in-a-different-shape-visual-basic"></a><span data-ttu-id="01ad6-102">Prognozowanie XML w różnych kształtu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01ad6-102">Projecting XML in a Different Shape (Visual Basic)</span></span>
<span data-ttu-id="01ad6-103">W tym temacie przedstawiono przykład projekcji kod XML, który jest w kształcie innego niż źródło XML.</span><span class="sxs-lookup"><span data-stu-id="01ad6-103">This topic shows an example of projecting XML that is in a different shape than the source XML.</span></span>  
  
 <span data-ttu-id="01ad6-104">Wiele typowych transformacji XML składają się z łańcuchowa zapytań, jak w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="01ad6-104">Many typical XML transformations consist of chained queries, as in this example.</span></span> <span data-ttu-id="01ad6-105">Jest często do jakiegoś typu XML, projektu pośrednich wyników jako kolekcji typy anonimowe lub nazw typów, a następnie na koniec projektu wyniki z powrotem w formacie XML, który znajduje się w zupełnie innego kształtu niż źródłowy XML.</span><span class="sxs-lookup"><span data-stu-id="01ad6-105">It is common to start with some form of XML, project intermediate results as collections of anonymous types or named types, and then finally to project the results back into XML that is in an entirely different shape than the source XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01ad6-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="01ad6-106">Example</span></span>  
 <span data-ttu-id="01ad6-107">W tym przykładzie przetwarza dokument schemat WordprocessingML pobieranie węzłów akapitu z dokumentem schemat WordprocessingML.</span><span class="sxs-lookup"><span data-stu-id="01ad6-107">This example processes a WordprocessingML document, retrieving the paragraph nodes from a WordprocessingML document.</span></span> <span data-ttu-id="01ad6-108">Identyfikuje również style i text każdego akapitu.</span><span class="sxs-lookup"><span data-stu-id="01ad6-108">It also identifies the style and text of each paragraph.</span></span> <span data-ttu-id="01ad6-109">Na koniec przykładzie projekcję XML z innego kształtu.</span><span class="sxs-lookup"><span data-stu-id="01ad6-109">Finally, the example projects XML with a different shape.</span></span> <span data-ttu-id="01ad6-110">W tym przykładzie kompilacje w poprzednich przykładach, w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="01ad6-110">This example builds on the previous examples in this tutorial.</span></span> <span data-ttu-id="01ad6-111">Nowy raport, który wykonuje projekcji nazywa w komentarzach w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="01ad6-111">The new statement that does the projection is called out in comments in the code below.</span></span>  
  
 <span data-ttu-id="01ad6-112">Aby uzyskać instrukcje dotyczące tworzenia dokumentu źródłowego dla tego przykładu, zobacz [tworzenie źródło dokumentu pakietu Office Open XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="01ad6-112">For instructions for creating the source document for this example, see [Creating the Source Office Open XML Document (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-the-source-office-open-xml-document.md).</span></span>  
  
 <span data-ttu-id="01ad6-113">W tym przykładzie użyto klasy z zestawu WindowsBase.</span><span class="sxs-lookup"><span data-stu-id="01ad6-113">This example uses classes from the WindowsBase assembly.</span></span> <span data-ttu-id="01ad6-114">Używa typów w <xref:System.IO.Packaging?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="01ad6-114">It uses types in the <xref:System.IO.Packaging?displayProperty=nameWithType> namespace.</span></span>  
  
```vb  
Imports <xmlns:w="http://schemas.openxmlformats.org/wordprocessingml/2006/main">  
  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(ByVal source As IEnumerable(Of String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As String In source  
            sb.Append(s)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String)) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item))  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each s As T In source  
            sb.Append(s).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function StringConcatenate(Of T)(ByVal source As IEnumerable(Of T), _  
    ByVal func As Func(Of T, String), ByVal separator As String) As String  
        Dim sb As StringBuilder = New StringBuilder()  
        For Each item As T In source  
            sb.Append(func(item)).Append(separator)  
        Next  
        Return sb.ToString()  
    End Function  
  
    Public Function ParagraphText(ByVal e As XElement) As String  
        Dim w As XNamespace = e.Name.Namespace  
        Return (e.<w:r>.<w:t>).StringConcatenate(Function(element) CStr(element))  
    End Function  
  
    ' Following function is required because VB does not support short circuit evaluation  
    Private Function GetStyleOfParagraph(ByVal styleNode As XElement, _  
                                         ByVal defaultStyle As String) As String  
        If (styleNode Is Nothing) Then  
            Return defaultStyle  
        Else  
            Return styleNode.@w:val  
        End If  
    End Function  
  
    Sub Main()  
        Dim fileName = "SampleDoc.docx"  
  
        Dim documentRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/officeDocument"  
        Dim stylesRelationshipType = _  
          "http://schemas.openxmlformats.org/officeDocument/2006/relationships/styles"  
        Dim wordmlNamespace = _  
          "http://schemas.openxmlformats.org/wordprocessingml/2006/main"  
        Dim xDoc As XDocument = Nothing  
        Dim styleDoc As XDocument = Nothing  
  
        Using wdPackage As Package = Package.Open(fileName, FileMode.Open, FileAccess.Read)  
            Dim docPackageRelationship As PackageRelationship = _  
              wdPackage.GetRelationshipsByType(documentRelationshipType).FirstOrDefault()  
            If (docPackageRelationship IsNot Nothing) Then  
                Dim documentUri As Uri = PackUriHelper.ResolvePartUri(New Uri("/", UriKind.Relative), _  
                  docPackageRelationship.TargetUri)  
                Dim documentPart As PackagePart = wdPackage.GetPart(documentUri)  
  
                '  Load the document XML in the part into an XDocument instance.  
                xDoc = XDocument.Load(XmlReader.Create(documentPart.GetStream()))  
  
                '  Find the styles part. There will only be one.  
                Dim styleRelation As PackageRelationship = _  
                  documentPart.GetRelationshipsByType(stylesRelationshipType).FirstOrDefault()  
                If (Not (styleRelation Is Nothing)) Then  
                    Dim styleUri As Uri = _  
                      PackUriHelper.ResolvePartUri(documentUri, styleRelation.TargetUri)  
                    Dim stylePart As PackagePart = wdPackage.GetPart(styleUri)  
  
                    '  Load the style XML in the part into an XDocument instance.  
                    styleDoc = XDocument.Load(XmlReader.Create(stylePart.GetStream()))  
                End If  
            End If  
        End Using  
  
        Dim defaultStyle As String = _  
            ( _  
                From style In styleDoc.Root.<w:style> _  
                Where style.@w:type = "paragraph" And _  
                      style.@w:default = "1" _  
                Select style _  
            ).First().@w:styleId  
  
        ' Find all paragraphs in the document.  
        Dim paragraphs = _  
            From para In xDoc.Root.<w:body>...<w:p> _  
        Let styleNode As XElement = para.<w:pPr>.<w:pStyle>.FirstOrDefault _  
        Select New With { _  
            .ParagraphNode = para, _  
            .StyleName = GetStyleOfParagraph(styleNode, defaultStyle) _  
        }  
  
        ' Retrieve the text of each paragraph.  
        Dim paraWithText = _  
            From para In paragraphs _  
            Select New With { _  
                .ParagraphNode = para.ParagraphNode, _  
                .StyleName = para.StyleName, _  
                .Text = ParagraphText(para.ParagraphNode) _  
            }  
  
        ' Following is the new code that projects XML in a new shape  
        Dim root As XElement = _  
            <Root>  
                <%= _  
                    From p In paraWithText _  
                    Select _  
                    <Paragraph>  
                        <StyleName><%= p.StyleName %></StyleName>  
                        <Text><%= p.Text %></Text>  
                    </Paragraph> _  
                %>  
            </Root>  
  
        Console.WriteLine(root)  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="01ad6-115">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="01ad6-115">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Paragraph>  
    <StyleName>Heading1</StyleName>  
    <Text>Parsing WordprocessingML with LINQ to XML</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text>The following example prints to the console.</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>Imports System</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>Class Program</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>    Public Shared  Sub Main(ByVal args() As String)</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>        Console.WriteLine("Hello World")</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>    End Sub</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>End Class</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text>This example produces the following output:</Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Normal</StyleName>  
    <Text></Text>  
  </Paragraph>  
  <Paragraph>  
    <StyleName>Code</StyleName>  
    <Text>Hello World</Text>  
  </Paragraph>  
</Root>  
```  
  
## <a name="next-steps"></a><span data-ttu-id="01ad6-116">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="01ad6-116">Next Steps</span></span>  
 <span data-ttu-id="01ad6-117">W następnym przykładzie będzie kwerendy można znaleźć w dokumencie programu Word cały tekst:</span><span class="sxs-lookup"><span data-stu-id="01ad6-117">In the next example, you'll query to find all the text in a Word document:</span></span>  
  
-   [<span data-ttu-id="01ad6-118">Wyszukiwanie tekstu w dokumentach programu Word (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01ad6-118">Finding Text in Word Documents (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/finding-text-in-word-documents.md)  
  
## <a name="see-also"></a><span data-ttu-id="01ad6-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01ad6-119">See Also</span></span>  
 [<span data-ttu-id="01ad6-120">Samouczek: Manipulowanie zawartości w dokumencie schemat WordprocessingML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01ad6-120">Tutorial: Manipulating Content in a WordprocessingML Document (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)