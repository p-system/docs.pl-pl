---
title: "SplitContainer — Informacje o formancie [Formularze systemu Windows]"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SplitContainer
helpviewer_keywords: SplitContainer control [Windows Forms], about SplitContainer control
ms.assetid: 6de5a5f7-97a5-402d-be6d-7e2785483db5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 10f18c46c85ed840b6625d9ed754d1d036a80975
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="splitcontainer-control-overview-windows-forms"></a><span data-ttu-id="4267b-102">SplitContainer — Informacje o formancie [Formularze systemu Windows]</span><span class="sxs-lookup"><span data-stu-id="4267b-102">SplitContainer Control Overview (Windows Forms)</span></span>
<span data-ttu-id="4267b-103">Formularze systemu Windows <xref:System.Windows.Forms.SplitContainer> formantu można traktować jako projekt wstępny; jest dwa panele oddzielone ruchomy paska.</span><span class="sxs-lookup"><span data-stu-id="4267b-103">The Windows Forms <xref:System.Windows.Forms.SplitContainer> control can be thought of as a composite; it is two panels separated by a movable bar.</span></span> <span data-ttu-id="4267b-104">Gdy wskaźnik myszy znajduje się nad paskiem, kursor zmienia kształt pokazują, że pasek jest ruchomy.</span><span class="sxs-lookup"><span data-stu-id="4267b-104">When the mouse pointer is over the bar, the pointer changes shape to show that the bar is movable.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4267b-105">W **przybornika**, <xref:System.Windows.Forms.SplitContainer> kontrolować zastępuje <xref:System.Windows.Forms.Splitter> formant, który był w poprzedniej wersji [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4267b-105">In the **Toolbox**, <xref:System.Windows.Forms.SplitContainer> control replaces the <xref:System.Windows.Forms.Splitter> control that was there in the previous version of [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="4267b-106"><xref:System.Windows.Forms.SplitContainer> Formant jest znacznie preferowany nad <xref:System.Windows.Forms.Splitter> formantu.</span><span class="sxs-lookup"><span data-stu-id="4267b-106">The <xref:System.Windows.Forms.SplitContainer> control is much preferred over the <xref:System.Windows.Forms.Splitter> control.</span></span> <span data-ttu-id="4267b-107"><xref:System.Windows.Forms.Splitter> Klasy jest dostępny w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dla zgodności z istniejącymi aplikacjami, ale zdecydowanie zalecamy używania <xref:System.Windows.Forms.SplitContainer> kontroli dla nowych projektów.</span><span class="sxs-lookup"><span data-stu-id="4267b-107">The <xref:System.Windows.Forms.Splitter> class is still included in the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] for compatibility with existing applications, but we strongly encourage you to use the <xref:System.Windows.Forms.SplitContainer> control for new projects.</span></span>  
  
 <span data-ttu-id="4267b-108">Z <xref:System.Windows.Forms.SplitContainer> formantu, mogą tworzyć interfejsy użytkownika złożonych; często zaznaczenia w jednym panelu Określa, jakie obiekty są wyświetlane w panelu.</span><span class="sxs-lookup"><span data-stu-id="4267b-108">With the <xref:System.Windows.Forms.SplitContainer> control, you can create complex user interfaces; often, a selection in one panel determines what objects are shown in the other panel.</span></span> <span data-ttu-id="4267b-109">To rozmieszczenie jest bardzo efektywnym sposobem wyświetlania oraz informacji o przeglądaniu.</span><span class="sxs-lookup"><span data-stu-id="4267b-109">This arrangement is very effective for displaying and browsing information.</span></span> <span data-ttu-id="4267b-110">Pozwala na dwa panele o agregacji informacji w obszarach i paska lub "podziału," ułatwia użytkownikom zmienianie rozmiaru paneli.</span><span class="sxs-lookup"><span data-stu-id="4267b-110">Having two panels lets you aggregate information in areas, and the bar, or "splitter," makes it easy for users to resize the panels.</span></span>  
  
 <span data-ttu-id="4267b-111">Więcej niż jeden <xref:System.Windows.Forms.SplitContainer> kontroli mogą być zagnieżdżone, drugi <xref:System.Windows.Forms.SplitContainer> kontroli orientacji poziomej, aby utworzyć górny i dolny paneli.</span><span class="sxs-lookup"><span data-stu-id="4267b-111">More than one <xref:System.Windows.Forms.SplitContainer> control can also be nested, with the second <xref:System.Windows.Forms.SplitContainer> control oriented horizontally, to create top and bottom panels.</span></span>  
  
 <span data-ttu-id="4267b-112">Należy pamiętać, że <xref:System.Windows.Forms.SplitContainer> kontroli jest klawiatury dostępny domyślnie; użytkowników można nacisnąć klawisze strzałek, aby przenieść rozdzielacza, jeśli <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> właściwość jest ustawiona na `false`.</span><span class="sxs-lookup"><span data-stu-id="4267b-112">Be aware that the <xref:System.Windows.Forms.SplitContainer> control is keyboard-accessible by default; users can press the ARROW keys to move the splitter if the <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property is set to `false`.</span></span>  
  
 <span data-ttu-id="4267b-113"><xref:System.Windows.Forms.SplitContainer.Orientation%2A> Właściwość <xref:System.Windows.Forms.SplitContainer> kontroli określa kierunek rozdzielacza, a nie samego formantu.</span><span class="sxs-lookup"><span data-stu-id="4267b-113">The <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property of the <xref:System.Windows.Forms.SplitContainer> control determines the direction of the splitter, not of the control itself.</span></span> <span data-ttu-id="4267b-114">W związku z tym, jeśli ta właściwość jest równa <xref:System.Windows.Forms.Orientation.Vertical>, rozdzielacz jest uruchamiany od góry do dołu, tworzenie lewy i prawy paneli.</span><span class="sxs-lookup"><span data-stu-id="4267b-114">Hence, when this property is set to <xref:System.Windows.Forms.Orientation.Vertical>, the splitter runs from top to bottom, creating left and right panels.</span></span>  
  
 <span data-ttu-id="4267b-115">Ponadto należy pamiętać, że wartość <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> właściwość może być różna w zależności od wartości <xref:System.Windows.Forms.SplitContainer.Orientation%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4267b-115">Additionally, be aware that the value of the <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> property varies depending on the value of the <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property.</span></span> <span data-ttu-id="4267b-116">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4267b-116">For more information, see <xref:System.Windows.Forms.SplitContainer.SplitterRectangle%2A> property.</span></span>  
  
 <span data-ttu-id="4267b-117">Można również ograniczyć rozmiar i przepływu <xref:System.Windows.Forms.SplitContainer> formantu.</span><span class="sxs-lookup"><span data-stu-id="4267b-117">You can also restrict the size and movement of the <xref:System.Windows.Forms.SplitContainer> control.</span></span> <span data-ttu-id="4267b-118"><xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> Właściwość określa, który panel pozostaje taki sam rozmiar po <xref:System.Windows.Forms.SplitContainer> zostanie zmieniony rozmiar formantu i <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> właściwość określa, czy rozdzielacz jest ruchomy klawiatury lub myszy.</span><span class="sxs-lookup"><span data-stu-id="4267b-118">The <xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> property determines which panel will remain the same size after the <xref:System.Windows.Forms.SplitContainer> control is resized, and the <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property determines if the splitter is movable by the keyboard or mouse.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4267b-119">Nawet jeśli <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> właściwość jest ustawiona na `true`, rozdzielacza nadal może przenieść programowo, na przykład za pomocą <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="4267b-119">Even if the <xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property is set to `true`, the splitter may still be moved programmatically; for example, by using the <xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> property.</span></span>  
  
 <span data-ttu-id="4267b-120">Na koniec każdego panelu <xref:System.Windows.Forms.SplitContainer> formant ma właściwości, aby określić rozmiar poszczególnych.</span><span class="sxs-lookup"><span data-stu-id="4267b-120">Finally, each panel of the <xref:System.Windows.Forms.SplitContainer> control has properties to determine its individual size.</span></span>  
  
