---
title: "Funkcje jako wartości pierwszej klasy (F#)"
description: "Dowiedz się, jak funkcje zostaną podniesione do najwyższej jakości stan w języku programowania w języku F #."
keywords: "Visual f #, f #, funkcjonalności programowania"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6b76b93b-a141-40f4-976c-7f0c558d6d09
ms.openlocfilehash: bca0e09edbe0aa86f0db746282acd4f4b3237a03
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="functions-as-first-class-values"></a><span data-ttu-id="d1383-104">Funkcje jako wartości pierwszej klasy</span><span class="sxs-lookup"><span data-stu-id="d1383-104">Functions as First-Class Values</span></span>

<span data-ttu-id="d1383-105">Definiowanie cech funkcjonalności języków programowania jest podniesienia uprawnień funkcji do pierwszej klasy stanu.</span><span class="sxs-lookup"><span data-stu-id="d1383-105">A defining characteristic of functional programming languages is the elevation of functions to first-class status.</span></span> <span data-ttu-id="d1383-106">Można będzie wykonać za pomocą funkcji niezależnie od można wykonać za pomocą wbudowanych typów wartości i można w tym celu o stopniu można porównywać pod względem nakładu pracy.</span><span class="sxs-lookup"><span data-stu-id="d1383-106">You should be able to do with a function whatever you can do with values of the other built-in types, and be able to do so with a comparable degree of effort.</span></span>

<span data-ttu-id="d1383-107">Następujące typowe środki najwyższej jakości stanu:</span><span class="sxs-lookup"><span data-stu-id="d1383-107">Typical measures of first-class status include the following:</span></span>

- <span data-ttu-id="d1383-108">Można powiązać funkcji do identyfikatorów?</span><span class="sxs-lookup"><span data-stu-id="d1383-108">Can you bind functions to identifiers?</span></span> <span data-ttu-id="d1383-109">Oznacza to możesz nadać im nazw?</span><span class="sxs-lookup"><span data-stu-id="d1383-109">That is, can you give them names?</span></span>

- <span data-ttu-id="d1383-110">Można przechowujesz funkcje w strukturach danych, takich jak na liście?</span><span class="sxs-lookup"><span data-stu-id="d1383-110">Can you store functions in data structures, such as in a list?</span></span>

- <span data-ttu-id="d1383-111">Można przekazać funkcji jako argument w wywołaniu funkcji?</span><span class="sxs-lookup"><span data-stu-id="d1383-111">Can you pass a function as an argument in a function call?</span></span>

- <span data-ttu-id="d1383-112">Można zwrócić funkcji po wywołaniu funkcji?</span><span class="sxs-lookup"><span data-stu-id="d1383-112">Can you return a function from a function call?</span></span>

<span data-ttu-id="d1383-113">Ostatnie dwa środki zdefiniować, co to są określane jako *operacji wyższego rzędu* lub *funkcje wyższego rzędu*.</span><span class="sxs-lookup"><span data-stu-id="d1383-113">The last two measures define what are known as *higher-order operations* or *higher-order functions*.</span></span> <span data-ttu-id="d1383-114">Funkcje wyższego rzędu zaakceptować funkcje jako argumenty i zwracać funkcji jako wartość wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1383-114">Higher-order functions accept functions as arguments and return functions as the value of function calls.</span></span> <span data-ttu-id="d1383-115">Te operacje obsługuje takie filarów programowanie funkcjonalne jako mapowanie funkcji i kompozycja funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1383-115">These operations support such mainstays of functional programming as mapping functions and composition of functions.</span></span>


## <a name="give-the-value-a-name"></a><span data-ttu-id="d1383-116">Nadaj nazwę wartości</span><span class="sxs-lookup"><span data-stu-id="d1383-116">Give the Value a Name</span></span>

