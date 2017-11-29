---
title: "Porady: ustawianie domyślnych stylów komórki dla formantu DataGridView formularzy systemu Windows"
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
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd55034ee97b6e13da8a8a0bdadb8c191ba16ae2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="1b74a-102">Porady: ustawianie domyślnych stylów komórki dla formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1b74a-102">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1b74a-103">Z <xref:System.Windows.Forms.DataGridView> sterowania, można określić domyślnych stylów komórki dla formantu całego i określonych kolumn i wierszy.</span><span class="sxs-lookup"><span data-stu-id="1b74a-103">With the <xref:System.Windows.Forms.DataGridView> control, you can specify default cell styles for the entire control and for specific columns and rows.</span></span> <span data-ttu-id="1b74a-104">Te ustawienia domyślne filtru w dół z poziomu kontroli na poziomie kolumny, a następnie na poziomie wiersza, a następnie na poziomie komórki.</span><span class="sxs-lookup"><span data-stu-id="1b74a-104">These defaults filter down from the control level to the column level, then to the row level, then to the cell level.</span></span> <span data-ttu-id="1b74a-105">Jeśli danego <xref:System.Windows.Forms.DataGridViewCellStyle> właściwość nie jest ustawiona na poziomie komórki, używane jest domyślne ustawienie właściwości na poziomie wiersza.</span><span class="sxs-lookup"><span data-stu-id="1b74a-105">If a particular <xref:System.Windows.Forms.DataGridViewCellStyle> property is not set at the cell level, the default property setting at the row level is used.</span></span> <span data-ttu-id="1b74a-106">Jeśli właściwość nie jest również ustawiona na poziomie wiersza, używane jest domyślne ustawienie kolumny.</span><span class="sxs-lookup"><span data-stu-id="1b74a-106">If the property is also not set at the row level, the default column setting is used.</span></span> <span data-ttu-id="1b74a-107">Na koniec Jeśli właściwość również nie jest ustawiona na poziomie kolumny, domyślnie <xref:System.Windows.Forms.DataGridView> ustawienie jest używane.</span><span class="sxs-lookup"><span data-stu-id="1b74a-107">Finally, if the property is also not set at the column level, the default <xref:System.Windows.Forms.DataGridView> setting is used.</span></span> <span data-ttu-id="1b74a-108">To ustawienie, można uniknąć konieczności zduplikowane ustawienia właściwości na różnych poziomach.</span><span class="sxs-lookup"><span data-stu-id="1b74a-108">With this setting, you can avoid having to duplicate the property settings at multiple levels.</span></span> <span data-ttu-id="1b74a-109">Na każdym poziomie wystarczy określić style, które różnią się od poziomy wyżej.</span><span class="sxs-lookup"><span data-stu-id="1b74a-109">At each level, simply specify the styles that differ from the levels above it.</span></span> <span data-ttu-id="1b74a-110">Aby uzyskać więcej informacji, zobacz [style komórki w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1b74a-110">For more information, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="1b74a-111">Brak kompleksową obsługę tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1b74a-111">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="1b74a-112">Zobacz też [porady: Ustawianie domyślne style komórek i formatów danych dla systemu Windows Forms DataGridView formantu przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="1b74a-112">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).</span></span>  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a><span data-ttu-id="1b74a-113">Aby ustawić domyślne style komórki programowo</span><span class="sxs-lookup"><span data-stu-id="1b74a-113">To set the default cell styles programmatically</span></span>  
  
1.  <span data-ttu-id="1b74a-114">Ustawianie właściwości <xref:System.Windows.Forms.DataGridViewCellStyle> pobierane w drodze <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b74a-114">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> retrieved through the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2.  <span data-ttu-id="1b74a-115">Utwórz i zainicjuj nowy <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów używanych przez wiele wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="1b74a-115">Create and initialize new <xref:System.Windows.Forms.DataGridViewCellStyle> objects for use by multiple rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3.  <span data-ttu-id="1b74a-116">Ustaw `DefaultCellStyle` właściwości określonych wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="1b74a-116">Set the `DefaultCellStyle` property of specific rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a><span data-ttu-id="1b74a-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b74a-117">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1b74a-118">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1b74a-118">Compiling the Code</span></span>  
 <span data-ttu-id="1b74a-119">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="1b74a-119">This example requires:</span></span>  
  
-   <span data-ttu-id="1b74a-120">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="1b74a-120">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="1b74a-121">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="1b74a-121">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1b74a-122">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="1b74a-122">Robust Programming</span></span>  
 <span data-ttu-id="1b74a-123">Aby osiągnąć maksymalną skalowalność, podczas pracy z bardzo dużych zestawów danych, powinny współużytkować <xref:System.Windows.Forms.DataGridViewCellStyle> obiektów między wiele wierszy, kolumny lub komórki za pomocą tego samego stylów, zamiast ponownego obliczenia właściwości stylu dla poszczególnych elementów osobno.</span><span class="sxs-lookup"><span data-stu-id="1b74a-123">To achieve maximum scalability when you work with very large data sets, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than set the style properties for individual elements separately.</span></span> <span data-ttu-id="1b74a-124">Ponadto należy utworzyć udostępnione wiersze i uzyskiwać do nich dostęp za pomocą <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="1b74a-124">Additionally, you should create shared rows and access them by using the <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="1b74a-125">Aby uzyskać więcej informacji, zobacz [najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="1b74a-125">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b74a-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b74a-126">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="1b74a-127">Podstawowe formatowanie i style w oknach formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="1b74a-127">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1b74a-128">Style komórki w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1b74a-128">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1b74a-129">Najlepsze praktyki dotyczące skalowania formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1b74a-129">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1b74a-130">Porady: Ustawianie przemiennych wierszy dla formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1b74a-130">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)