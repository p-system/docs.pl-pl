---
title: "Porady: kotwiczenie formantów na formularzach systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4c6f7cc527c7409ffecab2ac67386d0f819cce3e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="7a121-102">Porady: kotwiczenie formantów na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7a121-102">How to: Anchor Controls on Windows Forms</span></span>
<span data-ttu-id="7a121-103">W przypadku projektowania formularza, który użytkownik może zmienić rozmiar w czasie wykonywania, formantów w formularzu należy zmienić rozmiar i zmienia położenie poprawnie.</span><span class="sxs-lookup"><span data-stu-id="7a121-103">If you are designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="7a121-104">Aby zmienić rozmiar kontrolki dynamicznie za pomocą formularza, można użyć <xref:System.Windows.Forms.Control.Anchor%2A> właściwości formantów formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="7a121-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="7a121-105"><xref:System.Windows.Forms.Control.Anchor%2A> Właściwość definiuje pozycji zakotwiczenia dla formantu.</span><span class="sxs-lookup"><span data-stu-id="7a121-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="7a121-106">Gdy formant jest zakotwiczony do formularza i rozmiarów formularza, formant zachowuje odległość między formantem a pozycji zakotwiczenia.</span><span class="sxs-lookup"><span data-stu-id="7a121-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="7a121-107">Na przykład, jeśli masz <xref:System.Windows.Forms.TextBox> formant, który jest zakotwiczona lewy, prawy i dolnej krawędzi formularza, ponieważ rozmiarów formularza <xref:System.Windows.Forms.TextBox> kontroli zmienia rozmiar w poziomie, aby przechowuje takiej samej odległości od prawej i lewej stronie formularza.</span><span class="sxs-lookup"><span data-stu-id="7a121-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="7a121-108">Ponadto kontrolka umieszcza się pionowo tak, aby jego lokalizacji jest zawsze tej samej odległości od dolnej krawędzi formularza.</span><span class="sxs-lookup"><span data-stu-id="7a121-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="7a121-109">Jeśli formant jest zakotwiczony nie zmieni się rozmiar formularza, pozycja kontroli względem krawędzi formularzu zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="7a121-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>  
  
 <span data-ttu-id="7a121-110"><xref:System.Windows.Forms.Control.Anchor%2A> Właściwości współdziała z <xref:System.Windows.Forms.Control.AutoSize%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7a121-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="7a121-111">Aby uzyskać więcej informacji, zobacz [AutoSize — Przegląd właściwości](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7a121-111">For more information, see [AutoSize Property Overview](../../../../docs/framework/winforms/controls/autosize-property-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a121-112">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="7a121-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7a121-113">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="7a121-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7a121-114">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="7a121-114">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-anchor-a-control-on-a-form"></a><span data-ttu-id="7a121-115">Aby móc zakotwiczyć kontrolkę w formularzu</span><span class="sxs-lookup"><span data-stu-id="7a121-115">To anchor a control on a form</span></span>  
  
1.  <span data-ttu-id="7a121-116">Wybierz formant, który ma być zakotwiczenia.</span><span class="sxs-lookup"><span data-stu-id="7a121-116">Select the control you want to anchor.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7a121-117">Można zakotwiczyć jednocześnie wiele formantów, klawisz CTRL, klikając każdego formantu, aby go zaznaczyć, a następnie po pozostałą część tej procedury.</span><span class="sxs-lookup"><span data-stu-id="7a121-117">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>  
  
2.  <span data-ttu-id="7a121-118">W **właściwości** okna, kliknij strzałkę po prawej stronie <xref:System.Windows.Forms.Control.Anchor%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="7a121-118">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>  
  
     <span data-ttu-id="7a121-119">Zostanie wyświetlony Edytor, pokazujący krzyżyk.</span><span class="sxs-lookup"><span data-stu-id="7a121-119">An editor is displayed that shows a cross.</span></span>  
  
3.  <span data-ttu-id="7a121-120">Aby ustawić zakotwiczenie, kliknij przycisk, lewego górnego, prawej lub dolnej części krzyżyk.</span><span class="sxs-lookup"><span data-stu-id="7a121-120">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>  
  
     <span data-ttu-id="7a121-121">Formanty są zakotwiczony górnego i lewego domyślnie.</span><span class="sxs-lookup"><span data-stu-id="7a121-121">Controls are anchored to the top and left by default.</span></span>  
  
4.  <span data-ttu-id="7a121-122">Aby wyczyścić po stronie formantu, który ma zostać zakotwiczony, kliknij tego arm krzyżyk.</span><span class="sxs-lookup"><span data-stu-id="7a121-122">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>  
  
5.  <span data-ttu-id="7a121-123">Aby zamknąć <xref:System.Windows.Forms.Control.Anchor%2A> Edytor właściwości, kliknij przycisk <xref:System.Windows.Forms.Control.Anchor%2A> ponownie nazwę właściwości.</span><span class="sxs-lookup"><span data-stu-id="7a121-123">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>  
  
 <span data-ttu-id="7a121-124">Gdy formularz jest wyświetlany w czasie wykonywania, pozostaje pozycjonowane w tej samej odległości od krawędzi formularza zmienia rozmiar formantu.</span><span class="sxs-lookup"><span data-stu-id="7a121-124">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="7a121-125">Odległość od krawędzi zakotwiczonej zawsze pozostaje taki sam jak odległość zdefiniowana, jeśli kontrolka znajduje się w narzędziu Projektant dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="7a121-125">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a121-126">Niektóre formanty, takie jak <xref:System.Windows.Forms.ComboBox> kontrolować, mają limit ich wysokość.</span><span class="sxs-lookup"><span data-stu-id="7a121-126">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="7a121-127">Zakotwiczanie formantu z dolną krawędzią jego formularza lub kontenera nie może wymusić przekroczenie limitu wysokość formantu.</span><span class="sxs-lookup"><span data-stu-id="7a121-127">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>  
  
 <span data-ttu-id="7a121-128">Formanty dziedziczone muszą być `Protected` mógł być zakotwiczona.</span><span class="sxs-lookup"><span data-stu-id="7a121-128">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="7a121-129">Aby zmienić poziom dostępu do formantu, ustaw jej `Modifiers` właściwości w **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="7a121-129">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a121-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7a121-130">See Also</span></span>  
 [<span data-ttu-id="7a121-131">Formanty formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7a121-131">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="7a121-132">Rozmieszczanie formantów na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7a121-132">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="7a121-133">AutoSize — Przegląd właściwości</span><span class="sxs-lookup"><span data-stu-id="7a121-133">AutoSize Property Overview</span></span>](../../../../docs/framework/winforms/controls/autosize-property-overview.md)  
 [<span data-ttu-id="7a121-134">Porady: dokowanie formantów na formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7a121-134">How to: Dock Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-dock-controls-on-windows-forms.md)  
 [<span data-ttu-id="7a121-135">Wskazówki: Rozmieszczanie formantów na formularzach systemu Windows za pomocą FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7a121-135">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [<span data-ttu-id="7a121-136">Wskazówki: Rozmieszczanie formantów na formularzach systemu Windows za pomocą TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="7a121-136">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [<span data-ttu-id="7a121-137">Wskazówki: Tworzenie Windows formantów formularzy dopełnienie, marginesami oraz właściwościami AutoSize właściwość</span><span class="sxs-lookup"><span data-stu-id="7a121-137">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-padding-autosize.md)