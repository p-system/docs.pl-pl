---
title: "LINQ do SQL zapytań"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a080dd13f4e9950c9e65b8031ffc77ddf18eaf9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-sql-queries"></a><span data-ttu-id="8e086-102">LINQ do SQL zapytań</span><span class="sxs-lookup"><span data-stu-id="8e086-102">LINQ to SQL Queries</span></span>
<span data-ttu-id="8e086-103">Należy zdefiniować [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania przy użyciu takiej samej składni jak [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8e086-103">You define [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] queries by using the same syntax as you would in [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].</span></span> <span data-ttu-id="8e086-104">Jedyna różnica polega na tym, że obiekty odwołuje się do zapytania są mapowane do elementów w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="8e086-104">The only difference is that the objects referenced in your queries are mapped to elements in a database.</span></span> <span data-ttu-id="8e086-105">Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span><span class="sxs-lookup"><span data-stu-id="8e086-105">For more information, see [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).</span></span>  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8e086-106">tłumaczy zapytania zostanie zapisany na równoważne zapytania SQL, a następnie wysyła je do serwera w celu przetworzenia.</span><span class="sxs-lookup"><span data-stu-id="8e086-106"> translates the queries you write into equivalent SQL queries and sends them to the server for processing.</span></span> <span data-ttu-id="8e086-107">W szczególności, aplikacja używa [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] interfejsu API do wykonywania zapytania żądania.</span><span class="sxs-lookup"><span data-stu-id="8e086-107">More specifically, your application uses the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API to request query execution.</span></span> <span data-ttu-id="8e086-108">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Dostawcy następnie przekształca zapytania w tekstu SQL i deleguje do dostawcy ADO wykonania.</span><span class="sxs-lookup"><span data-stu-id="8e086-108">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provider then transforms the query into SQL text and delegates execution to the ADO provider.</span></span> <span data-ttu-id="8e086-109">Dostawca ADO zwraca wyniki zapytania jako `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="8e086-109">The ADO provider returns query results as a `DataReader`.</span></span> <span data-ttu-id="8e086-110">[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Dostawca tłumaczy wyniki ADO w <xref:System.Linq.IQueryable> kolekcji obiektów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8e086-110">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] provider translates the ADO results to an <xref:System.Linq.IQueryable> collection of user objects.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e086-111">Większość metod i operatory w [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] typy wbudowane mieć tłumaczeń bezpośrednio do bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="8e086-111">Most methods and operators on [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] built-in types have direct translations to SQL.</span></span> <span data-ttu-id="8e086-112">Te, które [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] nie może dokonywać translacji Generowanie wyjątki czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="8e086-112">Those that [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] cannot translate generate run-time exceptions.</span></span> <span data-ttu-id="8e086-113">Aby uzyskać więcej informacji, zobacz [mapowanie typu środowiska CLR SQL](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span><span class="sxs-lookup"><span data-stu-id="8e086-113">For more information, see [SQL-CLR Type Mapping](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).</span></span>  
  
 <span data-ttu-id="8e086-114">W poniższej tabeli przedstawiono podobieństwa i różnice między [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] zapytania elementów.</span><span class="sxs-lookup"><span data-stu-id="8e086-114">The following table shows the similarities and differences between [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] and [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] query items.</span></span>  
  
|<span data-ttu-id="8e086-115">Element</span><span class="sxs-lookup"><span data-stu-id="8e086-115">Item</span></span>|<span data-ttu-id="8e086-116">Zapytania LINQ</span><span class="sxs-lookup"><span data-stu-id="8e086-116">LINQ Query</span></span>|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8e086-117">Zapytania</span><span class="sxs-lookup"><span data-stu-id="8e086-117"> Query</span></span>|  
|----------|----------------|----------------------------------------------------------------------|  
|<span data-ttu-id="8e086-118">Zwracany typ zmiennej lokalnej, która przechowuje zapytania (w przypadku zapytań, które zwracają sekwencji)</span><span class="sxs-lookup"><span data-stu-id="8e086-118">Return type of the local variable that holds the query (for queries that return sequences)</span></span>|<span data-ttu-id="8e086-119">Ogólny`IEnumerable`</span><span class="sxs-lookup"><span data-stu-id="8e086-119">Generic `IEnumerable`</span></span>|<span data-ttu-id="8e086-120">Ogólny`IQueryable`</span><span class="sxs-lookup"><span data-stu-id="8e086-120">Generic `IQueryable`</span></span>|  
|<span data-ttu-id="8e086-121">Określanie źródła danych</span><span class="sxs-lookup"><span data-stu-id="8e086-121">Specifying the data source</span></span>|<span data-ttu-id="8e086-122">Używa `From` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) lub `from` — klauzula (C#)</span><span class="sxs-lookup"><span data-stu-id="8e086-122">Uses the `From` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) or `from` (C#) clause</span></span>|<span data-ttu-id="8e086-123">tym samym</span><span class="sxs-lookup"><span data-stu-id="8e086-123">Same</span></span>|  
|<span data-ttu-id="8e086-124">Filtrowanie</span><span class="sxs-lookup"><span data-stu-id="8e086-124">Filtering</span></span>|<span data-ttu-id="8e086-125">Używa `Where` / `where` — klauzula</span><span class="sxs-lookup"><span data-stu-id="8e086-125">Uses the `Where`/`where` clause</span></span>|<span data-ttu-id="8e086-126">tym samym</span><span class="sxs-lookup"><span data-stu-id="8e086-126">Same</span></span>|  
|<span data-ttu-id="8e086-127">Grupowanie</span><span class="sxs-lookup"><span data-stu-id="8e086-127">Grouping</span></span>|<span data-ttu-id="8e086-128">Używa `Group…By` / `groupby` — klauzula</span><span class="sxs-lookup"><span data-stu-id="8e086-128">Uses the `Group…By`/`groupby` clause</span></span>|<span data-ttu-id="8e086-129">tym samym</span><span class="sxs-lookup"><span data-stu-id="8e086-129">Same</span></span>|  
|<span data-ttu-id="8e086-130">Wybieranie (projekcji)</span><span class="sxs-lookup"><span data-stu-id="8e086-130">Selecting (Projecting)</span></span>|<span data-ttu-id="8e086-131">Używa `Select` / `select` — klauzula</span><span class="sxs-lookup"><span data-stu-id="8e086-131">Uses the `Select`/`select` clause</span></span>|<span data-ttu-id="8e086-132">tym samym</span><span class="sxs-lookup"><span data-stu-id="8e086-132">Same</span></span>|  
|<span data-ttu-id="8e086-133">Odroczone i natychmiastowego wykonania</span><span class="sxs-lookup"><span data-stu-id="8e086-133">Deferred versus immediate execution</span></span>|<span data-ttu-id="8e086-134">Zobacz [wprowadzenie do kwerend LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)</span><span class="sxs-lookup"><span data-stu-id="8e086-134">See [Introduction to LINQ Queries (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)</span></span>|<span data-ttu-id="8e086-135">tym samym</span><span class="sxs-lookup"><span data-stu-id="8e086-135">Same</span></span>|  
|<span data-ttu-id="8e086-136">Implementowanie sprzężeń</span><span class="sxs-lookup"><span data-stu-id="8e086-136">Implementing joins</span></span>|<span data-ttu-id="8e086-137">Używa `Join` / `join` — klauzula</span><span class="sxs-lookup"><span data-stu-id="8e086-137">Uses the `Join`/`join` clause</span></span>|<span data-ttu-id="8e086-138">Można użyć `Join` / `join` klauzuli, ale efektywniej używa <xref:System.Data.Linq.Mapping.AssociationAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8e086-138">Can use the `Join`/`join` clause, but more effectively uses the <xref:System.Data.Linq.Mapping.AssociationAttribute> attribute.</span></span> <span data-ttu-id="8e086-139">Aby uzyskać więcej informacji, zobacz [zapytań w relacji](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).</span><span class="sxs-lookup"><span data-stu-id="8e086-139">For more information, see [Querying Across Relationships](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).</span></span>|  
|<span data-ttu-id="8e086-140">Zdalne i wykonanie lokalne</span><span class="sxs-lookup"><span data-stu-id="8e086-140">Remote versus local execution</span></span>||<span data-ttu-id="8e086-141">Aby uzyskać więcej informacji, zobacz [zdalnego programu vs. Wykonanie lokalne](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md).</span><span class="sxs-lookup"><span data-stu-id="8e086-141">For more information, see [Remote vs. Local Execution](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md).</span></span>|  
|<span data-ttu-id="8e086-142">Przesyłanie strumieniowe i kwerendy w pamięci podręcznej</span><span class="sxs-lookup"><span data-stu-id="8e086-142">Streaming versus cached querying</span></span>|<span data-ttu-id="8e086-143">Nie ma zastosowania w przypadku scenariusza pamięci lokalnej</span><span class="sxs-lookup"><span data-stu-id="8e086-143">Not applicable in a local memory scenario</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="8e086-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e086-144">See Also</span></span>  
 [<span data-ttu-id="8e086-145">Wprowadzenie do kwerend LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="8e086-145">Introduction to LINQ Queries (C#)</span></span>](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 [<span data-ttu-id="8e086-146">Podstawowe operacje zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="8e086-146">Basic LINQ Query Operations</span></span>](~/docs/csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)  
 [<span data-ttu-id="8e086-147">Relacje typu w operacjach zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="8e086-147">Type Relationships in LINQ Query Operations</span></span>](~/docs/csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)  
 [<span data-ttu-id="8e086-148">Pojęcia dotyczące zapytań</span><span class="sxs-lookup"><span data-stu-id="8e086-148">Query Concepts</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)