<span data-ttu-id="d1383-117">Jeśli funkcja jest wartością najwyższej jakości, musi można nazwę, tak samo, jak można określić nazwę liczb całkowitych, ciągi i inne typy wbudowane.</span><span class="sxs-lookup"><span data-stu-id="d1383-117">If a function is a first-class value, you must be able to name it, just as you can name integers, strings, and other built-in types.</span></span> <span data-ttu-id="d1383-118">Jest to określane w funkcjonalności materiały programowania jako powiązanie identyfikator na wartość.</span><span class="sxs-lookup"><span data-stu-id="d1383-118">This is referred to in functional programming literature as binding an identifier to a value.</span></span> <span data-ttu-id="d1383-119">F # używa [ `let` powiązania](../language-reference/functions/let-bindings.md) można powiązać nazwy wartości: `let <identifier> = <value>`.</span><span class="sxs-lookup"><span data-stu-id="d1383-119">F# uses [`let` bindings](../language-reference/functions/let-bindings.md) to bind names to values: `let <identifier> = <value>`.</span></span> <span data-ttu-id="d1383-120">Poniższy kod przedstawia dwa przykłady.</span><span class="sxs-lookup"><span data-stu-id="d1383-120">The following code shows two examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet20.fs)]

<span data-ttu-id="d1383-121">Można określić nazwę funkcji równie łatwo.</span><span class="sxs-lookup"><span data-stu-id="d1383-121">You can name a function just as easily.</span></span> <span data-ttu-id="d1383-122">W poniższym przykładzie zdefiniowano funkcję o nazwie `squareIt` przez powiązanie identyfikatora `squareIt` do [wyrażenia lambda](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="d1383-122">The following example defines a function named `squareIt` by binding the identifier `squareIt` to the [lambda expression](../language-reference/functions/lambda-expressions-the-fun-keyword.md) `fun n -> n * n`.</span></span> <span data-ttu-id="d1383-123">Funkcja `squareIt` ma jeden parametr `n`, i zwraca kwadrat tego parametru.</span><span class="sxs-lookup"><span data-stu-id="d1383-123">Function `squareIt` has one parameter, `n`, and it returns the square of that parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

<span data-ttu-id="d1383-124">F # udostępnia następujące bardziej zwięzły składni uzyskanie takiego samego wyniku z mniej wpisywania.</span><span class="sxs-lookup"><span data-stu-id="d1383-124">F# provides the following more concise syntax to achieve the same result with less typing.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet22.fs)]

<span data-ttu-id="d1383-125">Przykłady, które należy wykonać przede wszystkim Użyj pierwszego stylu `let <function-name> = <lambda-expression>`, aby wyróżnić podobieństwa między deklaracji funkcji i deklaracji z innych typów wartości.</span><span class="sxs-lookup"><span data-stu-id="d1383-125">The examples that follow mostly use the first style, `let <function-name> = <lambda-expression>`, to emphasize the similarities between the declaration of functions and the declaration of other types of values.</span></span> <span data-ttu-id="d1383-126">Jednak wszystkie funkcje nazwany również można pisać ze zwięzłą składnią.</span><span class="sxs-lookup"><span data-stu-id="d1383-126">However, all the named functions can also be written with the concise syntax.</span></span> <span data-ttu-id="d1383-127">Przykłady są napisane w obu kierunkach.</span><span class="sxs-lookup"><span data-stu-id="d1383-127">Some of the examples are written in both ways.</span></span>


## <a name="store-the-value-in-a-data-structure"></a><span data-ttu-id="d1383-128">Przechowywanie wartości w strukturze danych</span><span class="sxs-lookup"><span data-stu-id="d1383-128">Store the Value in a Data Structure</span></span>

<span data-ttu-id="d1383-129">Wartości pierwszej klasy mogą być przechowywane w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="d1383-129">A first-class value can be stored in a data structure.</span></span> <span data-ttu-id="d1383-130">Poniższy kod przedstawia przykłady, których przechowywanie wartości na listach i spójnych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d1383-130">The following code shows examples that store values in lists and in tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet23.fs)]

<span data-ttu-id="d1383-131">Aby sprawdzić, czy nazwy funkcji przechowywane w spójnej kolekcji w rzeczywistości oceny funkcji, w poniższym przykładzie użyto `fst` i `snd` operatorom Wyodrębnij elementy pierwszej i drugiej z spójnej kolekcji `funAndArgTuple`.</span><span class="sxs-lookup"><span data-stu-id="d1383-131">To verify that a function name stored in a tuple does in fact evaluate to a function, the following example uses the `fst` and `snd` operators to extract the first and second elements from tuple `funAndArgTuple`.</span></span> <span data-ttu-id="d1383-132">Pierwszy element w spójnej kolekcji jest `squareIt` i drugi element `num`.</span><span class="sxs-lookup"><span data-stu-id="d1383-132">The first element in the tuple is `squareIt` and the second element is `num`.</span></span> <span data-ttu-id="d1383-133">Identyfikator `num` jest powiązana w poprzednim przykładzie do liczby całkowitej 10, prawidłowym argumentem dla `squareIt` funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1383-133">Identifier `num` is bound in a previous example to integer 10, a valid argument for the `squareIt` function.</span></span> <span data-ttu-id="d1383-134">Drugie wyrażenie dotyczy drugiego elementu w spójnej kolekcji pierwszym elementem w spójnej kolekcji: `squareIt num`.</span><span class="sxs-lookup"><span data-stu-id="d1383-134">The second expression applies the first element in the tuple to the second element in the tuple: `squareIt num`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet24.fs)]

<span data-ttu-id="d1383-135">Podobnie, po prostu jako identyfikator `num` i może być liczbą całkowitą 10 używane zamiennie, dlatego można identyfikator `squareIt` i wyrażenia lambda `fun n -> n * n`.</span><span class="sxs-lookup"><span data-stu-id="d1383-135">Similarly, just as identifier `num` and integer 10 can be used interchangeably, so can identifier `squareIt` and lambda expression `fun n -> n * n`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet25.fs)]
    
