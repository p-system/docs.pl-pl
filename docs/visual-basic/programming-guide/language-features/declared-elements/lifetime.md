---
title: Okres istnienia w Visual Basic
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- static variables [Visual Basic], lifetime
- static variables [Visual Basic], Visual Basic
- declared elements [Visual Basic], lifetime
- Shared variable lifetime [Visual Basic]
- lifetime [Visual Basic], declared elements
- lifetime [Visual Basic], Visual Basic
- lifetime [Visual Basic]
ms.assetid: bd91e390-690a-469a-9946-8dca70bc14e7
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 999490885571889b2de911cc14754f8db257d0af
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="lifetime-in-visual-basic"></a><span data-ttu-id="ba538-102">Okres istnienia w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba538-102">Lifetime in Visual Basic</span></span>
<span data-ttu-id="ba538-103">*Okres istnienia* elementu zadeklarowane jest okres, w którym jest dostępny do użytku.</span><span class="sxs-lookup"><span data-stu-id="ba538-103">The *lifetime* of a declared element is the period of time during which it is available for use.</span></span> <span data-ttu-id="ba538-104">Zmienne są tylko elementy, które mają cykl życia.</span><span class="sxs-lookup"><span data-stu-id="ba538-104">Variables are the only elements that have lifetime.</span></span> <span data-ttu-id="ba538-105">W tym celu kompilator traktuje parametry procedury i funkcja zwraca jako szczególnych przypadkach zmiennych.</span><span class="sxs-lookup"><span data-stu-id="ba538-105">For this purpose, the compiler treats procedure parameters and function returns as special cases of variables.</span></span> <span data-ttu-id="ba538-106">Okres istnienia zmiennej, która reprezentuje okres, w którym można zapisać wartości.</span><span class="sxs-lookup"><span data-stu-id="ba538-106">The lifetime of a variable represents the period of time during which it can hold a value.</span></span> <span data-ttu-id="ba538-107">Wartość można zmienić jego okresu istnienia, ale zawsze zawiera niektóre wartości.</span><span class="sxs-lookup"><span data-stu-id="ba538-107">Its value can change over its lifetime, but it always holds some value.</span></span>  
  
## <a name="different-lifetimes"></a><span data-ttu-id="ba538-108">Różne okresy istnienia</span><span class="sxs-lookup"><span data-stu-id="ba538-108">Different Lifetimes</span></span>  
 <span data-ttu-id="ba538-109">A *zmiennej członkowskiej* (zadeklarowane na poziomie modułu, poza dowolnej procedury) zwykle ma tego samego istnienia jako element, w którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="ba538-109">A *member variable* (declared at module level, outside any procedure) typically has the same lifetime as the element in which it is declared.</span></span> <span data-ttu-id="ba538-110">Udostępniana Zmienna zadeklarowana w klasie lub strukturze istnieje jako oddzielna kopia dla każdego wystąpienia klasy lub struktury, w którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="ba538-110">A nonshared variable declared in a class or structure exists as a separate copy for each instance of the class or structure in which it is declared.</span></span> <span data-ttu-id="ba538-111">Każdej z takich zmiennej ma tego samego czas istnienia jako jego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ba538-111">Each such variable has the same lifetime as its instance.</span></span> <span data-ttu-id="ba538-112">Jednak `Shared` zmienna ma tylko jeden okres istnienia, który jest ważny przez cały czas, aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="ba538-112">However, a `Shared` variable has only a single lifetime, which lasts for the entire time your application is running.</span></span>  
  
 <span data-ttu-id="ba538-113">A *zmiennej lokalnej* (zadeklarowana wewnątrz procedury) istnieje tylko w czasie wykonywania procedury, w którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="ba538-113">A *local variable* (declared inside a procedure) exists only while the procedure in which it is declared is running.</span></span> <span data-ttu-id="ba538-114">Dotyczy to również parametry tej procedury i zwrot funkcji.</span><span class="sxs-lookup"><span data-stu-id="ba538-114">This applies also to that procedure's parameters and to any function return.</span></span> <span data-ttu-id="ba538-115">Jednak jeśli tej procedury wywołuje innych procedur, zmienne lokalne przechowywać ich wartości podczas wykonywania procedury o nazwie.</span><span class="sxs-lookup"><span data-stu-id="ba538-115">However, if that procedure calls other procedures, the local variables retain their values while the called procedures are running.</span></span>  
  
