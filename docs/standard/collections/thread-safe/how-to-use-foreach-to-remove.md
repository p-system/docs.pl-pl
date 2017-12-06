---
title: "Porady: używanie ForEach do usuwanie elementów BlockingCollection"
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
helpviewer_keywords: thread-safe collections, how to enumerate blocking collectoin
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7683e295bd1d898e112a754b06993dabf4483871
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a><span data-ttu-id="ed92f-102">Porady: używanie ForEach do usuwanie elementów BlockingCollection</span><span class="sxs-lookup"><span data-stu-id="ed92f-102">How to: Use ForEach to Remove Items in a BlockingCollection</span></span>
<span data-ttu-id="ed92f-103">Oprócz pobieranie elementów z <xref:System.Collections.Concurrent.BlockingCollection%601> za pomocą <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> i <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metody, można również użyć [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([dla każdego](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) w języku Visual Basic) aby usunąć elementy, dopóki nie zostanie Dodawanie zakończone i kolekcji jest pusty.</span><span class="sxs-lookup"><span data-stu-id="ed92f-103">In addition to taking items from a <xref:System.Collections.Concurrent.BlockingCollection%601> by using the <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> and <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> method, you can also use a [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([For Each](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) in Visual Basic) to remove items until adding is completed and the collection is empty.</span></span> <span data-ttu-id="ed92f-104">Ta metoda jest wywoływana *mutacja wyliczenie* lub *wykorzystywanie wyliczenie* , ponieważ w odróżnieniu od typowych `foreach` (`For Each`) pętli, ten moduł wyliczający modyfikuje kolekcji źródłowej przez usunięcie elementy.</span><span class="sxs-lookup"><span data-stu-id="ed92f-104">This is called a *mutating enumeration* or *consuming enumeration* because, unlike a typical `foreach` (`For Each`) loop, this enumerator modifies the source collection by removing items.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed92f-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="ed92f-105">Example</span></span>  
 <span data-ttu-id="ed92f-106">Poniższy przykład przedstawia sposób usunąć wszystkie elementy w <xref:System.Collections.Concurrent.BlockingCollection%601> za pomocą `foreach` (`For Each`) pętli.</span><span class="sxs-lookup"><span data-stu-id="ed92f-106">The following example shows how to remove all the items in a <xref:System.Collections.Concurrent.BlockingCollection%601> by using a `foreach` (`For Each`) loop.</span></span>  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 <span data-ttu-id="ed92f-107">W tym przykładzie użyto `foreach` pętli z <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> metoda odbierającą wątku, co powoduje, że każdy element, aby usunąć z kolekcji, ponieważ jest on wyliczone.</span><span class="sxs-lookup"><span data-stu-id="ed92f-107">This example uses a `foreach` loop with the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> method in the consuming thread, which causes each item to be removed from the collection as it is enumerated.</span></span> <span data-ttu-id="ed92f-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>Ogranicza maksymalną liczbę elementów znajdujących się w kolekcji w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="ed92f-108"><xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> limits the maximum number of items that are in the collection at any time.</span></span> <span data-ttu-id="ed92f-109">Wyliczanie kolekcji w ten sposób blokuje wątku konsumenta, jeśli brak dostępnych elementów lub jeśli kolekcja jest pusta.</span><span class="sxs-lookup"><span data-stu-id="ed92f-109">Enumerating the collection in this way blocks the consumer thread if no items are available or if the collection is empty.</span></span> <span data-ttu-id="ed92f-110">W tym przykładzie blokuje nie ma znaczenia, ponieważ wątek producent dodaje elementy szybciej niż mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="ed92f-110">In this example blocking is not a concern because the producer thread adds items faster than they can be consumed.</span></span>  
  
 <span data-ttu-id="ed92f-111">Nie ma żadnej gwarancji, że elementy są wyliczane w tej samej kolejności, w której są dodawane przez wątki producenta.</span><span class="sxs-lookup"><span data-stu-id="ed92f-111">There is no guarantee that the items are enumerated in the same order in which they are added by the producer threads.</span></span>  
  
 <span data-ttu-id="ed92f-112">Aby wyliczyć kolekcji bez modyfikowania jej, wystarczy użyć `foreach` (`For Each`) bez <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="ed92f-112">To enumerate the collection without modifying it, just use `foreach` (`For Each`) without the <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> method.</span></span> <span data-ttu-id="ed92f-113">Jednak ważne jest zrozumienie, że tego rodzaju wyliczenie reprezentuje migawki kolekcji w określonym punkcie w czasie.</span><span class="sxs-lookup"><span data-stu-id="ed92f-113">However, it is important to understand that this kind of enumeration represents a snapshot of the collection at a precise point in time.</span></span> <span data-ttu-id="ed92f-114">Jeśli inne wątki dodawania lub usuwania elementów współbieżnie, podczas wykonywania pętli, pętla może reprezentuje rzeczywisty stan kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ed92f-114">If other threads are adding or removing items concurrently while you are executing the loop, then the loop might not represent the actual state of the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed92f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed92f-115">See Also</span></span>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [<span data-ttu-id="ed92f-116">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="ed92f-116">Parallel Programming</span></span>](../../../../docs/standard/parallel-programming/index.md)