## <a name="pass-the-value-as-an-argument"></a><span data-ttu-id="d1383-136">Przekaż wartość jako Argument</span><span class="sxs-lookup"><span data-stu-id="d1383-136">Pass the Value as an Argument</span></span>

<span data-ttu-id="d1383-137">Jeśli wartość ma stan pierwszą klasą w języku, można przekazać go jako argument do funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1383-137">If a value has first-class status in a language, you can pass it as an argument to a function.</span></span> <span data-ttu-id="d1383-138">Na przykład jest typowe do przekazania liczb całkowitych i ciągi jako argumenty.</span><span class="sxs-lookup"><span data-stu-id="d1383-138">For example, it is common to pass integers and strings as arguments.</span></span> <span data-ttu-id="d1383-139">Poniższy kod przedstawia liczb całkowitych i ciągi przekazywane jako argumenty w języku F #.</span><span class="sxs-lookup"><span data-stu-id="d1383-139">The following code shows integers and strings passed as arguments in F#.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet26.fs)]

<span data-ttu-id="d1383-140">Jeśli stanem najwyższej jakości funkcji musi być przekazywane jako argumenty w taki sam sposób.</span><span class="sxs-lookup"><span data-stu-id="d1383-140">If functions have first-class status, you must be able to pass them as arguments in the same way.</span></span> <span data-ttu-id="d1383-141">Należy pamiętać, że jest to pierwszy charakterystyczne dla funkcji wyższego rzędu.</span><span class="sxs-lookup"><span data-stu-id="d1383-141">Remember that this is the first characteristic of higher-order functions.</span></span>

<span data-ttu-id="d1383-142">W poniższym przykładzie funkcja `applyIt` zawiera dwa parametry `op` i `arg`.</span><span class="sxs-lookup"><span data-stu-id="d1383-142">In the following example, function `applyIt` has two parameters, `op` and `arg`.</span></span> <span data-ttu-id="d1383-143">Po wysłaniu w funkcję, która przyjmuje jeden parametr `op` i odpowiednie argumentu dla funkcji `arg`, funkcja zwraca wynik zastosowania `op` do `arg`.</span><span class="sxs-lookup"><span data-stu-id="d1383-143">If you send in a function that has one parameter for `op` and an appropriate argument for the function to `arg`, the function returns the result of applying `op` to `arg`.</span></span> <span data-ttu-id="d1383-144">W poniższym przykładzie zarówno argument funkcji, jak i argument całkowitą są wysyłane w taki sam sposób, przy użyciu ich nazw.</span><span class="sxs-lookup"><span data-stu-id="d1383-144">In the following example, both the function argument and the integer argument are sent in the same way, by using their names.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet27.fs)]

