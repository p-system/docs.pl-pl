---
title: "NotifyIcon — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: NotifyIcon
helpviewer_keywords:
- NotifyIcon component [Windows Forms], about NotifyIcon component
- system tray icons [Windows Forms], about system tray icons
- system tray icons [Windows Forms], using in Windows Forms
ms.assetid: 5b9189fa-d4ae-41a6-9b97-eb1f44bb1a69
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d951d45232437026cc41d8e40284207ea1c64ab9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="notifyicon-component-overview-windows-forms"></a><span data-ttu-id="a6a13-102">NotifyIcon — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="a6a13-102">NotifyIcon Component Overview (Windows Forms)</span></span>
<span data-ttu-id="a6a13-103">Formularze systemu Windows <xref:System.Windows.Forms.NotifyIcon> składnik jest zazwyczaj używany do wyświetlania ikon dla procesów, które są uruchomione w tle i nie pokazuj użytkownika interfejsu większość czasu.</span><span class="sxs-lookup"><span data-stu-id="a6a13-103">The Windows Forms <xref:System.Windows.Forms.NotifyIcon> component is typically used to display icons for processes that run in the background and do not show a user interface much of the time.</span></span> <span data-ttu-id="a6a13-104">Przykładem może być programu ochrony przed wirusami, którego mogą uzyskać dostęp, klikając ikonę w obszarze powiadomień stanu na pasku zadań.</span><span class="sxs-lookup"><span data-stu-id="a6a13-104">An example would be a virus protection program that can be accessed by clicking an icon in the status notification area of the taskbar.</span></span>  
  
## <a name="key-properties-of-notifyicons"></a><span data-ttu-id="a6a13-105">Właściwości klucza obiektu NotifyIcons</span><span class="sxs-lookup"><span data-stu-id="a6a13-105">Key Properties of NotifyIcons</span></span>  
 <span data-ttu-id="a6a13-106">Każdy <xref:System.Windows.Forms.NotifyIcon> składnik Wyświetla pojedynczą ikonę w obszarze stanu.</span><span class="sxs-lookup"><span data-stu-id="a6a13-106">Each <xref:System.Windows.Forms.NotifyIcon> component displays a single icon in the status area.</span></span> <span data-ttu-id="a6a13-107">Jeśli masz trzy procesy w tle i ma być wyświetlana ikona, dla każdego należy dodać trzy <xref:System.Windows.Forms.NotifyIcon> składników do formularza.</span><span class="sxs-lookup"><span data-stu-id="a6a13-107">If you have three background processes and wish to display an icon for each, you must add three <xref:System.Windows.Forms.NotifyIcon> components to the form.</span></span> <span data-ttu-id="a6a13-108">Właściwości klucza obiektu <xref:System.Windows.Forms.NotifyIcon> są składnika <xref:System.Windows.Forms.NotifyIcon.Icon%2A> i <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span><span class="sxs-lookup"><span data-stu-id="a6a13-108">The key properties of the <xref:System.Windows.Forms.NotifyIcon> component are <xref:System.Windows.Forms.NotifyIcon.Icon%2A> and <xref:System.Windows.Forms.NotifyIcon.Visible%2A>.</span></span> <span data-ttu-id="a6a13-109"><xref:System.Windows.Forms.NotifyIcon.Icon%2A> Właściwość ustawia ikonę, która jest wyświetlana w obszarze stanu.</span><span class="sxs-lookup"><span data-stu-id="a6a13-109">The <xref:System.Windows.Forms.NotifyIcon.Icon%2A> property sets the icon that appears in the status area.</span></span> <span data-ttu-id="a6a13-110">Aby pojawia się ikona <xref:System.Windows.Forms.NotifyIcon.Visible%2A> musi mieć ustawioną właściwość `true`.</span><span class="sxs-lookup"><span data-stu-id="a6a13-110">In order for the icon to appear, the <xref:System.Windows.Forms.NotifyIcon.Visible%2A> property must be set to `true`.</span></span>  
  
 <span data-ttu-id="a6a13-111">Jeśli używasz [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], masz dostęp do dużych biblioteki standardowe obrazów, które można używać z <xref:System.Windows.Forms.NotifyIcon> formantu.</span><span class="sxs-lookup"><span data-stu-id="a6a13-111">If you are using [!INCLUDE[vsprvslong](../../../../includes/vsprvslong-md.md)], you have access to a large library of standard images that you can use with the <xref:System.Windows.Forms.NotifyIcon> control.</span></span>  
  
## <a name="notifyicons-options"></a><span data-ttu-id="a6a13-112">Opcje NotifyIcons</span><span class="sxs-lookup"><span data-stu-id="a6a13-112">NotifyIcons Options</span></span>  
 <span data-ttu-id="a6a13-113">Możesz skojarzyć porady dymek, menu skrótów i etykietki narzędzi z <xref:System.Windows.Forms.NotifyIcon> ułatwiających użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a6a13-113">You can associate balloon tips, shortcut menus, and ToolTips with a <xref:System.Windows.Forms.NotifyIcon> to assist the user.</span></span>  
  
 <span data-ttu-id="a6a13-114">Można wyświetlić dymek porady dotyczące <xref:System.Windows.Forms.NotifyIcon> przez wywołanie metody <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> metody, określając zakres czasu chcesz etykieta dymka do wyświetlenia.</span><span class="sxs-lookup"><span data-stu-id="a6a13-114">You can display balloon tips for a <xref:System.Windows.Forms.NotifyIcon> by calling the <xref:System.Windows.Forms.NotifyIcon.ShowBalloonTip%2A> method specifying the time span you wish the balloon tip to display.</span></span> <span data-ttu-id="a6a13-115">Można również określić tekst, ikonę i tytuł etykieta dymka z <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> i <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="a6a13-115">You can also specify the text, icon and title of the balloon tip with the <xref:System.Windows.Forms.NotifyIcon.BalloonTipText%2A>, <xref:System.Windows.Forms.NotifyIcon.BalloonTipIcon%2A> and <xref:System.Windows.Forms.NotifyIcon.BalloonTipTitle%2A>, respectively.</span></span> <span data-ttu-id="a6a13-116"><xref:System.Windows.Forms.NotifyIcon>składniki można również skojarzyć etykietki narzędzi i menu skrótów.</span><span class="sxs-lookup"><span data-stu-id="a6a13-116"><xref:System.Windows.Forms.NotifyIcon> components can also have associated ToolTips and shortcut menus.</span></span> <span data-ttu-id="a6a13-117">Aby uzyskać więcej informacji, zobacz [informacje o składniku ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md) i [informacje o składniku ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="a6a13-117">For more information, see [ToolTip Component Overview](../../../../docs/framework/winforms/controls/tooltip-component-overview-windows-forms.md) and [ContextMenu Component Overview](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6a13-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a6a13-118">See Also</span></span>  
 <xref:System.Windows.Forms.NotifyIcon>  
 [<span data-ttu-id="a6a13-119">Notifyicon — składnik</span><span class="sxs-lookup"><span data-stu-id="a6a13-119">NotifyIcon Component</span></span>](../../../../docs/framework/winforms/controls/notifyicon-component-windows-forms.md)