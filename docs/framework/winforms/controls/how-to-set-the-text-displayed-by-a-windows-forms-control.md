---
title: 'Porady: ustawianie tekstu wyświetlanego przez formant formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, captions
- Button control [Windows Forms], button text
- StdFont object and CommandButton caption
- captions [Windows Forms], Windows Forms controls
- Text property [Windows Forms], Windows Forms control
- Button control [Windows Forms], text display
- labels [Windows Forms], adding to CommandButton control
- buttons [Windows Forms], text
- captions [Windows Forms], setting
- text
- examples [Windows Forms], controls
- text [Windows Forms], Windows Forms controls
- controls [Windows Forms], captions
- forms [Windows Forms], captions
ms.assetid: 36b95bff-8780-479d-b86a-f1a0673653aa
ms.openlocfilehash: d39b0b7ccf95f0da22086a72aa2cee424d7ea8ae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535616"
---
# <a name="how-to-set-the-text-displayed-by-a-windows-forms-control"></a>Porady: ustawianie tekstu wyświetlanego przez formant formularzy systemu Windows
Formanty formularzy systemu Windows zazwyczaj wyświetlić tekst związany z podstawowej funkcji formantu. Na przykład <xref:System.Windows.Forms.Button> kontroli zwykle zawiera nagłówek wskazującą, jakie działania zostaną wykonane, po kliknięciu przycisku. Dla wszystkich kontrolek, można ustawić lub zwróć tekst za pomocą <xref:System.Windows.Forms.Control.Text%2A> właściwości. Czcionkę można zmienić za pomocą <xref:System.Windows.Forms.Control.Font%2A> właściwości. Można również ustawić tekst przy użyciu narzędzia Projektant.  Zobacz też [jak: utworzyć dostępu do kluczy dla systemu Windows formularzy formantów przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/ms233673\(v=vs.110\)), [porady: ustawić tekst wyświetlany za pomocą formantu formularzy systemu Windows projektanta](http://msdn.microsoft.com/library/ms233665\(v=vs.110\)), [porady: Ustawianie obrazu Wyświetlany przez formant przy użyciu narzędzia Projektant formularzy systemu Windows](http://msdn.microsoft.com/library/ms233656\(v=vs.110\)).  
  
### <a name="to-set-the-text-displayed-by-a-control-programmatically"></a>Aby ustawić tekst wyświetlany przez formant programowo  
  
1.  Ustaw <xref:System.Windows.Forms.Control.Text%2A> właściwości na ciąg.  
  
     Można utworzyć klucza dostępu podkreślony obejmuje handlowego "i" (&) przed literą, która będzie klucz dostępu.  
  
2.  Ustaw <xref:System.Windows.Forms.Control.Font%2A> dla właściwości typu obiektu <xref:System.Drawing.Font>.  
  
    ```vb  
    Button1.Text = "Click here to save changes"  
    Button1.Font = New Font("Arial", 10, FontStyle.Bold, GraphicsUnit.Point)  
    ```  
  
    ```csharp  
    button1.Text = "Click here to save changes";  
    button1.Font = new Font("Arial", 10, FontStyle.Bold,  
       GraphicsUnit.Point);  
    ```  
  
    ```cpp  
    button1->Text = "Click here to save changes";  
    button1->Font = new System::Drawing::Font("Arial",  
       10, FontStyle::Bold, GraphicsUnit::Point);  
    ```  
  
    > [!NOTE]
    >  Znak ucieczki służy do wyświetlania znaków specjalnych w elementy interfejsu użytkownika, które będzie zwykle je interpretować, takich jak elementy menu. Na przykład następujący wiersz kodu ustawia tekst elementu menu do odczytu "& teraz na coś dwóch zupełnie różnych":  
  
    ```vb  
    MPMenuItem.Text = "&& Now For Something Completely Different"  
    ```  
  
    ```csharp  
    mpMenuItem.Text = "&& Now For Something Completely Different";  
    ```  
  
    ```cpp  
    mpMenuItem->Text = "&& Now For Something Completely Different";  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Control.Text%2A?displayProperty=nameWithType>  
 [Instrukcje: tworzenie klawiszy dostępu dla kontrolek formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md)  
 [Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