<span data-ttu-id="d1383-145">Umożliwia wysyłanie funkcji jako argument do innej funkcji źródłową obiektów wspólnych abstrakcyjnych w funkcjonalności języków programowania, takimi jak operacje mapy albo filtr.</span><span class="sxs-lookup"><span data-stu-id="d1383-145">The ability to send a function as an argument to another function underlies common abstractions in functional programming languages, such as map or filter operations.</span></span> <span data-ttu-id="d1383-146">Operacja mapy, na przykład to funkcja wyższego rzędu przechwytujący obliczenia współużytkowane przez funkcje, które krokowo listy, Zrób coś do każdego elementu, a następnie wróć listę wyników.</span><span class="sxs-lookup"><span data-stu-id="d1383-146">A map operation, for example, is a higher-order function that captures the computation shared by functions that step through a list, do something to each element, and then return a list of the results.</span></span> <span data-ttu-id="d1383-147">Można zwiększyć każdy element na liście liczb całkowitych, kwadratowe każdy element lub zmienić każdy element na liście ciągi na wielkie litery.</span><span class="sxs-lookup"><span data-stu-id="d1383-147">You might want to increment each element in a list of integers, or to square each element, or to change each element in a list of strings to uppercase.</span></span> <span data-ttu-id="d1383-148">Podatnych część obliczenia to proces cyklicznego tej czynności za pośrednictwem listy i tworzy listę wyników do zwrócenia.</span><span class="sxs-lookup"><span data-stu-id="d1383-148">The error-prone part of the computation is the recursive process that steps through the list and builds a list of the results to return.</span></span> <span data-ttu-id="d1383-149">Tej części są przechwytywane w funkcji mapowania.</span><span class="sxs-lookup"><span data-stu-id="d1383-149">That part is captured in the mapping function.</span></span> <span data-ttu-id="d1383-150">Wszystkie trzeba napisać dla określonej aplikacji jest funkcji, które chcesz zastosować do każdego elementu listy pojedynczo (Dodawanie, squaring, zmienianie wielkości liter).</span><span class="sxs-lookup"><span data-stu-id="d1383-150">All you have to write for a particular application is the function that you want to apply to each list element individually (adding, squaring, changing case).</span></span> <span data-ttu-id="d1383-151">Czy funkcja jest wysyłany jako argument do funkcji mapowania podobnie jak `squareIt` są wysyłane do `applyIt` w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d1383-151">That function is sent as an argument to the mapping function, just as `squareIt` is sent to `applyIt` in the previous example.</span></span>

<span data-ttu-id="d1383-152">F # udostępnia metody mapy dla większości typów kolekcji, w tym [wymieniono](../language-reference/lists.md), [tablice](../language-reference/arrays.md), i [sekwencji](../language-reference/sequences.md).</span><span class="sxs-lookup"><span data-stu-id="d1383-152">F# provides map methods for most collection types, including [lists](../language-reference/lists.md), [arrays](../language-reference/arrays.md), and [sequences](../language-reference/sequences.md).</span></span> <span data-ttu-id="d1383-153">W poniższych przykładach użyto list.</span><span class="sxs-lookup"><span data-stu-id="d1383-153">The following examples use lists.</span></span> <span data-ttu-id="d1383-154">Składnia jest `List.map <the function> <the list>`.</span><span class="sxs-lookup"><span data-stu-id="d1383-154">The syntax is `List.map <the function> <the list>`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet28.fs)]

<span data-ttu-id="d1383-155">Aby uzyskać więcej informacji, zobacz [wymieniono](../language-reference/lists.md).</span><span class="sxs-lookup"><span data-stu-id="d1383-155">For more information, see [Lists](../language-reference/lists.md).</span></span>

## <a name="return-the-value-from-a-function-call"></a><span data-ttu-id="d1383-156">Zwracanie wartości z wywołania funkcji</span><span class="sxs-lookup"><span data-stu-id="d1383-156">Return the Value from a Function Call</span></span>

<span data-ttu-id="d1383-157">Na koniec Jeśli funkcja ma stan pierwszą klasą w języku, należy może zwrócić go jako wartość wywołanie funkcji tak samo, jak zwrócić innych typów, takich jak liczby całkowite i ciągi.</span><span class="sxs-lookup"><span data-stu-id="d1383-157">Finally, if a function has first-class status in a language, you must be able to return it as the value of a function call, just as you return other types, such as integers and strings.</span></span>