## <a name="commonly-used-properties-methods-and-events"></a><span data-ttu-id="4267b-121">Typowe właściwości, metod i zdarzeń</span><span class="sxs-lookup"><span data-stu-id="4267b-121">Commonly Used Properties, Methods, and Events</span></span>  
  
|<span data-ttu-id="4267b-122">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4267b-122">Name</span></span>|<span data-ttu-id="4267b-123">Opis</span><span class="sxs-lookup"><span data-stu-id="4267b-123">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="4267b-124"><xref:System.Windows.Forms.SplitContainer.FixedPanel%2A>Właściwość</span><span class="sxs-lookup"><span data-stu-id="4267b-124"><xref:System.Windows.Forms.SplitContainer.FixedPanel%2A> property</span></span>|<span data-ttu-id="4267b-125">Określa, który panel pozostaje taki sam rozmiar po <xref:System.Windows.Forms.SplitContainer> zostanie zmieniony rozmiar formantu.</span><span class="sxs-lookup"><span data-stu-id="4267b-125">Determines which panel will remain the same size after the <xref:System.Windows.Forms.SplitContainer> control is resized.</span></span>|  
|<span data-ttu-id="4267b-126"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A>Właściwość</span><span class="sxs-lookup"><span data-stu-id="4267b-126"><xref:System.Windows.Forms.SplitContainer.IsSplitterFixed%2A> property</span></span>|<span data-ttu-id="4267b-127">Określa, czy rozdzielacz można przenosić z klawiatury lub myszy.</span><span class="sxs-lookup"><span data-stu-id="4267b-127">Determines if the splitter can be moved with the keyboard or mouse.</span></span>|  
|<span data-ttu-id="4267b-128"><xref:System.Windows.Forms.SplitContainer.Orientation%2A>Właściwość</span><span class="sxs-lookup"><span data-stu-id="4267b-128"><xref:System.Windows.Forms.SplitContainer.Orientation%2A> property</span></span>|<span data-ttu-id="4267b-129">Określa, czy rozdzielacz jest rozmieszczona pionie lub poziomie.</span><span class="sxs-lookup"><span data-stu-id="4267b-129">Determines if the splitter is arranged vertically or horizontally.</span></span>|  
|<span data-ttu-id="4267b-130"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A>Właściwość</span><span class="sxs-lookup"><span data-stu-id="4267b-130"><xref:System.Windows.Forms.SplitContainer.SplitterDistance%2A> property</span></span>|<span data-ttu-id="4267b-131">Określa odległość w pikselach pasek podziału ruchomy od lewej lub górnej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="4267b-131">Determines the distance in pixels from the left or upper edge to the movable splitter bar.</span></span>|  
|<span data-ttu-id="4267b-132"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A>Właściwość</span><span class="sxs-lookup"><span data-stu-id="4267b-132"><xref:System.Windows.Forms.SplitContainer.SplitterIncrement%2A> property</span></span>|<span data-ttu-id="4267b-133">Określa minimalny odstęp w pikselach, że rozdzielacza mogą być przenoszone przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="4267b-133">Determines the minimum distance, in pixels, that the splitter can be moved by the user.</span></span>|  
|<span data-ttu-id="4267b-134"><xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A>Właściwość</span><span class="sxs-lookup"><span data-stu-id="4267b-134"><xref:System.Windows.Forms.SplitContainer.SplitterWidth%2A> property</span></span>|<span data-ttu-id="4267b-135">Określa szerokość, w pikselach rozdzielacza.</span><span class="sxs-lookup"><span data-stu-id="4267b-135">Determines the thickness, in pixels, of the splitter.</span></span>|  
|<span data-ttu-id="4267b-136"><xref:System.Windows.Forms.SplitContainer.SplitterMoving>zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4267b-136"><xref:System.Windows.Forms.SplitContainer.SplitterMoving> event</span></span>|<span data-ttu-id="4267b-137">Występuje, gdy rozdzielacz jest przenoszenie.</span><span class="sxs-lookup"><span data-stu-id="4267b-137">Occurs when the splitter is moving.</span></span>|  
|<span data-ttu-id="4267b-138"><xref:System.Windows.Forms.SplitContainer.SplitterMoved>zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4267b-138"><xref:System.Windows.Forms.SplitContainer.SplitterMoved> event</span></span>|<span data-ttu-id="4267b-139">Występuje, gdy rozdzielacz został przeniesiony.</span><span class="sxs-lookup"><span data-stu-id="4267b-139">Occurs when the splitter has moved.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4267b-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4267b-140">See Also</span></span>  
 <xref:System.Windows.Forms.SplitContainer>  
 [<span data-ttu-id="4267b-141">SplitContainer — formant</span><span class="sxs-lookup"><span data-stu-id="4267b-141">SplitContainer Control</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)  
 [<span data-ttu-id="4267b-142">Przykładowe SplitContainer — formant</span><span class="sxs-lookup"><span data-stu-id="4267b-142">SplitContainer Control Sample</span></span>](http://msdn.microsoft.com/en-us/9015fad0-7108-4d85-a83a-a72d038c4f65)