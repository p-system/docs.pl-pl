---
title: "Porady: dodawanie i usuwanie elementów za pomocą formantu ComboBox, ListBox lub CheckedListBox formularzy systemu Windows"
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
- combo boxes [Windows Forms], adding items
- list boxes [Windows Forms], removing items
- ComboBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], adding and removing items
- list boxes [Windows Forms], adding items
- combo boxes [Windows Forms], removing items
- CheckedListBox control [Windows Forms], adding and removing items
ms.assetid: 7224c8d2-4118-443e-ae1e-d7c17d1e69ee
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 96f18f02f82b0e7f9f517890ec963b43fa8d8f60
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-items-from-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a><span data-ttu-id="5e70e-102">Porady: dodawanie i usuwanie elementów za pomocą formantu ComboBox, ListBox lub CheckedListBox formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5e70e-102">How to: Add and Remove Items from a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>
<span data-ttu-id="5e70e-103">Elementy mogą być dodawane do pola kombi formularzy systemu Windows, pole listy lub zaznaczone pole listy na różne sposoby, ponieważ tych kontrolek można powiązać z różnych źródeł danych.</span><span class="sxs-lookup"><span data-stu-id="5e70e-103">Items can be added to a Windows Forms combo box, list box, or checked list box in a variety of ways, because these controls can be bound to a variety of data sources.</span></span> <span data-ttu-id="5e70e-104">Jednak w tym temacie przedstawiono najprostszą metodą i wymaga nie powiązania danych.</span><span class="sxs-lookup"><span data-stu-id="5e70e-104">However, this topic demonstrates the simplest method and requires no data binding.</span></span> <span data-ttu-id="5e70e-105">Elementy wyświetlane są zwykle ciągi; jednak można użyć dowolnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5e70e-105">The items displayed are usually strings; however, any object can be used.</span></span> <span data-ttu-id="5e70e-106">Tekst, który jest wyświetlany w formancie jest wartość zwrócona przez obiekt `ToString` metody.</span><span class="sxs-lookup"><span data-stu-id="5e70e-106">The text that is displayed in the control is the value returned by the object's `ToString` method.</span></span>  
  
### <a name="to-add-items"></a><span data-ttu-id="5e70e-107">Aby dodać elementy</span><span class="sxs-lookup"><span data-stu-id="5e70e-107">To add items</span></span>  
  
1.  <span data-ttu-id="5e70e-108">Dodaj ciąg lub obiekt do listy przy użyciu `Add` metody `ObjectCollection` klasy.</span><span class="sxs-lookup"><span data-stu-id="5e70e-108">Add the string or object to the list by using the `Add` method of the `ObjectCollection` class.</span></span> <span data-ttu-id="5e70e-109">Kolekcja odwołuje się przy użyciu `Items` właściwości:</span><span class="sxs-lookup"><span data-stu-id="5e70e-109">The collection is referenced using the `Items` property:</span></span>  
  
    ```vb  
    ComboBox1.Items.Add("Tokyo")  
    ```  
  
    ```csharp  
    comboBox1.Items.Add("Tokyo");  
    ```  
  
    ```cpp  
    comboBox1->Items->Add("Tokyo");  
    ```  
  
     - <span data-ttu-id="5e70e-110">lub -</span><span class="sxs-lookup"><span data-stu-id="5e70e-110">or -</span></span>  
  
2.  <span data-ttu-id="5e70e-111">Wstaw ciąg lub obiekt w wybrane miejsce na liście zawierającej `Insert` metody:</span><span class="sxs-lookup"><span data-stu-id="5e70e-111">Insert the string or object at the desired point in the list with the `Insert` method:</span></span>  
  
    ```vb  
    CheckedListBox1.Items.Insert(0, "Copenhagen")  
    ```  
  
    ```csharp  
    checkedListBox1.Items.Insert(0, "Copenhagen");  
    ```  
  
    ```cpp  
    checkedListBox1->Items->Insert(0, "Copenhagen");  
    ```  
  
     - <span data-ttu-id="5e70e-112">lub -</span><span class="sxs-lookup"><span data-stu-id="5e70e-112">or -</span></span>  
  