<span data-ttu-id="d1383-158">Następujące wywołania funkcji przywrócić liczb całkowitych i wyświetlić je.</span><span class="sxs-lookup"><span data-stu-id="d1383-158">The following function calls return integers and display them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet29.fs)]

<span data-ttu-id="d1383-159">Następujące wywołanie funkcja zwraca wartość typu ciąg.</span><span class="sxs-lookup"><span data-stu-id="d1383-159">The following function call returns a string.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet30.fs)]

<span data-ttu-id="d1383-160">Następujące wywołanie funkcji zadeklarowana śródwierszowo, zwraca wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="d1383-160">The following function call, declared inline, returns a Boolean value.</span></span> <span data-ttu-id="d1383-161">Wartość wyświetlana jest `True`.</span><span class="sxs-lookup"><span data-stu-id="d1383-161">The value displayed is `True`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet31.fs)]

<span data-ttu-id="d1383-162">Możliwość zwracania funkcji jako wartość wywołania funkcji jest drugi charakterystyczne dla funkcji wyższego rzędu.</span><span class="sxs-lookup"><span data-stu-id="d1383-162">The ability to return a function as the value of a function call is the second characteristic of higher-order functions.</span></span> <span data-ttu-id="d1383-163">W poniższym przykładzie `checkFor` jest zdefiniowane jako funkcję, która przyjmuje jeden argument `item`i zwraca nową funkcję jako jego wartość.</span><span class="sxs-lookup"><span data-stu-id="d1383-163">In the following example, `checkFor` is defined to be a function that takes one argument, `item`, and returns a new function as its value.</span></span> <span data-ttu-id="d1383-164">Zwrócony funkcja przyjmuje listę jako jej argument `lst`i wyszukuje `item` w `lst`.</span><span class="sxs-lookup"><span data-stu-id="d1383-164">The returned function takes a list as its argument, `lst`, and searches for `item` in `lst`.</span></span> <span data-ttu-id="d1383-165">Jeśli `item` jest obecny, funkcja zwraca `true`.</span><span class="sxs-lookup"><span data-stu-id="d1383-165">If `item` is present, the function returns `true`.</span></span> <span data-ttu-id="d1383-166">Jeśli `item` nie jest obecny, funkcja zwraca `false`.</span><span class="sxs-lookup"><span data-stu-id="d1383-166">If `item` is not present, the function returns `false`.</span></span> <span data-ttu-id="d1383-167">Jak w poprzedniej sekcji, w poniższym kodzie użyto funkcji dostarczona lista [list.EXISTS —](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), do listy wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="d1383-167">As in the previous section, the following code uses a provided list function, [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8), to search the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="d1383-168">Poniższy kod używa `checkFor` Aby utworzyć nową funkcję, która przyjmuje jeden argument, listy i wyszukuje 7 na liście.</span><span class="sxs-lookup"><span data-stu-id="d1383-168">The following code uses `checkFor` to create a new function that takes one argument, a list, and searches for 7 in the list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet33.fs)]

<span data-ttu-id="d1383-169">W poniższym przykładzie użyto najwyższej jakości stanu funkcji w języku F # w celu zadeklarowania funkcji, `compose`, która zwraca złożenie dwóch argumentów funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1383-169">The following example uses the first-class status of functions in F# to declare a function, `compose`, that returns a composition of two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet34.fs)]
    
>[!NOTE]
<span data-ttu-id="d1383-170">Nawet krótszą wersję zobacz następującą sekcję "Funkcje Curried."</span><span class="sxs-lookup"><span data-stu-id="d1383-170">For an even shorter version, see the following section, "Curried Functions."</span></span>


<span data-ttu-id="d1383-171">Poniższy kod wysyła dwie funkcje jako argumenty do `compose`, zarówno z zająć pojedynczy argument tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="d1383-171">The following code sends two functions as arguments to `compose`, both of which take a single argument of the same type.</span></span> <span data-ttu-id="d1383-172">Wartość zwracana jest nową funkcję, która jest złożeniem argumenty dwóch funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1383-172">The return value is a new function that is a composition of the two function arguments.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet35.fs)]
    
