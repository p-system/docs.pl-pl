---
title: "Porady: dodawanie i usuwanie elementów za pomocą formantu ListView formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListView control [Windows Forms], populating
- ListView control [Windows Forms], adding list items
ms.assetid: 217611ee-fd11-4d39-9a54-a37c3e781be1
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1fe301f4c504d43fd83eb52e3b32f78af2ca78a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-items-with-the-windows-forms-listview-control-using-the-designer"></a><span data-ttu-id="c6c91-102">Porady: dodawanie i usuwanie elementów za pomocą formantu ListView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="c6c91-102">How to: Add and Remove Items with the Windows Forms ListView Control Using the Designer</span></span>
<span data-ttu-id="c6c91-103">Proces dodawania elementu do formularzy systemu Windows <xref:System.Windows.Forms.ListView> kontroli obejmuje głównie określenie elementu i przypisywanie właściwości.</span><span class="sxs-lookup"><span data-stu-id="c6c91-103">The process of adding an item to a Windows Forms <xref:System.Windows.Forms.ListView> control consists primarily of specifying the item and assigning properties to it.</span></span> <span data-ttu-id="c6c91-104">Dodawanie lub usuwanie elementów listy można zrobić w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="c6c91-104">Adding or removing list items can be done at any time.</span></span>  
  
 <span data-ttu-id="c6c91-105">Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="c6c91-105">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ListView> control.</span></span> <span data-ttu-id="c6c91-106">Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c6c91-106">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6c91-107">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="c6c91-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c6c91-108">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="c6c91-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c6c91-109">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="c6c91-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-items-using-the-designer"></a><span data-ttu-id="c6c91-110">Aby dodać lub usunąć elementy przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="c6c91-110">To add or remove items using the designer</span></span>  
  
1.  <span data-ttu-id="c6c91-111">Wybierz <xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="c6c91-111">Select the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
2.  <span data-ttu-id="c6c91-112">W **właściwości** okna, kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) znajdujący się obok <xref:System.Windows.Forms.ListView.Items%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c6c91-112">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.ListView.Items%2A> property.</span></span>  
  
     <span data-ttu-id="c6c91-113">**Edytora kolekcji ListViewItem** pojawi się.</span><span class="sxs-lookup"><span data-stu-id="c6c91-113">The **ListViewItem Collection Editor** appears.</span></span>  
  
3.  <span data-ttu-id="c6c91-114">Aby dodać element, kliknij przycisk **Dodaj** przycisku.</span><span class="sxs-lookup"><span data-stu-id="c6c91-114">To add an item, click the **Add** button.</span></span> <span data-ttu-id="c6c91-115">Następnie można ustawić właściwości nowy element, taki jak <xref:System.Windows.Forms.ListView.Text%2A> i <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c6c91-115">You can then set properties of the new item, such as the <xref:System.Windows.Forms.ListView.Text%2A> and <xref:System.Windows.Forms.ListViewItem.ImageIndex%2A> properties.</span></span>  
  
4.  <span data-ttu-id="c6c91-116">Aby usunąć element, zaznacz go i kliknij przycisk **Usuń** przycisku.</span><span class="sxs-lookup"><span data-stu-id="c6c91-116">To remove an item, select it and click the **Remove** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6c91-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c6c91-117">See Also</span></span>  
 [<span data-ttu-id="c6c91-118">Informacje o formancie ListView</span><span class="sxs-lookup"><span data-stu-id="c6c91-118">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="c6c91-119">Porady: Dodawanie kolumn do systemu Windows formantu ListView formularzy</span><span class="sxs-lookup"><span data-stu-id="c6c91-119">How to: Add Columns to the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="c6c91-120">Porady: wyświetlanie podelementów w kolumnach z systemu Windows formantu ListView formularzy</span><span class="sxs-lookup"><span data-stu-id="c6c91-120">How to: Display Subitems in Columns with the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="c6c91-121">Porady: wyświetlanie ikon dla formantu ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c6c91-121">How to: Display Icons for the Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [<span data-ttu-id="c6c91-122">Porady: Dodawanie niestandardowych informacji do formantu TreeView lub ListView (formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="c6c91-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)  
 [<span data-ttu-id="c6c91-123">Porady: grupowanie elementów w systemie Windows formantu ListView formularzy</span><span class="sxs-lookup"><span data-stu-id="c6c91-123">How to: Group Items in a Windows Forms ListView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-group-items-in-a-windows-forms-listview-control.md)