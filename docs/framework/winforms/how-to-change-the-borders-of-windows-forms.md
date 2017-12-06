---
title: 'Porady: zmienianie granic formularzy systemu Windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords: Windows Forms, changing the borders
ms.assetid: b3d5fa56-80c6-4b10-b505-f9672307ed55
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 94c95d1d938ff8038f1057ac7648082819562b98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-borders-of-windows-forms"></a><span data-ttu-id="9ac96-102">Porady: zmienianie granic formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9ac96-102">How to: Change the Borders of Windows Forms</span></span>
<span data-ttu-id="9ac96-103">Masz kilka style obramowania do wyboru przy ustalaniu wygląd i zachowanie formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9ac96-103">You have several border styles to choose from when you are determining the appearance and behavior of your Windows Forms.</span></span> <span data-ttu-id="9ac96-104">Zmieniając <xref:System.Windows.Forms.Form.FormBorderStyle%2A> właściwości, można kontrolować zachowanie zmiany rozmiaru formularza.</span><span class="sxs-lookup"><span data-stu-id="9ac96-104">By changing the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property, you can control the resizing behavior of the form.</span></span> <span data-ttu-id="9ac96-105">Ponadto ustawienie <xref:System.Windows.Forms.Form.FormBorderStyle%2A> wpływa na sposób wyświetlania paska podpisu oraz przyciski wygląda na nim.</span><span class="sxs-lookup"><span data-stu-id="9ac96-105">In addition, setting the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> affects how the caption bar is displayed as well as what buttons might appear on it.</span></span> <span data-ttu-id="9ac96-106">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.FormBorderStyle>.</span><span class="sxs-lookup"><span data-stu-id="9ac96-106">For more information, see <xref:System.Windows.Forms.FormBorderStyle>.</span></span>  
  
 <span data-ttu-id="9ac96-107">Brak kompleksową obsługę tego zadania w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9ac96-107">There is extensive support for this task in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="9ac96-108">Zobacz też [porady: Zmienianie granic formularzy systemu Windows przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/yettzh3e\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="9ac96-108">See also [How to: Change the Borders of Windows Forms Using the Designer](http://msdn.microsoft.com/library/yettzh3e\(v=vs.110\)).</span></span>  
  
### <a name="to-set-the-border-style-of-windows-forms-programmatically"></a><span data-ttu-id="9ac96-109">Aby ustawić programowo styl obramowania formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9ac96-109">To set the border style of Windows Forms programmatically</span></span>  
  
-   <span data-ttu-id="9ac96-110">Ustaw <xref:System.Windows.Forms.Form.FormBorderStyle%2A> właściwości stylu ma.</span><span class="sxs-lookup"><span data-stu-id="9ac96-110">Set the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to the style you want.</span></span> <span data-ttu-id="9ac96-111">Poniższy przykład kodu ustawia styl obramowania formularza `DlgBx1` do <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span><span class="sxs-lookup"><span data-stu-id="9ac96-111">The following code example sets the border style of form `DlgBx1` to <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>.</span></span>  
  
    ```vb  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog  
    ```  
  
    ```csharp  
    DlgBx1.FormBorderStyle = System.Windows.Forms.FormBorderStyle.FixedDialog;  
    ```  
  
    ```cpp  
    DlgBx1->FormBorderStyle =  
       System::Windows::Forms::FormBorderStyle::FixedDialog;  
    ```  
  
     <span data-ttu-id="9ac96-112">Zobacz też [porady: tworzenie okien dialogowych w czasie projektowania](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="9ac96-112">Also see [How to: Create Dialog Boxes at Design Time](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\)).</span></span>  
  
     <span data-ttu-id="9ac96-113">Ponadto jeśli wybrano styl obramowania formularza, który zapewnia opcjonalne **Minimalizuj** i **Maksymalizuj** przycisków, użytkownik może określić, czy jednego lub obu tych przycisków, aby działała.</span><span class="sxs-lookup"><span data-stu-id="9ac96-113">Additionally, if you have chosen a border style for the form that provides optional **Minimize** and **Maximize** buttons, you can specify whether you want either or both of these buttons to be functional.</span></span> <span data-ttu-id="9ac96-114">Przyciski te są przydatne, gdy chcesz ściśle kontrolują środowisko użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9ac96-114">These buttons are useful when you want to closely control the user experience.</span></span> <span data-ttu-id="9ac96-115">**Minimalizuj** i **Maksymalizuj** przyciski są domyślnie włączone, a ich funkcjonalność steruje się za pośrednictwem **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="9ac96-115">The **Minimize** and **Maximize** buttons are enabled by default, and their functionality is manipulated through the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ac96-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ac96-116">See Also</span></span>  
 <xref:System.Windows.Forms.FormBorderStyle>  
 <xref:System.Windows.Forms.FormBorderStyle.FixedDialog>  
 [<span data-ttu-id="9ac96-117">Wprowadzenie do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="9ac96-117">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)