3.  <span data-ttu-id="5e70e-113">Przypisz całą tablicę do `Items` kolekcji:</span><span class="sxs-lookup"><span data-stu-id="5e70e-113">Assign an entire array to the `Items` collection:</span></span>  
  
    ```vb  
    Dim ItemObject(9) As System.Object  
    Dim i As Integer  
       For i = 0 To 9  
       ItemObject(i) = "Item" & i  
    Next i  
    ListBox1.Items.AddRange(ItemObject)  
    ```  
  
    ```csharp  
    System.Object[] ItemObject = new System.Object[10];  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = "Item" + i;  
    }  
    listBox1.Items.AddRange(ItemObject);  
    ```  
  
    ```cpp  
    Array<System::Object^>^ ItemObject = gcnew Array<System::Object^>(10);  
    for (int i = 0; i <= 9; i++)  
    {  
       ItemObject[i] = String::Concat("Item", i.ToString());  
    }  
    listBox1->Items->AddRange(ItemObject);  
    ```  
  
### <a name="to-remove-an-item"></a><span data-ttu-id="5e70e-114">Aby usunąć element</span><span class="sxs-lookup"><span data-stu-id="5e70e-114">To remove an item</span></span>  
  
1.  <span data-ttu-id="5e70e-115">Wywołanie `Remove` lub `RemoveAt` metodę, aby usunąć elementy.</span><span class="sxs-lookup"><span data-stu-id="5e70e-115">Call the `Remove` or `RemoveAt` method to delete items.</span></span>  
  
     <span data-ttu-id="5e70e-116">`Remove`ma jeden argument, który określa element do usunięcia.`RemoveAt`</span><span class="sxs-lookup"><span data-stu-id="5e70e-116">`Remove` has one argument that specifies the item to remove.`RemoveAt`</span></span> <span data-ttu-id="5e70e-117">Usuwa element z określonym indeksem.</span><span class="sxs-lookup"><span data-stu-id="5e70e-117">removes the item with the specified index number.</span></span>  
  
    ```vb  
    ' To remove item with index 0:  
    ComboBox1.Items.RemoveAt(0)  
    ' To remove currently selected item:  
    ComboBox1.Items.Remove(ComboBox1.SelectedItem)  
    ' To remove "Tokyo" item:  
    ComboBox1.Items.Remove("Tokyo")  
    ```  
  
    ```csharp  
    // To remove item with index 0:  
    comboBox1.Items.RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1.Items.Remove(comboBox1.SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1.Items.Remove("Tokyo");  
    ```  
  
    ```cpp  
    // To remove item with index 0:  
    comboBox1->Items->RemoveAt(0);  
    // To remove currently selected item:  
    comboBox1->Items->Remove(comboBox1->SelectedItem);  
    // To remove "Tokyo" item:  
    comboBox1->Items->Remove("Tokyo");  
    ```  
  
### <a name="to-remove-all-items"></a><span data-ttu-id="5e70e-118">Aby usunąć wszystkie elementy</span><span class="sxs-lookup"><span data-stu-id="5e70e-118">To remove all items</span></span>  
  
1.  <span data-ttu-id="5e70e-119">Wywołanie `Clear` metodę, aby usunąć wszystkie elementy z kolekcji:</span><span class="sxs-lookup"><span data-stu-id="5e70e-119">Call the `Clear` method to remove all items from the collection:</span></span>  
  
    ```vb  
    ListBox1.Items.Clear()  
    ```  
  
    ```csharp  
    listBox1.Items.Clear();  
    ```  
  
    ```cpp  
    listBox1->Items->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="5e70e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e70e-120">See Also</span></span>  
 <xref:System.Windows.Forms.ComboBox>  
 <xref:System.Windows.Forms.ListBox>  
 <xref:System.Windows.Forms.CheckedListBox>  
 [<span data-ttu-id="5e70e-121">Porady: sortowanie zawartości systemu Windows ComboBox, ListBox lub CheckedListBox formularzy</span><span class="sxs-lookup"><span data-stu-id="5e70e-121">How to: Sort the Contents of a Windows Forms ComboBox, ListBox, or CheckedListBox Control</span></span>](../../../../docs/framework/winforms/controls/sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)  
 [<span data-ttu-id="5e70e-122">Kiedy należy używać formantu ComboBox formularzy systemu Windows zamiast ListBox</span><span class="sxs-lookup"><span data-stu-id="5e70e-122">When to Use a Windows Forms ComboBox Instead of a ListBox</span></span>](../../../../docs/framework/winforms/controls/when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)  
 [<span data-ttu-id="5e70e-123">Formanty używane do obsługi opcji List formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="5e70e-123">Windows Forms Controls Used to List Options</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)