---
title: "Tryby wyświetlania danych w formancie DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], display modes
- data grids [Windows Forms], display modes
- DataGridView control [Windows Forms], display modes
ms.assetid: 9755a030-3f3f-4705-a661-ba5a48a81875
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dc7fd3d3012053d8c40edf5fdce8af45c62c98c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="data-display-modes-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f9884-102">Tryby wyświetlania danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f9884-102">Data Display Modes in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f9884-103"><xref:System.Windows.Forms.DataGridView> Formant może wyświetlać dane w trzech różnych trybach: powiązane, niezwiązanej i wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="f9884-103">The <xref:System.Windows.Forms.DataGridView> control can display data in three distinct modes: bound, unbound, and virtual.</span></span> <span data-ttu-id="f9884-104">Wybierz najbardziej odpowiedniego tryb, w zależności od wymagań.</span><span class="sxs-lookup"><span data-stu-id="f9884-104">Choose the most suitable mode based on your requirements.</span></span>  
  
## <a name="unbound"></a><span data-ttu-id="f9884-105">Anulowano powiązania</span><span class="sxs-lookup"><span data-stu-id="f9884-105">Unbound</span></span>  
 <span data-ttu-id="f9884-106">Tryb niepowiązany nadaje się do wyświetlania względnie niewielkich ilości danych, które można programowo zarządzać.</span><span class="sxs-lookup"><span data-stu-id="f9884-106">Unbound mode is suitable for displaying relatively small amounts of data that you manage programmatically.</span></span> <span data-ttu-id="f9884-107">Nie dołączaj <xref:System.Windows.Forms.DataGridView> kontroli bezpośrednio ze źródłem danych w trybie powiązane.</span><span class="sxs-lookup"><span data-stu-id="f9884-107">You do not attach the <xref:System.Windows.Forms.DataGridView> control directly to a data source as in bound mode.</span></span> <span data-ttu-id="f9884-108">Zamiast tego możesz musi wypełnić kontrolki samodzielnie, zwykle za pomocą <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="f9884-108">Instead, you must populate the control yourself, typically by using the <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="f9884-109">Tryb niepowiązany może być szczególnie przydatne dla danych statycznych, tylko do odczytu, lub gdy chcesz zapewnić swoim własnym kodem, który współdziała z magazynem danych zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="f9884-109">Unbound mode can be particularly useful for static, read-only data, or when you want to provide your own code that interacts with an external data store.</span></span> <span data-ttu-id="f9884-110">Użytkownikom na interakcję z zewnętrznego źródła danych, należy jednak zwykle użyjesz trybu powiązania.</span><span class="sxs-lookup"><span data-stu-id="f9884-110">When you want your users to interact with an external data source, however, you will typically use bound mode.</span></span>  
  
 <span data-ttu-id="f9884-111">Na przykład, który używa tylko do odczytu niepowiązane <xref:System.Windows.Forms.DataGridView>, zobacz [jak: utworzyć niezwiązanego formantu DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f9884-111">For an example that uses a read-only unbound <xref:System.Windows.Forms.DataGridView>, see [How to: Create an Unbound Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="bound"></a><span data-ttu-id="f9884-112">Powiązany</span><span class="sxs-lookup"><span data-stu-id="f9884-112">Bound</span></span>  
 <span data-ttu-id="f9884-113">Tryb powiązanej nadaje się do zarządzania danych przy użyciu automatycznego interakcji z magazynem danych.</span><span class="sxs-lookup"><span data-stu-id="f9884-113">Bound mode is suitable for managing data using automatic interaction with the data store.</span></span> <span data-ttu-id="f9884-114">Możesz dołączyć <xref:System.Windows.Forms.DataGridView> kontroli bezpośrednio do źródła danych przez ustawienie <xref:System.Windows.Forms.DataGridView.DataSource%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f9884-114">You can attach the <xref:System.Windows.Forms.DataGridView> control directly to its data source by setting the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span> <span data-ttu-id="f9884-115">Kontrolka jest powiązana z danymi, wiersze danych są wypychana i pobierane bez konieczności jawnego zarządzania ze strony użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f9884-115">When the control is data bound, data rows are pushed and pulled without the need of explicit management on your part.</span></span> <span data-ttu-id="f9884-116">Gdy <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> właściwość jest `true`, każdej kolumny w źródle danych spowoduje przerwanie odpowiadającej mu kolumny, która ma zostać utworzony w formancie.</span><span class="sxs-lookup"><span data-stu-id="f9884-116">When the <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> property is `true`, each column in your data source will cause a corresponding column to be created in the control.</span></span> <span data-ttu-id="f9884-117">Jeśli wolisz utworzyć własne kolumny tę właściwość można ustawić `false` i użyj <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> właściwości do powiązania każdej kolumny, gdy jest skonfigurowany.</span><span class="sxs-lookup"><span data-stu-id="f9884-117">If you prefer to create your own columns, you can set this property to `false` and use the <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A> property to bind each column when you configure it.</span></span> <span data-ttu-id="f9884-118">Jest to przydatne, jeśli chcesz użyć kolumny typu innego niż typów, generowanych przez domyślny.</span><span class="sxs-lookup"><span data-stu-id="f9884-118">This is useful when you want to use a column type other than the types that are generated by default.</span></span> <span data-ttu-id="f9884-119">Aby uzyskać więcej informacji, zobacz [typy kolumn w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f9884-119">For more information, see [Column Types in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="f9884-120">Na przykład, który używa powiązanej <xref:System.Windows.Forms.DataGridView> sterowania, zobacz [wskazówki: Sprawdzanie poprawności danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f9884-120">For an example that uses a bound <xref:System.Windows.Forms.DataGridView> control, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="f9884-121">Możesz także dodać niepowiązanych kolumn do <xref:System.Windows.Forms.DataGridView> formant w trybie powiązania.</span><span class="sxs-lookup"><span data-stu-id="f9884-121">You can also add unbound columns to a <xref:System.Windows.Forms.DataGridView> control in bound mode.</span></span> <span data-ttu-id="f9884-122">Jest to przydatne, jeśli chcesz wyświetlić kolumnę przyciski lub linki, które użytkownicy mogą wykonywać działania na określonych wierszy.</span><span class="sxs-lookup"><span data-stu-id="f9884-122">This is useful when you want to display a column of buttons or links that enable users to perform actions on specific rows.</span></span> <span data-ttu-id="f9884-123">Warto również wyświetlenie kolumn z wartościami obliczana na podstawie powiązane kolumny.</span><span class="sxs-lookup"><span data-stu-id="f9884-123">It is also useful to display columns with values calculated from bound columns.</span></span> <span data-ttu-id="f9884-124">Można go wypełnić wartości komórek w kolumnach obliczeniowych w procedurze obsługi dla <xref:System.Windows.Forms.DataGridView.CellFormatting> zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="f9884-124">You can populate the cell values for calculated columns in a handler for the <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span> <span data-ttu-id="f9884-125">Jeśli używasz <xref:System.Data.DataSet> lub <xref:System.Data.DataTable> jako źródło danych, jednak warto użyć <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType> właściwość, aby zamiast tego utworzyć kolumnę obliczeniową.</span><span class="sxs-lookup"><span data-stu-id="f9884-125">If you are using a <xref:System.Data.DataSet> or <xref:System.Data.DataTable> as the data source, however, you might want to use the <xref:System.Data.DataColumn.Expression%2A?displayProperty=nameWithType> property to create a calculated column instead.</span></span> <span data-ttu-id="f9884-126">W takim przypadku <xref:System.Windows.Forms.DataGridView> formant będzie traktować kolumny obliczeniowej, podobnie jak inne kolumny w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="f9884-126">In this case, the <xref:System.Windows.Forms.DataGridView> control will treat calculated column just like any other column in the data source.</span></span>  
  
 <span data-ttu-id="f9884-127">Sortowanie według niepowiązanych kolumn w trybie powiązania nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="f9884-127">Sorting by unbound columns in bound mode is not supported.</span></span> <span data-ttu-id="f9884-128">Jeśli tworzysz niepowiązanych kolumn w trybie powiązania, który zawiera wartości można edytować użytkownika, musi implementować trybu wirtualnego do obsługi tych wartości, gdy formant jest sortowana według powiązane kolumny.</span><span class="sxs-lookup"><span data-stu-id="f9884-128">If you create an unbound column in bound mode that contains user-editable values, you must implement virtual mode to maintain these values when the control is sorted by a bound column.</span></span>  
  
## <a name="virtual"></a><span data-ttu-id="f9884-129">Wirtualny</span><span class="sxs-lookup"><span data-stu-id="f9884-129">Virtual</span></span>  
 <span data-ttu-id="f9884-130">Tryb wirtualny można zaimplementować własne operacje zarządzania danych.</span><span class="sxs-lookup"><span data-stu-id="f9884-130">With virtual mode, you can implement your own data management operations.</span></span> <span data-ttu-id="f9884-131">Jest to konieczne do zachowania wartości niepowiązanych kolumn w trybie powiązane, gdy formant jest sortowana według powiązane kolumny.</span><span class="sxs-lookup"><span data-stu-id="f9884-131">This is necessary to maintain the values of unbound columns in bound mode when the control is sorted by bound columns.</span></span> <span data-ttu-id="f9884-132">Podstawowym zastosowaniem trybie wirtualnym, jest jednak aby zoptymalizować wydajność podczas interakcji z dużych ilości danych.</span><span class="sxs-lookup"><span data-stu-id="f9884-132">The primary use of virtual mode, however, is to optimize performance when interacting with large amounts of data.</span></span>  
  
 <span data-ttu-id="f9884-133">Możesz dołączyć <xref:System.Windows.Forms.DataGridView> kontroli do pamięci podręcznej, którą zarządzasz i formantów kodu podczas wypychana i pobierane wiersze danych.</span><span class="sxs-lookup"><span data-stu-id="f9884-133">You attach the <xref:System.Windows.Forms.DataGridView> control to a cache that you manage, and your code controls when data rows are pushed and pulled.</span></span> <span data-ttu-id="f9884-134">Aby zachować zużycie pamięci jest mała, pamięci podręcznej powinien być podobny rozmiar liczba aktualnie wyświetlanych wierszy.</span><span class="sxs-lookup"><span data-stu-id="f9884-134">To keep the memory footprint small, the cache should be similar in size to the number of rows currently displayed.</span></span> <span data-ttu-id="f9884-135">Gdy użytkownik przewija nowych wierszy w widoku, kod żądania nowych danych z pamięci podręcznej i opcjonalnie opróżnia stare dane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="f9884-135">When the user scrolls new rows into view, your code requests new data from the cache and optionally flushes old data from memory.</span></span>  
  
 <span data-ttu-id="f9884-136">Są Implementowanie trybu wirtualnego, należy sprawdzić, kiedy nowy wiersz nie jest konieczna w modelu danych, a podczas wycofywania dodanie nowego wiersza.</span><span class="sxs-lookup"><span data-stu-id="f9884-136">When you are implementing virtual mode, you will need to track when a new row is needed in the data model and when to rollback the addition of the new row.</span></span> <span data-ttu-id="f9884-137">Dokładne stosowania tej funkcji zależy od implementacji modelu danych i semantyki transakcji modelu danych; Określa, czy zakres zatwierdzania jest na poziomie komórki lub wiersza.</span><span class="sxs-lookup"><span data-stu-id="f9884-137">The exact implementation of this functionality will depend on the implementation of the data model and the transaction semantics of the data model; whether commit scope is at the cell or row level.</span></span>  
  
 <span data-ttu-id="f9884-138">Aby uzyskać więcej informacji o trybie wirtualnym, zobacz [tryb wirtualny w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f9884-138">For more information about virtual mode, see [Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="f9884-139">Aby uzyskać przykład przedstawia sposób użycia zdarzeń w trybie wirtualnym, zobacz [wskazówki: Implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f9884-139">For an example that shows how to use virtual mode events, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9884-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9884-140">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="f9884-141">Wyświetlanie danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f9884-141">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f9884-142">Typy kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f9884-142">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f9884-143">Wskazówki: Tworzenie formantu DataGridView formularzy Windows niepowiązanych</span><span class="sxs-lookup"><span data-stu-id="f9884-143">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f9884-144">Porady: wiązanie danych formularzy systemu Windows formantu DataGridView</span><span class="sxs-lookup"><span data-stu-id="f9884-144">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f9884-145">Tryb wirtualny w systemie Windows do formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="f9884-145">Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="f9884-146">Wskazówki: Implementowanie trybu wirtualnego w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="f9884-146">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)