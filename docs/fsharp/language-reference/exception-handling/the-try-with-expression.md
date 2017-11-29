---
title: "Wyjątki: try...with — Wyrażenie (F#)"
description: "Dowiedz się, jak użyć F # \"try... with\" wyrażenia dla obsługi wyjątków."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 36721076-95cd-4636-ae43-79dd512bee6c
ms.openlocfilehash: 163dfab49d4aaf23123800246fae2cad33e2257c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-the-trywith-expression"></a><span data-ttu-id="59fa5-104">Wyjątki: try...with — Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="59fa5-104">Exceptions: The try...with Expression</span></span>

<span data-ttu-id="59fa5-105">W tym temacie opisano `try...with` wyrażenia, wyrażenie, które służy do obsługi wyjątków w języku F #.</span><span class="sxs-lookup"><span data-stu-id="59fa5-105">This topic describes the `try...with` expression, the expression that is used for exception handling in the F# language.</span></span>


## <a name="syntax"></a><span data-ttu-id="59fa5-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="59fa5-106">Syntax</span></span>

```fsharp
try
    expression1
with
| pattern1 -> expression2
| pattern2 -> expression3
...
```

## <a name="remarks"></a><span data-ttu-id="59fa5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="59fa5-107">Remarks</span></span>
<span data-ttu-id="59fa5-108">`try...with` Wyrażenie jest używane do obsługi wyjątków w języku F #.</span><span class="sxs-lookup"><span data-stu-id="59fa5-108">The `try...with` expression is used to handle exceptions in F#.</span></span> <span data-ttu-id="59fa5-109">Jest on podobny do `try...catch` instrukcji w języku C#.</span><span class="sxs-lookup"><span data-stu-id="59fa5-109">It is similar to the `try...catch` statement in C#.</span></span> <span data-ttu-id="59fa5-110">W powyższej składni kod w *wyrażenie1* może generować wyjątek.</span><span class="sxs-lookup"><span data-stu-id="59fa5-110">In the preceding syntax, the code in *expression1* might generate an exception.</span></span> <span data-ttu-id="59fa5-111">`try...with` Wyrażenie zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="59fa5-111">The `try...with` expression returns a value.</span></span> <span data-ttu-id="59fa5-112">Jeśli żaden wyjątek jest zgłaszany, całe wyrażenie zwraca wartość *wyrażenie1*.</span><span class="sxs-lookup"><span data-stu-id="59fa5-112">If no exception is thrown, the whole expression returns the value of *expression1*.</span></span> <span data-ttu-id="59fa5-113">Jeśli jest zgłaszany wyjątek, każdy *wzorzec* jest porównywany z kolei, z wyjątkiem i pierwszy pasujący wzorzec odpowiadającego *wyrażenie*, znaną jako *program obsługi wyjątku*dla tej gałęzi jest wykonywana, a ogólną wyrażenie zwraca wartość wyrażenia w tym obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="59fa5-113">If an exception is thrown, each *pattern* is compared in turn with the exception, and for the first matching pattern, the corresponding *expression*, known as the *exception handler*, for that branch is executed, and the overall expression returns the value of the expression in that exception handler.</span></span> <span data-ttu-id="59fa5-114">Jeśli wzorzec nie jest zgodny, wyjątek propaguje górę stosu wywołań, aż do znalezienia zgodnego programu obsługi.</span><span class="sxs-lookup"><span data-stu-id="59fa5-114">If no pattern matches, the exception propagates up the call stack until a matching handler is found.</span></span> <span data-ttu-id="59fa5-115">Typy wartości zwrócone przez każde wyrażenie w programy obsługi wyjątków musi odpowiadać typowi zwrócony z wyrażenia w `try` bloku.</span><span class="sxs-lookup"><span data-stu-id="59fa5-115">The types of the values returned from each expression in the exception handlers must match the type returned from the expression in the `try` block.</span></span>

<span data-ttu-id="59fa5-116">Często fakt również wystąpił błąd oznacza, że nie ma prawidłowej wartości, które mogą być zwrócone z wyrażeń w każdym obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="59fa5-116">Frequently, the fact that an error occurred also means that there is no valid value that can be returned from the expressions in each exception handler.</span></span> <span data-ttu-id="59fa5-117">Częste wzorzec jest typ wyrażenia jest typ opcji.</span><span class="sxs-lookup"><span data-stu-id="59fa5-117">A frequent pattern is to have the type of the expression be an option type.</span></span> <span data-ttu-id="59fa5-118">Poniższy przykład kodu pokazuje tego wzorca.</span><span class="sxs-lookup"><span data-stu-id="59fa5-118">The following code example illustrates this pattern.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5601.fs)]

<span data-ttu-id="59fa5-119">Wyjątki mogą być wyjątki .NET lub mogą być wyjątki F #.</span><span class="sxs-lookup"><span data-stu-id="59fa5-119">Exceptions can be .NET exceptions, or they can be F# exceptions.</span></span> <span data-ttu-id="59fa5-120">Możesz zdefiniować wyjątki F # za pomocą `exception` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="59fa5-120">You can define F# exceptions by using the `exception` keyword.</span></span>

<span data-ttu-id="59fa5-121">Można użyć różnych wzorców do filtrowania typ wyjątku i innych warunków; Opcje podsumowano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="59fa5-121">You can use a variety of patterns to filter on the exception type and other conditions; the options are summarized in the following table.</span></span>


