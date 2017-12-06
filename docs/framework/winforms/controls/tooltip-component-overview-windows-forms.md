---
title: "ToolTip — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ToolTip
helpviewer_keywords:
- tooltips [Windows Forms], about tooltips
- ToolTip component [Windows Forms], about ToolTip component
ms.assetid: 3fbc6f08-c882-4acd-a960-a08efe3c7e6e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff2364b5c7223c265571257920a7c7e794b4921b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="tooltip-component-overview-windows-forms"></a><span data-ttu-id="cec3b-102">ToolTip — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="cec3b-102">ToolTip Component Overview (Windows Forms)</span></span>
<span data-ttu-id="cec3b-103">Formularze systemu Windows <xref:System.Windows.Forms.ToolTip> składnika wyświetla tekst, gdy użytkownik wskazuje na formanty.</span><span class="sxs-lookup"><span data-stu-id="cec3b-103">The Windows Forms <xref:System.Windows.Forms.ToolTip> component displays text when the user points at controls.</span></span> <span data-ttu-id="cec3b-104">Etykietka narzędzia może być skojarzony z żadnym formantem.</span><span class="sxs-lookup"><span data-stu-id="cec3b-104">A ToolTip can be associated with any control.</span></span> <span data-ttu-id="cec3b-105">Przykładowe zastosowanie tego składnika: Aby zaoszczędzić miejsce na formularzu, można wyświetlić na małe ikony na przycisku i używać etykietka narzędzia wyjaśnić funkcja przycisku.</span><span class="sxs-lookup"><span data-stu-id="cec3b-105">An example use of this component: to save space on a form, you can display a small icon on a button and use a ToolTip to explain the button's function.</span></span>  
  
## <a name="working-with-the-tooltip-component"></a><span data-ttu-id="cec3b-106">Praca z ToolTip — składnik</span><span class="sxs-lookup"><span data-stu-id="cec3b-106">Working with the ToolTip Component</span></span>  
 <span data-ttu-id="cec3b-107">A <xref:System.Windows.Forms.ToolTip> stanowi `ToolTip` właściwości wielu formantów w formularzu systemu Windows lub innych kontenera.</span><span class="sxs-lookup"><span data-stu-id="cec3b-107">A <xref:System.Windows.Forms.ToolTip> component provides a `ToolTip` property to multiple controls on a Windows Form or other container.</span></span> <span data-ttu-id="cec3b-108">Na przykład, jeśli zostanie umieszczony <xref:System.Windows.Forms.ToolTip> składnika w formularzu, można wyświetlić "Wpisz tutaj nazwę" <xref:System.Windows.Forms.TextBox> kontroli oraz "Kliknij tutaj, aby zapisać zmiany" dla <xref:System.Windows.Forms.Button> formantu.</span><span class="sxs-lookup"><span data-stu-id="cec3b-108">For example, if you place one <xref:System.Windows.Forms.ToolTip> component on a form, you can display "Type your name here" for a <xref:System.Windows.Forms.TextBox> control and "Click here to save changes" for a <xref:System.Windows.Forms.Button> control.</span></span>  
  
 <span data-ttu-id="cec3b-109">Metody klucza <xref:System.Windows.Forms.ToolTip> są składnika <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> i <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>.</span><span class="sxs-lookup"><span data-stu-id="cec3b-109">The key methods of the <xref:System.Windows.Forms.ToolTip> component are <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> and <xref:System.Windows.Forms.ToolTip.GetToolTip%2A>.</span></span> <span data-ttu-id="cec3b-110">Można użyć <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> metodę, aby ustawić etykietki narzędzi wyświetlane dla formantów.</span><span class="sxs-lookup"><span data-stu-id="cec3b-110">You can use the <xref:System.Windows.Forms.ToolTip.SetToolTip%2A> method to set the ToolTips displayed for controls.</span></span> <span data-ttu-id="cec3b-111">Aby uzyskać więcej informacji, zobacz [porady: Ustawianie etykietki narzędzi dla formantów w formularzu systemu Windows w czasie projektowania](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="cec3b-111">For more information, see [How to: Set ToolTips for Controls on a Windows Form at Design Time](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md).</span></span> <span data-ttu-id="cec3b-112">Właściwości klucza są <xref:System.Windows.Forms.ToolTip.Active%2A>, musi być ustawiona na `true` dla etykietki narzędzia w celu wyświetlenia, i <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, która określa długość czasu, który jest wyświetlany ciąg etykietki narzędzia, jak długo użytkownik musi wskazywać na formantu etykietki narzędzia w celu wyświetlenia i jak długie go Przejście do kolejnego elementu ToolTip pojawią się.</span><span class="sxs-lookup"><span data-stu-id="cec3b-112">The key properties are <xref:System.Windows.Forms.ToolTip.Active%2A>, which must be set to `true` for the ToolTip to appear, and <xref:System.Windows.Forms.ToolTip.AutomaticDelay%2A>, which sets the length of time that the ToolTip string is shown, how long the user must point at the control for the ToolTip to appear, and how long it takes for subsequent ToolTip windows to appear.</span></span> <span data-ttu-id="cec3b-113">Aby uzyskać więcej informacji, zobacz [porady: zmienianie opóźnienia składnika ToolTip formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).</span><span class="sxs-lookup"><span data-stu-id="cec3b-113">For more information, see [How to: Change the Delay of the Windows Forms ToolTip Component](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cec3b-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cec3b-114">See Also</span></span>  
 <xref:System.Windows.Forms.ToolTip>  
 [<span data-ttu-id="cec3b-115">Porady: ustawienie elementu ToolTips dla formantów w formularzu systemu Windows w czasie projektowania</span><span class="sxs-lookup"><span data-stu-id="cec3b-115">How to: Set ToolTips for Controls on a Windows Form at Design Time</span></span>](../../../../docs/framework/winforms/controls/how-to-set-tooltips-for-controls-on-a-windows-form-at-design-time.md)  
 [<span data-ttu-id="cec3b-116">Porady: zmienianie opóźnienia składnika ToolTip formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="cec3b-116">How to: Change the Delay of the Windows Forms ToolTip Component</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-delay-of-the-windows-forms-tooltip-component.md)