---
title: "bool (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- bool_CSharpKeyword
- bool
helpviewer_keywords: bool keyword [C#]
ms.assetid: 551cfe35-2632-4343-af49-33ad12da08e2
caps.latest.revision: "30"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1d52955d64a6c8063e4ea93ceb096459c1c5e984
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="bool-c-reference"></a><span data-ttu-id="0a670-102">bool (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0a670-102">bool (C# Reference)</span></span>
<span data-ttu-id="0a670-103">`bool` — Słowo kluczowe jest aliasem <xref:System.Boolean?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0a670-103">The `bool` keyword is an alias of <xref:System.Boolean?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0a670-104">Służy do deklarowania zmiennych do przechowywania wartości logicznych, [true](../../../csharp/language-reference/keywords/true.md) i [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="0a670-104">It is used to declare variables to store the Boolean values, [true](../../../csharp/language-reference/keywords/true.md) and [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a670-105">Jeśli potrzebujesz zmienną wartości logicznej, która również może mieć wartość `null`, użyj `bool?`.</span><span class="sxs-lookup"><span data-stu-id="0a670-105">If you require a Boolean variable that can also have a value of `null`, use `bool?`.</span></span> <span data-ttu-id="0a670-106">Aby uzyskać więcej informacji, zobacz [typy dopuszczające wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="0a670-106">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="literals"></a><span data-ttu-id="0a670-107">Literały</span><span class="sxs-lookup"><span data-stu-id="0a670-107">Literals</span></span>  
 <span data-ttu-id="0a670-108">Można przypisać wartość logiczną umożliwiającą `bool` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0a670-108">You can assign a Boolean value to a `bool` variable.</span></span> <span data-ttu-id="0a670-109">Można także przypisać wyrażenie obliczane do `bool` do `bool` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0a670-109">You can also assign an expression that evaluates to `bool` to a `bool` variable.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_1.cs)]  
  
 <span data-ttu-id="0a670-110">Wartość domyślna `bool` zmienna jest `false`.</span><span class="sxs-lookup"><span data-stu-id="0a670-110">The default value of a `bool` variable is `false`.</span></span> <span data-ttu-id="0a670-111">Wartość domyślna `bool?` zmienna jest `null`.</span><span class="sxs-lookup"><span data-stu-id="0a670-111">The default value of a `bool?` variable is `null`.</span></span>  
  
## <a name="conversions"></a><span data-ttu-id="0a670-112">Konwersje</span><span class="sxs-lookup"><span data-stu-id="0a670-112">Conversions</span></span>  
 <span data-ttu-id="0a670-113">W języku C++ wartości typu `bool` można przekonwertować wartości typu `int`; innymi słowy, `false` jest odpowiednikiem zero i `true` jest odpowiednikiem wartości niezerowych.</span><span class="sxs-lookup"><span data-stu-id="0a670-113">In C++, a value of type `bool` can be converted to a value of type `int`; in other words, `false` is equivalent to zero and `true` is equivalent to nonzero values.</span></span> <span data-ttu-id="0a670-114">W języku C# nie jest konwersja między `bool` typu i innych typów.</span><span class="sxs-lookup"><span data-stu-id="0a670-114">In C#, there is no conversion between the `bool` type and other types.</span></span> <span data-ttu-id="0a670-115">Na przykład następująca `if` instrukcja jest nieprawidłowa w języku C#:</span><span class="sxs-lookup"><span data-stu-id="0a670-115">For example, the following `if` statement is invalid in C#:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_2.cs)]  
  
 <span data-ttu-id="0a670-116">Aby przetestować zmiennej typu `int`, musisz jawnie porównaj je z wartość, na przykład wartość 0, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="0a670-116">To test a variable of the type `int`, you have to explicitly compare it to a value, such as zero, as follows:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="0a670-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a670-117">Example</span></span>  
 <span data-ttu-id="0a670-118">W tym przykładzie Wprowadź znak z klawiatury i program sprawdza, czy wprowadzany znak jest literą.</span><span class="sxs-lookup"><span data-stu-id="0a670-118">In this example, you enter a character from the keyboard and the program checks if the input character is a letter.</span></span> <span data-ttu-id="0a670-119">Jest literą, sprawdza, czy jest małe lub wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="0a670-119">If it is a letter, it checks if it is lowercase or uppercase.</span></span> <span data-ttu-id="0a670-120">Te testy są wykonywane z <xref:System.Char.IsLetter%2A>, i <xref:System.Char.IsLower%2A>, zarówno które zwrotu `bool` typu:</span><span class="sxs-lookup"><span data-stu-id="0a670-120">These checks are performed with the <xref:System.Char.IsLetter%2A>, and <xref:System.Char.IsLower%2A>, both of which return the `bool` type:</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/bool_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="0a670-121">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0a670-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0a670-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a670-122">See Also</span></span>  
 [<span data-ttu-id="0a670-123">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="0a670-123">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0a670-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0a670-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0a670-125">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="0a670-125">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="0a670-126">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="0a670-126">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="0a670-127">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="0a670-127">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="0a670-128">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="0a670-128">Implicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [<span data-ttu-id="0a670-129">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="0a670-129">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)