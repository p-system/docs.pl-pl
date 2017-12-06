---
title: 'Porady: ustawianie rozmiaru paneli paska stanu'
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
helpviewer_keywords:
- StatusBar control [Windows Forms], panel size
- status bars [Windows Forms], setting panel size
- panels [Windows Forms], setting size in status bars
ms.assetid: a01bee43-d9eb-4954-84e6-45a93532d08d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bc9eca130b238ac686e88ebbc6e8491bc7be93bf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a><span data-ttu-id="1af2a-102">Porady: ustawianie rozmiaru paneli paska stanu</span><span class="sxs-lookup"><span data-stu-id="1af2a-102">How to: Set the Size of Status-Bar Panels</span></span>
> [!NOTE]
>  <span data-ttu-id="1af2a-103"><xref:System.Windows.Forms.ToolStripStatusLabel> Kontroli zastępuje i dodaje funkcje do <xref:System.Windows.Forms.StatusBar> kontrolować; jednak <xref:System.Windows.Forms.StatusBar> formantu są przechowywane dla zgodności z poprzednimi wersjami i użycia w przyszłości, jeśli zostanie wybrana.</span><span class="sxs-lookup"><span data-stu-id="1af2a-103">The <xref:System.Windows.Forms.ToolStripStatusLabel> control replaces and adds functionality to the <xref:System.Windows.Forms.StatusBar> control; however, the <xref:System.Windows.Forms.StatusBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="1af2a-104">Każde wystąpienie <xref:System.Windows.Forms.StatusBarPanel> klas w ramach [formantu StatusBar](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) formant ma wiele właściwości dynamiczne, które określają jego szerokość, a następnie zmień rozmiar zachowania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="1af2a-104">Each instance of the <xref:System.Windows.Forms.StatusBarPanel> class within a [StatusBar Control](../../../../docs/framework/winforms/controls/statusbar-control-windows-forms.md) control has a number of dynamic properties that determine its width and resize behavior at run time.</span></span>  
  
### <a name="to-set-the-size-of-a-panel"></a><span data-ttu-id="1af2a-105">Aby określić rozmiar panelu</span><span class="sxs-lookup"><span data-stu-id="1af2a-105">To set the size of a panel</span></span>  
  
1.  <span data-ttu-id="1af2a-106">W procedurze, ustaw <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, i <xref:System.Windows.Forms.StatusBarPanel.Width%2A> właściwości (lub dowolnego podzbioru tam) na pasku stanu paneli przy użyciu jej indeksu przekazywane <xref:System.Windows.Forms.StatusBar.Panels%2A> właściwość <xref:System.Windows.Forms.StatusBarPanel> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="1af2a-106">In a procedure, set the <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>, <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, and <xref:System.Windows.Forms.StatusBarPanel.Width%2A> properties (or any subset therein) for the status-bar panels using their index passed through the <xref:System.Windows.Forms.StatusBar.Panels%2A> property of the <xref:System.Windows.Forms.StatusBarPanel> collection.</span></span>  
  
    ```vb  
    Public Sub SetStatusBarPanelSize()  
    ' Create panel and set text property.  
       StatusBar1.Panels.Add("One")  
    ' Set properties of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(0).Width = 200  
    ' Enable the StatusBar control to display panels.  
       StatusBar1.ShowPanels = True  
        End Sub  
    ```  
  
    ```csharp  
    public void SetStatusBarPanelSize()  
    {  
       // Create panel and set text property.  
       statusBar1.Panels.Add("One");  
       // Set properties of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[0].Width = 200;  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void SetStatusBarPanelSize()  
       {  
          // Create panel and set text property.  
          statusBar1->Panels->Add("One");  
          // Set properties of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[0]->Width = 200;  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1af2a-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1af2a-107">See Also</span></span>  
 <xref:System.Windows.Forms.StatusBar>  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 [<span data-ttu-id="1af2a-108">Wskazówki: Aktualizowanie informacji na pasku stanu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="1af2a-108">Walkthrough: Updating Status Bar Information at Run Time</span></span>](../../../../docs/framework/winforms/controls/walkthrough-updating-status-bar-information-at-run-time.md)  
 [<span data-ttu-id="1af2a-109">Porady: Określanie, które panelu w formancie StatusBar formularzy systemu Windows został kliknięty</span><span class="sxs-lookup"><span data-stu-id="1af2a-109">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](../../../../docs/framework/winforms/controls/determine-which-panel-wf-statusbar-control-was-clicked.md)  
 [<span data-ttu-id="1af2a-110">Informacje o formancie StatusBar</span><span class="sxs-lookup"><span data-stu-id="1af2a-110">StatusBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/statusbar-control-overview-windows-forms.md)