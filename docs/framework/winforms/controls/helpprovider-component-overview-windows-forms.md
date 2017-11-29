---
title: "HelpProvider — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 42a788e44fde80662748e19a7244ce77bb26118f
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="helpprovider-component-overview-windows-forms"></a><span data-ttu-id="76d1d-102">HelpProvider — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="76d1d-102">HelpProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="76d1d-103">Formularze systemu Windows [helpprovider —](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) składnik jest używany do skojarzenia z aplikacją Windows pomocy HTML 1.x pliku pomocy (plik .chm produkowanych Workshop pomocy HTML, lub plik htm).</span><span class="sxs-lookup"><span data-stu-id="76d1d-103">The Windows Forms [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows application.</span></span> <span data-ttu-id="76d1d-104">Zapewniają pomoc na wiele sposobów:</span><span class="sxs-lookup"><span data-stu-id="76d1d-104">You can provide help in a variety of ways:</span></span>  
  
-   <span data-ttu-id="76d1d-105">Podaj pomocy kontekstowej dla formantów na formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="76d1d-105">Provide context-sensitive Help for controls on Windows Forms.</span></span>  
  
-   <span data-ttu-id="76d1d-106">Podaj Pomoc kontekstowa w szczególności okno dialogowe lub określonych formantów w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="76d1d-106">Provide context-sensitive Help on a particular dialog box or specific controls on a dialog box.</span></span>  
  
-   <span data-ttu-id="76d1d-107">Otwórz plik pomocy do określonych obszarów, takich jak strona główna spisu treści, indeksu lub funkcję wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="76d1d-107">Open a Help file to specific areas, such as the main page of a Table of Contents, the Index, or a search function.</span></span>  
  
## <a name="using-the-help-provider"></a><span data-ttu-id="76d1d-108">Przy użyciu dostawcy pomocy</span><span class="sxs-lookup"><span data-stu-id="76d1d-108">Using the Help Provider</span></span>  
 <span data-ttu-id="76d1d-109">Dodawanie <xref:System.Windows.Forms.HelpProvider> składnik do formularza systemu Windows umożliwia inne formanty na formularzu, aby udostępnić pomocy właściwości <xref:System.Windows.Forms.HelpProvider> składnika.</span><span class="sxs-lookup"><span data-stu-id="76d1d-109">Adding a <xref:System.Windows.Forms.HelpProvider> component to your Windows Form allows the other controls on the form to expose the Help properties of the <xref:System.Windows.Forms.HelpProvider> component.</span></span> <span data-ttu-id="76d1d-110">Dzięki temu można zapewnić pomoc dla formantów w formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="76d1d-110">This enables you to provide help for the controls on your Windows Form.</span></span> <span data-ttu-id="76d1d-111">Można skojarzyć plik pomocy z <xref:System.Windows.Forms.HelpProvider> przy użyciu składnika <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="76d1d-111">You can associate a Help file with the <xref:System.Windows.Forms.HelpProvider> component using the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property.</span></span> <span data-ttu-id="76d1d-112">Określ typ pomoc wywoływania <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> i podawania wartości z <xref:System.Windows.Forms.HelpNavigator> wyliczenie dla określonego formantu.</span><span class="sxs-lookup"><span data-stu-id="76d1d-112">You specify the type of Help provided by calling <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> and providing a value from the <xref:System.Windows.Forms.HelpNavigator> enumeration for the specified control.</span></span> <span data-ttu-id="76d1d-113">Podanie — słowo kluczowe lub tematu do pomocy przez wywołanie metody <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="76d1d-113">You provide the keyword or topic for Help by calling the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> method.</span></span>  
  
 <span data-ttu-id="76d1d-114">Opcjonalnie, aby skojarzyć określony ciąg pomocy z formantem, należy użyć <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="76d1d-114">Optionally, to associate a specific Help string with another control, use the <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> method.</span></span> <span data-ttu-id="76d1d-115">Ciąg, który należy powiązać z formantu przy użyciu tej metody jest wyświetlany w oknie podręcznym, gdy użytkownik naciśnie klawisz F1, gdy formant ma fokus.</span><span class="sxs-lookup"><span data-stu-id="76d1d-115">The string that you associate with a control using this method is displayed in a pop-up window when the user presses the F1 key while the control has focus.</span></span>  
  
 <span data-ttu-id="76d1d-116">Jeśli <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> nie został ustawiony, należy użyć <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> zapewnienie tekst pomocy.</span><span class="sxs-lookup"><span data-stu-id="76d1d-116">If <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> has not been set, you must use <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> to provide the Help text.</span></span> <span data-ttu-id="76d1d-117">Jeśli ustawiono oba <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> i ciąg pomocy, na podstawie pomocy <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> mają wyższy priorytet.</span><span class="sxs-lookup"><span data-stu-id="76d1d-117">If you have set both <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> and the Help string, Help based on <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> will take precedence.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76d1d-118">Mogą wystąpić problemy przy użyciu ścieżki względnej podczas podając ścieżkę do pliku pomocy w <xref:System.Windows.Forms.Help.ShowHelp%2A> metody lub <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> właściwość <xref:System.Windows.Forms.HelpProvider> formantu.</span><span class="sxs-lookup"><span data-stu-id="76d1d-118">You may encounter problems using the relative path when specifiying the path to the Help file in the <xref:System.Windows.Forms.Help.ShowHelp%2A> method or <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property of the <xref:System.Windows.Forms.HelpProvider> control.</span></span> <span data-ttu-id="76d1d-119">Tak należy użyć ścieżki bezwzględnej, aby określić plik pomocy.</span><span class="sxs-lookup"><span data-stu-id="76d1d-119">As such, be sure to use the absolute file path to specify the Help file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76d1d-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="76d1d-120">See Also</span></span>  
 [<span data-ttu-id="76d1d-121">Systemy pomocy w aplikacjach formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="76d1d-121">Help Systems in Windows Forms Applications</span></span>](../../../../docs/framework/winforms/advanced/help-systems-in-windows-forms-applications.md)