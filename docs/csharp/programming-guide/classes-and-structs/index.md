---
title: "Klasy i struktury (Przewodnik programowania w języku C#)"
description: "Zawiera opis klas i struktur (struktury) w języku C#."
keywords: "klasy (C#), struktur (C#) i struktury (struktury) (C#), typy odwołań (C#) typy wartości (C#)"
ms.date: 01/17/2016
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- structs [C#], about structs
- classes [C#], overview
- C# language, structs
- C# language, objects
- objects [C#]
- C# language, classes
ms.assetid: cc39dbda-8754-423e-b5b1-16a1db0734c0
caps.latest.revision: "48"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8c4cbbdd0384c0c0e97d6a7c655e798d0562d9a8
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2017
---
# <a name="classes-and-structs-c-programming-guide"></a><span data-ttu-id="129e0-104">Klasy i struktury (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="129e0-104">Classes and Structs (C# Programming Guide)</span></span>
<span data-ttu-id="129e0-105">Klasy i struktury są dwa podstawowe konstrukcje system typu wspólnego w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="129e0-105">Classes and structs are two of the basic constructs of the common type system in the .NET Framework.</span></span> <span data-ttu-id="129e0-106">Każdy jest zasadniczo to struktura danych, która hermetyzuje zestaw danych i zachowania, które należy razem jako jednostki logicznej.</span><span class="sxs-lookup"><span data-stu-id="129e0-106">Each is essentially a data structure that encapsulates a set of data and behaviors that belong together as a logical unit.</span></span> <span data-ttu-id="129e0-107">Danych i zachowania *członków* klasy lub struktury, i wymienionych w dalszej części tego tematu zawierają metody, właściwości i zdarzeń i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="129e0-107">The data and behaviors are the *members* of the class or struct, and they include its methods, properties, and events, and so on, as listed later in this topic.</span></span>  
  
 <span data-ttu-id="129e0-108">Deklaracja klasy lub struktury jest podobny do planu, który jest używany do tworzenia wystąpień lub obiektów w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="129e0-108">A class or struct declaration is like a blueprint that is used to create instances or objects at run time.</span></span> <span data-ttu-id="129e0-109">Po zdefiniowaniu klasy lub struktury o nazwie `Person`, `Person` jest nazwa typu.</span><span class="sxs-lookup"><span data-stu-id="129e0-109">If you define a class or struct called `Person`, `Person` is the name of the type.</span></span> <span data-ttu-id="129e0-110">Jeśli zadeklarować i zainicjuj zmienną `p` typu `Person`, `p` jest określany jako obiektu lub wystąpienie `Person`.</span><span class="sxs-lookup"><span data-stu-id="129e0-110">If you declare and initialize a variable `p` of type `Person`, `p` is said to be an object or instance of `Person`.</span></span> <span data-ttu-id="129e0-111">Wiele wystąpień tego samego `Person` można utworzyć typu, a każde wystąpienie mogą mieć różne wartości w polach i właściwości.</span><span class="sxs-lookup"><span data-stu-id="129e0-111">Multiple instances of the same `Person` type can be created, and each instance can have different values in its properties and fields.</span></span>  
  
 <span data-ttu-id="129e0-112">Klasa jest typem referencyjnym.</span><span class="sxs-lookup"><span data-stu-id="129e0-112">A class is a reference type.</span></span> <span data-ttu-id="129e0-113">Po utworzeniu obiektu klasy zmiennej, do której przypisano obiekt zawiera tylko odwołanie do pamięci.</span><span class="sxs-lookup"><span data-stu-id="129e0-113">When an object of the class is created, the variable to which the object is assigned holds only a reference to that memory.</span></span> <span data-ttu-id="129e0-114">Gdy odwołanie do obiektu jest przypisany do nowej zmiennej, nowej zmiennej odwołuje się do oryginalnego obiektu.</span><span class="sxs-lookup"><span data-stu-id="129e0-114">When the object reference is assigned to a new variable, the new variable refers to the original object.</span></span> <span data-ttu-id="129e0-115">Zmiany wprowadzane za pośrednictwem jednej zmiennej są odzwierciedlane w innej zmiennej obydwie odwołuje się do tych samych danych.</span><span class="sxs-lookup"><span data-stu-id="129e0-115">Changes made through one variable are reflected in the other variable because they both refer to the same data.</span></span>  
  
 <span data-ttu-id="129e0-116">Struktury jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="129e0-116">A struct is a value type.</span></span> <span data-ttu-id="129e0-117">Podczas tworzenia struktury zmiennej, do której przypisano struktury zawiera struktury danych rzeczywistych.</span><span class="sxs-lookup"><span data-stu-id="129e0-117">When a struct is created, the variable to which the struct is assigned holds the struct's actual data.</span></span> <span data-ttu-id="129e0-118">Struktura jest przypisany do nowej zmiennej, są kopiowane.</span><span class="sxs-lookup"><span data-stu-id="129e0-118">When the struct is assigned to a new variable, it is copied.</span></span> <span data-ttu-id="129e0-119">Nową zmienną i pierwotnej zmiennej w związku z tym zawierają dwa osobne kopie tych samych danych.</span><span class="sxs-lookup"><span data-stu-id="129e0-119">The new variable and the original variable therefore contain two separate copies of the same data.</span></span> <span data-ttu-id="129e0-120">Zmiany wprowadzone w jednej kopii nie wpływają na innej kopii.</span><span class="sxs-lookup"><span data-stu-id="129e0-120">Changes made to one copy do not affect the other copy.</span></span>  
  
 <span data-ttu-id="129e0-121">Ogólnie rzecz biorąc klasy służą do modelowania bardziej złożonych zachowanie lub dane, które ma na celu można zmodyfikować po utworzeniu obiektu klasy.</span><span class="sxs-lookup"><span data-stu-id="129e0-121">In general, classes are used to model more complex behavior, or data that is intended to be modified after a class object is created.</span></span> <span data-ttu-id="129e0-122">Struktury są najbardziej odpowiednie dla struktur danych w małych, które zawierają głównie dane, które nie jest przeznaczona do można zmodyfikować po utworzeniu struktury.</span><span class="sxs-lookup"><span data-stu-id="129e0-122">Structs are best suited for small data structures that contain primarily data that is not intended to be modified after the struct is created.</span></span>  
  
 <span data-ttu-id="129e0-123">Aby uzyskać więcej informacji, zobacz [klasy](../../../csharp/programming-guide/classes-and-structs/classes.md), [obiektów](../../../csharp/programming-guide/classes-and-structs/objects.md), i [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="129e0-123">For more information, see [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md), [Objects](../../../csharp/programming-guide/classes-and-structs/objects.md), and [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="129e0-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="129e0-124">Example</span></span>  
 <span data-ttu-id="129e0-125">W poniższym przykładzie `CustomClass` w `ProgrammingGuide` przestrzeń nazw ma trzy elementy członkowskie: konstruktor wystąpień, właściwość o nazwie `Number`i metodę o nazwie `Multiply`.</span><span class="sxs-lookup"><span data-stu-id="129e0-125">In the following example, `CustomClass` in the `ProgrammingGuide` namespace has three members: an instance constructor, a property named `Number`, and a method named `Multiply`.</span></span> <span data-ttu-id="129e0-126">`Main` Metody w `Program` klasy tworzy wystąpienie (obiekt) `CustomClass`, oraz metody i właściwości obiektu są dostępne przy użyciu notacji kropki.</span><span class="sxs-lookup"><span data-stu-id="129e0-126">The `Main` method in the `Program` class creates an instance (object) of `CustomClass`, and the object’s method and property are accessed by using dot notation.</span></span>
  
 [!code-csharp[csProgGuideObjects#1](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/class1.cs#1)]  
  
## <a name="encapsulation"></a><span data-ttu-id="129e0-127">Hermetyzacja protokołu</span><span class="sxs-lookup"><span data-stu-id="129e0-127">Encapsulation</span></span>  
 <span data-ttu-id="129e0-128">*Hermetyzacja* jest czasami nazywany pierwszego słupka lub zasada programowanie zorientowane obiektowo.</span><span class="sxs-lookup"><span data-stu-id="129e0-128">*Encapsulation* is sometimes referred to as the first pillar or principle of object-oriented programming.</span></span> <span data-ttu-id="129e0-129">Zgodnie z zasadą hermetyzacji klasie lub strukturze można określić, jak przystępna wszystkich członków jest kod poza klasą lub strukturą.</span><span class="sxs-lookup"><span data-stu-id="129e0-129">According to the principle of encapsulation, a class or struct can specify how accessible each of its members is to code outside of the class or struct.</span></span> <span data-ttu-id="129e0-130">Aby ograniczyć możliwość kodowania błędy lub złośliwe oprogramowanie może być ukryte metod i zmienne, które nie są przeznaczone do użycia w poza klasy lub zestawu.</span><span class="sxs-lookup"><span data-stu-id="129e0-130">Methods and variables that are not intended to be used from outside of the class or assembly can be hidden to limit the potential for coding errors or malicious exploits.</span></span>  
  
 <span data-ttu-id="129e0-131">Aby uzyskać więcej informacji na temat klas, zobacz [klasy](../../../csharp/programming-guide/classes-and-structs/classes.md) i [obiektów](../../../csharp/programming-guide/classes-and-structs/objects.md).</span><span class="sxs-lookup"><span data-stu-id="129e0-131">For more information about classes, see [Classes](../../../csharp/programming-guide/classes-and-structs/classes.md) and [Objects](../../../csharp/programming-guide/classes-and-structs/objects.md).</span></span>  
  
### <a name="members"></a><span data-ttu-id="129e0-132">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="129e0-132">Members</span></span>  
 <span data-ttu-id="129e0-133">Wszystkie metody, pola, stałe, właściwości i zdarzenia musi być zadeklarowana w typie; są one nazywane *członków* typu.</span><span class="sxs-lookup"><span data-stu-id="129e0-133">All methods, fields, constants, properties, and events must be declared within a type; these are called the *members* of the type.</span></span> <span data-ttu-id="129e0-134">W języku C# nie ma żadnych zmiennych globalnych ani metod się w przypadku niektórych innych języków.</span><span class="sxs-lookup"><span data-stu-id="129e0-134">In C#, there are no global variables or methods as there are in some other languages.</span></span> <span data-ttu-id="129e0-135">Nawet punktu wejścia programu `Main` metody, musi być zadeklarowana w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="129e0-135">Even a program's entry point, the `Main` method, must be declared within a class or struct.</span></span> <span data-ttu-id="129e0-136">Poniższa lista zawiera opisano różne typy elementów członkowskich, które może być zadeklarowana w klasie lub strukturze.</span><span class="sxs-lookup"><span data-stu-id="129e0-136">The following list includes all the various kinds of members that may be declared in a class or struct.</span></span>  
  
-   [<span data-ttu-id="129e0-137">Pola</span><span class="sxs-lookup"><span data-stu-id="129e0-137">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)  
  
-   [<span data-ttu-id="129e0-138">Stałe</span><span class="sxs-lookup"><span data-stu-id="129e0-138">Constants</span></span>](../../../csharp/programming-guide/classes-and-structs/constants.md)  
  
-   [<span data-ttu-id="129e0-139">Właściwości</span><span class="sxs-lookup"><span data-stu-id="129e0-139">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
  
-   [<span data-ttu-id="129e0-140">Metody</span><span class="sxs-lookup"><span data-stu-id="129e0-140">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
  
-   [<span data-ttu-id="129e0-141">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="129e0-141">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
  
-   [<span data-ttu-id="129e0-142">Zdarzenia</span><span class="sxs-lookup"><span data-stu-id="129e0-142">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
  
-   [<span data-ttu-id="129e0-143">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="129e0-143">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)  
  
-   [<span data-ttu-id="129e0-144">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="129e0-144">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
  
-   [<span data-ttu-id="129e0-145">Operatory</span><span class="sxs-lookup"><span data-stu-id="129e0-145">Operators</span></span>](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
  
-   [<span data-ttu-id="129e0-146">Zagnieżdżone typy</span><span class="sxs-lookup"><span data-stu-id="129e0-146">Nested Types</span></span>](../../../csharp/programming-guide/classes-and-structs/nested-types.md)  
  
### <a name="accessibility"></a><span data-ttu-id="129e0-147">Ułatwienia dostępu</span><span class="sxs-lookup"><span data-stu-id="129e0-147">Accessibility</span></span>  
 <span data-ttu-id="129e0-148">Niektóre metody i właściwości, które są przeznaczone do można wywołać lub uzyskać dostępu do z kodu spoza Twojej klasy lub struktury, znany jako *kodu klienta*.</span><span class="sxs-lookup"><span data-stu-id="129e0-148">Some methods and properties are meant to be called or accessed from code outside your class or struct, known as *client code*.</span></span> <span data-ttu-id="129e0-149">Inne metody i właściwości mogą być tylko do użytku w klasie lub strukturze, samej siebie.</span><span class="sxs-lookup"><span data-stu-id="129e0-149">Other methods and properties might be only for use in the class or struct itself.</span></span> <span data-ttu-id="129e0-150">Należy ograniczyć ułatwień dostępu kodu, tak aby tylko kodu przeznaczone klienckich można uzyskać do niej dostęp.</span><span class="sxs-lookup"><span data-stu-id="129e0-150">It is important to limit the accessibility of your code so that only the intended client code can reach it.</span></span> <span data-ttu-id="129e0-151">Można zdecydować, jak przystępna z typów i ich elementy członkowskie do kodu klienta za pomocą modyfikatorów dostępu [publicznego](../../../csharp/language-reference/keywords/public.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [ chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md), [prywatnej](../../../csharp/language-reference/keywords/private.md) i [prywatne chronione](../../../csharp/language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="129e0-151">You specify how accessible your types and their members are to client code by using the access modifiers [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md), [private](../../../csharp/language-reference/keywords/private.md) and [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="129e0-152">Dostępność domyślny jest `private`.</span><span class="sxs-lookup"><span data-stu-id="129e0-152">The default accessibility is `private`.</span></span> <span data-ttu-id="129e0-153">Aby uzyskać więcej informacji, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="129e0-153">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
### <a name="inheritance"></a><span data-ttu-id="129e0-154">Dziedziczenie</span><span class="sxs-lookup"><span data-stu-id="129e0-154">Inheritance</span></span>  
 <span data-ttu-id="129e0-155">Klasy (ale nie struktury) obsługuje koncepcja dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="129e0-155">Classes (but not structs) support the concept of inheritance.</span></span> <span data-ttu-id="129e0-156">Klasa, która pochodzi z innej klasy ( *klasa podstawowa*) automatycznie zawiera wszystkich publicznych, chronionych i wewnętrznych elementów członkowskich klasy podstawowej, z wyjątkiem jej konstruktorów i finalizatory.</span><span class="sxs-lookup"><span data-stu-id="129e0-156">A class that derives from another class (the *base class*) automatically contains all the public, protected, and internal members of the base class except its constructors and finalizers.</span></span> <span data-ttu-id="129e0-157">Aby uzyskać więcej informacji, zobacz [dziedziczenia](../../../csharp/programming-guide/classes-and-structs/inheritance.md) i [polimorfizm](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span><span class="sxs-lookup"><span data-stu-id="129e0-157">For more information, see [Inheritance](../../../csharp/programming-guide/classes-and-structs/inheritance.md) and [Polymorphism](../../../csharp/programming-guide/classes-and-structs/polymorphism.md).</span></span>  
  
 <span data-ttu-id="129e0-158">Klasy może być zadeklarowana jako [abstrakcyjny](../../../csharp/language-reference/keywords/abstract.md), co oznacza, że przynajmniej jedna z metod nie ma żadnej implementacji.</span><span class="sxs-lookup"><span data-stu-id="129e0-158">Classes may be declared as [abstract](../../../csharp/language-reference/keywords/abstract.md), which means that one or more of their methods have no implementation.</span></span> <span data-ttu-id="129e0-159">Mimo że nie można bezpośrednio utworzyć wystąpienia klasy abstrakcyjnej, mogą stanowić klasy podstawowe dla innych klas, które zapewniają Brak implementacji.</span><span class="sxs-lookup"><span data-stu-id="129e0-159">Although abstract classes cannot be instantiated directly, they can serve as base classes for other classes that provide the missing implementation.</span></span> <span data-ttu-id="129e0-160">Klasy mogą również być deklarowane jako [zapieczętowanego](../../../csharp/language-reference/keywords/sealed.md) aby dziedziczyły innych klas z nich.</span><span class="sxs-lookup"><span data-stu-id="129e0-160">Classes can also be declared as [sealed](../../../csharp/language-reference/keywords/sealed.md) to prevent other classes from inheriting from them.</span></span> <span data-ttu-id="129e0-161">Aby uzyskać więcej informacji, zobacz [abstrakcyjne i zapieczętowane klasy oraz członkowie klas](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="129e0-161">For more information, see [Abstract and Sealed Classes and Class Members](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
### <a name="interfaces"></a><span data-ttu-id="129e0-162">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="129e0-162">Interfaces</span></span>  
 <span data-ttu-id="129e0-163">Klasy i struktury może dziedziczyć wiele interfejsów.</span><span class="sxs-lookup"><span data-stu-id="129e0-163">Classes and structs can inherit multiple interfaces.</span></span> <span data-ttu-id="129e0-164">Można dziedziczyć interfejsu oznacza, że typ implementuje wszystkie metody, które są zdefiniowane w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="129e0-164">To inherit from an interface means that the type implements all the methods defined in the interface.</span></span> <span data-ttu-id="129e0-165">Aby uzyskać więcej informacji, zobacz [interfejsów](../../../csharp/programming-guide/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="129e0-165">For more information, see [Interfaces](../../../csharp/programming-guide/interfaces/index.md).</span></span>  
  
### <a name="generic-types"></a><span data-ttu-id="129e0-166">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="129e0-166">Generic Types</span></span>  
 <span data-ttu-id="129e0-167">Można zdefiniować klasy i struktury z co najmniej jednego parametru typu.</span><span class="sxs-lookup"><span data-stu-id="129e0-167">Classes and structs can be defined with one or more type parameters.</span></span> <span data-ttu-id="129e0-168">Kod klienta zawiera typ, podczas tworzenia wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="129e0-168">Client code supplies the type when it creates an instance of the type.</span></span> <span data-ttu-id="129e0-169">Na przykład <xref:System.Collections.Generic.List%601> klasy w <xref:System.Collections.Generic> przestrzeni nazw jest zdefiniowana z parametrem typu.</span><span class="sxs-lookup"><span data-stu-id="129e0-169">For example The <xref:System.Collections.Generic.List%601> class in the <xref:System.Collections.Generic> namespace is defined with one type parameter.</span></span> <span data-ttu-id="129e0-170">Kod klienta tworzy wystąpienie `List<string>` lub `List<int>` do określania typu, w którym będą przechowywane listy.</span><span class="sxs-lookup"><span data-stu-id="129e0-170">Client code creates an instance of a `List<string>` or `List<int>` to specify the type that the list will hold.</span></span> <span data-ttu-id="129e0-171">Aby uzyskać więcej informacji, zobacz [ogólne](../../../csharp/programming-guide/generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="129e0-171">For more information, see [Generics](../../../csharp/programming-guide/generics/index.md).</span></span>  
  
### <a name="static-types"></a><span data-ttu-id="129e0-172">Statyczne typy</span><span class="sxs-lookup"><span data-stu-id="129e0-172">Static Types</span></span>  
 <span data-ttu-id="129e0-173">Klasy (ale nie struktury) mogą być deklarowane jako [statycznych](../../../csharp/language-reference/keywords/static.md).</span><span class="sxs-lookup"><span data-stu-id="129e0-173">Classes (but not structs) can be declared as [static](../../../csharp/language-reference/keywords/static.md).</span></span> <span data-ttu-id="129e0-174">Klasa statyczna może zawierać tylko statyczne elementy członkowskie i nie można utworzyć wystąpienia o słowo kluczowe new.</span><span class="sxs-lookup"><span data-stu-id="129e0-174">A static class can contain only static members and cannot be instantiated with the new keyword.</span></span> <span data-ttu-id="129e0-175">Jedna kopia klasy jest ładowany do pamięci podczas ładowania programu i jej elementów członkowskich są dostępne za pośrednictwem nazwy klasy.</span><span class="sxs-lookup"><span data-stu-id="129e0-175">One copy of the class is loaded into memory when the program loads, and its members are accessed through the class name.</span></span> <span data-ttu-id="129e0-176">Zarówno klas i struktur może zawierać statycznych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="129e0-176">Both classes and structs can contain static members.</span></span> <span data-ttu-id="129e0-177">Aby uzyskać więcej informacji, zobacz [klasy statyczne i statycznych elementów członkowskich klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="129e0-177">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
### <a name="nested-types"></a><span data-ttu-id="129e0-178">Zagnieżdżone typy</span><span class="sxs-lookup"><span data-stu-id="129e0-178">Nested Types</span></span>  
 <span data-ttu-id="129e0-179">Klasy lub struktury, może być zagnieżdżona w innej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="129e0-179">A class or struct can be nested within another class or struct.</span></span> <span data-ttu-id="129e0-180">Aby uzyskać więcej informacji, zobacz [zagnieżdżone typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md).</span><span class="sxs-lookup"><span data-stu-id="129e0-180">For more information, see [Nested Types](../../../csharp/programming-guide/classes-and-structs/nested-types.md).</span></span>  
  
### <a name="partial-types"></a><span data-ttu-id="129e0-181">Typy częściowe</span><span class="sxs-lookup"><span data-stu-id="129e0-181">Partial Types</span></span>  
 <span data-ttu-id="129e0-182">Można zdefiniować klasy, struktury lub metoda w jednym pliku kodu i inną część w osobnym pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="129e0-182">You can define part of a class, struct or method in one code file and another part in a separate code file.</span></span> <span data-ttu-id="129e0-183">Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span><span class="sxs-lookup"><span data-stu-id="129e0-183">For more information, see [Partial Classes and Methods](../../../csharp/programming-guide/classes-and-structs/partial-classes-and-methods.md).</span></span>  
  
### <a name="object-initializers"></a><span data-ttu-id="129e0-184">Inicjatory obiektów</span><span class="sxs-lookup"><span data-stu-id="129e0-184">Object Initializers</span></span>  
 <span data-ttu-id="129e0-185">Można utworzyć wystąpienia i zainicjować klasy lub struktury obiektów i kolekcji obiektów, bez jawnie podczas wywoływania konstruktora ich.</span><span class="sxs-lookup"><span data-stu-id="129e0-185">You can instantiate and initialize class or struct objects, and collections of objects, without explicitly calling their constructor.</span></span> <span data-ttu-id="129e0-186">Aby uzyskać więcej informacji, zobacz [inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span><span class="sxs-lookup"><span data-stu-id="129e0-186">For more information, see [Object and Collection Initializers](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md).</span></span>  
  
### <a name="anonymous-types"></a><span data-ttu-id="129e0-187">Typy anonimowe</span><span class="sxs-lookup"><span data-stu-id="129e0-187">Anonymous Types</span></span>  
 <span data-ttu-id="129e0-188">W sytuacjach, gdy nie jest wygodne lub niezbędne do utworzenia nazwanego klasy na przykład gdy są podczas wypełniania listy z danymi konstrukcje że nie trzeba zachować lub Przekaż do innej metody, można użyć typów anonimowych.</span><span class="sxs-lookup"><span data-stu-id="129e0-188">In situations where it is not convenient or necessary to create a named class, for example when you are populating a list with data structures that you do not have to persist or pass to another method, you use anonymous types.</span></span> <span data-ttu-id="129e0-189">Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="129e0-189">For more information, see [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
### <a name="extension-methods"></a><span data-ttu-id="129e0-190">Metody rozszerzeń</span><span class="sxs-lookup"><span data-stu-id="129e0-190">Extension Methods</span></span>  
 <span data-ttu-id="129e0-191">Można "rozszerzyć" klasy bez tworzenia klasy pochodnej przez utworzenie oddzielnych typu, której metody można wywołać tak, jakby należały do oryginalnego typu.</span><span class="sxs-lookup"><span data-stu-id="129e0-191">You can "extend" a class without creating a derived class by creating a separate type whose methods can be called as if they belonged to the original type.</span></span> <span data-ttu-id="129e0-192">Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="129e0-192">For more information, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="129e0-193">Jawnie wpisana zmienna lokalna</span><span class="sxs-lookup"><span data-stu-id="129e0-193">Implicitly Typed Local Variables</span></span>  
 <span data-ttu-id="129e0-194">W klasie lub strukturze — metoda umożliwia wpisywanie niejawne poinstruować kompilator, aby ustalić poprawnego typu w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="129e0-194">Within a class or struct method, you can use implicit typing to instruct the compiler to determine the correct type at compile time.</span></span> <span data-ttu-id="129e0-195">Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span><span class="sxs-lookup"><span data-stu-id="129e0-195">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="129e0-196">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="129e0-196">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="129e0-197">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="129e0-197">See Also</span></span>  
 [<span data-ttu-id="129e0-198">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="129e0-198">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)