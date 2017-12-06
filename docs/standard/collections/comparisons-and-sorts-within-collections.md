---
title: "Porównywanie i sortowanie w kolekcjach"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET Framework], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bb7092a2eae8d950f3709ea4fde63f6c7d5b32b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="comparisons-and-sorts-within-collections"></a><span data-ttu-id="085ff-102">Porównywanie i sortowanie w kolekcjach</span><span class="sxs-lookup"><span data-stu-id="085ff-102">Comparisons and Sorts Within Collections</span></span>
<span data-ttu-id="085ff-103"><xref:System.Collections> Klasy wykonywać porównania w niemal wszystkich procesów Zarządzanie kolekcjami, czy wyszukiwanie elementu do usunięcia lub zwrócenie wartości parę klucza i wartości.</span><span class="sxs-lookup"><span data-stu-id="085ff-103">The <xref:System.Collections> classes perform comparisons in almost all the processes involved in managing collections, whether searching for the element to remove or returning the value of a key-and-value pair.</span></span>  
  
 <span data-ttu-id="085ff-104">Kolekcje wykorzystywać zwykle porównania równości i/lub porównania porządkowania.</span><span class="sxs-lookup"><span data-stu-id="085ff-104">Collections typically utilize an equality comparer and/or an ordering comparer.</span></span> <span data-ttu-id="085ff-105">Konstrukcje dwóch służą do porównania.</span><span class="sxs-lookup"><span data-stu-id="085ff-105">Two constructs are used for comparisons.</span></span>  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a><span data-ttu-id="085ff-106">Sprawdzanie pod kątem równości</span><span class="sxs-lookup"><span data-stu-id="085ff-106">Checking for equality</span></span>  
 <span data-ttu-id="085ff-107">Metody, takie jak `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, i `Remove` Użyj porównania równości dla elementów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="085ff-107">Methods such as `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, and `Remove` use an equality comparer for the collection elements.</span></span> <span data-ttu-id="085ff-108">Jeśli kolekcja jest ogólny, niż elementy są porównywane pod kątem równości, zgodnie z poniższymi wytycznymi:</span><span class="sxs-lookup"><span data-stu-id="085ff-108">If the collection is generic, than items are compared for equality according to the following guidelines:</span></span>  
  
-   <span data-ttu-id="085ff-109">Jeśli implementuje typu T <xref:System.IEquatable%601> jest ogólny interfejs, a następnie porównania równości <xref:System.IEquatable%601.Equals%2A> metody tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="085ff-109">If type T implements the <xref:System.IEquatable%601> generic interface, then the equality comparer is the <xref:System.IEquatable%601.Equals%2A> method of that interface.</span></span>  
  
-   <span data-ttu-id="085ff-110">Jeśli typ T nie implementuje <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> jest używany.</span><span class="sxs-lookup"><span data-stu-id="085ff-110">If type T does not implement <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> is used.</span></span>  
  
 <span data-ttu-id="085ff-111">Ponadto niektóre przeładowania konstruktora dla kolekcji słownika zaakceptować <xref:System.Collections.Generic.IEqualityComparer%601> wdrożenia, który służy do porównywania klucze pod kątem równości.</span><span class="sxs-lookup"><span data-stu-id="085ff-111">In addition, Some constructor overloads for dictionary collections accept an <xref:System.Collections.Generic.IEqualityComparer%601> implementation, which is used to compare keys for equality.</span></span> <span data-ttu-id="085ff-112">Na przykład zobacz <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> konstruktora.</span><span class="sxs-lookup"><span data-stu-id="085ff-112">For an example, see the <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> constructor.</span></span>  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a><span data-ttu-id="085ff-113">Określanie kolejności sortowania</span><span class="sxs-lookup"><span data-stu-id="085ff-113">Determining sort order</span></span>  
 <span data-ttu-id="085ff-114">Metody, takie jak `BinarySearch` i `Sort` Użyj porównania porządkowania elementów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="085ff-114">Methods such as `BinarySearch` and `Sort` use an ordering comparer for the collection elements.</span></span> <span data-ttu-id="085ff-115">Porównanie może być między elementy kolekcji lub elementu i określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="085ff-115">The comparisons can be between elements of the collection, or between an element and a specified value.</span></span> <span data-ttu-id="085ff-116">Porównanie obiektów, istnieje pojęcie `default comparer` i `explicit comparer`.</span><span class="sxs-lookup"><span data-stu-id="085ff-116">For comparing objects, there is the concept of a `default comparer` and an `explicit comparer`.</span></span>  
  
 <span data-ttu-id="085ff-117">Domyślna funkcja porównująca opiera się na co najmniej jeden z obiektów są porównywane w celu zaimplementowania **IComparable** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="085ff-117">The default comparer relies on at least one of the objects being compared to implement the **IComparable** interface.</span></span> <span data-ttu-id="085ff-118">Dobrym rozwiązaniem do zaimplementowania jest **IComparable** na wszystkie klasy są używane jako wartości w kolekcji list lub kluczy w słowniku kolekcji.</span><span class="sxs-lookup"><span data-stu-id="085ff-118">It is a good practice to implement **IComparable** on all classes are used as values in a list collection or as keys in a dictionary collection.</span></span> <span data-ttu-id="085ff-119">Do kolekcji uniwersalnej porównania równości określa się zgodnie z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="085ff-119">For a generic collection, equality comparison is determined according to the following:</span></span>  
  
