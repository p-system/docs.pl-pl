---
title: 'Porady: ustawianie tła panelu formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- background colors [Windows Forms], Windows Forms Panel controls
- background images [Windows Forms], Windows Forms Panel controls
- Panel control [Windows Forms], background
- colors [Windows Forms], Windows Forms Panel controls
ms.assetid: db83cf54-3c69-4b08-ac6c-25b9b5abb1b0
ms.openlocfilehash: 896aa61f3f0900760dffd09bcab6a08bbc01628d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535721"
---
# <a name="how-to-set-the-background-of-a-windows-forms-panel-using-the-designer"></a>Porady: ustawianie tła panelu formularzy systemu Windows przy użyciu narzędzia Projektant
Formularze systemu Windows <xref:System.Windows.Forms.Panel> formant może wyświetlać zarówno kolor tła i obraz tła. <xref:System.Windows.Forms.Control.BackColor%2A> Właściwość określa kolor tła dla kontrolek, które są zawarte w panelu, takich jak etykiety i przyciski radiowe. Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> nie ustawiono właściwości <xref:System.Windows.Forms.Control.BackColor%2A> wyboru spowoduje wypełnienie wszystkich panelu. Jeśli <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwość jest ustawiona, obrazu będzie wyświetlany za formantów, które są zawarte w panelu.  
  
 Poniższa procedura wymaga **aplikacji systemu Windows** projektu z formularza, który zawiera <xref:System.Windows.Forms.Panel> formantu. Informacje dotyczące sposobu konfigurowania tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/library/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-set-the-background-in-the-windows-forms-designer"></a>Aby ustawić tła w narzędziu Projektant dla formularzy systemu Windows  
  
1.  Wybierz <xref:System.Windows.Forms.Panel> formantu.  
  
2.  W **właściwości** , kliknij strzałkę przycisk Dalej, aby <xref:System.Windows.Forms.Control.BackColor%2A> właściwość, aby wyświetlić okno z trzema kartami.  
  
3.  Wybierz **niestandardowy** kartę, aby wyświetlić paletę kolorów.  
  
4.  Wybierz **Web** lub **systemu** karty, aby wyświetlić listę wstępnie zdefiniowane nazwy kolorów, a następnie wybierz kolor.  
  
5.  W **właściwości** , kliknij strzałkę przycisk Dalej, aby <xref:System.Windows.Forms.Control.BackgroundImage%2A> właściwości.  
  
6.  W **Otwórz** oknie dialogowym Wybierz plik, który chcesz wyświetlić.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Control.BackColor%2A>  
 <xref:System.Windows.Forms.Control.BackgroundImage%2A>  
 [Panel, kontrolka](../../../../docs/framework/winforms/controls/panel-control-windows-forms.md)  
 [Panel, kontrolka — omówienie](../../../../docs/framework/winforms/controls/panel-control-overview-windows-forms.md)  
 [Instrukcje: grupowanie kontrolek za pomocą kontrolki Panel formularzy Windows Forms przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/group-controls-with-wf-panel-control-using-the-designer.md)