>[!NOTE] 
<span data-ttu-id="d1383-173">F # zawiera dwa operatory `<<` i `>>`, które tworzą funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1383-173">F# provides two operators, `<<` and `>>`, that compose functions.</span></span> <span data-ttu-id="d1383-174">Na przykład `let squareAndDouble2 = doubleIt << squareIt` jest odpowiednikiem `let squareAndDouble = compose doubleIt squareIt` w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d1383-174">For example, `let squareAndDouble2 = doubleIt << squareIt` is equivalent to `let squareAndDouble = compose doubleIt squareIt` in the previous example.</span></span>

<span data-ttu-id="d1383-175">Poniższy przykład przedstawia zwracanie funkcji jako wartość wywołania funkcji tworzy prosty odgadnięcie gier.</span><span class="sxs-lookup"><span data-stu-id="d1383-175">The following example of returning a function as the value of a function call creates a simple guessing game.</span></span> <span data-ttu-id="d1383-176">Do tworzenia gier, wywołaj `makeGame` o wartości mają ktoś odgadnąć wysłanych `target`.</span><span class="sxs-lookup"><span data-stu-id="d1383-176">To create a game, call `makeGame` with the value that you want someone to guess sent in for `target`.</span></span> <span data-ttu-id="d1383-177">Wartość zwrócona przez funkcję `makeGame` to funkcja, która przyjmuje jeden argument. (wynik) i w raportach, czy wynik jest poprawna.</span><span class="sxs-lookup"><span data-stu-id="d1383-177">The return value from function `makeGame` is a function that takes one argument (the guess) and reports whether the guess is correct.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet36.fs)]

<span data-ttu-id="d1383-178">Poniższy kod wywołania `makeGame`, wysyłania wartości `7` dla `target`.</span><span class="sxs-lookup"><span data-stu-id="d1383-178">The following code calls `makeGame`, sending the value `7` for `target`.</span></span> <span data-ttu-id="d1383-179">Identyfikator `playGame` jest powiązany z wyrażeniem lambda zwrócony.</span><span class="sxs-lookup"><span data-stu-id="d1383-179">Identifier `playGame` is bound to the returned lambda expression.</span></span> <span data-ttu-id="d1383-180">W związku z tym `playGame` to funkcja, która przyjmuje jako jej argument jedną wartość dla `guess`.</span><span class="sxs-lookup"><span data-stu-id="d1383-180">Therefore, `playGame` is a function that takes as its one argument a value for `guess`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet37.fs)]
    
## <a name="curried-functions"></a><span data-ttu-id="d1383-181">Funkcje rozwinięte</span><span class="sxs-lookup"><span data-stu-id="d1383-181">Curried Functions</span></span>

<span data-ttu-id="d1383-182">Większość przykładów w poprzedniej sekcji mogą być zapisywane więcej zwięzłym dzięki wykorzystaniu niejawne *currying* w deklaracji funkcji F #.</span><span class="sxs-lookup"><span data-stu-id="d1383-182">Many of the examples in the previous section can be written more concisely by taking advantage of the implicit *currying* in F# function declarations.</span></span> <span data-ttu-id="d1383-183">Currying jest procesem, który przekształca funkcja, która ma więcej niż jeden parametr do serii osadzonych funkcji, z których każda ma jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="d1383-183">Currying is a process that transforms a function that has more than one parameter into a series of embedded functions, each of which has a single parameter.</span></span> <span data-ttu-id="d1383-184">W języku F # funkcje, które mają więcej niż jeden parametr są z założenia typu curried.</span><span class="sxs-lookup"><span data-stu-id="d1383-184">In F#, functions that have more than one parameter are inherently curried.</span></span> <span data-ttu-id="d1383-185">Na przykład `compose` z poprzedniej sekcji, można napisać tak, jak pokazano w następujący styl zwięzła, z trzema parametrami.</span><span class="sxs-lookup"><span data-stu-id="d1383-185">For example, `compose` from the previous section can be written as shown in the following concise style, with three parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet38.fs)]

