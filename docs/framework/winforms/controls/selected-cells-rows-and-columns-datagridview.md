---
title: "Porady: pobieranie wybranych komórek, wierszy i kolumn w formancie DataGridView formularzy systemu Windows"
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
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: aada475af0ccac03dfa6ef9248b0fb07fd86b3ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="ef17a-102">Porady: pobieranie wybranych komórek, wierszy i kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ef17a-102">How to: Get the Selected Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ef17a-103">Można uzyskać zaznaczonych komórek, wierszy i kolumn z <xref:System.Windows.Forms.DataGridView> formantu przy użyciu odpowiednich właściwości: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, i <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef17a-103">You can get the selected cells, rows, or columns from a <xref:System.Windows.Forms.DataGridView> control by using the corresponding properties: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>, <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>, and <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span></span> <span data-ttu-id="ef17a-104">W poniższych procedurach, będzie pobrać zaznaczonych komórek i wyświetlić ich indeksy wierszy i kolumn w <xref:System.Windows.Forms.MessageBox>.</span><span class="sxs-lookup"><span data-stu-id="ef17a-104">In the following procedures, you will get the selected cells and display their row and column indexes in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a><span data-ttu-id="ef17a-105">Aby uzyskać zaznaczonych komórek w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="ef17a-105">To get the selected cells in a DataGridView control</span></span>  
  
-   <span data-ttu-id="ef17a-106">Użyj <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ef17a-106">Use the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> property.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ef17a-107">Użyj <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> metodę, aby uniknąć wyświetlania potencjalnie dużą liczbę komórek.</span><span class="sxs-lookup"><span data-stu-id="ef17a-107">Use the <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> method to avoid showing a potentially large number of cells.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a><span data-ttu-id="ef17a-108">Aby uzyskać wybranych wierszy w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="ef17a-108">To get the selected rows in a DataGridView control</span></span>  
  
-   <span data-ttu-id="ef17a-109">Użyj <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ef17a-109">Use the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> property.</span></span> <span data-ttu-id="ef17a-110">Aby umożliwić użytkownikom wybierz wiersze, musisz ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span><span class="sxs-lookup"><span data-stu-id="ef17a-110">To enable users to select rows, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a><span data-ttu-id="ef17a-111">Aby uzyskać wybranych kolumn w formancie DataGridView</span><span class="sxs-lookup"><span data-stu-id="ef17a-111">To get the selected columns in a DataGridView control</span></span>  
  
-   <span data-ttu-id="ef17a-112">Użyj <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ef17a-112">Use the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> property.</span></span> <span data-ttu-id="ef17a-113">Aby umożliwić użytkownikom zaznaczyć kolumny, należy ustawić <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> właściwości <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> lub <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span><span class="sxs-lookup"><span data-stu-id="ef17a-113">To enable users to select columns, you must set the <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> property to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> or <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ef17a-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ef17a-114">Compiling the Code</span></span>  
 <span data-ttu-id="ef17a-115">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="ef17a-115">This example requires:</span></span>  
  
-   <span data-ttu-id="ef17a-116"><xref:System.Windows.Forms.Button>formanty o nazwie `selectedCellsButton`, `selectedRowsButton`, i `selectedColumnsButton`, każde z nich obsługi <xref:System.Windows.Forms.Control.Click> zdarzeń dołączony.</span><span class="sxs-lookup"><span data-stu-id="ef17a-116"><xref:System.Windows.Forms.Button> controls named `selectedCellsButton`, `selectedRowsButton`, and `selectedColumnsButton`, each with handlers for the <xref:System.Windows.Forms.Control.Click> event attached.</span></span>  
  
-   <span data-ttu-id="ef17a-117">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="ef17a-117">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="ef17a-118">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, i <xref:System.Text?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="ef17a-118">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Text?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ef17a-119">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="ef17a-119">Robust Programming</span></span>  
 <span data-ttu-id="ef17a-120">Kolekcje opisanych w tym temacie należy wykonywać wydajnie, jeśli wybrano dużą liczbę komórek, wierszy lub kolumn.</span><span class="sxs-lookup"><span data-stu-id="ef17a-120">The collections described in this topic do not perform efficiently when large numbers of cells, rows, or columns are selected.</span></span> <span data-ttu-id="ef17a-121">Aby uzyskać więcej informacji o korzystaniu z tych kolekcji z dużych ilości danych, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="ef17a-121">For more information about using these collections with large amounts of data, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef17a-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef17a-122">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>  
 <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>  
 <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>  
 [<span data-ttu-id="ef17a-123">Wybór i używanie Schowka z formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ef17a-123">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)