-   <span data-ttu-id="085ff-120">Jeśli implementuje typu T <xref:System.IComparable%601?displayProperty=nameWithType> jest ogólny interfejs, a następnie domyślna funkcja porównująca <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> metody interfejsu</span><span class="sxs-lookup"><span data-stu-id="085ff-120">If type T implements the <xref:System.IComparable%601?displayProperty=nameWithType> generic interface, then the default comparer is the <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> method of that interface</span></span>  
  
-   <span data-ttu-id="085ff-121">Jeśli typ T implementuje nieogólnego <xref:System.IComparable?displayProperty=nameWithType> interfejsu, a następnie jest domyślna funkcja porównująca <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> metody tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="085ff-121">If type T implements the non-generic <xref:System.IComparable?displayProperty=nameWithType> interface, then the default comparer is the <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> method of that interface.</span></span>  
  
-   <span data-ttu-id="085ff-122">Jeśli typ T nie implementuje interfejsu albo, to nie ma żadnych domyślna funkcja porównująca i podać jawnie delegata porównania lub porównania.</span><span class="sxs-lookup"><span data-stu-id="085ff-122">If type T doesn’t implement either interface, then there is no default comparer, and a comparer or comparison delegate must be provided explicitly.</span></span>  
  
 <span data-ttu-id="085ff-123">Aby podać jawne porównań, Zaakceptuj niektóre metody **IComparer** implementacji jako parametr.</span><span class="sxs-lookup"><span data-stu-id="085ff-123">To provide explicit comparisons, some methods accept an **IComparer** implementation as a parameter.</span></span> <span data-ttu-id="085ff-124">Na przykład <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metoda przyjmuje <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementacji.</span><span class="sxs-lookup"><span data-stu-id="085ff-124">For example, the <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> method accepts an <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementation.</span></span>  
  
 <span data-ttu-id="085ff-125">Bieżące ustawienia kulturowe systemu może mieć wpływ na porównywanie i sortowanie w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="085ff-125">The current culture setting of the system can affect the comparisons and sorts within a collection.</span></span> <span data-ttu-id="085ff-126">Domyślnie porównywanie i sortowanie w **kolekcje** klasy są zależne od kultury.</span><span class="sxs-lookup"><span data-stu-id="085ff-126">By default, the comparisons and sorts in the **Collections** classes are culture-sensitive.</span></span> <span data-ttu-id="085ff-127">Ignoruj ustawienia kulturowe i w związku z tym uzyskanie spójnej porównywanie i sortowanie wyników, należy użyć <xref:System.Globalization.CultureInfo.InvariantCulture%2A> z przeciążeń elementu członkowskiego, które akceptują <xref:System.Globalization.CultureInfo>.</span><span class="sxs-lookup"><span data-stu-id="085ff-127">To ignore the culture setting and therefore obtain consistent comparison and sorting results, use the <xref:System.Globalization.CultureInfo.InvariantCulture%2A> with member overloads that accept a <xref:System.Globalization.CultureInfo>.</span></span> <span data-ttu-id="085ff-128">Aby uzyskać więcej informacji, zobacz [wykonywanie niezależnych od kultury operacje na ciągach w kolekcjach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) i [wykonywanie niezależnych od kultury operacje na ciągach w tablicach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="085ff-128">For more information, see [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) and [Performing Culture-Insensitive String Operations in Arrays](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).</span></span>  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a><span data-ttu-id="085ff-129">Przykład równości i sortowanie</span><span class="sxs-lookup"><span data-stu-id="085ff-129">Equality and sort example</span></span>  
 <span data-ttu-id="085ff-130">Poniższy kod przedstawia implementację <xref:System.IEquatable%601> i <xref:System.IComparable%601> na obiekt biznesowy proste.</span><span class="sxs-lookup"><span data-stu-id="085ff-130">The following code demonstrates an implementation of <xref:System.IEquatable%601> and <xref:System.IComparable%601> on a simple business object.</span></span> <span data-ttu-id="085ff-131">Ponadto, gdy obiekt jest przechowywany w postaci listy i sortowane, zobaczysz tego wywołania <xref:System.Collections.Generic.List%601.Sort> metoda powoduje użycie domyślna funkcja porównująca dla `Part` typu i <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> metody implementowane za pomocą metody anonimowej.</span><span class="sxs-lookup"><span data-stu-id="085ff-131">In addition, when the object is stored in a list and sorted, you will see that calling the <xref:System.Collections.Generic.List%601.Sort> method results in the use of the default comparer for the `Part` type, and the <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> method implemented by using an anonymous method.</span></span>  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="085ff-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="085ff-132">See Also</span></span>  
 <xref:System.Collections.IComparer>  
 <xref:System.IEquatable%601>  
 <xref:System.Collections.Generic.IComparer%601>  
 <xref:System.IComparable>  
 <xref:System.IComparable%601>