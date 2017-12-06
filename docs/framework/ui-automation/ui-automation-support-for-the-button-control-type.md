---
title: "Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu przycisk"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control types, Button
- UI Automation, Button control type
- Button control type
ms.assetid: 057c983a-da83-4c50-86c7-26fe381076a6
caps.latest.revision: "34"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 54d00506a252c40bf3c8a67d5a228eae72e6464e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-support-for-the-button-control-type"></a><span data-ttu-id="fd40b-102">Obsługa automatyzacji interfejsu użytkownika dla kontrolek typu przycisk</span><span class="sxs-lookup"><span data-stu-id="fd40b-102">UI Automation Support for the Button Control Type</span></span>
> [!NOTE]
>  <span data-ttu-id="fd40b-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="fd40b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="fd40b-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="fd40b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="fd40b-105">Ten temat zawiera informacje na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsługi dla typu formantu przycisku.</span><span class="sxs-lookup"><span data-stu-id="fd40b-105">This topic provides information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] support for the Button control type.</span></span> <span data-ttu-id="fd40b-106">W [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typu formantu to zestaw warunków, które muszą spełniać formantu, aby można było używać <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> właściwości.</span><span class="sxs-lookup"><span data-stu-id="fd40b-106">In [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], a control type is a set of conditions that a control must meet in order to use the <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> property.</span></span> <span data-ttu-id="fd40b-107">Takie szczegółowe wytyczne dla [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury drzewa [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] wartości właściwości, wzorce formantu i [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fd40b-107">The conditions include specific guidelines for [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] property values, control patterns, and [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] events.</span></span>  
  
 <span data-ttu-id="fd40b-108">Obiekt, który użytkownik użyje do wykonywania akcji, takich jak jest przycisk **OK** i **anulować** przyciski w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="fd40b-108">A button is an object that a user interacts with to perform an action such as the **OK** and **Cancel** buttons on a dialog box.</span></span> <span data-ttu-id="fd40b-109">Kontrolka przycisku jest proste kontrolce ujawnienie, ponieważ mapuje jednego polecenia, które użytkownik chce wykonać.</span><span class="sxs-lookup"><span data-stu-id="fd40b-109">The button control is a simple control to expose because it maps to a single command that the user wishes to complete.</span></span>  
  
 <span data-ttu-id="fd40b-110">Następujące sekcje definiują wymaganych [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] struktury, właściwości, wzorce formantów i zdarzeń dla formantów typu przycisk drzewa.</span><span class="sxs-lookup"><span data-stu-id="fd40b-110">The following sections define the required [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree structure, properties, control patterns, and events for the Button control type.</span></span> <span data-ttu-id="fd40b-111">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Wymagania dotyczą wszystkich kontrolek przycisku czy [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], lub [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fd40b-111">The [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] requirements apply to all button controls, whether [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], or [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].</span></span>  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a><span data-ttu-id="fd40b-112">Struktura drzewa automatyzacji interfejsu użytkownika wymagane</span><span class="sxs-lookup"><span data-stu-id="fd40b-112">Required UI Automation Tree Structure</span></span>  
 <span data-ttu-id="fd40b-113">Poniższa tabela przedstawia kontroli i widok zawartości [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa odnoszą się do kontrolek przycisku, który opisano, jakie mogą być zawarte w każdym widoku.</span><span class="sxs-lookup"><span data-stu-id="fd40b-113">The following table depicts the control view and the content view of the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree that pertains to button controls and describes what can be contained in each view.</span></span> <span data-ttu-id="fd40b-114">Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa, zobacz [Przegląd drzewa automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fd40b-114">For more information about the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree, see [UI Automation Tree Overview](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).</span></span>  
  
|<span data-ttu-id="fd40b-115">Kontrolki widoku</span><span class="sxs-lookup"><span data-stu-id="fd40b-115">Control View</span></span>|<span data-ttu-id="fd40b-116">Widok zawartości</span><span class="sxs-lookup"><span data-stu-id="fd40b-116">Content View</span></span>|  
|------------------|------------------|  
|<span data-ttu-id="fd40b-117">Przycisk</span><span class="sxs-lookup"><span data-stu-id="fd40b-117">Button</span></span><br /><br /> <span data-ttu-id="fd40b-118">-Obrazu (0 lub więcej)</span><span class="sxs-lookup"><span data-stu-id="fd40b-118">-   Image (0 or more)</span></span><br /><span data-ttu-id="fd40b-119">-Tekst (0 lub więcej)</span><span class="sxs-lookup"><span data-stu-id="fd40b-119">-   Text (0 or more)</span></span>|<span data-ttu-id="fd40b-120">Przycisk</span><span class="sxs-lookup"><span data-stu-id="fd40b-120">Button</span></span>|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a><span data-ttu-id="fd40b-121">Właściwości automatyzacji interfejsu użytkownika wymagane</span><span class="sxs-lookup"><span data-stu-id="fd40b-121">Required UI Automation Properties</span></span>  
 <span data-ttu-id="fd40b-122">W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, której wartość lub definicji jest szczególnie istotne w formantach, które implementują przycisku kontrolowanie typu (np. formanty przycisku).</span><span class="sxs-lookup"><span data-stu-id="fd40b-122">The following table lists the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties whose value or definition is especially relevant to the controls that implement the Button control type (such as button controls).</span></span> <span data-ttu-id="fd40b-123">Aby uzyskać więcej informacji na temat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] właściwości, zobacz [właściwości automatyzacji interfejsu użytkownika dla klientów](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).</span><span class="sxs-lookup"><span data-stu-id="fd40b-123">For more information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] properties, see [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).</span></span>  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="fd40b-124">Właściwość</span><span class="sxs-lookup"><span data-stu-id="fd40b-124"> Property</span></span>|<span data-ttu-id="fd40b-125">Wartość</span><span class="sxs-lookup"><span data-stu-id="fd40b-125">Value</span></span>|<span data-ttu-id="fd40b-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd40b-126">Notes</span></span>|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>|<span data-ttu-id="fd40b-127">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="fd40b-127">See notes.</span></span>|<span data-ttu-id="fd40b-128">Kontrolka przycisku zwykle musi obsługiwać klawiszem skrótu, aby umożliwić użytkownikom końcowym wykonywać akcję, którą reprezentuje szybko z klawiatury.</span><span class="sxs-lookup"><span data-stu-id="fd40b-128">The Button control typically must support an accelerator key to enable an end user to perform the action it represents quickly from the keyboard.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|<span data-ttu-id="fd40b-129">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="fd40b-129">See notes.</span></span>|<span data-ttu-id="fd40b-130">Wartość tej właściwości musi być unikatowy w obrębie wszystkich kontrolek w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fd40b-130">The value of this property needs to be unique across all controls in an application.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|<span data-ttu-id="fd40b-131">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="fd40b-131">See notes.</span></span>|<span data-ttu-id="fd40b-132">Prostokąt peryferyjnych zawiera całą formantu.</span><span class="sxs-lookup"><span data-stu-id="fd40b-132">The outermost rectangle that contains the whole control.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|<span data-ttu-id="fd40b-133">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="fd40b-133">See notes.</span></span>|<span data-ttu-id="fd40b-134">Obsługiwane w przypadku prostokąt ograniczający.</span><span class="sxs-lookup"><span data-stu-id="fd40b-134">Supported if there is a bounding rectangle.</span></span> <span data-ttu-id="fd40b-135">Jeśli nie każdy punkt w obrębie prostokątem jest aktywne i wykonywać specjalne testowanie trafień, zastąpienia i podaj elementu do kliknięcia.</span><span class="sxs-lookup"><span data-stu-id="fd40b-135">If not every point within the bounding rectangle is clickable, and you perform specialized hit testing, then override and provide a clickable point.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|<span data-ttu-id="fd40b-136">Przycisk</span><span class="sxs-lookup"><span data-stu-id="fd40b-136">Button</span></span>|<span data-ttu-id="fd40b-137">Ta wartość jest taka sama dla wszystkich platform interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fd40b-137">This value is the same for all UI frameworks.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|<span data-ttu-id="fd40b-138">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="fd40b-138">See notes.</span></span>|<span data-ttu-id="fd40b-139">Tekst pomocy można wskazać, jaki będzie wynik końcowy aktywacji przycisku.</span><span class="sxs-lookup"><span data-stu-id="fd40b-139">The Help Text can indicate what the end result of activating the button will be.</span></span> <span data-ttu-id="fd40b-140">Jest to zazwyczaj tego samego typu informacji przedstawionych w etykietce narzędzia.</span><span class="sxs-lookup"><span data-stu-id="fd40b-140">This is typically the same type of information presented through a ToolTip.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|<span data-ttu-id="fd40b-141">Wartość true</span><span class="sxs-lookup"><span data-stu-id="fd40b-141">True</span></span>|<span data-ttu-id="fd40b-142">Kontrolka przycisku musi być zawsze zawartości.</span><span class="sxs-lookup"><span data-stu-id="fd40b-142">The Button control must always be content.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|<span data-ttu-id="fd40b-143">Wartość true</span><span class="sxs-lookup"><span data-stu-id="fd40b-143">True</span></span>|<span data-ttu-id="fd40b-144">Kontrolka przycisku zawsze musi być formantem.</span><span class="sxs-lookup"><span data-stu-id="fd40b-144">The Button control must always be a control.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|<span data-ttu-id="fd40b-145">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="fd40b-145">See notes.</span></span>|<span data-ttu-id="fd40b-146">Formant może przyjmować fokus klawiatury, musi obsługiwać tej właściwości.</span><span class="sxs-lookup"><span data-stu-id="fd40b-146">If the control can receive keyboard focus, it must support this property.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|<span data-ttu-id="fd40b-147">Formanty przycisków własnym są oznaczone przez ich zawartość.</span><span class="sxs-lookup"><span data-stu-id="fd40b-147">Button controls are self-labeled by their contents.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|<span data-ttu-id="fd40b-148">"button"</span><span class="sxs-lookup"><span data-stu-id="fd40b-148">"button"</span></span>|<span data-ttu-id="fd40b-149">Zlokalizowany ciąg odpowiadający przycisk — typ kontrolki.</span><span class="sxs-lookup"><span data-stu-id="fd40b-149">Localized string corresponding to the Button control type.</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|<span data-ttu-id="fd40b-150">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="fd40b-150">See notes.</span></span>|<span data-ttu-id="fd40b-151">Nazwa kontrolki przycisku jest tekst, który umożliwia mu przypisać inną etykietę.</span><span class="sxs-lookup"><span data-stu-id="fd40b-151">The name of the button control is the text that is used to label it.</span></span> <span data-ttu-id="fd40b-152">Gdy obraz jest etykieta przycisku, tekst zastępczy musi zostać dostarczona dla właściwości Nazwa przycisku.</span><span class="sxs-lookup"><span data-stu-id="fd40b-152">Whenever an image is used to label a button, alternate text must be supplied for the button's Name property.</span></span>|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a><span data-ttu-id="fd40b-153">Wzorce formantów automatyzacji interfejsu użytkownika wymagane</span><span class="sxs-lookup"><span data-stu-id="fd40b-153">Required UI Automation Control Patterns</span></span>  
 <span data-ttu-id="fd40b-154">W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] kontrolować wzorce wymagane do obsługi przez wszystkich kontrolek przycisku.</span><span class="sxs-lookup"><span data-stu-id="fd40b-154">The following table lists the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] control patterns required to be supported by all button controls.</span></span> <span data-ttu-id="fd40b-155">Aby uzyskać więcej informacji na wzorce formantów, zobacz [Przegląd wzorców formantu automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fd40b-155">For more information on control patterns, see [UI Automation Control Patterns Overview](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).</span></span>  
  
|<span data-ttu-id="fd40b-156">— Wzorzec formantu</span><span class="sxs-lookup"><span data-stu-id="fd40b-156">Control Pattern</span></span>|<span data-ttu-id="fd40b-157">Obsługa</span><span class="sxs-lookup"><span data-stu-id="fd40b-157">Support</span></span>|<span data-ttu-id="fd40b-158">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd40b-158">Notes</span></span>|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|<span data-ttu-id="fd40b-159">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="fd40b-159">See notes.</span></span>|<span data-ttu-id="fd40b-160">Wszystkie przyciski powinien obsługiwać Invoke — wzorzec kontrolki lub Toggle — wzorzec formantu.</span><span class="sxs-lookup"><span data-stu-id="fd40b-160">All buttons should support the Invoke control pattern or the Toggle control pattern.</span></span> <span data-ttu-id="fd40b-161">Wywołanie jest obsługiwana, gdy przycisk wykonuje polecenia na żądanie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="fd40b-161">Invoke is supported when the button performs a command at the request of the user.</span></span> <span data-ttu-id="fd40b-162">To polecenie jest mapowany na jednej operacji, takich jak wycinania, kopiowania, wklejania lub Delete.</span><span class="sxs-lookup"><span data-stu-id="fd40b-162">This command maps to a single operation such as Cut, Copy, Paste, or Delete.</span></span>|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|<span data-ttu-id="fd40b-163">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="fd40b-163">See notes.</span></span>|<span data-ttu-id="fd40b-164">Wszystkie przyciski powinien obsługiwać Invoke — wzorzec kontrolki lub Toggle — wzorzec formantu.</span><span class="sxs-lookup"><span data-stu-id="fd40b-164">All buttons should support the Invoke control pattern or the Toggle control pattern.</span></span> <span data-ttu-id="fd40b-165">Przełącz jest obsługiwana, gdy przycisk można ponownym przez szereg maksymalnie trzy stany.</span><span class="sxs-lookup"><span data-stu-id="fd40b-165">Toggle is supported if the button can be cycled through a series of up to three states.</span></span> <span data-ttu-id="fd40b-166">Zazwyczaj jest to postrzegane jako włączony/wyłączony dla określonych funkcji.</span><span class="sxs-lookup"><span data-stu-id="fd40b-166">Typically this is seen as an on/off switch for specific features.</span></span>|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|<span data-ttu-id="fd40b-167">Zobacz uwagi.</span><span class="sxs-lookup"><span data-stu-id="fd40b-167">See notes.</span></span>|<span data-ttu-id="fd40b-168">Gdy przycisk jest obsługiwany jako element podrzędny przycisku podziału, przycisk podrzędnych obsługuje ExpandCollapse — wzorzec zamiast Invoke lub Toggle — wzorzec.</span><span class="sxs-lookup"><span data-stu-id="fd40b-168">When a button is hosted as a child of a split button, the child button can support the ExpandCollapse pattern instead of the Invoke or Toggle pattern.</span></span> <span data-ttu-id="fd40b-169">ExpandCollapse — wzorzec może służyć do otwierania lub zamykania menu lub inne struktury podrzędne skojarzone z elementem przycisku.</span><span class="sxs-lookup"><span data-stu-id="fd40b-169">The ExpandCollapse pattern can be used for opening or closing a menu or other sub-structure associated with the button element.</span></span>|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a><span data-ttu-id="fd40b-170">Zdarzeń automatyzacji interfejsu użytkownika wymagane</span><span class="sxs-lookup"><span data-stu-id="fd40b-170">Required UI Automation Events</span></span>  
 <span data-ttu-id="fd40b-171">W poniższej tabeli wymieniono [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdarzenia wymagane do obsługi przez wszystkich kontrolek przycisku.</span><span class="sxs-lookup"><span data-stu-id="fd40b-171">The following table lists the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] events required to be supported by all button controls.</span></span> <span data-ttu-id="fd40b-172">Aby uzyskać więcej informacji dotyczących zdarzeń, zobacz [Przegląd zdarzeń automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/ui-automation-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="fd40b-172">For more information on events, see [UI Automation Events Overview](../../../docs/framework/ui-automation/ui-automation-events-overview.md).</span></span>  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="fd40b-173">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="fd40b-173"> Event</span></span>|<span data-ttu-id="fd40b-174">Obsługa</span><span class="sxs-lookup"><span data-stu-id="fd40b-174">Support</span></span>|<span data-ttu-id="fd40b-175">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fd40b-175">Notes</span></span>|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|<span data-ttu-id="fd40b-176">Wymagane</span><span class="sxs-lookup"><span data-stu-id="fd40b-176">Required</span></span>|<span data-ttu-id="fd40b-177">Brak</span><span class="sxs-lookup"><span data-stu-id="fd40b-177">None</span></span>|  
|<span data-ttu-id="fd40b-178"><xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>Zdarzenie zmiany właściwości.</span><span class="sxs-lookup"><span data-stu-id="fd40b-178"><xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> property-changed event.</span></span>|<span data-ttu-id="fd40b-179">Wymagane</span><span class="sxs-lookup"><span data-stu-id="fd40b-179">Required</span></span>|<span data-ttu-id="fd40b-180">Brak</span><span class="sxs-lookup"><span data-stu-id="fd40b-180">None</span></span>|  
|<span data-ttu-id="fd40b-181"><xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>Zdarzenie zmiany właściwości.</span><span class="sxs-lookup"><span data-stu-id="fd40b-181"><xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> property-changed event.</span></span>|<span data-ttu-id="fd40b-182">Wymagane</span><span class="sxs-lookup"><span data-stu-id="fd40b-182">Required</span></span>|<span data-ttu-id="fd40b-183">Brak</span><span class="sxs-lookup"><span data-stu-id="fd40b-183">None</span></span>|  
|<span data-ttu-id="fd40b-184"><xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>Zdarzenie zmiany właściwości.</span><span class="sxs-lookup"><span data-stu-id="fd40b-184"><xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> property-changed event.</span></span>|<span data-ttu-id="fd40b-185">Wymagane</span><span class="sxs-lookup"><span data-stu-id="fd40b-185">Required</span></span>|<span data-ttu-id="fd40b-186">Brak</span><span class="sxs-lookup"><span data-stu-id="fd40b-186">None</span></span>|  
|<span data-ttu-id="fd40b-187"><xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>Zdarzenie zmiany właściwości.</span><span class="sxs-lookup"><span data-stu-id="fd40b-187"><xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> property-changed event.</span></span>|<span data-ttu-id="fd40b-188">Wymagane</span><span class="sxs-lookup"><span data-stu-id="fd40b-188">Required</span></span>|<span data-ttu-id="fd40b-189">Brak</span><span class="sxs-lookup"><span data-stu-id="fd40b-189">None</span></span>|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|<span data-ttu-id="fd40b-190">Wymagane</span><span class="sxs-lookup"><span data-stu-id="fd40b-190">Required</span></span>|<span data-ttu-id="fd40b-191">Brak</span><span class="sxs-lookup"><span data-stu-id="fd40b-191">None</span></span>|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|<span data-ttu-id="fd40b-192">Zależy od</span><span class="sxs-lookup"><span data-stu-id="fd40b-192">Depends</span></span>|<span data-ttu-id="fd40b-193">Invoke — wzorzec formantu obsługiwane przez kontrolkę, musi obsługiwać tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fd40b-193">If the control supports the Invoke control pattern, it must support this event.</span></span>|  
|<span data-ttu-id="fd40b-194"><xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>Zdarzenie zmiany właściwości.</span><span class="sxs-lookup"><span data-stu-id="fd40b-194"><xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> property-changed event.</span></span>|<span data-ttu-id="fd40b-195">Zależy od</span><span class="sxs-lookup"><span data-stu-id="fd40b-195">Depends</span></span>|<span data-ttu-id="fd40b-196">Toggle — wzorzec formantu obsługiwane przez kontrolkę, musi obsługiwać tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="fd40b-196">If the control supports the Toggle control pattern, it must support this event.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd40b-197">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd40b-197">See Also</span></span>  
 <xref:System.Windows.Automation.ControlType.Button>  
 [<span data-ttu-id="fd40b-198">Przegląd typów formantu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fd40b-198">UI Automation Control Types Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [<span data-ttu-id="fd40b-199">Przegląd automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="fd40b-199">UI Automation Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-overview.md)