## <a name="beginning-of-lifetime"></a><span data-ttu-id="ba538-116">Początek okresu istnienia</span><span class="sxs-lookup"><span data-stu-id="ba538-116">Beginning of Lifetime</span></span>  
 <span data-ttu-id="ba538-117">Okres istnienia zmiennej lokalnej uruchamia się, gdy formant przechodzi procedury, w którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="ba538-117">A local variable's lifetime begins when control enters the procedure in which it is declared.</span></span> <span data-ttu-id="ba538-118">Co lokalnego zmienna jest ustawiana na wartość domyślną dla tego typu danych, natychmiast rozpoczyna się procedura uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="ba538-118">Every local variable is initialized to the default value for its data type as soon as the procedure begins running.</span></span> <span data-ttu-id="ba538-119">Gdy wystąpi procedury `Dim` instrukcji, która określa wartości początkowej, ustawia tych zmiennych tych wartości, nawet jeśli kod ma już przypisanego inne wartości.</span><span class="sxs-lookup"><span data-stu-id="ba538-119">When the procedure encounters a `Dim` statement that specifies initial values, it sets those variables to those values, even if your code had already assigned other values to them.</span></span>  
  
 <span data-ttu-id="ba538-120">Każdy element członkowski zmiennej struktury został zainicjowany, tak jakby był on osobnej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ba538-120">Each member of a structure variable is initialized as if it were a separate variable.</span></span> <span data-ttu-id="ba538-121">Podobnie każdy element tablicy zmiennej zainicjowano pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="ba538-121">Similarly, each element of an array variable is initialized individually.</span></span>  
  
 <span data-ttu-id="ba538-122">Zmienne zadeklarowane w bloku wewnątrz procedury (takie jak `For` pętli) są inicjowane przy wejściu do procedury.</span><span class="sxs-lookup"><span data-stu-id="ba538-122">Variables declared within a block inside a procedure (such as a `For` loop) are initialized on entry to the procedure.</span></span> <span data-ttu-id="ba538-123">Te inicjalizacji zaczynają obowiązywać, czy kod kiedykolwiek wykonuje bloku.</span><span class="sxs-lookup"><span data-stu-id="ba538-123">These initializations take effect whether or not your code ever executes the block.</span></span>  
  
