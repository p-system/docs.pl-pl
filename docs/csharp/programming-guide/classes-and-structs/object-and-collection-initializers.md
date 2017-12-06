---
title: "Inicjatory obiektów i kolekcji (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- object initializers [C#]
- collection initializers [C#]
ms.assetid: c58f3db5-d7d4-4651-bd2d-5a3a97357f61
caps.latest.revision: "27"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7445a2919baaa477b4611c4c5ee5a0031539ca30
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="object-and-collection-initializers-c-programming-guide"></a><span data-ttu-id="9b279-102">Inicjatory obiektów i kolekcji (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="9b279-102">Object and Collection Initializers (C# Programming Guide)</span></span>
<span data-ttu-id="9b279-103">Inicjatory obiektów umożliwiają przypisywanie wartości do dowolnych dostępnych pól lub właściwości obiektu w czasie jego tworzenia, bez konieczności wywoływania konstruktora, po którym występują wiersze instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="9b279-103">Object initializers let you assign values to any accessible fields or properties of an object at creation time without having to invoke a constructor followed by lines of assignment statements.</span></span> <span data-ttu-id="9b279-104">Składnia inicjatora obiektów umożliwia określenie argumentów dla konstruktora lub pominięcie argumentów (i składni z nawiasami).</span><span class="sxs-lookup"><span data-stu-id="9b279-104">The object initializer syntax enables you to specify arguments for a constructor or omit the arguments (and parentheses syntax).</span></span>  <span data-ttu-id="9b279-105">Poniższy przykład przedstawia użycie inicjatora obiektów z nazwanym typem `Cat` oraz sposób wywołania konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="9b279-105">The following example shows how to use an object initializer with a named type, `Cat` and how to invoke the default constructor.</span></span> <span data-ttu-id="9b279-106">Zwróć uwagę na użycie właściwości zaimplementowane automatycznie w `Cat` klasy.</span><span class="sxs-lookup"><span data-stu-id="9b279-106">Note the use of auto-implemented properties in the `Cat` class.</span></span> <span data-ttu-id="9b279-107">Aby uzyskać więcej informacji, zobacz [Auto-Implemented właściwości](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="9b279-107">For more information, see [Auto-Implemented Properties](../../../csharp/programming-guide/classes-and-structs/auto-implemented-properties.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_1.cs)]  
  
 [!code-csharp[csProgGuideLINQ#45](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_2.cs)] 
 
<span data-ttu-id="9b279-108">Składnię inicjatory obiektów służy do tworzenia wystąpienia, i po tym nowo utworzony obiekt z jego właściwości przypisane, przypisuje do zmiennej przypisania.</span><span class="sxs-lookup"><span data-stu-id="9b279-108">The object initializers syntax allows you to create an instance, and after that it assigns the newly created object, with its assigned properties, to the variable in the assignment.</span></span>
  
## <a name="object-initializers-with-anonymous-types"></a><span data-ttu-id="9b279-109">Inicjatory obiektów z typami anonimowymi</span><span class="sxs-lookup"><span data-stu-id="9b279-109">Object Initializers with anonymous types</span></span>  
 <span data-ttu-id="9b279-110">Chociaż inicjatory obiektów można używać w dowolnym kontekście, jest szczególnie przydatne w [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] wyrażenia zapytań.</span><span class="sxs-lookup"><span data-stu-id="9b279-110">Although object initializers can be used in any context, they are especially useful in [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expressions.</span></span> <span data-ttu-id="9b279-111">Wyrażenia zapytań wykorzystują częste [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), które można zainicjować tylko za pomocą inicjatora obiektów, jak pokazano w poniższych deklaracji.</span><span class="sxs-lookup"><span data-stu-id="9b279-111">Query expressions make frequent use of [anonymous types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md), which can only be initialized by using an object initializer, as shown in the following declaration.</span></span>  
  
```csharp
var pet = new { Age = 10, Name = "Fluffy" };  
```  
  
 <span data-ttu-id="9b279-112">Włącz typy anonimowe `select` w klauzuli [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] zapytania wyrażenia do przekształcania obiekty z oryginalnej sekwencji obiektów, których wartość i kształtu mogą się różnić od oryginału.</span><span class="sxs-lookup"><span data-stu-id="9b279-112">Anonymous types enable the `select` clause in a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query expression to transform objects of the original sequence into objects whose value and shape may differ from the original.</span></span> <span data-ttu-id="9b279-113">Jest to użyteczne, gdy chce się przechowywać tylko część informacji z każdego obiektu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="9b279-113">This is useful if you want to store only a part of the information from each object in a sequence.</span></span> <span data-ttu-id="9b279-114">W poniższym przykładzie przyjęto założenie, że obiekt produktu (`p`) zawiera wiele pól i metod, i że interesuje Cię tylko podczas tworzenia sekwencji obiektów, które zawierają nazwę produktu i cenie jednostkowej.</span><span class="sxs-lookup"><span data-stu-id="9b279-114">In the following example, assume that a product object (`p`) contains many fields and methods, and that you are only interested in creating a sequence of objects that contain the product name and the unit price.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_3.cs)]  
  
 <span data-ttu-id="9b279-115">Podczas wykonywania tego zapytania `productInfos` zmienna będzie zawierać sekwencji obiektów, które są dostępne w `foreach` instrukcji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9b279-115">When this query is executed, the `productInfos` variable will contain a sequence of objects that can be accessed in a `foreach` statement as shown in this example:</span></span>  
  
```csharp
foreach(var p in productInfos){...}  
```  
  
 <span data-ttu-id="9b279-116">Każdy obiekt w nowym typie anonimowym ma dwie właściwości publiczne, które otrzymują takie same nazwy, jak właściwości lub pola w oryginalnym obiekcie.</span><span class="sxs-lookup"><span data-stu-id="9b279-116">Each object in the new anonymous type has two public properties which receive the same names as the properties or fields in the original object.</span></span> <span data-ttu-id="9b279-117">Można również zmienić nazwę pola, podczas tworzenia typu anonimowego; Poniższy przykład zmienia nazwę `UnitPrice` do `Price`.</span><span class="sxs-lookup"><span data-stu-id="9b279-117">You can also rename a field when you are creating an anonymous type; the following example renames the `UnitPrice` field to `Price`.</span></span>  
  
```csharp
select new {p.ProductName, Price = p.UnitPrice};  
```  
  
## <a name="object-initializers-with-nullable-types"></a><span data-ttu-id="9b279-118">Inicjatory obiektów z typami zerowalnymi</span><span class="sxs-lookup"><span data-stu-id="9b279-118">Object initializers with nullable types</span></span>  
 <span data-ttu-id="9b279-119">Jest to błąd czasu kompilowania spowodowany użyciem inicjatora obiektów ze strukturą dopuszczającą wartości null.</span><span class="sxs-lookup"><span data-stu-id="9b279-119">It is a compile-time error to use an object initializer with a nullable struct.</span></span>  
  
## <a name="collection-initializers"></a><span data-ttu-id="9b279-120">Inicjatory kolekcji</span><span class="sxs-lookup"><span data-stu-id="9b279-120">Collection initializers</span></span>  
 <span data-ttu-id="9b279-121">Inicjatory kolekcji pozwalają określić jedną lub więcej inicjatory elementów podczas inicjowania kolekcji typ implementuje ten <xref:System.Collections.IEnumerable> i ma `Add` z odpowiednim podpisem jako metodę wystąpienia lub metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="9b279-121">Collection initializers let you specify one or more element initializers when you initialize a collection type that implements <xref:System.Collections.IEnumerable> and has `Add` with the appropriate signature as an instance method or an extension method.</span></span> <span data-ttu-id="9b279-122">Inicjatory elementów mogą być wartościami prostymi, wyrażeniami lub inicjatorami obiektów.</span><span class="sxs-lookup"><span data-stu-id="9b279-122">The element initializers can be a simple value, an expression or an object initializer.</span></span> <span data-ttu-id="9b279-123">Za pomocą inicjatora kolekcji jest konieczne określanie wielu wywołań `Add` klasy w kodzie źródłowym; kompilator dodaje wywołań.</span><span class="sxs-lookup"><span data-stu-id="9b279-123">By using a collection initializer you do not have to specify multiple calls to the `Add` method of the class in your source code; the compiler adds the calls.</span></span>  
  
 <span data-ttu-id="9b279-124">W poniższych przykładach pokazano dwa proste inicjatory kolekcji:</span><span class="sxs-lookup"><span data-stu-id="9b279-124">The following examples shows two simple collection initializers:</span></span>  
  
```csharp
List<int> digits = new List<int> { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };  
List<int> digits2 = new List<int> { 0 + 1, 12 % 3, MakeInt() };  
```  
  
 <span data-ttu-id="9b279-125">Następujące inicjatora kolekcji używa inicjatory obiektów do zainicjowania obiekty `Cat` klas zdefiniowanych w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9b279-125">The following collection initializer uses object initializers to initialize objects of the `Cat` class defined in a previous example.</span></span> <span data-ttu-id="9b279-126">Należy zauważyć, że poszczególne inicjatory obiektów są umieszczone w nawiasach klamrowych i rozdzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="9b279-126">Note that the individual object initializers are enclosed in braces and separated by commas.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_4.cs)]  
  
 <span data-ttu-id="9b279-127">Można określić [null](../../../csharp/language-reference/keywords/null.md) jako elementu inicjatora kolekcji Jeśli kolekcji `Add` pozwala metody.</span><span class="sxs-lookup"><span data-stu-id="9b279-127">You can specify [null](../../../csharp/language-reference/keywords/null.md) as an element in a collection initializer if the collection's `Add` method allows it.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_5.cs)]  
  
 <span data-ttu-id="9b279-128">Można określić indeksowane elementy, jeśli kolekcja obsługuje indeksowania.</span><span class="sxs-lookup"><span data-stu-id="9b279-128">You can specify indexed elements if the collection supports indexing.</span></span>  
  
```csharp
var numbers = new Dictionary<int, string> {   
    [7] = "seven",   
    [9] = "nine",   
    [13] = "thirteen"   
};  
```  
  
## <a name="example"></a><span data-ttu-id="9b279-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="9b279-129">Example</span></span>  
 [!code-csharp[csProgGuideLINQ#46](../../../csharp/programming-guide/arrays/codesnippet/CSharp/object-and-collection-initializers_6.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9b279-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9b279-130">See Also</span></span>  
 [<span data-ttu-id="9b279-131">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9b279-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9b279-132">Wyrażenia zapytań LINQ</span><span class="sxs-lookup"><span data-stu-id="9b279-132">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="9b279-133">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="9b279-133">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)