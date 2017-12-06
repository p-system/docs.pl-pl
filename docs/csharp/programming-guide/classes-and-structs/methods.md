---
title: "Metody (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
caps.latest.revision: "41"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ff6e59f70a5718f6616fa9a585dd84144e1774a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="methods-c-programming-guide"></a><span data-ttu-id="1551c-102">Metody (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="1551c-102">Methods (C# Programming Guide)</span></span>
<span data-ttu-id="1551c-103">Metoda jest blok kodu, który zawiera serię instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1551c-103">A method is a code block that contains a series of statements.</span></span> <span data-ttu-id="1551c-104">Program powoduje, że instrukcje, które ma być wykonane przez wywołanie metody i określanie żadnych argumentów wymaganej metody.</span><span class="sxs-lookup"><span data-stu-id="1551c-104">A program causes the statements to be executed by calling the method and specifying any required method arguments.</span></span> <span data-ttu-id="1551c-105">W języku C# co wykonanie instrukcji jest wykonywane w kontekście metody.</span><span class="sxs-lookup"><span data-stu-id="1551c-105">In C#, every executed instruction is performed in the context of a method.</span></span> <span data-ttu-id="1551c-106">Metoda Main jest punkt wejścia dla każdej aplikacji C# i jest wywoływane przez środowisko uruchomieniowe języka wspólnego (CLR), gdy program jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="1551c-106">The Main method is the entry point for every C# application and it is called by the common language runtime (CLR) when the program is started.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1551c-107">W tym temacie omówiono nazwane metody.</span><span class="sxs-lookup"><span data-stu-id="1551c-107">This topic discusses named methods.</span></span> <span data-ttu-id="1551c-108">Aby uzyskać informacje na temat funkcji anonimowych, zobacz [funkcje anonimowe](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span><span class="sxs-lookup"><span data-stu-id="1551c-108">For information about anonymous functions, see [Anonymous Functions](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).</span></span>  
  
## <a name="method-signatures"></a><span data-ttu-id="1551c-109">Podpisy — metoda</span><span class="sxs-lookup"><span data-stu-id="1551c-109">Method Signatures</span></span>  
 <span data-ttu-id="1551c-110">Metody są zadeklarowane w [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md) określając poziom dostępu, takich jak `public` lub `private`, Modyfikatory opcjonalne, takie jak `abstract` lub `sealed`, zwracany wartość, nazwę metody i wszelkie parametry metody.</span><span class="sxs-lookup"><span data-stu-id="1551c-110">Methods are declared in a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) by specifying the access level such as `public` or `private`, optional modifiers such as `abstract` or `sealed`, the return value, the name of the method, and any method parameters.</span></span> <span data-ttu-id="1551c-111">Części te są ze sobą podpis metody.</span><span class="sxs-lookup"><span data-stu-id="1551c-111">These parts together are the signature of the method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1551c-112">Typem zwracanym metody nie jest częścią podpis metody na potrzeby przeciążenie metody.</span><span class="sxs-lookup"><span data-stu-id="1551c-112">A return type of a method is not part of the signature of the method for the purposes of method overloading.</span></span> <span data-ttu-id="1551c-113">Jednak jest częścią podpis metody podczas określania zgodności między delegata i wskazujący do metody.</span><span class="sxs-lookup"><span data-stu-id="1551c-113">However, it is part of the signature of the method when determining the compatibility between a delegate and the method that it points to.</span></span>  
  
 <span data-ttu-id="1551c-114">Parametry metody są ujęte w nawiasy i są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="1551c-114">Method parameters are enclosed in parentheses and are separated by commas.</span></span> <span data-ttu-id="1551c-115">Puste nawiasy wskazują, że metoda nie wymaga parametrów.</span><span class="sxs-lookup"><span data-stu-id="1551c-115">Empty parentheses indicate that the method requires no parameters.</span></span> <span data-ttu-id="1551c-116">Ta klasa zawiera trzy metody:</span><span class="sxs-lookup"><span data-stu-id="1551c-116">This class contains three methods:</span></span>  
  
 [!code-csharp[csProgGuideObjects#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_1.cs)]  
  
## <a name="method-access"></a><span data-ttu-id="1551c-117">Metody dostępu</span><span class="sxs-lookup"><span data-stu-id="1551c-117">Method Access</span></span>  
 <span data-ttu-id="1551c-118">Wywoływanie metody do obiektu jest podobne do uzyskiwania dostępu do pola.</span><span class="sxs-lookup"><span data-stu-id="1551c-118">Calling a method on an object is like accessing a field.</span></span> <span data-ttu-id="1551c-119">Po nazwie obiektu dodać okres, nazwę metody i nawiasów.</span><span class="sxs-lookup"><span data-stu-id="1551c-119">After the object name, add a period, the name of the method, and parentheses.</span></span> <span data-ttu-id="1551c-120">Argumenty są wyświetlane w nawiasach i są oddzielone przecinkami.</span><span class="sxs-lookup"><span data-stu-id="1551c-120">Arguments are listed within the parentheses, and are separated by commas.</span></span> <span data-ttu-id="1551c-121">Metody `Motorcycle` klasa może zostać wywołana w związku z tym jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="1551c-121">The methods of the `Motorcycle` class can therefore be called as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_2.cs)]  
  
## <a name="method-parameters-vs-arguments"></a><span data-ttu-id="1551c-122">Parametry metody vs. Argumenty</span><span class="sxs-lookup"><span data-stu-id="1551c-122">Method Parameters vs. Arguments</span></span>  
 <span data-ttu-id="1551c-123">Definicja metody określa nazwy i typy parametrów, które są wymagane.</span><span class="sxs-lookup"><span data-stu-id="1551c-123">The method definition specifies the names and types of any parameters that are required.</span></span> <span data-ttu-id="1551c-124">Podczas wywoływania metody wywołań kodu, zapewnia konkretnych wartości o nazwie argumenty dla każdego parametru.</span><span class="sxs-lookup"><span data-stu-id="1551c-124">When calling code calls the method, it provides concrete values called arguments for each parameter.</span></span> <span data-ttu-id="1551c-125">Argumenty muszą być zgodne z typem parametru, ale nazwa argumentu (jeśli istnieją) używane w wywoływanym kodzie musi być taka sama jak parametr o nazwie w metodzie.</span><span class="sxs-lookup"><span data-stu-id="1551c-125">The arguments must be compatible with the parameter type but the argument name (if any) used in the calling code does not have to be the same as the parameter named defined in the method.</span></span> <span data-ttu-id="1551c-126">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1551c-126">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#74](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_3.cs)]  
  
## <a name="passing-by-reference-vs-passing-by-value"></a><span data-ttu-id="1551c-127">Przekazywanie poprzez odwołanie do wersji programu vs. Przekazywanie poprzez wartość</span><span class="sxs-lookup"><span data-stu-id="1551c-127">Passing by Reference vs. Passing by Value</span></span>  
 <span data-ttu-id="1551c-128">Domyślnie jeśli typ wartości jest przekazywany do metody, kopia jest przekazywany zamiast samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="1551c-128">By default, when a value type is passed to a method, a copy is passed instead of the object itself.</span></span> <span data-ttu-id="1551c-129">W związku z tym zmiany do argumentu nie mają wpływu na oryginał wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="1551c-129">Therefore, changes to the argument have no effect on the original copy in the calling method.</span></span> <span data-ttu-id="1551c-130">Można przekazać typu wartości przez odwołanie za pomocą ref — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="1551c-130">You can pass a value-type by reference by using the ref keyword.</span></span> <span data-ttu-id="1551c-131">Aby uzyskać więcej informacji, zobacz [przekazywanie parametrów typu wartość](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="1551c-131">For more information, see [Passing Value-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md).</span></span> <span data-ttu-id="1551c-132">Listę typów wartości wbudowanych, zobacz [Tabela typów wartości](../../../csharp/language-reference/keywords/value-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="1551c-132">For a list of built-in value types, see [Value Types Table](../../../csharp/language-reference/keywords/value-types-table.md).</span></span>  
  
 <span data-ttu-id="1551c-133">Gdy obiekt typu referencyjnego jest przekazywany do metody, są przekazywane odwołania do obiektu.</span><span class="sxs-lookup"><span data-stu-id="1551c-133">When an object of a reference type is passed to a method, a reference to the object is passed.</span></span> <span data-ttu-id="1551c-134">Oznacza to, że metoda odbiera, ale nie samego obiektu argument, który wskazuje lokalizację, do obiektu.</span><span class="sxs-lookup"><span data-stu-id="1551c-134">That is, the method receives not the object itself but an argument that indicates the location of the object.</span></span> <span data-ttu-id="1551c-135">Jeśli zmienisz element członkowski obiektu przy użyciu tego odwołania, zmiana ta jest uwzględniana w argumencie w przypadku wywołania metody nawet wtedy, gdy obiekt jest przekazanie przez wartość.</span><span class="sxs-lookup"><span data-stu-id="1551c-135">If you change a member of the object by using this reference, the change is reflected in the argument in the calling method, even if you pass the object by value.</span></span>  
  
 <span data-ttu-id="1551c-136">Utwórz typ referencyjny przy użyciu `class` — słowo kluczowe, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1551c-136">You create a reference type by using the `class` keyword, as the following example shows.</span></span>  
  
 [!code-csharp[csProgGuideObjects#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_4.cs)]  
  
 <span data-ttu-id="1551c-137">Teraz przekazując obiekt, który jest oparty na typie tej metody jest przekazywany odwołania do obiektu.</span><span class="sxs-lookup"><span data-stu-id="1551c-137">Now, if you pass an object that is based on this type to a method, a reference to the object is passed.</span></span> <span data-ttu-id="1551c-138">Poniższy przykład przekazuje obiekt typu `SampleRefType` do metody `ModifyObject`.</span><span class="sxs-lookup"><span data-stu-id="1551c-138">The following example passes an object of type `SampleRefType` to method `ModifyObject`.</span></span>  
  
 [!code-csharp[csProgGuideObjects#75](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_5.cs)]  
  
 <span data-ttu-id="1551c-139">Przykład jest zasadniczo sam efekt co w poprzednim przykładzie, w tym przekazuje argumentu przez wartość do metody.</span><span class="sxs-lookup"><span data-stu-id="1551c-139">The example does essentially the same thing as the previous example in that it passes an argument by value to a method.</span></span> <span data-ttu-id="1551c-140">Jednak ponieważ używany jest typ referencyjny, wynik jest inny.</span><span class="sxs-lookup"><span data-stu-id="1551c-140">But, because a reference type is used, the result is different.</span></span> <span data-ttu-id="1551c-141">Ze zmianami, które jest przeprowadzane w `ModifyObject` do `value` pole parametru, `obj`, zmieniają się także `value` pole argumentu, `rt`w `TestRefType` metody.</span><span class="sxs-lookup"><span data-stu-id="1551c-141">The modification that is made in `ModifyObject` to the `value` field of the parameter, `obj`, also changes the `value` field of the argument, `rt`, in the `TestRefType` method.</span></span> <span data-ttu-id="1551c-142">`TestRefType` Metoda Wyświetla 33 jako dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="1551c-142">The `TestRefType` method displays 33 as the output.</span></span>  
  
 <span data-ttu-id="1551c-143">Aby uzyskać więcej informacji na temat przekazywania typów referencyjnych przez odwołanie, a wartość, zobacz [przekazywanie parametrów typu odwołanie](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) i [typy referencyjne](../../../csharp/language-reference/keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="1551c-143">For more information about how to pass reference types by reference and by value, see [Passing Reference-Type Parameters](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) and [Reference Types](../../../csharp/language-reference/keywords/reference-types.md).</span></span>  
  
## <a name="return-values"></a><span data-ttu-id="1551c-144">Wartości zwrócone</span><span class="sxs-lookup"><span data-stu-id="1551c-144">Return Values</span></span>  
<span data-ttu-id="1551c-145">Metody może zwracać wartości do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="1551c-145">Methods can return a value to the caller.</span></span> <span data-ttu-id="1551c-146">Jeśli zwracany typ, typ wyświetlanych przed nazwę metody nie jest `void`, metoda może zwracać wartości przy użyciu `return` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="1551c-146">If the return type, the type listed before the method name, is not `void`, the method can return the value by using the `return` keyword.</span></span> <span data-ttu-id="1551c-147">Instrukcja zawierająca `return` — słowo kluczowe, a następnie wartość, która jest zgodny z typem zwracanym zwraca tę wartość do wywołującego metody.</span><span class="sxs-lookup"><span data-stu-id="1551c-147">A statement with the `return` keyword followed by a value that matches the return type will return that value to the method caller.</span></span> 

<span data-ttu-id="1551c-148">Wartość może być zwracany do obiektu wywołującego przez wartość lub, począwszy od C# 7, [przez odwołanie](ref-returns.md).</span><span class="sxs-lookup"><span data-stu-id="1551c-148">The value can be returned to the caller by value or, starting with C# 7, [by reference](ref-returns.md).</span></span> <span data-ttu-id="1551c-149">Wartości są zwracane do obiektu wywołującego przez odwołanie, jeśli `ref` — słowo kluczowe jest używane w podpisie metody i wynika z każdym `return` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="1551c-149">Values are returned to the caller by reference if the `ref` keyword is used in the method signature and it follows each `return` keyword.</span></span> <span data-ttu-id="1551c-150">Na przykład następująca instrukcja podpisu i przywracać — metoda wskazywać, że ta metoda zwraca nazwy zmiennych `estDistance` przez odwołanie do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="1551c-150">For example, the following method signature and return statement indicate that the method returns a variable names `estDistance` by reference to the caller.</span></span>

```csharp
public ref double GetEstimatedDistance()
{
   return ref estDistance;
}
```

<span data-ttu-id="1551c-151">`return` — Słowo kluczowe również zatrzymuje wykonywanie metody.</span><span class="sxs-lookup"><span data-stu-id="1551c-151">The `return` keyword also stops the execution of the method.</span></span> <span data-ttu-id="1551c-152">Jeśli typem zwracanym jest `void`, `return` instrukcji bez wartości, warto nadal zatrzymuje wykonywanie metody.</span><span class="sxs-lookup"><span data-stu-id="1551c-152">If the return type is `void`, a `return` statement without a value is still useful to stop the execution of the method.</span></span> <span data-ttu-id="1551c-153">Bez `return` — słowo kluczowe, metoda spowoduje zatrzymanie wykonywania, gdy zostanie osiągnięty koniec bloku kodu.</span><span class="sxs-lookup"><span data-stu-id="1551c-153">Without the `return` keyword, the method will stop executing when it reaches the end of the code block.</span></span> <span data-ttu-id="1551c-154">Metod innych niż void zwracany typ muszą korzystać z `return` — słowo kluczowe, aby zwrócić wartość.</span><span class="sxs-lookup"><span data-stu-id="1551c-154">Methods with a non-void return type are required to use the `return` keyword to return a value.</span></span> <span data-ttu-id="1551c-155">Na przykład użyć te dwie metody `return` — słowo kluczowe do zwrócenia liczb całkowitych:</span><span class="sxs-lookup"><span data-stu-id="1551c-155">For example, these two methods use the `return` keyword to return integers:</span></span>  
  
 [!code-csharp[csProgGuideObjects#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_6.cs)]  
  
 <span data-ttu-id="1551c-156">Aby użyć wartość zwracana z metody, metody wywołującej użyć wywołania metody sam gdziekolwiek się, że wartość tego samego typu będą wystarczające.</span><span class="sxs-lookup"><span data-stu-id="1551c-156">To use a value returned from a method, the calling method can use the method call itself anywhere a value of the same type would be sufficient.</span></span> <span data-ttu-id="1551c-157">Można także przypisać zwracana wartość do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="1551c-157">You can also assign the return value to a variable.</span></span> <span data-ttu-id="1551c-158">Na przykład następujący przykładowy kod dwóch realizację tego samego celu:</span><span class="sxs-lookup"><span data-stu-id="1551c-158">For example, the following two code examples accomplish the same goal:</span></span>  
  
 [!code-csharp[csProgGuideObjects#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_7.cs)]  
  
 [!code-csharp[csProgGuideObjects#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_8.cs)]  
  
 <span data-ttu-id="1551c-159">Przy użyciu zmiennej lokalnej, w tym przypadku `result`, aby przechowywać wartość jest opcjonalna.</span><span class="sxs-lookup"><span data-stu-id="1551c-159">Using a local variable, in this case, `result`, to store a value is optional.</span></span> <span data-ttu-id="1551c-160">Może pomóc zwiększyć czytelność kodu, lub może być konieczne, jeśli zachodzi potrzeba przechowywania oryginalnej wartości argumentu dla całego zakresu metody.</span><span class="sxs-lookup"><span data-stu-id="1551c-160">It may help the readability of the code, or it may be necessary if you need to store the original value of the argument for the entire scope of the method.</span></span>  

<span data-ttu-id="1551c-161">Aby użyć wartości zwracane przez odwołanie z metody, należy zadeklarować [lokalnej typu ref](ref-returns.md#ref-locals) zmiennej, jeśli zamierzasz zmodyfikować jego wartości.</span><span class="sxs-lookup"><span data-stu-id="1551c-161">To use a value returned by reference from a method, you must declare a [ref local](ref-returns.md#ref-locals) variable if you intend to modify its value.</span></span> <span data-ttu-id="1551c-162">Na przykład jeśli `Planet.GetEstimatedDistance` metoda zwraca <xref:System.Double> wartość przez odwołanie, można zdefiniować ją jako zmienna lokalna ref z kodem podobnie do następującej:</span><span class="sxs-lookup"><span data-stu-id="1551c-162">For example, if the `Planet.GetEstimatedDistance` method returns a <xref:System.Double> value by reference, you can define it as a ref local variable with code like the following:</span></span>

```csharp
ref int distance = plant 
```

<span data-ttu-id="1551c-163">Zwracanie tablicy wielowymiarowej z metody, `M`, który modyfikuje tablicy zawartość nie jest konieczne, jeśli funkcji wywołującej przekazany do tablicy `M`.</span><span class="sxs-lookup"><span data-stu-id="1551c-163">Returning a multi-dimensional array from a method, `M`, that modifies the array's contents is not necessary if the calling function passed the array into `M`.</span></span>  <span data-ttu-id="1551c-164">Może zwracać tablicy wynikowej z `M` dla stylu dobrej lub funkcjonalności przepływu wartości, ale nie jest konieczne, ponieważ C# przekazuje wszystkie typy referencyjne przez wartość i wartość odwołania do tablicy jest wskaźnik do tablicy.</span><span class="sxs-lookup"><span data-stu-id="1551c-164">You may return the resulting array from `M` for good style or functional flow of values, but it is not necessary because C# passes all reference types by value, and the value of an array reference is the pointer to the array.</span></span> <span data-ttu-id="1551c-165">W metodzie `M`, wszystkie zmiany do zawartości tablicy są według przez kodu, który zawiera odwołanie do tablicy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1551c-165">In the method `M`, any changes to the array's contents are observable by any code that has a reference to the array, as shown in the following example.</span></span>  
  
```csharp  
static void Main(string[] args)  
        {  
            int[,] matrix = new int[2, 2];  
            FillMatrix(matrix);  
            // matrix is now full of -1  
        }  
  
        public static void FillMatrix(int[,] matrix)  
        {  
            for (int i = 0; i < matrix.GetLength(0); i++)  
            {  
                for (int j = 0; j < matrix.GetLength(1); j++)  
                {  
                    matrix[i, j] = -1;  
                }  
            }  
        }  
```  
  
 <span data-ttu-id="1551c-166">Aby uzyskać więcej informacji, zobacz [zwracać](../../../csharp/language-reference/keywords/return.md).</span><span class="sxs-lookup"><span data-stu-id="1551c-166">For more information, see [return](../../../csharp/language-reference/keywords/return.md).</span></span>  
  
## <a name="async-methods"></a><span data-ttu-id="1551c-167">Metody asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="1551c-167">Async Methods</span></span>  
 <span data-ttu-id="1551c-168">Korzystając z funkcji asynchronicznych, można wywoływać metod asynchronicznych bez za pomocą jawnego wywołania zwrotne i ręcznie dzielenia kodu wielu metod lub wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="1551c-168">By using the async feature, you can invoke asynchronous methods without using explicit callbacks or manually splitting your code across multiple methods or lambda expressions.</span></span> 
  
 <span data-ttu-id="1551c-169">Po zaznaczeniu metodę o [async](../../../csharp/language-reference/keywords/async.md) modyfikator, można użyć [await](../../../csharp/language-reference/keywords/await.md) operatora w metodzie.</span><span class="sxs-lookup"><span data-stu-id="1551c-169">If you mark a method with the [async](../../../csharp/language-reference/keywords/async.md) modifier, you can use the [await](../../../csharp/language-reference/keywords/await.md) operator in the method.</span></span> <span data-ttu-id="1551c-170">Gdy formant osiągnie wyrażenie await w metodzie asynchronicznej, zwraca sterowania do obiektu wywołującego i postępu w metodzie jest wstrzymana, aż do zakończenia zadań oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="1551c-170">When control reaches an await expression in the async method, control returns to the caller, and progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="1551c-171">Po zakończeniu zadania wykonywania można wznowić w metodzie.</span><span class="sxs-lookup"><span data-stu-id="1551c-171">When the task is complete, execution can resume in the method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1551c-172">Metoda asynchroniczna zwraca do obiektu wywołującego po napotkaniu pierwszego oczekiwano obiekt, który nie został jeszcze ukończony lub pobiera na końcu metody asynchronicznej cokolwiek nastąpi najpierw.</span><span class="sxs-lookup"><span data-stu-id="1551c-172">An async method returns to the caller when either it encounters the first awaited object that’s not yet complete or it gets to the end of the async method, whichever occurs first.</span></span>  
  
 <span data-ttu-id="1551c-173">Metoda asynchroniczna może mieć typ zwracany <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, ani void.</span><span class="sxs-lookup"><span data-stu-id="1551c-173">An async method can have a return type of <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, or void.</span></span> <span data-ttu-id="1551c-174">Zwrócony typ void jest używany głównie w celu definiowania metod obsługi zdarzeń, którym wymagany jest zwrócony typ void.</span><span class="sxs-lookup"><span data-stu-id="1551c-174">The void return type is used primarily to define event handlers, where a void return type is required.</span></span> <span data-ttu-id="1551c-175">Metoda asynchroniczna zwracająca typ void nie może być oczekiwane, a obiekt wywołujący metody zwracające typ void nie może przechwytywać wyjątki, które metoda zgłasza.</span><span class="sxs-lookup"><span data-stu-id="1551c-175">An async method that returns void can't be awaited, and the caller of a void-returning method can't catch exceptions that the method throws.</span></span>  
  
 <span data-ttu-id="1551c-176">W poniższym przykładzie `DelayAsync` jest to metoda asynchroniczna, który ma typ zwracany <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="1551c-176">In the following example, `DelayAsync` is an async method that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="1551c-177">`DelayAsync`ma `return` instrukcji, która zwraca liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="1551c-177">`DelayAsync` has a `return` statement that returns an integer.</span></span> <span data-ttu-id="1551c-178">W związku z tym metoda deklaracja `DelayAsync` musi mieć typ zwracany `Task<int>`.</span><span class="sxs-lookup"><span data-stu-id="1551c-178">Therefore the method declaration of `DelayAsync` must have a return type of `Task<int>`.</span></span> <span data-ttu-id="1551c-179">Ponieważ typ zwracany jest `Task<int>`, oceny `await` wyrażenie w `DoSomethingAsync` tworzy całkowitą, jak pokazano następująca instrukcja: `int result = await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="1551c-179">Because the return type is `Task<int>`, the evaluation of the `await` expression in `DoSomethingAsync` produces an integer as the following statement demonstrates: `int result = await delayTask`.</span></span>  
  
 <span data-ttu-id="1551c-180">`startButton_Click` Metoda jest przykładem to metoda asynchroniczna, który ma zwracany typ void.</span><span class="sxs-lookup"><span data-stu-id="1551c-180">The `startButton_Click` method is an example of an async method that has a return type of void.</span></span> <span data-ttu-id="1551c-181">Ponieważ `DoSomethingAsync` jest to metoda asynchroniczna, zadania dla wywołania `DoSomethingAsync` musi być oczekiwane, jak przedstawiono na poniższym instrukcji: `await DoSomethingAsync();`.</span><span class="sxs-lookup"><span data-stu-id="1551c-181">Because `DoSomethingAsync` is an async method, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `await DoSomethingAsync();`.</span></span> <span data-ttu-id="1551c-182">`startButton_Click` Metoda musi być zdefiniowana z `async` modyfikator ponieważ metoda ma `await` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="1551c-182">The `startButton_Click` method must be defined with the `async` modifier because the method has an `await` expression.</span></span>  
  
 [!code-csharp[csAsyncMethod#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_9.cs)]  
  
 <span data-ttu-id="1551c-183">Metoda asynchroniczna nie można zadeklarować żadnego [ref](../../../csharp/language-reference/keywords/ref.md) lub [limit](../../../csharp/language-reference/keywords/out.md) parametrów, ale można wywołać metody, które mają takie parametry.</span><span class="sxs-lookup"><span data-stu-id="1551c-183">An async method can't declare any [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) parameters, but it can call methods that have such parameters.</span></span>  
  
 <span data-ttu-id="1551c-184">Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [programowanie asynchroniczne z async i await](../../../csharp/programming-guide/concepts/async/index.md), [przepływ sterowania w aplikacjach asynchronicznych](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md), i [Async zwracać typów](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="1551c-184">For more information about async methods, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="1551c-185">Definicje treść wyrażenia</span><span class="sxs-lookup"><span data-stu-id="1551c-185">Expression Body Definitions</span></span>  
 <span data-ttu-id="1551c-186">Jest często mają definicje — metoda, która po prostu zwrot wynik wyrażenia, lub które mają jednej instrukcji jako treść metody.</span><span class="sxs-lookup"><span data-stu-id="1551c-186">It is common to have method definitions that simply return immediately with the result of an expression, or that have a single statement as the body of the method.</span></span>  <span data-ttu-id="1551c-187">Brak skrót do definiowania tych metod, za pomocą składni `=>`:</span><span class="sxs-lookup"><span data-stu-id="1551c-187">There is a syntax shortcut for defining such methods using `=>`:</span></span>  
  
```csharp  
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);   
public void Print() => Console.WriteLine(First + " " + Last);  
// Works with operators, properties, and indexers too.  
public static Complex operator +(Complex a, Complex b) => a.Add(b);  
public string Name => First + " " + Last;   
public Customer this[long id] => store.LookupCustomer(id);  
```  
  
 <span data-ttu-id="1551c-188">Jeśli metoda zwraca `void` lub jest to metoda asynchroniczna, a następnie treści metody musi być wyrażeniem instrukcji (tak samo jak w przypadku wyrażeń lambda).</span><span class="sxs-lookup"><span data-stu-id="1551c-188">If the method returns `void` or is an async method, then the body of the method must be a statement expression (same as with lambdas).</span></span>  <span data-ttu-id="1551c-189">Dla właściwości i indeksatorów one musi być tylko do odczytu i nie używaj `get` akcesor — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="1551c-189">For properties and indexers, they must be read only, and you don't use the `get` accessor keyword.</span></span>  
  
## <a name="iterators"></a><span data-ttu-id="1551c-190">Iteratory</span><span class="sxs-lookup"><span data-stu-id="1551c-190">Iterators</span></span>  
 <span data-ttu-id="1551c-191">Iteratora wykonuje niestandardowych iteracji w kolekcji, takie jak listy lub tablicy.</span><span class="sxs-lookup"><span data-stu-id="1551c-191">An iterator performs a custom iteration over a collection, such as a list or an array.</span></span> <span data-ttu-id="1551c-192">Używa iteratora [yield return](../../../csharp/language-reference/keywords/yield.md) instrukcji, aby zwracany był każdy element jednym naraz.</span><span class="sxs-lookup"><span data-stu-id="1551c-192">An iterator uses the [yield return](../../../csharp/language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="1551c-193">Gdy [yield return](../../../csharp/language-reference/keywords/yield.md) osiągnięciu instrukcji zapamiętanych bieżącej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1551c-193">When a [yield return](../../../csharp/language-reference/keywords/yield.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="1551c-194">Wykonanie zostanie ponownie z tej lokalizacji, gdy iteratora jest wywoływana przy następnym.</span><span class="sxs-lookup"><span data-stu-id="1551c-194">Execution is restarted from that location when the iterator is called the next time.</span></span>  
  
 <span data-ttu-id="1551c-195">Wywołaj iteratora z kodu klienta za pomocą [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1551c-195">You call an iterator from client code by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement.</span></span>  
  
 <span data-ttu-id="1551c-196">Może być zwracany typ iteratora <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="1551c-196">The return type of an iterator can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="1551c-197">Aby uzyskać więcej informacji, zobacz [Iteratory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="1551c-197">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="1551c-198">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1551c-198">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1551c-199">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1551c-199">See Also</span></span>  
 [<span data-ttu-id="1551c-200">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1551c-200">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1551c-201">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="1551c-201">Classes and Structs</span></span>](index.md)  
 [<span data-ttu-id="1551c-202">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="1551c-202">Access Modifiers</span></span>](access-modifiers.md)  
 [<span data-ttu-id="1551c-203">Klasy statyczne i statyczni członkowie klas</span><span class="sxs-lookup"><span data-stu-id="1551c-203">Static Classes and Static Class Members</span></span>](static-classes-and-static-class-members.md)  
 [<span data-ttu-id="1551c-204">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="1551c-204">Inheritance</span></span>](inheritance.md)  
 [<span data-ttu-id="1551c-205">Klasy abstrakcyjne i zapieczętowane oraz członkowie klas</span><span class="sxs-lookup"><span data-stu-id="1551c-205">Abstract and Sealed Classes and Class Members</span></span>](abstract-and-sealed-classes-and-class-members.md)  
 [<span data-ttu-id="1551c-206">Parametry</span><span class="sxs-lookup"><span data-stu-id="1551c-206">params</span></span>](../../../csharp/language-reference/keywords/params.md)  
 [<span data-ttu-id="1551c-207">Zwraca</span><span class="sxs-lookup"><span data-stu-id="1551c-207">return</span></span>](../../../csharp/language-reference/keywords/return.md)  
 [<span data-ttu-id="1551c-208">limit</span><span class="sxs-lookup"><span data-stu-id="1551c-208">out</span></span>](../../../csharp/language-reference/keywords/out.md)  
 [<span data-ttu-id="1551c-209">REF</span><span class="sxs-lookup"><span data-stu-id="1551c-209">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
 [<span data-ttu-id="1551c-210">Przekazywanie parametrów</span><span class="sxs-lookup"><span data-stu-id="1551c-210">Passing Parameters</span></span>](passing-parameters.md)