## <a name="end-of-lifetime"></a><span data-ttu-id="ba538-124">Koniec okresu istnienia</span><span class="sxs-lookup"><span data-stu-id="ba538-124">End of Lifetime</span></span>  
 <span data-ttu-id="ba538-125">Podczas procedury składowanej, nie są zachowywane wartości jego zmienne lokalne, i [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zwraca ich pamięci.</span><span class="sxs-lookup"><span data-stu-id="ba538-125">When a procedure terminates, the values of its local variables are not preserved, and [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] reclaims their memory.</span></span> <span data-ttu-id="ba538-126">Podczas następnego wywołania tej procedury, jego zmiennych lokalnych są nowo utworzone i zainicjowane ponownie.</span><span class="sxs-lookup"><span data-stu-id="ba538-126">The next time you call the procedure, all its local variables are created afresh and reinitialized.</span></span>  
  
 <span data-ttu-id="ba538-127">Gdy zakończenie wystąpienia klasy lub struktury, udostępniana zmienne utratę ich pamięci i ich wartości.</span><span class="sxs-lookup"><span data-stu-id="ba538-127">When an instance of a class or structure terminates, its nonshared variables lose their memory and their values.</span></span> <span data-ttu-id="ba538-128">Każde nowe wystąpienie klasy lub struktury, tworzy i ponownie inicjuje udostępniana zmienne.</span><span class="sxs-lookup"><span data-stu-id="ba538-128">Each new instance of the class or structure creates and reinitializes its nonshared variables.</span></span> <span data-ttu-id="ba538-129">Jednak `Shared` zmienne są zachowywane, dopóki aplikacja przestanie działać.</span><span class="sxs-lookup"><span data-stu-id="ba538-129">However, `Shared` variables are preserved until your application stops running.</span></span>  
  
## <a name="extension-of-lifetime"></a><span data-ttu-id="ba538-130">Rozszerzenia okresu istnienia</span><span class="sxs-lookup"><span data-stu-id="ba538-130">Extension of Lifetime</span></span>  
 <span data-ttu-id="ba538-131">Deklarowanie zmiennej lokalnej o `Static` — słowo kluczowe, jego okres istnienia jest dłuższy niż czas wykonania jego procedury.</span><span class="sxs-lookup"><span data-stu-id="ba538-131">If you declare a local variable with the `Static` keyword, its lifetime is longer than the execution time of its procedure.</span></span> <span data-ttu-id="ba538-132">W poniższej tabeli przedstawiono sposób deklaracji procedury określa, jak długo `Static` istnieje zmienna.</span><span class="sxs-lookup"><span data-stu-id="ba538-132">The following table shows how the procedure declaration determines how long a `Static` variable exists.</span></span>  
  
|<span data-ttu-id="ba538-133">Udostępnianie i procedury lokalizacji</span><span class="sxs-lookup"><span data-stu-id="ba538-133">Procedure location and sharing</span></span>|<span data-ttu-id="ba538-134">Rozpoczyna się statycznych zmiennych okres istnienia</span><span class="sxs-lookup"><span data-stu-id="ba538-134">Static variable lifetime begins</span></span>|<span data-ttu-id="ba538-135">Kończy statycznych zmiennych okres istnienia</span><span class="sxs-lookup"><span data-stu-id="ba538-135">Static variable lifetime ends</span></span>|  
|------------------------------------|-------------------------------------|-----------------------------------|  
|<span data-ttu-id="ba538-136">W module (domyślnie udostępnione)</span><span class="sxs-lookup"><span data-stu-id="ba538-136">In a module (shared by default)</span></span>|<span data-ttu-id="ba538-137">Procedura jest wywoływana po raz pierwszy</span><span class="sxs-lookup"><span data-stu-id="ba538-137">The first time the procedure is called</span></span>|<span data-ttu-id="ba538-138">Gdy aplikacja przestaje działać</span><span class="sxs-lookup"><span data-stu-id="ba538-138">When your application stops running</span></span>|  
|<span data-ttu-id="ba538-139">W klasie `Shared` (procedury nie ma elementu członkowskiego wystąpienia)</span><span class="sxs-lookup"><span data-stu-id="ba538-139">In a class, `Shared` (procedure is not an instance member)</span></span>|<span data-ttu-id="ba538-140">Po raz pierwszy procedura jest wywoływana na określonym wystąpieniu lub na nazwę klasy lub struktury, sama</span><span class="sxs-lookup"><span data-stu-id="ba538-140">The first time the procedure is called either on a specific instance or on the class or structure name itself</span></span>|<span data-ttu-id="ba538-141">Gdy aplikacja przestaje działać</span><span class="sxs-lookup"><span data-stu-id="ba538-141">When your application stops running</span></span>|  
|<span data-ttu-id="ba538-142">W wystąpieniu klasy nie `Shared` (procedura jest elementu członkowskiego wystąpienia)</span><span class="sxs-lookup"><span data-stu-id="ba538-142">In an instance of a class, not `Shared` (procedure is an instance member)</span></span>|<span data-ttu-id="ba538-143">Po raz pierwszy procedura jest wywoływana w ramach określonego wystąpienia</span><span class="sxs-lookup"><span data-stu-id="ba538-143">The first time the procedure is called on the specific instance</span></span>|<span data-ttu-id="ba538-144">Po zwolnieniu wystąpienie dla wyrzucanie elementów bezużytecznych (GC)</span><span class="sxs-lookup"><span data-stu-id="ba538-144">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="static-variables-of-the-same-name"></a><span data-ttu-id="ba538-145">Zmienne statyczne o takiej samej nazwie</span><span class="sxs-lookup"><span data-stu-id="ba538-145">Static Variables of the Same Name</span></span>  
 <span data-ttu-id="ba538-146">Można deklarować statycznych zmiennych o takiej samej nazwie w więcej niż jednej procedury.</span><span class="sxs-lookup"><span data-stu-id="ba538-146">You can declare static variables with the same name in more than one procedure.</span></span> <span data-ttu-id="ba538-147">Jeśli to zrobisz, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] każdej takie zmiennej jako oddzielny element uwzględnia kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ba538-147">If you do this, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler considers each such variable to be a separate element.</span></span> <span data-ttu-id="ba538-148">Inicjowanie jednej z tych zmiennych nie ma wpływu na inne wartości.</span><span class="sxs-lookup"><span data-stu-id="ba538-148">The initialization of one of these variables does not affect the values of the others.</span></span> <span data-ttu-id="ba538-149">Takie same w przypadku zdefiniowania procedury z zestawem przeciążenia ani deklarować statyczna zmienna o takiej samej nazwie w każdym przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="ba538-149">The same applies if you define a procedure with a set of overloads and declare a static variable with the same name in each overload.</span></span>  
  
