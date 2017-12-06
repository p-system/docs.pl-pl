---
title: "Relacje typu w operacjach zapytań LINQ (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- inferring type information [LINQ in C#]
- data sources [LINQ in C#], type relationships
- queries [LINQ in C#], type relationships
- relationships [LINQ in C#]
- type relationships [LINQ in C#]
- variable relationships [LINQ in C#]
- type information inferred [LINQ in C#]
- data transformations [LINQ in C#]
- LINQ [C#], type relationships
ms.assetid: 99118938-d47c-4d7e-bb22-2657a9f95268
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a088a7f673a9f6aea7a0f50e18746259171bb7e2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="type-relationships-in-linq-query-operations-c"></a><span data-ttu-id="15f81-102">Relacje typu w operacjach zapytań LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="15f81-102">Type Relationships in LINQ Query Operations (C#)</span></span>
<span data-ttu-id="15f81-103">Skutecznie pisać zapytania, należy zrozumieć, jak typy zmiennych w operacji zapytania ukończone wszystkie powiązane ze sobą relacjami.</span><span class="sxs-lookup"><span data-stu-id="15f81-103">To write queries effectively, you should understand how types of the variables in a complete query operation all relate to each other.</span></span> <span data-ttu-id="15f81-104">Jeśli znasz te relacje będzie łatwo pojmować [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] przykłady i przykładów kodu w dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="15f81-104">If you understand these relationships you will more easily comprehend the [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] samples and code examples in the documentation.</span></span> <span data-ttu-id="15f81-105">Ponadto będzie zrozumiałe, występujące w tle podczas wpisywania niejawnie za pomocą zmiennych `var`.</span><span class="sxs-lookup"><span data-stu-id="15f81-105">Furthermore, you will understand what occurs behind the scenes when variables are implicitly typed by using `var`.</span></span>  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="15f81-106">Operacje kwerend są silnie typizowane w źródle danych, samą kwerendę i do wykonywania zapytania.</span><span class="sxs-lookup"><span data-stu-id="15f81-106"> query operations are strongly typed in the data source, in the query itself, and in the query execution.</span></span> <span data-ttu-id="15f81-107">Typ zmiennych w kwerendzie musi być zgodny z typem elementów w źródle danych i typ zmiennej iteracji w `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="15f81-107">The type of the variables in the query must be compatible with the type of the elements in the data source and with the type of the iteration variable in the `foreach` statement.</span></span> <span data-ttu-id="15f81-108">Silne wpisywanie gwarantuje, że typ błędy są przechwytywane w czasie kompilacji podczas ich może zostać poprawione przed ich napotkaniu.</span><span class="sxs-lookup"><span data-stu-id="15f81-108">This strong typing guarantees that type errors are caught at compile time when they can be corrected before users encounter them.</span></span>  
  
 <span data-ttu-id="15f81-109">W celu zaprezentowania relacje tych typów, większość przykładów, które należy wykonać Użyj jawnego wpisanie wszystkich zmiennych.</span><span class="sxs-lookup"><span data-stu-id="15f81-109">In order to demonstrate these type relationships, most of the examples that follow use explicit typing for all variables.</span></span> <span data-ttu-id="15f81-110">Ostatni przykładzie pokazano, jak te same zasady stosowane, nawet jeśli używasz wpisanie niejawna przy użyciu [var](../../../../csharp/language-reference/keywords/var.md).</span><span class="sxs-lookup"><span data-stu-id="15f81-110">The last example shows how the same principles apply even when you use implicit typing by using [var](../../../../csharp/language-reference/keywords/var.md).</span></span>  
  
## <a name="queries-that-do-not-transform-the-source-data"></a><span data-ttu-id="15f81-111">Zapytania, które nie przetwarzają dane źródłowe</span><span class="sxs-lookup"><span data-stu-id="15f81-111">Queries that do not Transform the Source Data</span></span>  
 <span data-ttu-id="15f81-112">Na poniższej ilustracji pokazano [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] do obiektów operacji, który wykonuje nie przekształcenia danych zapytania.</span><span class="sxs-lookup"><span data-stu-id="15f81-112">The following illustration shows a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] to Objects query operation that performs no transformations on the data.</span></span> <span data-ttu-id="15f81-113">Źródło zawiera sekwencję ciągów i wyników zapytania jest również sekwencję ciągów.</span><span class="sxs-lookup"><span data-stu-id="15f81-113">The source contains a sequence of strings and the query output is also a sequence of strings.</span></span>  
  
 <span data-ttu-id="15f81-114">![Typy relacji danych w zapytaniu składnika LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_flow1.png "LINQ_flow1")</span><span class="sxs-lookup"><span data-stu-id="15f81-114">![Relation of data types in a LINQ query](../../../../csharp/programming-guide/concepts/linq/media/linq_flow1.png "LINQ_flow1")</span></span>  
  
1.  <span data-ttu-id="15f81-115">Argument typu źródła danych określa rodzaj zmiennej zakresu.</span><span class="sxs-lookup"><span data-stu-id="15f81-115">The type argument of the data source determines the type of the range variable.</span></span>  
  
2.  <span data-ttu-id="15f81-116">Typ obiektu, który wybrano określa typu zmienną zapytania.</span><span class="sxs-lookup"><span data-stu-id="15f81-116">The type of the object that is selected determines the type of the query variable.</span></span> <span data-ttu-id="15f81-117">W tym miejscu `name` jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="15f81-117">Here `name` is a string.</span></span> <span data-ttu-id="15f81-118">W związku z tym jest zmienną zapytania `IEnumerable` \<ciąg >.</span><span class="sxs-lookup"><span data-stu-id="15f81-118">Therefore, the query variable is an `IEnumerable`\<string>.</span></span>  
  
3.  <span data-ttu-id="15f81-119">Do zmiennej zapytania jest powtórzyć za pośrednictwem w `foreach` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="15f81-119">The query variable is iterated over in the `foreach` statement.</span></span> <span data-ttu-id="15f81-120">Ponieważ zmienną zapytania jest sekwencję ciągów, zmiennej iteracji również jest ciągiem.</span><span class="sxs-lookup"><span data-stu-id="15f81-120">Because the query variable is a sequence of strings, the iteration variable is also a string.</span></span>  
  
## <a name="queries-that-transform-the-source-data"></a><span data-ttu-id="15f81-121">Zapytania, które przetwarzają dane źródłowe</span><span class="sxs-lookup"><span data-stu-id="15f81-121">Queries that Transform the Source Data</span></span>  
 <span data-ttu-id="15f81-122">Na poniższej ilustracji pokazano [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] operacji, który wykonuje transformację proste danych zapytania.</span><span class="sxs-lookup"><span data-stu-id="15f81-122">The following illustration shows a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query operation that performs a simple transformation on the data.</span></span> <span data-ttu-id="15f81-123">Zapytanie pobiera sekwencję `Customer` obiekty jako dane wejściowe i wybierze opcję tylko `Name` właściwości w wyniku.</span><span class="sxs-lookup"><span data-stu-id="15f81-123">The query takes a sequence of `Customer` objects as input, and selects only the `Name` property in the result.</span></span> <span data-ttu-id="15f81-124">Ponieważ `Name` to ciąg zapytania i tworzy sekwencję ciągów jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="15f81-124">Because `Name` is a string, the query produces a sequence of strings as output.</span></span>  
  
 <span data-ttu-id="15f81-125">![Zapytanie, które przekształca typu danych](../../../../csharp/programming-guide/concepts/linq/media/linq_flow2.png "LINQ_flow2")</span><span class="sxs-lookup"><span data-stu-id="15f81-125">![A query that transforms the data type](../../../../csharp/programming-guide/concepts/linq/media/linq_flow2.png "LINQ_flow2")</span></span>  
  
1.  <span data-ttu-id="15f81-126">Argument typu źródła danych określa rodzaj zmiennej zakresu.</span><span class="sxs-lookup"><span data-stu-id="15f81-126">The type argument of the data source determines the type of the range variable.</span></span>  
  
2.  <span data-ttu-id="15f81-127">`select` Zwraca instrukcji `Name` zamiast pełnej właściwości `Customer` obiektu.</span><span class="sxs-lookup"><span data-stu-id="15f81-127">The `select` statement returns the `Name` property instead of the complete `Customer` object.</span></span> <span data-ttu-id="15f81-128">Ponieważ `Name` to ciąg argumentu typu `custNameQuery` jest `string`, a nie `Customer`.</span><span class="sxs-lookup"><span data-stu-id="15f81-128">Because `Name` is a string, the type argument of `custNameQuery` is `string`, not `Customer`.</span></span>  
  
3.  <span data-ttu-id="15f81-129">Ponieważ `custNameQuery` Sekwencja ciągów, `foreach` zmiennej iteracji pętli musi być również `string`.</span><span class="sxs-lookup"><span data-stu-id="15f81-129">Because `custNameQuery` is a sequence of strings, the `foreach` loop's iteration variable must also be a `string`.</span></span>  
  
 <span data-ttu-id="15f81-130">Na poniższej ilustracji przedstawiono nieco bardziej złożone przekształcenia.</span><span class="sxs-lookup"><span data-stu-id="15f81-130">The following illustration shows a slightly more complex transformation.</span></span> <span data-ttu-id="15f81-131">`select` Instrukcja zwraca typ anonimowy, który przechwytuje tylko dwa elementy członkowskie z oryginalną `Customer` obiektu.</span><span class="sxs-lookup"><span data-stu-id="15f81-131">The `select` statement returns an anonymous type that captures just two members of the original `Customer` object.</span></span>  
  
 <span data-ttu-id="15f81-132">![Zapytanie, które przekształca typu danych](../../../../csharp/programming-guide/concepts/linq/media/linq_flow3.png "LINQ_flow3")</span><span class="sxs-lookup"><span data-stu-id="15f81-132">![A query that transforms the data type](../../../../csharp/programming-guide/concepts/linq/media/linq_flow3.png "LINQ_flow3")</span></span>  
  
1.  <span data-ttu-id="15f81-133">Argument typu źródła danych jest zawsze typu zmienną zakresu w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="15f81-133">The type argument of the data source is always the type of the range variable in the query.</span></span>  
  
2.  <span data-ttu-id="15f81-134">Ponieważ `select` instrukcji powoduje typu anonimowego, zmienną zapytania musi być niejawnie wpisanych przy użyciu `var`.</span><span class="sxs-lookup"><span data-stu-id="15f81-134">Because the `select` statement produces an anonymous type, the query variable must be implicitly typed by using `var`.</span></span>  
  
3.  <span data-ttu-id="15f81-135">Ponieważ pośrednie, jest typu zmienną zapytania zmiennej iteracji w `foreach` pętli musi być również niejawnej.</span><span class="sxs-lookup"><span data-stu-id="15f81-135">Because the type of the query variable is implicit, the iteration variable in the `foreach` loop must also be implicit.</span></span>  
  
## <a name="letting-the-compiler-infer-type-information"></a><span data-ttu-id="15f81-136">Umożliwienie kompilatora wnioskowanie informacji o typie</span><span class="sxs-lookup"><span data-stu-id="15f81-136">Letting the compiler infer type information</span></span>  
 <span data-ttu-id="15f81-137">Chociaż należy zrozumieć relacje typu w operacji zapytania, masz opcję umożliwiającą programowi kompilatora wykonać całą pracę za Ciebie.</span><span class="sxs-lookup"><span data-stu-id="15f81-137">Although you should understand the type relationships in a query operation, you have the option to let the compiler do all the work for you.</span></span> <span data-ttu-id="15f81-138">Słowo kluczowe [var](../../../../csharp/language-reference/keywords/var.md) może służyć do dowolnej zmiennej lokalnej w operacji zapytania.</span><span class="sxs-lookup"><span data-stu-id="15f81-138">The keyword [var](../../../../csharp/language-reference/keywords/var.md) can be used for any local variable in a query operation.</span></span> <span data-ttu-id="15f81-139">Poniższa ilustracja jest podobny do numer przykład 2 wcześniejszym opisem.</span><span class="sxs-lookup"><span data-stu-id="15f81-139">The following illustration is similar to example number 2 that was discussed earlier.</span></span> <span data-ttu-id="15f81-140">Jednak kompilator dostarcza silnego typu dla każdej zmiennej w operacji zapytania.</span><span class="sxs-lookup"><span data-stu-id="15f81-140">However, the compiler supplies the strong type for each variable in the query operation.</span></span>  
  
 <span data-ttu-id="15f81-141">![Typ przepływu niejawnego wpisując](../../../../csharp/programming-guide/concepts/linq/media/linq_flow4.png "LINQ_flow4")</span><span class="sxs-lookup"><span data-stu-id="15f81-141">![Type flow with implicit typing](../../../../csharp/programming-guide/concepts/linq/media/linq_flow4.png "LINQ_flow4")</span></span>  
  
 <span data-ttu-id="15f81-142">Aby uzyskać więcej informacji na temat `var`, zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="15f81-142">For more information about `var`, see [Implicitly Typed Local Variables](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15f81-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15f81-143">See Also</span></span>  
 [<span data-ttu-id="15f81-144">Wprowadzenie do korzystania z LINQ w C#</span><span class="sxs-lookup"><span data-stu-id="15f81-144">Getting Started with LINQ in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)