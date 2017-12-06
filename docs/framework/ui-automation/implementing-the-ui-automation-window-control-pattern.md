---
title: "Implementacja wzorca formantu okna automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control patterns, Window
- UI Automation, Window control pattern
- Window control pattern
ms.assetid: a28cb286-296e-4a62-b4cb-55ad636ebccc
caps.latest.revision: "21"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 9e8d83c3ef40ccc6e97ba3128cab5d88a5af5305
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-window-control-pattern"></a><span data-ttu-id="aca3a-102">Implementacja wzorca kontrolki okna automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="aca3a-102">Implementing the UI Automation Window Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="aca3a-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="aca3a-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="aca3a-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="aca3a-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="aca3a-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IWindowProvider>, wraz z informacjami o <xref:System.Windows.Automation.WindowPattern> właściwości, metod i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="aca3a-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IWindowProvider>, including information about <xref:System.Windows.Automation.WindowPattern> properties, methods, and events.</span></span> <span data-ttu-id="aca3a-106">Łącza do dodatkowe informacje są wyświetlane na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="aca3a-106">Links to additional references are listed at the end of the topic.</span></span>  
  
 <span data-ttu-id="aca3a-107"><xref:System.Windows.Automation.WindowPattern> — Wzorzec formantu jest używana do obsługi formantów, które zapewniają podstawowe funkcje oparte na okna w tradycyjny [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aca3a-107">The <xref:System.Windows.Automation.WindowPattern> control pattern is used to support controls that provide fundamental window-based functionality within a traditional [!INCLUDE[TLA#tla_gui](../../../includes/tlasharptla-gui-md.md)].</span></span> <span data-ttu-id="aca3a-108">Formanty, które muszą implementować ten wzorzec kontroli przykładów okien najwyższego poziomu aplikacji, [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] okno podrzędne, podziału o zmiennym rozmiarze okienka kontrolki, modalne okna dialogowe i dymki Pomoc systemu windows.</span><span class="sxs-lookup"><span data-stu-id="aca3a-108">Examples of controls that must implement this control pattern include top-level application windows, [!INCLUDE[TLA#tla_mdi](../../../includes/tlasharptla-mdi-md.md)] child windows, resizable split pane controls, modal dialogs and balloon help windows.</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="aca3a-109">Implementacja — wskazówki i konwencje</span><span class="sxs-lookup"><span data-stu-id="aca3a-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="aca3a-110">Gdy implementacja wzorca kontrolki okna, należy zwrócić uwagę następujące wskazówki i konwencje:</span><span class="sxs-lookup"><span data-stu-id="aca3a-110">When implementing the Window control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="aca3a-111">Aby obsługiwać możliwość modyfikowania zarówno rozmiaru okna i ekranu pozycji przy użyciu automatyzacji interfejsu użytkownika, musi implementować formantu <xref:System.Windows.Automation.Provider.ITransformProvider> oprócz <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="aca3a-111">To support the ability to modify both window size and screen position using UI Automation, a control must implement <xref:System.Windows.Automation.Provider.ITransformProvider> in addition to <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="aca3a-112">Formanty, które zawierają paski tytułu i elementy paska tytułu, które umożliwiają formantu do przeniesienia, zmiany rozmiaru, zmaksymalizowane, zminimalizowane lub zamknięty są zwykle wymagane do zaimplementowania <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="aca3a-112">Controls that contain title bars and title bar elements that enable the control to be moved, resized, maximized, minimized, or closed are typically required to implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="aca3a-113">Formanty, takie jak wyskakujących okienek etykietki narzędzia i kombi pola lub menu rozwijane zwykle nie implementują <xref:System.Windows.Automation.Provider.IWindowProvider>.</span><span class="sxs-lookup"><span data-stu-id="aca3a-113">Controls such as tooltip pop-ups and combo box or menu drop-downs do not typically implement <xref:System.Windows.Automation.Provider.IWindowProvider>.</span></span>  
  
-   <span data-ttu-id="aca3a-114">Windows pomocy w dymku różnią się od podstawowego tooltip wyskakujące okienka poprzez dostarczanie okna przypominającej przycisk Zamknij.</span><span class="sxs-lookup"><span data-stu-id="aca3a-114">Balloon help windows are differentiated from basic tooltip pop-ups by the provision of a window-like Close button.</span></span>  
  
-   <span data-ttu-id="aca3a-115">Tryb pełnoekranowy nie jest obsługiwana przez IWindowProvider, ponieważ jest on właściwych dla funkcji do aplikacji i nie jest zachowanie typowego okna.</span><span class="sxs-lookup"><span data-stu-id="aca3a-115">Full-screen mode is not supported by IWindowProvider as it is feature-specific to an application and is not typical window behavior.</span></span>  
  
<a name="Required_Members_for_IWindowProvider"></a>   
## <a name="required-members-for-iwindowprovider"></a><span data-ttu-id="aca3a-116">Wymagane elementy IWindowProvider</span><span class="sxs-lookup"><span data-stu-id="aca3a-116">Required Members for IWindowProvider</span></span>  
 <span data-ttu-id="aca3a-117">Poniższe właściwości, metod i zdarzeń są wymagane dla interfejsu IWindowProvider.</span><span class="sxs-lookup"><span data-stu-id="aca3a-117">The following properties, methods, and events are required for the IWindowProvider interface.</span></span>  
  
|<span data-ttu-id="aca3a-118">Wymagany element członkowski</span><span class="sxs-lookup"><span data-stu-id="aca3a-118">Required member</span></span>|<span data-ttu-id="aca3a-119">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="aca3a-119">Member type</span></span>|<span data-ttu-id="aca3a-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="aca3a-120">Notes</span></span>|  
|---------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.InteractionState%2A>|<span data-ttu-id="aca3a-121">Właściwość</span><span class="sxs-lookup"><span data-stu-id="aca3a-121">Property</span></span>|<span data-ttu-id="aca3a-122">Brak</span><span class="sxs-lookup"><span data-stu-id="aca3a-122">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsModal%2A>|<span data-ttu-id="aca3a-123">Właściwość</span><span class="sxs-lookup"><span data-stu-id="aca3a-123">Property</span></span>|<span data-ttu-id="aca3a-124">Brak</span><span class="sxs-lookup"><span data-stu-id="aca3a-124">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.IsTopmost%2A>|<span data-ttu-id="aca3a-125">Właściwość</span><span class="sxs-lookup"><span data-stu-id="aca3a-125">Property</span></span>|<span data-ttu-id="aca3a-126">Brak</span><span class="sxs-lookup"><span data-stu-id="aca3a-126">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Maximizable%2A>|<span data-ttu-id="aca3a-127">Właściwość</span><span class="sxs-lookup"><span data-stu-id="aca3a-127">Property</span></span>|<span data-ttu-id="aca3a-128">Brak</span><span class="sxs-lookup"><span data-stu-id="aca3a-128">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Minimizable%2A>|<span data-ttu-id="aca3a-129">Właściwość</span><span class="sxs-lookup"><span data-stu-id="aca3a-129">Property</span></span>|<span data-ttu-id="aca3a-130">Brak</span><span class="sxs-lookup"><span data-stu-id="aca3a-130">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.VisualState%2A>|<span data-ttu-id="aca3a-131">Właściwość</span><span class="sxs-lookup"><span data-stu-id="aca3a-131">Property</span></span>|<span data-ttu-id="aca3a-132">Brak</span><span class="sxs-lookup"><span data-stu-id="aca3a-132">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.Close%2A>|<span data-ttu-id="aca3a-133">Metoda</span><span class="sxs-lookup"><span data-stu-id="aca3a-133">Method</span></span>|<span data-ttu-id="aca3a-134">Brak</span><span class="sxs-lookup"><span data-stu-id="aca3a-134">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A>|<span data-ttu-id="aca3a-135">Metoda</span><span class="sxs-lookup"><span data-stu-id="aca3a-135">Method</span></span>|<span data-ttu-id="aca3a-136">Brak</span><span class="sxs-lookup"><span data-stu-id="aca3a-136">None</span></span>|  
|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A>|<span data-ttu-id="aca3a-137">Metoda</span><span class="sxs-lookup"><span data-stu-id="aca3a-137">Method</span></span>|<span data-ttu-id="aca3a-138">Brak</span><span class="sxs-lookup"><span data-stu-id="aca3a-138">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|<span data-ttu-id="aca3a-139">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="aca3a-139">Event</span></span>|<span data-ttu-id="aca3a-140">Brak</span><span class="sxs-lookup"><span data-stu-id="aca3a-140">None</span></span>|  
|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|<span data-ttu-id="aca3a-141">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="aca3a-141">Event</span></span>|<span data-ttu-id="aca3a-142">Brak</span><span class="sxs-lookup"><span data-stu-id="aca3a-142">None</span></span>|  
|<xref:System.Windows.Automation.WindowInteractionState>|<span data-ttu-id="aca3a-143">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="aca3a-143">Event</span></span>|<span data-ttu-id="aca3a-144">Nie gwarantuje to<xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span><span class="sxs-lookup"><span data-stu-id="aca3a-144">Is not guaranteed to be <xref:System.Windows.Automation.WindowInteractionState.ReadyForUserInteraction></span></span>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="aca3a-145">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="aca3a-145">Exceptions</span></span>  
 <span data-ttu-id="aca3a-146">Dostawców należy zgłosić następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="aca3a-146">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="aca3a-147">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="aca3a-147">Exception type</span></span>|<span data-ttu-id="aca3a-148">Warunek</span><span class="sxs-lookup"><span data-stu-id="aca3a-148">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<xref:System.Windows.Automation.Provider.IWindowProvider.SetVisualState%2A><br /><br /> <span data-ttu-id="aca3a-149">— Gdy formantu nie obsługuje żądanego zachowania.</span><span class="sxs-lookup"><span data-stu-id="aca3a-149">-   When a control does not support a requested behavior.</span></span>|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IWindowProvider.WaitForInputIdle%2A><br /><br /> <span data-ttu-id="aca3a-150">-Gdy parametr nie jest prawidłową liczbą.</span><span class="sxs-lookup"><span data-stu-id="aca3a-150">-   When the parameter is not a valid number.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aca3a-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aca3a-151">See Also</span></span>  
 [<span data-ttu-id="aca3a-152">Przegląd wzorców formantu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="aca3a-152">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="aca3a-153">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="aca3a-153">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="aca3a-154">Wzorce formantów automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="aca3a-154">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="aca3a-155">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="aca3a-155">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="aca3a-156">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="aca3a-156">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)