## <a name="containing-elements-for-static-variables"></a><span data-ttu-id="ba538-150">Zawierający elementy zmienne statyczne</span><span class="sxs-lookup"><span data-stu-id="ba538-150">Containing Elements for Static Variables</span></span>  
 <span data-ttu-id="ba538-151">Statyczna zmienna lokalna w obrębie klasy, mogą zadeklarować oznacza to, wewnątrz procedury w tej klasie.</span><span class="sxs-lookup"><span data-stu-id="ba538-151">You can declare a static local variable within a class, that is, inside a procedure in that class.</span></span> <span data-ttu-id="ba538-152">Jednak statyczna zmienna lokalna w strukturze nie można zadeklarować jako element członkowski struktury lub jako zmienną lokalną, procedura w tej struktury.</span><span class="sxs-lookup"><span data-stu-id="ba538-152">However, you cannot declare a static local variable within a structure, either as a structure member or as a local variable of a procedure within that structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba538-153">Przykład</span><span class="sxs-lookup"><span data-stu-id="ba538-153">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="ba538-154">Opis</span><span class="sxs-lookup"><span data-stu-id="ba538-154">Description</span></span>  
 <span data-ttu-id="ba538-155">Poniższy przykład deklaruje zmienną z [statycznych](../../../../visual-basic/language-reference/modifiers/static.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="ba538-155">The following example declares a variable with the [Static](../../../../visual-basic/language-reference/modifiers/static.md) keyword.</span></span> <span data-ttu-id="ba538-156">(Należy pamiętać, że nie ma potrzeby `Dim` — słowo kluczowe podczas [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) korzysta z takich jak modyfikujący `Static`.)</span><span class="sxs-lookup"><span data-stu-id="ba538-156">(Note that you do not need the `Dim` keyword when the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) uses a modifier such as `Static`.)</span></span>  
  