<span data-ttu-id="d1383-186">Jednak wynik jest funkcją jeden parametr, który zwraca funkcję jeden parametr, który z kolei zwraca innej funkcji jeden parametr, jak pokazano w `compose4curried`.</span><span class="sxs-lookup"><span data-stu-id="d1383-186">However, the result is a function of one parameter that returns a function of one parameter that in turn returns another function of one parameter, as shown in `compose4curried`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet39.fs)]

<span data-ttu-id="d1383-187">Można uzyskać dostępu do tej funkcji na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="d1383-187">You can access this function in several ways.</span></span> <span data-ttu-id="d1383-188">Każdy z poniższych przykładach zwraca i wyświetla 18.</span><span class="sxs-lookup"><span data-stu-id="d1383-188">Each of the following examples returns and displays 18.</span></span> <span data-ttu-id="d1383-189">Można zastąpić `compose4` z `compose4curried` w jednym z przykładów.</span><span class="sxs-lookup"><span data-stu-id="d1383-189">You can replace `compose4` with `compose4curried` in any of the examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet40.fs)]

<span data-ttu-id="d1383-190">Aby zweryfikować, że nadal działa tak jak poprzednio, spróbuj ponownie oryginalnej przypadków testowych.</span><span class="sxs-lookup"><span data-stu-id="d1383-190">To verify that the function still works as it did before, try the original test cases again.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet41.fs)]
    
>[!NOTE] 
<span data-ttu-id="d1383-191">Można ograniczyć currying umieszczając parametrów w spójnych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="d1383-191">You can restrict currying by enclosing parameters in tuples.</span></span> <span data-ttu-id="d1383-192">Aby uzyskać więcej informacji, zobacz "Parametr wzorce" w [parametry i argumenty](../language-reference/parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="d1383-192">For more information, see "Parameter Patterns" in [Parameters and Arguments](../language-reference/parameters-and-arguments.md).</span></span>

<span data-ttu-id="d1383-193">W poniższym przykładzie użyto niejawne currying zapisu krótszą wersję `makeGame`.</span><span class="sxs-lookup"><span data-stu-id="d1383-193">The following example uses implicit currying to write a shorter version of `makeGame`.</span></span> <span data-ttu-id="d1383-194">Szczegóły dotyczące `makeGame` tworzy i zwraca `game` funkcji są mniej jawną w następującym formacie, ale można sprawdzić za pomocą oryginalnego przypadków testowych, czy wynik jest taka sama.</span><span class="sxs-lookup"><span data-stu-id="d1383-194">The details of how `makeGame` constructs and returns the `game` function are less explicit in this format, but you can verify by using the original test cases that the result is the same.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet42.fs)]

<span data-ttu-id="d1383-195">Aby uzyskać więcej informacji na temat currying, zobacz "Częściowe aplikacji argumenty" w [funkcji](../language-reference/functions/index.md).</span><span class="sxs-lookup"><span data-stu-id="d1383-195">For more information about currying, see "Partial Application of Arguments" in [Functions](../language-reference/functions/index.md).</span></span>


## <a name="identifier-and-function-definition-are-interchangeable"></a><span data-ttu-id="d1383-196">Identyfikator i definicji funkcji są wymienne</span><span class="sxs-lookup"><span data-stu-id="d1383-196">Identifier and Function Definition Are Interchangeable</span></span>
<span data-ttu-id="d1383-197">Nazwa zmiennej `num` w poprzedniej przykłady ocenia do liczby całkowitej 10, a następnie niespodziewanego nie jest to, w którym `num` jest prawidłowy, 10 jest również prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="d1383-197">The variable name `num` in the previous examples evaluates to the integer 10, and it is no surprise that where `num` is valid, 10 is also valid.</span></span> <span data-ttu-id="d1383-198">To samo dotyczy funkcji identyfikatorów i wartości: gdziekolwiek może służyć nazwa funkcji, można użyć wyrażenia lambda, z którą jest powiązany.</span><span class="sxs-lookup"><span data-stu-id="d1383-198">The same is true of function identifiers and their values: anywhere the name of the function can be used, the lambda expression to which it is bound can be used.</span></span>

