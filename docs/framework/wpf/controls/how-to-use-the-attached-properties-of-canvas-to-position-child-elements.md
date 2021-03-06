---
title: Jak użyć załączonych właściwości kanwy, aby ustawić położenie elementów podrzędnych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- attached properties [WPF Designer]
- Canvas control [WPF], attached properties
ms.assetid: 48f1d25d-3820-4107-a4cc-d6c1e5664a44
ms.openlocfilehash: 886440304dc1bebdcfae66676254bef7ac35457d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552377"
---
# <a name="how-to-use-the-attached-properties-of-canvas-to-position-child-elements"></a>Jak użyć załączonych właściwości kanwy, aby ustawić położenie elementów podrzędnych
Ten przykład przedstawia sposób użycia właściwości dołączonych <xref:System.Windows.Controls.Canvas> położenie elementów podrzędnych.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie dodano cztery <xref:System.Windows.Controls.Button> jako elementy podrzędne elementu nadrzędnego <xref:System.Windows.Controls.Canvas>. Każdy element podrzędny reprezentuje różne właściwości dołączonych <xref:System.Windows.Controls.Canvas>: <xref:System.Windows.Controls.Canvas.Bottom%2A>, <xref:System.Windows.Controls.Canvas.Left%2A>, <xref:System.Windows.Controls.Canvas.Right%2A>, i <xref:System.Windows.Controls.Canvas.Top%2A>. Każdy <xref:System.Windows.Controls.Button> znajduje się względem nadrzędnego <xref:System.Windows.Controls.Canvas> i zgodnie z jego wartość właściwości przypisane.  
  
 [!code-cpp[CanvasAttachedProperties#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/CanvasAttachedProperties/CPP/CanvasAttachedProps.cpp#1)]
 [!code-csharp[CanvasAttachedProperties#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CanvasAttachedProperties/CSharp/CanvasAttachedProps.cs#1)]
 [!code-vb[CanvasAttachedProperties#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CanvasAttachedProperties/VisualBasic/CanvasAttachedProps.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Canvas>  
 <xref:System.Windows.Controls.Canvas.Bottom%2A>  
 <xref:System.Windows.Controls.Canvas.Left%2A>  
 <xref:System.Windows.Controls.Canvas.Right%2A>  
 <xref:System.Windows.Controls.Canvas.Top%2A>  
 <xref:System.Windows.Controls.Button>  
 [Panele — omówienie](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Tematy z instrukcjami](../../../../docs/framework/wpf/controls/canvas-how-to-topics.md)  
 [Przegląd właściwości dołączonych](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)
