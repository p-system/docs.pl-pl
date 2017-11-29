---
title: "ToolTip — Przegląd"
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
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31bd56323e90368f850ae54854e6f50b63d5f7fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="tooltip-overview"></a><span data-ttu-id="945d1-102">ToolTip — Przegląd</span><span class="sxs-lookup"><span data-stu-id="945d1-102">ToolTip Overview</span></span>
<span data-ttu-id="945d1-103">Etykietka narzędzia jest mała okno podręczne pojawia się po zatrzymaniu wskaźnika myszy nad elementem, takie jak ponad <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="945d1-103">A tooltip is a small pop-up window that appears when a user pauses the mouse pointer over an element, such as over a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="945d1-104">W tym temacie przedstawiono wskazówki i opisano, jak tworzyć i dostosowywać zawartość etykietka narzędzia.</span><span class="sxs-lookup"><span data-stu-id="945d1-104">This topic introduces the tooltip and discusses how to create and customize tooltip content.</span></span>  
  
 
  
<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a><span data-ttu-id="945d1-105">Co to jest etykietka narzędzia?</span><span class="sxs-lookup"><span data-stu-id="945d1-105">What Is a Tooltip?</span></span>  
 <span data-ttu-id="945d1-106">Gdy użytkownik przesuwa wskaźnik myszy nad elementem ma etykietka narzędzia, zostanie wyświetlone okno z zawartością etykietki narzędzia (na przykład tekstu zawierającego opis funkcji formantu), która określoną ilość czasu.</span><span class="sxs-lookup"><span data-stu-id="945d1-106">When a user moves the mouse pointer over an element that has a tooltip, a window that contains tooltip content (for example, text content that describes the function of a control) appears for a specified amount of time.</span></span> <span data-ttu-id="945d1-107">Jeśli użytkownik przesuwa wskaźnik myszy formantu, okno zniknie, ponieważ zawartość etykietki narzędzia nie można ustawić fokusu.</span><span class="sxs-lookup"><span data-stu-id="945d1-107">If the user moves the mouse pointer away from the control, the window disappears because the tooltip content cannot receive focus.</span></span>  
  
 <span data-ttu-id="945d1-108">Zawartość etykietka narzędzia może zawierać jeden lub więcej wierszy tekstu, obrazów, kształtów lub innych zawartości wizualnej.</span><span class="sxs-lookup"><span data-stu-id="945d1-108">The content of a tooltip can contain one or more lines of text, images, shapes, or other visual content.</span></span> <span data-ttu-id="945d1-109">Należy zdefiniować etykietkę narzędzia dla kontrolki ustawiając jedną z następujących właściwości zawartości etykietka narzędzia.</span><span class="sxs-lookup"><span data-stu-id="945d1-109">You define a tooltip for a control by setting one of the following properties to the tooltip content.</span></span>  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="945d1-110">Właściwości, których używasz zależy od tego, czy formant, który definiuje element tooltip dziedziczy <xref:System.Windows.FrameworkContentElement> lub <xref:System.Windows.FrameworkElement> klasy.</span><span class="sxs-lookup"><span data-stu-id="945d1-110">Which property you use depends on whether the control that defines the tooltip inherits from the <xref:System.Windows.FrameworkContentElement> or <xref:System.Windows.FrameworkElement> class.</span></span>  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a><span data-ttu-id="945d1-111">Etykietka narzędzia tworzenia</span><span class="sxs-lookup"><span data-stu-id="945d1-111">Creating a ToolTip</span></span>  
 <span data-ttu-id="945d1-112">Poniższy przykład przedstawia sposób utworzyć prosty etykietka narzędzia, ustawiając <xref:System.Windows.FrameworkElement.ToolTip%2A> właściwości dla <xref:System.Windows.Controls.Button> kontroli ciąg tekstowy.</span><span class="sxs-lookup"><span data-stu-id="945d1-112">The following example shows how to create a simple tooltip by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A> property for a <xref:System.Windows.Controls.Button> control to a text string.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 <span data-ttu-id="945d1-113">Można również zdefiniować jako etykietka narzędzia <xref:System.Windows.Controls.ToolTip> obiektu.</span><span class="sxs-lookup"><span data-stu-id="945d1-113">You can also define a tooltip as a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="945d1-114">W poniższym przykładzie użyto [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] do określenia <xref:System.Windows.Controls.ToolTip> obiektu jako etykietka narzędzia <xref:System.Windows.Controls.TextBox> elementu.</span><span class="sxs-lookup"><span data-stu-id="945d1-114">The following example uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to specify a <xref:System.Windows.Controls.ToolTip> object as the tooltip of a <xref:System.Windows.Controls.TextBox> element.</span></span> <span data-ttu-id="945d1-115">Należy pamiętać, że w przykładzie określono <xref:System.Windows.Controls.ToolTip> przez ustawienie <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="945d1-115">Note that the example specifies the <xref:System.Windows.Controls.ToolTip> by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> property.</span></span>  
  
 [!code-xaml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 <span data-ttu-id="945d1-116">W poniższym przykładzie użyto kod można wygenerować <xref:System.Windows.Controls.ToolTip> obiektu.</span><span class="sxs-lookup"><span data-stu-id="945d1-116">The following example uses code to generate a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="945d1-117">W przykładzie jest tworzony <xref:System.Windows.Controls.ToolTip> (`tt`) i kojarzy ją z <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="945d1-117">The example creates a <xref:System.Windows.Controls.ToolTip> (`tt`) and associates it with a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 <span data-ttu-id="945d1-118">Można również utworzyć zawartość etykietka narzędzia, która nie jest zdefiniowany jako <xref:System.Windows.Controls.ToolTip> obiektu otaczającej zawartości etykietki narzędzia w elemencie układu, takich jak <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="945d1-118">You can also create tooltip content that is not defined as a <xref:System.Windows.Controls.ToolTip> object by enclosing the tooltip content in a layout element, such as a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="945d1-119">Poniższy przykład przedstawia sposób ustawiania <xref:System.Windows.FrameworkElement.ToolTip%2A> właściwość <xref:System.Windows.Controls.TextBox> do zawartości, która jest zawarta w <xref:System.Windows.Controls.DockPanel> formantu.</span><span class="sxs-lookup"><span data-stu-id="945d1-119">The following example shows how to set the <xref:System.Windows.FrameworkElement.ToolTip%2A> property of a <xref:System.Windows.Controls.TextBox> to content that is enclosed in a <xref:System.Windows.Controls.DockPanel> control.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a><span data-ttu-id="945d1-120">Przy użyciu właściwości etykietka narzędzia i ToolTipService klas</span><span class="sxs-lookup"><span data-stu-id="945d1-120">Using the Properties of the ToolTip and ToolTipService Classes</span></span>  
 <span data-ttu-id="945d1-121">Etykietka narzędzia zawartości można dostosować przez ustawienie właściwości wizualnego i stosowanie stylów.</span><span class="sxs-lookup"><span data-stu-id="945d1-121">You can customize tooltip content by setting visual properties and applying styles.</span></span> <span data-ttu-id="945d1-122">W przypadku definiowania zawartości jako etykietka narzędzia <xref:System.Windows.Controls.ToolTip> obiektu, można ustawić właściwości visual <xref:System.Windows.Controls.ToolTip> obiektu.</span><span class="sxs-lookup"><span data-stu-id="945d1-122">If you define the tooltip content as a <xref:System.Windows.Controls.ToolTip> object, you can set the visual properties of the <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="945d1-123">W przeciwnym razie należy ustawić na równoważne dołączone właściwości <xref:System.Windows.Controls.ToolTipService> klasy.</span><span class="sxs-lookup"><span data-stu-id="945d1-123">Otherwise, you must set equivalent attached properties on the <xref:System.Windows.Controls.ToolTipService> class.</span></span>  
  
 <span data-ttu-id="945d1-124">Na przykład ustawiania właściwości, aby określić położenie zawartości etykietka narzędzia, za pomocą <xref:System.Windows.Controls.ToolTip> i <xref:System.Windows.Controls.ToolTipService> właściwości, zobacz [umieść etykietka narzędzia](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).</span><span class="sxs-lookup"><span data-stu-id="945d1-124">For an example of how to set properties in order to specify the position of tooltip content by using the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> properties, see [Position a ToolTip](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).</span></span>  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a><span data-ttu-id="945d1-125">Style etykietki narzędzia</span><span class="sxs-lookup"><span data-stu-id="945d1-125">Styling a ToolTip</span></span>  
 <span data-ttu-id="945d1-126">Styl możesz <xref:System.Windows.Controls.ToolTip> , definiując własne <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="945d1-126">You can style a <xref:System.Windows.Controls.ToolTip> by defining a custom <xref:System.Windows.Style>.</span></span> <span data-ttu-id="945d1-127">W poniższym przykładzie zdefiniowano <xref:System.Windows.Style> o nazwie `Simple` który pokazuje, jak przesunięcie rozmieszczenia <xref:System.Windows.Controls.ToolTip> i zmień jego wygląd przez ustawienie <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, i <xref:System.Windows.Controls.Control.FontWeight%2A>.</span><span class="sxs-lookup"><span data-stu-id="945d1-127">The following example defines a <xref:System.Windows.Style> called `Simple` that shows how to offset the placement of the <xref:System.Windows.Controls.ToolTip> and change its appearance by setting the <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, and <xref:System.Windows.Controls.Control.FontWeight%2A>.</span></span>  
  
 [!code-xaml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a><span data-ttu-id="945d1-128">Za pomocą właściwości interwału czasu ToolTipService</span><span class="sxs-lookup"><span data-stu-id="945d1-128">Using the Time Interval Properties of ToolTipService</span></span>  
 <span data-ttu-id="945d1-129"><xref:System.Windows.Controls.ToolTipService> Klasa udostępnia następujące właściwości można ustawić tooltip wyświetlić razy: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, i <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span><span class="sxs-lookup"><span data-stu-id="945d1-129">The <xref:System.Windows.Controls.ToolTipService> class provides the following properties for you to set tooltip display times: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span></span>  
  
 <span data-ttu-id="945d1-130">Użyj <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> i <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> właściwości, aby określić opóźnienie, zwykle krótki, przed <xref:System.Windows.Controls.ToolTip> pojawia się, a także, aby określić, jak długo <xref:System.Windows.Controls.ToolTip> pozostaje widoczna.</span><span class="sxs-lookup"><span data-stu-id="945d1-130">Use the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> properties to specify a delay, typically brief, before a <xref:System.Windows.Controls.ToolTip> appears and also to specify how long a <xref:System.Windows.Controls.ToolTip> remains visible.</span></span> <span data-ttu-id="945d1-131">Aby uzyskać więcej informacji, zobacz [porady: opóźnienia wyświetlania etykietka narzędzia](http://msdn.microsoft.com/en-us/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).</span><span class="sxs-lookup"><span data-stu-id="945d1-131">For more information, see [How to: Delay the Display of a ToolTip](http://msdn.microsoft.com/en-us/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).</span></span>  
  
 <span data-ttu-id="945d1-132"><xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> Właściwość określa etykietki narzędzi dla różnych formantów wyświetlane niezwłocznie początkowej podczas szybko przesuń wskaźnik myszy między nimi.</span><span class="sxs-lookup"><span data-stu-id="945d1-132">The <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property determines if tooltips for different controls appear without an initial delay when you move the mouse pointer quickly between them.</span></span> <span data-ttu-id="945d1-133">Aby uzyskać więcej informacji na temat <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> właściwości, zobacz [, użyj właściwości BetweenShowDelay](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).</span><span class="sxs-lookup"><span data-stu-id="945d1-133">For more information about the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property, see [Use the BetweenShowDelay Property](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).</span></span>  
  
 <span data-ttu-id="945d1-134">Poniższy przykład przedstawia sposób ustawiania tych właściwości w etykietce narzędzia.</span><span class="sxs-lookup"><span data-stu-id="945d1-134">The following example shows how to set these properties for a tooltip.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="945d1-135">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="945d1-135">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTipService>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipEventArgs>  
 <xref:System.Windows.Controls.ToolTipEventHandler>  
 [<span data-ttu-id="945d1-136">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="945d1-136">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)