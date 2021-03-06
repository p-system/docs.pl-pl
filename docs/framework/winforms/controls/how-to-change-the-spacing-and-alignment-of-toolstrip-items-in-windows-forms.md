---
title: 'Porady: zmienianie odstępów i wyrównania elementów ToolStrip w formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], aligning items
- examples [Windows Forms], toolbars
- toolbars [Windows Forms], aligning items
ms.assetid: cd483466-0f49-43df-addf-e2b5fcd64027
ms.openlocfilehash: 7951a545fd8cbd0ae30907922551216161171a8d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531267"
---
# <a name="how-to-change-the-spacing-and-alignment-of-toolstrip-items-in-windows-forms"></a>Porady: zmienianie odstępów i wyrównania elementów ToolStrip w formularzach systemu Windows
<xref:System.Windows.Forms.ToolStrip> Kontroli w pełni obsługuje układ funkcje, takie jak zmiany rozmiaru, odstępy <xref:System.Windows.Forms.ToolStripItem> formantów względem siebie, rozmieszczenie formantów w <xref:System.Windows.Forms.ToolStrip>i odstępy formantów względem <xref:System.Windows.Forms.ToolStrip>.  
  
 Ponieważ domyślna wartość <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> właściwość jest `true`, formanty mają rozmiar automatycznie, chyba że ustawisz <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> właściwości `false`.  
  
### <a name="to-manually-size-a-toolstripitem"></a>Aby ręcznie rozmiar elementu ToolStripItem  
  
1.  Ustaw <xref:System.Windows.Forms.ToolStripItem.AutoSize%2A> właściwości `false` skojarzonego formantu.  
  
    ```vb  
    ToolStripButton1.AutoSize = False  
    ```  
  
    ```csharp  
    toolStripButton1.AutoSize = false;  
    ```  
  
2.  Ustaw <xref:System.Windows.Forms.ToolStripItem.Size%2A> właściwości skojarzonych z nim sposób <xref:System.Windows.Forms.ToolStripItem>.  
  
### <a name="to-set-the-spacing-of-a-toolstripitem"></a>Aby ustawić odstępy elementu ToolStripItem  
  
1.  Włóż odpowiednie wartości w pikselach <xref:System.Windows.Forms.ToolStripItem.Margin%2A> właściwości skojarzony formant.  
  
     Wartości <xref:System.Windows.Forms.ToolStripItem.Margin%2A> właściwości Określ odstępy między elementem a sąsiadujących elementów w następującej kolejności: po lewej, górnej, prawej i dolnej.  
  
    ```vb  
    ToolStripTextBox1.Margin = New System.Windows.Forms.Padding _  
        (3, 0, 3, 0)  
    ```  
  
    ```csharp  
    toolStripTextBox1.Margin = new System.Windows.Forms.Padding   
        (3, 0, 3, 0);  
    ```  
  
### <a name="to-align-a-toolstripitem-to-the-right-side-of-the-toolstrip"></a>Aby wyrównać ToolStripItem do prawej krawędzi elementu ToolStrip  
  
1.  Ustaw <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> właściwości <xref:System.Windows.Forms.ToolStripItemAlignment.Right> skojarzonego formantu. Domyślnie <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> ustawiono <xref:System.Windows.Forms.ToolStripItemAlignment.Left>, która wyrównuje kontrolki do lewej strony <xref:System.Windows.Forms.ToolStrip>.  
  
    ```vb  
    ToolStripSplitButton1.Alignment = _  
        System.Windows.Forms.ToolStripItemAlignment.Right  
    ```  
  
    ```csharp  
    toolStripSplitButton1.Alignment =   
        System.Windows.Forms.ToolStripItemAlignment.Right;  
    ```  
  
### <a name="to-arrange-toolstrip-items-on-the-toolstrip"></a>Aby zorganizować elementów ToolStrip w elemencie ToolStrip  
  
-   Ustaw <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> właściwości do wartości <xref:System.Windows.Forms.ToolStripLayoutStyle> żądany.  
  
    ```vb  
    ToolStripDropDown1.LayoutStyle = _  
        System.Windows.Forms.ToolStripLayoutStyle.Flow  
    ```  
  
    ```csharp  
    toolStripDropDown1.LayoutStyle =   
        System.Windows.Forms.ToolStripLayoutStyle.Flow;  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.Control.Layout>  
 <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>  
 <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Placement%2A>  
 <xref:System.Windows.Forms.ToolStrip.CanOverflow%2A>  
 [ToolStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip, kontrolka — architektura](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [ToolStrip — podsumowanie informacji o technologii](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)