<span data-ttu-id="d1383-199">W poniższym przykładzie zdefiniowano `Boolean` wywołana funkcja `isNegative`, a następnie zamiennie używa nazwy funkcji i definicji funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1383-199">The following example defines a `Boolean` function called `isNegative`, and then uses the name of the function and the definition of the function interchangeably.</span></span> <span data-ttu-id="d1383-200">Przykłady trzech kolejnych wszystkie wrócić i wyświetlić `False`.</span><span class="sxs-lookup"><span data-stu-id="d1383-200">The next three examples all return and display `False`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet43.fs)]

<span data-ttu-id="d1383-201">Podejmowanie go jednym kroku, należy zastąpić wartość która `applyIt` jest powiązany z dla `applyIt`.</span><span class="sxs-lookup"><span data-stu-id="d1383-201">To take it one step further, substitute the value that `applyIt` is bound to for `applyIt`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet44.fs)]

## <a name="functions-are-first-class-values-in-f"></a><span data-ttu-id="d1383-202">Funkcje są wartości pierwszej klasy w języku F #</span><span class="sxs-lookup"><span data-stu-id="d1383-202">Functions Are First-Class Values in F#</span></span> #

<span data-ttu-id="d1383-203">Przykłady w poprzednich sekcjach pokazują, że funkcje w języku F # spełniają kryteria są wartości pierwszej klasy w języku F #:</span><span class="sxs-lookup"><span data-stu-id="d1383-203">The examples in the previous sections demonstrate that functions in F# satisfy the criteria for being first-class values in F#:</span></span>

- <span data-ttu-id="d1383-204">Identyfikator można powiązać z definicji funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1383-204">You can bind an identifier to a function definition.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet21.fs)]

- <span data-ttu-id="d1383-205">Funkcja można przechowywać w strukturze danych.</span><span class="sxs-lookup"><span data-stu-id="d1383-205">You can store a function in a data structure.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet45.fs)]

- <span data-ttu-id="d1383-206">Funkcja można przekazać jako argument.</span><span class="sxs-lookup"><span data-stu-id="d1383-206">You can pass a function as an argument.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet46.fs)]

- <span data-ttu-id="d1383-207">Funkcja może zwrócić jako wartość wywołania funkcji.</span><span class="sxs-lookup"><span data-stu-id="d1383-207">You can return a function as the value of a function call.</span></span>
[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet32.fs)]

<span data-ttu-id="d1383-208">Aby uzyskać więcej informacji na temat języka F #, zobacz [dokumentację języka F #](../language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="d1383-208">For more information about F#, see the [F# Language Reference](../language-reference/index.md).</span></span>

## <a name="example"></a><span data-ttu-id="d1383-209">Przykład</span><span class="sxs-lookup"><span data-stu-id="d1383-209">Example</span></span>

### <a name="description"></a><span data-ttu-id="d1383-210">Opis</span><span class="sxs-lookup"><span data-stu-id="d1383-210">Description</span></span>

<span data-ttu-id="d1383-211">Poniższy kod zawiera wszystkie przykłady w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="d1383-211">The following code contains all the examples in this topic.</span></span>

### <a name="code"></a><span data-ttu-id="d1383-212">Kod</span><span class="sxs-lookup"><span data-stu-id="d1383-212">Code</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/contour/snippet47.fs)]
    
## <a name="see-also"></a><span data-ttu-id="d1383-213">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1383-213">See Also</span></span>

[<span data-ttu-id="d1383-214">Wyświetla listę</span><span class="sxs-lookup"><span data-stu-id="d1383-214">Lists</span></span>](../language-reference/lists.md)

[<span data-ttu-id="d1383-215">Krotki</span><span class="sxs-lookup"><span data-stu-id="d1383-215">Tuples</span></span>](../language-reference/tuples.md)

[<span data-ttu-id="d1383-216">Funkcje</span><span class="sxs-lookup"><span data-stu-id="d1383-216">Functions</span></span>](../language-reference/functions/index.md)

[<span data-ttu-id="d1383-217">`let`Powiązania</span><span class="sxs-lookup"><span data-stu-id="d1383-217">`let` Bindings</span></span>](../language-reference/functions/let-bindings.md)

[<span data-ttu-id="d1383-218">Wyrażenia lambda: `fun` — słowo kluczowe</span><span class="sxs-lookup"><span data-stu-id="d1383-218">Lambda Expressions: The `fun` Keyword</span></span>](../language-reference/functions/lambda-expressions-the-fun-keyword.md)