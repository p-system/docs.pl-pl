---
title: Zdarzenia (WPF)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: AutoGeneratedOrientationPage
helpviewer_keywords:
- Windows Presentation Foundation [WPF], events
- events [WPF], windows
- WPF [WPF], events
ms.assetid: d3b93c6f-aa6b-486d-a010-d097ea8a516b
caps.latest.revision: "73"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dda7f9497751356c4c650e7fb672f7721ec3dd09
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="events-wpf"></a><span data-ttu-id="0f870-102">Zdarzenia (WPF)</span><span class="sxs-lookup"><span data-stu-id="0f870-102">Events (WPF)</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="0f870-103">wprowadza kierowane zdarzenia, które mogą być wywoływane programy obsługi, które istnieją na różnych odbiorników w drzewie elementu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0f870-103"> introduces routed events that can invoke handlers that exist on various listeners in the element tree of an application.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0f870-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0f870-104">In This Section</span></span>  
 [<span data-ttu-id="0f870-105">Omówienie kierowane zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0f870-105">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="0f870-106">Omówienie dołączone zdarzenia</span><span class="sxs-lookup"><span data-stu-id="0f870-106">Attached Events Overview</span></span>](../../../../docs/framework/wpf/advanced/attached-events-overview.md)  
 [<span data-ttu-id="0f870-107">Zdarzenia okresu istnienia obiektu</span><span class="sxs-lookup"><span data-stu-id="0f870-107">Object Lifetime Events</span></span>](../../../../docs/framework/wpf/advanced/object-lifetime-events.md)  
 [<span data-ttu-id="0f870-108">Oznaczanie kierowane zdarzenia, ponieważ obsługiwane i klasy obsługi</span><span class="sxs-lookup"><span data-stu-id="0f870-108">Marking Routed Events as Handled, and Class Handling</span></span>](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [<span data-ttu-id="0f870-109">Podgląd zdarzeń</span><span class="sxs-lookup"><span data-stu-id="0f870-109">Preview Events</span></span>](../../../../docs/framework/wpf/advanced/preview-events.md)  
 [<span data-ttu-id="0f870-110">Zdarzenia zmiany właściwości</span><span class="sxs-lookup"><span data-stu-id="0f870-110">Property Change Events</span></span>](../../../../docs/framework/wpf/advanced/property-change-events.md)  
 [<span data-ttu-id="0f870-111">Visual Basic i obsługa zdarzeń WPF</span><span class="sxs-lookup"><span data-stu-id="0f870-111">Visual Basic and WPF Event Handling</span></span>](../../../../docs/framework/wpf/advanced/visual-basic-and-wpf-event-handling.md)  
 [<span data-ttu-id="0f870-112">Wzorce słabe zdarzeń</span><span class="sxs-lookup"><span data-stu-id="0f870-112">Weak Event Patterns</span></span>](../../../../docs/framework/wpf/advanced/weak-event-patterns.md)  
 [<span data-ttu-id="0f870-113">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="0f870-113">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)  
  
## <a name="reference"></a><span data-ttu-id="0f870-114">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="0f870-114">Reference</span></span>  
 <xref:System.Windows.RoutedEvent>  
  
 <xref:System.Windows.EventManager>  
  
 <xref:System.Windows.RoutingStrategy>  
  
## <a name="related-sections"></a><span data-ttu-id="0f870-115">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="0f870-115">Related Sections</span></span>  
 [<span data-ttu-id="0f870-116">Architektura WPF</span><span class="sxs-lookup"><span data-stu-id="0f870-116">WPF Architecture</span></span>](../../../../docs/framework/wpf/advanced/wpf-architecture.md)  
  [<span data-ttu-id="0f870-117">XAML w WPF</span><span class="sxs-lookup"><span data-stu-id="0f870-117">XAML in WPF</span></span>](../../../../docs/framework/wpf/advanced/xaml-in-wpf.md)  
  [<span data-ttu-id="0f870-118">Elementy podstawowe</span><span class="sxs-lookup"><span data-stu-id="0f870-118">Base Elements</span></span>](../../../../docs/framework/wpf/advanced/base-elements.md)  
  [<span data-ttu-id="0f870-119">Element drzewa i serializacja</span><span class="sxs-lookup"><span data-stu-id="0f870-119">Element Tree and Serialization</span></span>](../../../../docs/framework/wpf/advanced/element-tree-and-serialization.md)  
  [<span data-ttu-id="0f870-120">Właściwości</span><span class="sxs-lookup"><span data-stu-id="0f870-120">Properties</span></span>](../../../../docs/framework/wpf/advanced/properties-wpf.md)  
  [<span data-ttu-id="0f870-121">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="0f870-121">Input</span></span>](../../../../docs/framework/wpf/advanced/input-wpf.md)  
  [<span data-ttu-id="0f870-122">Zasoby</span><span class="sxs-lookup"><span data-stu-id="0f870-122">Resources</span></span>](../../../../docs/framework/wpf/advanced/resources-wpf.md)  
  [<span data-ttu-id="0f870-123">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="0f870-123">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
  [<span data-ttu-id="0f870-124">Model zawartości WPF</span><span class="sxs-lookup"><span data-stu-id="0f870-124">WPF Content Model</span></span>](../../../../docs/framework/wpf/controls/wpf-content-model.md)  
  [<span data-ttu-id="0f870-125">Model wątkowości</span><span class="sxs-lookup"><span data-stu-id="0f870-125">Threading Model</span></span>](../../../../docs/framework/wpf/advanced/threading-model.md)