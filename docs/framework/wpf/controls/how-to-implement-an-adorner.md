---
title: "Jak implementować moduły definiowania układu"
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
helpviewer_keywords: adorners [WPF], implementing
ms.assetid: 56ae32b6-0599-455c-b52f-2ff97e6f1ec2
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a3f69fee64ea65e8d49cce523c85669993cc6bce
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-implement-an-adorner"></a><span data-ttu-id="48017-102">Jak implementować moduły definiowania układu</span><span class="sxs-lookup"><span data-stu-id="48017-102">How to: Implement an Adorner</span></span>
<span data-ttu-id="48017-103">Ten przykład przedstawia implementację minimalnego modułu definiowania układu kodu.</span><span class="sxs-lookup"><span data-stu-id="48017-103">This example shows a minimal adorner implementation.</span></span>  
  
## <a name="notes-for-implementers"></a><span data-ttu-id="48017-104">Uwagi dotyczące implementacji</span><span class="sxs-lookup"><span data-stu-id="48017-104">Notes for Implementers</span></span>  
 <span data-ttu-id="48017-105">Należy pamiętać, że modułu definiowania układu kodu nie zawierają żadnych zachowania związanego z używaniem renderowania; zapewnienie, że moduł definiowania układu renderuje jest odpowiedzialny za implementujący modułu definiowania układu kodu.</span><span class="sxs-lookup"><span data-stu-id="48017-105">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span>   <span data-ttu-id="48017-106">Jest to często stosowana metoda wdrażania sposób renderowania do przesłonięcia <xref:System.Windows.UIElement.OnRender%2A> — metoda i użyj co najmniej jeden <xref:System.Windows.Media.DrawingContext> obiekty do renderowania elementów wizualnych moduł definiowania układu, zgodnie z potrzebami (jak pokazano w tym przykładzie).</span><span class="sxs-lookup"><span data-stu-id="48017-106">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in this example).</span></span>  
  
## <a name="example"></a><span data-ttu-id="48017-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="48017-107">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="48017-108">Opis</span><span class="sxs-lookup"><span data-stu-id="48017-108">Description</span></span>  
 <span data-ttu-id="48017-109">Niestandardowy moduł definiowania układu kodu jest tworzony przez implementującej klasy, która dziedziczy z klasy abstrakcyjnej <xref:System.Windows.Documents.Adorner> klasy.</span><span class="sxs-lookup"><span data-stu-id="48017-109">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>  <span data-ttu-id="48017-110">Moduł definiowania układu kodu w przykładzie po prostu adorns narożników <xref:System.Windows.UIElement> z okręgi przez zastąpienie <xref:System.Windows.UIElement.OnRender%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="48017-110">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles by overriding the <xref:System.Windows.UIElement.OnRender%2A> method.</span></span>  
  
### <a name="code"></a><span data-ttu-id="48017-111">Kod</span><span class="sxs-lookup"><span data-stu-id="48017-111">Code</span></span>  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
## <a name="see-also"></a><span data-ttu-id="48017-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="48017-112">See Also</span></span>  
 [<span data-ttu-id="48017-113">Omówienie modułu definiowania układu kodu</span><span class="sxs-lookup"><span data-stu-id="48017-113">Adorners Overview</span></span>](../../../../docs/framework/wpf/controls/adorners-overview.md)