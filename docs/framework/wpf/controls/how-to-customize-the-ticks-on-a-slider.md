---
title: Jak dostosować znaczniki na suwaku
ms.date: 03/30/2017
helpviewer_keywords:
- TickBar [WPF]
- Slider control [WPF], creating with TickBar
ms.assetid: 4fa694f2-a620-4b15-be78-5f4286f89361
ms.openlocfilehash: 667ec5d5504e18449800598f0b14548b7463bdf3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550881"
---
# <a name="how-to-customize-the-ticks-on-a-slider"></a>Jak dostosować znaczniki na suwaku
W tym przykładzie przedstawiono sposób tworzenia <xref:System.Windows.Controls.Slider> formantu, który ma znaczniki osi.  
  
## <a name="example"></a>Przykład  
 <xref:System.Windows.Controls.Primitives.TickBar> Wyświetla po ustawieniu <xref:System.Windows.Controls.Slider.TickPlacement%2A> właściwości na wartość inną niż <xref:System.Windows.Controls.Primitives.TickPlacement.None>, która jest wartością domyślną.  
  
 Poniższy przykład przedstawia sposób tworzenia <xref:System.Windows.Controls.Slider> z <xref:System.Windows.Controls.Primitives.TickBar> czy wyświetla znaczniki. <xref:System.Windows.Controls.Slider.TickPlacement%2A> i <xref:System.Windows.Controls.Slider.TickFrequency%2A> właściwości definiowanie lokalizacji znaczników oraz interwału między nimi. Po przeniesieniu <xref:System.Windows.Controls.Primitives.Thumb>, etykietki narzędzi zawierają wartość <xref:System.Windows.Controls.Slider>. <xref:System.Windows.Controls.Slider.AutoToolTipPlacement%2A> Właściwość określa, gdzie występuje etykietki narzędzi. <xref:System.Windows.Controls.Primitives.Thumb> Przeniesień odpowiadają lokalizacji znaczników, ponieważ <xref:System.Windows.Controls.Slider.IsSnapToTickEnabled%2A> ma ustawioną wartość `true`.  
  
 Poniższy przykład przedstawia użycie <xref:System.Windows.Controls.Slider.Ticks%2A> właściwość, aby utworzyć znaczniki wzdłuż osi <xref:System.Windows.Controls.Slider> w nieregularnych odstępach czasu.  
  
 [!code-xaml[Slider#4](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Slider/xaml/window1.xaml#4)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.Slider>  
 <xref:System.Windows.Controls.Primitives.TickBar>  
 <xref:System.Windows.Controls.Slider.TickPlacement%2A>  
 [Suwak — tematy porad](http://msdn.microsoft.com/library/534be86c-afb2-425d-8186-631278a9925e)
