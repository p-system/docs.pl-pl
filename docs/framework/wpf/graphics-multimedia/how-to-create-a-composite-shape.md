---
title: "Jak utworzyć kształt złożony"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- shapes [WPF], composite
- composite shapes [WPF]
- graphics [WPF], composite shapes
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9ded7bd25f7f416bc512051f883b4ae12b2fa56d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-create-a-composite-shape"></a><span data-ttu-id="28d9a-102">Jak utworzyć kształt złożony</span><span class="sxs-lookup"><span data-stu-id="28d9a-102">How to: Create a Composite Shape</span></span>
<span data-ttu-id="28d9a-103">W tym przykładzie przedstawiono sposób tworzenia złożonych kształtów za pomocą <xref:System.Windows.Media.Geometry> obiekty i wyświetlać je za pomocą <xref:System.Windows.Shapes.Path> elementu.</span><span class="sxs-lookup"><span data-stu-id="28d9a-103">This example shows how to create composite shapes using <xref:System.Windows.Media.Geometry> objects and display them using a <xref:System.Windows.Shapes.Path> element.</span></span> <span data-ttu-id="28d9a-104">W poniższym przykładzie <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, a <xref:System.Windows.Media.RectangleGeometry> są używane z <xref:System.Windows.Media.GeometryGroup> do tworzenia złożonych kształtu.</span><span class="sxs-lookup"><span data-stu-id="28d9a-104">In the following example, a <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.EllipseGeometry>, and a <xref:System.Windows.Media.RectangleGeometry> are used with a <xref:System.Windows.Media.GeometryGroup> to create a composite shape.</span></span> <span data-ttu-id="28d9a-105">Mają geometrię są rysowane przy użyciu <xref:System.Windows.Shapes.Path> elementu.</span><span class="sxs-lookup"><span data-stu-id="28d9a-105">The geometries are then drawn using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="28d9a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="28d9a-106">Example</span></span>  
 [!code-xaml[GeometrySample#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 <span data-ttu-id="28d9a-107">Na poniższej ilustracji przedstawiono utworzone w poprzednim przykładzie kształtu.</span><span class="sxs-lookup"><span data-stu-id="28d9a-107">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="28d9a-108">![Złożona geometria utworzona przy użyciu obiektu GeometryGroup](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span><span class="sxs-lookup"><span data-stu-id="28d9a-108">![A composite geometry created using a GeometryGroup](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.jpg "wcpsdk_graphicsmm_compositegeometryexample1")</span></span>  
<span data-ttu-id="28d9a-109">Złożone typy geometryczne</span><span class="sxs-lookup"><span data-stu-id="28d9a-109">Composite Geometry</span></span>  
  
 <span data-ttu-id="28d9a-110">Kształtów bardziej złożonych, takie jak wielokątów i kształty z segmentów krzywych może zostać utworzony przy użyciu <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="28d9a-110">More complex shapes, such as polygons and shapes with curved segments, may be created using a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="28d9a-111">Na przykład pokazujący sposób tworzenia kształtu przy użyciu <xref:System.Windows.Media.PathGeometry>, zobacz [tworzenie kształtu przy użyciu PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="28d9a-111">For an example showing how to create a shape using a <xref:System.Windows.Media.PathGeometry>, see [Create a Shape by Using a PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  <span data-ttu-id="28d9a-112">Mimo że w tym przykładzie powoduje kształtu do ekranu przy użyciu <xref:System.Windows.Shapes.Path> elementu <xref:System.Windows.Media.Geometry> obiektów może również służyć do opisania zawartości <xref:System.Windows.Media.GeometryDrawing> lub <xref:System.Windows.Media.DrawingContext>.</span><span class="sxs-lookup"><span data-stu-id="28d9a-112">Although this example renders a shape to the screen using a <xref:System.Windows.Shapes.Path> element, <xref:System.Windows.Media.Geometry> objects may also be used to describe the contents of a <xref:System.Windows.Media.GeometryDrawing> or a <xref:System.Windows.Media.DrawingContext>.</span></span> <span data-ttu-id="28d9a-113">Mogą one również służyć do wycinka i testowania trafień.</span><span class="sxs-lookup"><span data-stu-id="28d9a-113">They may also be used for clipping and hit-testing.</span></span>  
  
 <span data-ttu-id="28d9a-114">Ten przykład jest częścią większego przykładu; pełny przykład, zobacz [próbki mają geometrię](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="28d9a-114">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>