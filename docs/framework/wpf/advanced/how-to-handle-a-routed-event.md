---
title: "Jak obsłużyć zdarzenie trasowane"
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
- routed events [WPF], handling
- bubbling events [WPF]
ms.assetid: 157787b4-f469-4047-8777-5b034145f32e
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 83f59f2df9311f30995b18529a733a5569c85ee0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-a-routed-event"></a><span data-ttu-id="c7fd7-102">Jak obsłużyć zdarzenie trasowane</span><span class="sxs-lookup"><span data-stu-id="c7fd7-102">How to: Handle a Routed Event</span></span>
<span data-ttu-id="c7fd7-103">Ten przykład przedstawia sposób propagacji pracy zdarzenia i jak napisać programu obsługi, który może przetwarzać danych kierowanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c7fd7-103">This example shows how bubbling events work and how to write a handler that can process the routed event data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7fd7-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="c7fd7-104">Example</span></span>  
 <span data-ttu-id="c7fd7-105">W [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], elementy są rozmieszczane w strukturze drzewa elementu.</span><span class="sxs-lookup"><span data-stu-id="c7fd7-105">In [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)], elements are arranged in an element tree structure.</span></span> <span data-ttu-id="c7fd7-106">Element nadrzędny mogą uczestniczyć w obsłudze zdarzeń, które są początkowo zgłoszony przez elementy podrzędne w drzewie elementu.</span><span class="sxs-lookup"><span data-stu-id="c7fd7-106">The parent element can participate in the handling of events that are initially raised by child elements in the element tree.</span></span> <span data-ttu-id="c7fd7-107">Jest to możliwe z powodu zdarzenia routingu.</span><span class="sxs-lookup"><span data-stu-id="c7fd7-107">This is possible because of event routing.</span></span>  
  
 <span data-ttu-id="c7fd7-108">Zazwyczaj kierowane zdarzenia wykonaj jedną z dwóch strategii routingu propagacji lub tunelowania.</span><span class="sxs-lookup"><span data-stu-id="c7fd7-108">Routed events typically follow one of two routing strategies, bubbling or tunneling.</span></span> <span data-ttu-id="c7fd7-109">W tym przykładzie koncentruje się na zdarzeń propagacji i używa <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> zdarzeń do wyświetlenia działa jak routingu.</span><span class="sxs-lookup"><span data-stu-id="c7fd7-109">This example focuses on the bubbling event and uses the <xref:System.Windows.Controls.Primitives.ButtonBase.Click?displayProperty=nameWithType> event to show how routing works.</span></span>  
  
 <span data-ttu-id="c7fd7-110">Poniższy przykład tworzy dwa <xref:System.Windows.Controls.Button> formanty i używa [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atrybutu dołączania program obsługi zdarzeń do wspólnego elementu nadrzędnego, który w tym przykładzie jest <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="c7fd7-110">The following example creates two <xref:System.Windows.Controls.Button> controls and uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] attribute syntax to attach an event handler to a common parent element, which in this example is <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="c7fd7-111">Zamiast dołączanie obsługi poszczególnych zdarzeń dla każdego <xref:System.Windows.Controls.Button> elementu podrzędnego w przykładzie użyto Składnia atrybutu można dołączyć do programu obsługi zdarzeń <xref:System.Windows.Controls.StackPanel> elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="c7fd7-111">Instead of attaching individual event handlers for each <xref:System.Windows.Controls.Button> child element, the example uses attribute syntax to attach the event handler to the <xref:System.Windows.Controls.StackPanel> parent element.</span></span> <span data-ttu-id="c7fd7-112">Ten wzorzec obsługi zdarzeń pokazano, jak używać zdarzeń routingu jako technika zmniejszenie liczby elementów, którego program obsługi jest podłączony.</span><span class="sxs-lookup"><span data-stu-id="c7fd7-112">This event-handling pattern shows how to use event routing as a technique for reducing the number of elements where a handler is attached.</span></span> <span data-ttu-id="c7fd7-113">Wszystkie zdarzenia propagacji dla każdego <xref:System.Windows.Controls.Button> Rozsyłanie za pomocą elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="c7fd7-113">All the bubbling events for each <xref:System.Windows.Controls.Button> route through the parent element.</span></span>  
  
 <span data-ttu-id="c7fd7-114">Należy pamiętać, że w nadrzędnej <xref:System.Windows.Controls.StackPanel> elementu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> Nazwa zdarzenia określony jako atrybut częściowo jest kwalifikowany za pomocą nazw <xref:System.Windows.Controls.Button> klasy.</span><span class="sxs-lookup"><span data-stu-id="c7fd7-114">Note that on the parent <xref:System.Windows.Controls.StackPanel> element, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event name specified as the attribute is partially qualified by naming the <xref:System.Windows.Controls.Button> class.</span></span> <span data-ttu-id="c7fd7-115"><xref:System.Windows.Controls.Button> Jest klasa <xref:System.Windows.Controls.Primitives.ButtonBase> klasy, która ma <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzenia w jego elementów członkowskich wyświetlania.</span><span class="sxs-lookup"><span data-stu-id="c7fd7-115">The <xref:System.Windows.Controls.Button> class is a <xref:System.Windows.Controls.Primitives.ButtonBase> derived class that has the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event in its members listing.</span></span> <span data-ttu-id="c7fd7-116">Ta technika częściowe kwalifikacji dołączanie program obsługi zdarzeń jest niezbędne, jeśli nie istnieje zdarzenie, które jest obsługiwane w elementach członkowskich wyświetlania elementu, w którym jest umocowana Obsługa kierowanego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="c7fd7-116">This partial qualification technique for attaching an event handler is necessary if the event that is being handled does not exist in the members listing of the element where the routed event handler is attached.</span></span>  
  
 [!code-xaml[RoutedEventHandle#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml#xaml)]  
  
 <span data-ttu-id="c7fd7-117">Następujący przykład uchwytów <xref:System.Windows.Controls.Primitives.ButtonBase.Click> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="c7fd7-117">The following example handles the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span>  <span data-ttu-id="c7fd7-118">Przykład raporty element, który obsługuje zdarzenie i który element wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="c7fd7-118">The example reports which element handles the event and which element raises the event.</span></span> <span data-ttu-id="c7fd7-119">Program obsługi zdarzeń jest wykonywany, gdy użytkownik kliknie przycisk albo.</span><span class="sxs-lookup"><span data-stu-id="c7fd7-119">The event handler is executed when the user clicks either button.</span></span>  
  
 [!code-csharp[RoutedEventHandle#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventHandle/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventHandle#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventHandle/VisualBasic/MainWindow.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="c7fd7-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c7fd7-120">See Also</span></span>  
 <xref:System.Windows.RoutedEvent>  
 [<span data-ttu-id="c7fd7-121">Dane wejściowe — omówienie</span><span class="sxs-lookup"><span data-stu-id="c7fd7-121">Input Overview</span></span>](../../../../docs/framework/wpf/advanced/input-overview.md)  
 [<span data-ttu-id="c7fd7-122">Omówienie kierowane zdarzenia</span><span class="sxs-lookup"><span data-stu-id="c7fd7-122">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="c7fd7-123">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="c7fd7-123">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)  
 [<span data-ttu-id="c7fd7-124">Składnia języka XAML szczegółowo</span><span class="sxs-lookup"><span data-stu-id="c7fd7-124">XAML Syntax In Detail</span></span>](../../../../docs/framework/wpf/advanced/xaml-syntax-in-detail.md)