|<span data-ttu-id="59fa5-122">Wzorzec</span><span class="sxs-lookup"><span data-stu-id="59fa5-122">Pattern</span></span>|<span data-ttu-id="59fa5-123">Opis</span><span class="sxs-lookup"><span data-stu-id="59fa5-123">Description</span></span>|
|-------|-----------|
|<span data-ttu-id="59fa5-124">:?</span><span class="sxs-lookup"><span data-stu-id="59fa5-124">:?</span></span> <span data-ttu-id="59fa5-125">*Typ wyjątku*</span><span class="sxs-lookup"><span data-stu-id="59fa5-125">*exception-type*</span></span>|<span data-ttu-id="59fa5-126">Zgodne z określonym typem wyjątku .NET.</span><span class="sxs-lookup"><span data-stu-id="59fa5-126">Matches the specified .NET exception type.</span></span>|
|<span data-ttu-id="59fa5-127">:?</span><span class="sxs-lookup"><span data-stu-id="59fa5-127">:?</span></span> <span data-ttu-id="59fa5-128">*Typ wyjątku* jako *identyfikator*</span><span class="sxs-lookup"><span data-stu-id="59fa5-128">*exception-type* as *identifier*</span></span>|<span data-ttu-id="59fa5-129">Zgodne z określonym typem wyjątku .NET, ale zapewnia wyjątek nazwanych wartości.</span><span class="sxs-lookup"><span data-stu-id="59fa5-129">Matches the specified .NET exception type, but gives the exception a named value.</span></span>|
|<span data-ttu-id="59fa5-130">*nazwa wyjątku*(*argumenty*)</span><span class="sxs-lookup"><span data-stu-id="59fa5-130">*exception-name*(*arguments*)</span></span>|<span data-ttu-id="59fa5-131">Zgodny z typem wyjątku języka F # i wiąże argumentów.</span><span class="sxs-lookup"><span data-stu-id="59fa5-131">Matches an F# exception type and binds the arguments.</span></span>|
|<span data-ttu-id="59fa5-132">*Identyfikator*</span><span class="sxs-lookup"><span data-stu-id="59fa5-132">*identifier*</span></span>|<span data-ttu-id="59fa5-133">Zgodny z żadnym wyjątku i wiąże nazwę obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="59fa5-133">Matches any exception and binds the name to the exception object.</span></span> <span data-ttu-id="59fa5-134">Odpowiednikiem **:? System.Exception jako***identyfikator*</span><span class="sxs-lookup"><span data-stu-id="59fa5-134">Equivalent to **:? System.Exception as***identifier*</span></span>|
|<span data-ttu-id="59fa5-135">*Identyfikator* podczas *warunku*</span><span class="sxs-lookup"><span data-stu-id="59fa5-135">*identifier* when *condition*</span></span>|<span data-ttu-id="59fa5-136">Odpowiada wyjątku, jeśli wynikiem warunku jest PRAWDA.</span><span class="sxs-lookup"><span data-stu-id="59fa5-136">Matches any exception if the condition is true.</span></span>|

## <a name="examples"></a><span data-ttu-id="59fa5-137">Przykłady</span><span class="sxs-lookup"><span data-stu-id="59fa5-137">Examples</span></span>
<span data-ttu-id="59fa5-138">W poniższych przykładach kodu ilustrują korzystanie z różnych wzorców obsługi wyjątków.</span><span class="sxs-lookup"><span data-stu-id="59fa5-138">The following code examples illustrate the use of the various exception handler patterns.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet5602.fs)]
    
>[!NOTE] 
<span data-ttu-id="59fa5-139">`try...with` Konstrukcja jest oddzielne wyrażenie z `try...finally` wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="59fa5-139">The `try...with` construct is a separate expression from the `try...finally` expression.</span></span> <span data-ttu-id="59fa5-140">W związku z tym jeśli kod wymaga obu `with` bloku i `finally` bloku, konieczne będzie zagnieździć dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="59fa5-140">Therefore, if your code requires both a `with` block and a `finally` block, you will have to nest the two expressions.</span></span>

>[!NOTE] 
<span data-ttu-id="59fa5-141">Można użyć `try...with` w Asynchroniczne przepływy pracy i inne wyrażenia obliczeń, w których przypadku dostosowaną wersję `try...with` wyrażenie jest używane.</span><span class="sxs-lookup"><span data-stu-id="59fa5-141">You can use `try...with` in asynchronous workflows and other computation expressions, in which case a customized version of the `try...with` expression is used.</span></span> <span data-ttu-id="59fa5-142">Aby uzyskać więcej informacji, zobacz [Asynchroniczne przepływy pracy](../asynchronous-workflows.md), i [wyrażenia obliczeń](../computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="59fa5-142">For more information, see [Asynchronous Workflows](../asynchronous-workflows.md), and [Computation Expressions](../computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="59fa5-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="59fa5-143">See Also</span></span>
[<span data-ttu-id="59fa5-144">Obsługa wyjątków</span><span class="sxs-lookup"><span data-stu-id="59fa5-144">Exception Handling</span></span>](index.md)

[<span data-ttu-id="59fa5-145">Typy wyjątków</span><span class="sxs-lookup"><span data-stu-id="59fa5-145">Exception Types</span></span>](exception-types.md)

[<span data-ttu-id="59fa5-146">Wyjątki: `try...finally` wyrażenia</span><span class="sxs-lookup"><span data-stu-id="59fa5-146">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)