---
title: Kiedy należy używać formantu ComboBox formularzy systemu Windows zamiast ListBox
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], vs. ComboBox
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- ComboBox control [Windows Forms], compared to ListBox
- combo boxes [Windows Forms], compared to list boxes
- ListBox control [Windows Forms], accessing items
- ListCount property
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
ms.openlocfilehash: 88b6a6023fbfdd8fa315fcd434357626ea69a9ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537771"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>Kiedy należy używać formantu ComboBox formularzy systemu Windows zamiast ListBox
<xref:System.Windows.Forms.ComboBox> i <xref:System.Windows.Forms.ListBox> formanty mają podobne zachowania, a w niektórych przypadkach może być wymienne. Brak sytuacji, gdy jednego lub drugiego jest bardziej odpowiednie do zadania.  
  
 Ogólnie rzecz biorąc pola kombi jest odpowiednie, gdy istnieje listę opcji sugerowane i pola listy jest odpowiednia, jeśli chcesz ograniczyć dane wejściowe, aby co znajduje się na liście. Pole kombi zawiera pola tekstowego, w związku z czym wpisane opcji nie ma na liście. Wyjątek stanowi kiedy <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.ComboBoxStyle.DropDownList>. W takim przypadku formantu wybierz element w przypadku wpisania jego pierwszą literę.  
  
 Ponadto pola kombi zaoszczędzić miejsce na formularzu. Ponieważ Pełna lista nie jest wyświetlany, dopóki użytkownik kliknie strzałkę w dół, pole kombi można łatwo zmieścić w mała ilość miejsca, której nie mieści się pole listy. Wyjątek jest gdy <xref:System.Windows.Forms.ComboBox.DropDownStyle%2A> właściwość jest ustawiona na <xref:System.Windows.Forms.ComboBoxStyle.Simple>: Pełna lista jest wyświetlana, a pole kombi zajmuje więcej miejsca niż czy pole listy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 [Instrukcje: dodawanie i usuwanie elementów za pomocą kontrolki ComboBox, ListBox lub CheckedListBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/add-and-remove-items-from-a-wf-combobox.md)  
 [Instrukcje: sortowanie zawartości kontrolki ComboBox, ListBox lub CheckedListBox formularzy Windows Forms](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [Kontrolki formularzy Windows Forms używane do obsługi opcji list](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