### <a name="code"></a><span data-ttu-id="ba538-157">Kod</span><span class="sxs-lookup"><span data-stu-id="ba538-157">Code</span></span>  
 [!code-vb[VbVbalrKeywords#13](../../../../visual-basic/language-reference/codesnippet/VisualBasic/lifetime_1.vb)]  
  
### <a name="comments"></a><span data-ttu-id="ba538-158">Komentarze</span><span class="sxs-lookup"><span data-stu-id="ba538-158">Comments</span></span>  
 <span data-ttu-id="ba538-159">W powyższym przykładzie zmienna `applesSold` zachowany po procedurze `runningTotal` zwraca do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="ba538-159">In the preceding example, the variable `applesSold` continues to exist after the procedure `runningTotal` returns to the calling code.</span></span> <span data-ttu-id="ba538-160">Przy następnym `runningTotal` jest nazywany `applesSold` zachowuje jej wcześniej obliczoną wartość.</span><span class="sxs-lookup"><span data-stu-id="ba538-160">The next time `runningTotal` is called, `applesSold` retains its previously calculated value.</span></span>  
  
 <span data-ttu-id="ba538-161">Jeśli `applesSold` zadeklarowano bez użycia `Static`, poprzednie wartości wszystkich może nie zostać zachowane w wywołaniach `runningTotal`.</span><span class="sxs-lookup"><span data-stu-id="ba538-161">If `applesSold` had been declared without using `Static`, the previous accumulated values would not be preserved across calls to `runningTotal`.</span></span> <span data-ttu-id="ba538-162">Przy następnym `runningTotal` została wywołana, `applesSold` czy zostały odtworzone i ustawiana na 0, a `runningTotal` czy po prostu zwracane taką samą wartość, z którą została wywołana.</span><span class="sxs-lookup"><span data-stu-id="ba538-162">The next time `runningTotal` was called, `applesSold` would have been recreated and initialized to 0, and `runningTotal` would have simply returned the same value with which it was called.</span></span>  
  
### <a name="compiling-the-code"></a><span data-ttu-id="ba538-163">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ba538-163">Compiling the Code</span></span>  
 <span data-ttu-id="ba538-164">Można zainicjować wartość statyczna zmienna lokalna jako części swojej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="ba538-164">You can initialize the value of a static local variable as part of its declaration.</span></span> <span data-ttu-id="ba538-165">W przypadku tablicy jako `Static`, można zainicjować jego ranking (liczba wymiarów), długość każdego wymiaru i wartości poszczególne elementy.</span><span class="sxs-lookup"><span data-stu-id="ba538-165">If you declare an array to be `Static`, you can initialize its rank (number of dimensions), the length of each dimension, and the values of the individual elements.</span></span>  
  
### <a name="security"></a><span data-ttu-id="ba538-166">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="ba538-166">Security</span></span>  
 <span data-ttu-id="ba538-167">W poprzednim przykładzie, można utworzyć sam cykl życia przez zadeklarowanie `applesSold` na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="ba538-167">In the preceding example, you can produce the same lifetime by declaring `applesSold` at module level.</span></span> <span data-ttu-id="ba538-168">Po zmianie zakresu zmiennej w ten sposób jednak procedura będzie już wyłączny dostęp do niego.</span><span class="sxs-lookup"><span data-stu-id="ba538-168">If you changed the scope of a variable this way, however, the procedure would no longer have exclusive access to it.</span></span> <span data-ttu-id="ba538-169">Ponieważ można uzyskać dostępu do innych procedur `applesSold` i zmień jego wartość, sumę bieżącą może być zawodne i kod może być bardziej trudne w utrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="ba538-169">Because other procedures could access `applesSold` and change its value, the running total could be unreliable and the code could be more difficult to maintain.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba538-170">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ba538-170">See Also</span></span>  
 [<span data-ttu-id="ba538-171">Udostępnione</span><span class="sxs-lookup"><span data-stu-id="ba538-171">Shared</span></span>](../../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="ba538-172">Nothing</span><span class="sxs-lookup"><span data-stu-id="ba538-172">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="ba538-173">Zadeklarowane nazwy elementów</span><span class="sxs-lookup"><span data-stu-id="ba538-173">Declared Element Names</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="ba538-174">Odwołania do elementów zadeklarowanych</span><span class="sxs-lookup"><span data-stu-id="ba538-174">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="ba538-175">Zakres w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba538-175">Scope in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [<span data-ttu-id="ba538-176">Poziomy dostępu w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ba538-176">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="ba538-177">Zmienne</span><span class="sxs-lookup"><span data-stu-id="ba538-177">Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [<span data-ttu-id="ba538-178">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="ba538-178">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="ba538-179">Rozwiązywanie problemów z typów danych</span><span class="sxs-lookup"><span data-stu-id="ba538-179">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="ba538-180">Statyczne</span><span class="sxs-lookup"><span data-stu-id="ba538-180">Static</span></span>](../../../../visual-basic/language-reference/modifiers/static.md)