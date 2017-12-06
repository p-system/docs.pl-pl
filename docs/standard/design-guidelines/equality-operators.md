---
title: "Operatory równości"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 55c0505f5a06dfc87897fa59e9d6083cbd63c8ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="equality-operators"></a><span data-ttu-id="7928e-102">Operatory równości</span><span class="sxs-lookup"><span data-stu-id="7928e-102">Equality Operators</span></span>
<span data-ttu-id="7928e-103">W tej sekcji omówiono przeciążania Operatory równości i odwołuje się do `operator==` i `operator!=` jako operatory równości.</span><span class="sxs-lookup"><span data-stu-id="7928e-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>  
  
 <span data-ttu-id="7928e-104">**X nie** jedną Operatory równości i nie inne przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="7928e-104">**X DO NOT** overload one of the equality operators and not the other.</span></span>  
  
 <span data-ttu-id="7928e-105">**CZY ✓** upewnij się, że <xref:System.Object.Equals%2A?displayProperty=nameWithType> i operatory porównania ma dokładnie tej samej semantyki i podobne charakterystyki wydajności.</span><span class="sxs-lookup"><span data-stu-id="7928e-105">**✓ DO** ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>  
  
 <span data-ttu-id="7928e-106">Często oznacza to, że `Object.Equals` musi zostać zastąpiona, gdy są przeciążone operatory równości.</span><span class="sxs-lookup"><span data-stu-id="7928e-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>  
  
 <span data-ttu-id="7928e-107">**X należy UNIKAĆ** zgłaszanie wyjątków z Operatory równości.</span><span class="sxs-lookup"><span data-stu-id="7928e-107">**X AVOID** throwing exceptions from equality operators.</span></span>  
  
 <span data-ttu-id="7928e-108">Na przykład zwróci wartość false, jeśli jeden z argumentów ma wartość null zamiast zgłaszanie `NullReferenceException`.</span><span class="sxs-lookup"><span data-stu-id="7928e-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>  
  
## <a name="equality-operators-on-value-types"></a><span data-ttu-id="7928e-109">Operatory równości dla typów wartości</span><span class="sxs-lookup"><span data-stu-id="7928e-109">Equality Operators on Value Types</span></span>  
 <span data-ttu-id="7928e-110">**CZY ✓** przeciążać Operatory równości w typach wartości, jeśli równości jest łatwy do rozpoznania.</span><span class="sxs-lookup"><span data-stu-id="7928e-110">**✓ DO** overload the equality operators on value types, if equality is meaningful.</span></span>  
  
 <span data-ttu-id="7928e-111">W większości języków programowania, nie ma żadnych domyślną implementację `operator==` dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="7928e-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>  
  
## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="7928e-112">Operatory równości w typach referencyjnych</span><span class="sxs-lookup"><span data-stu-id="7928e-112">Equality Operators on Reference Types</span></span>  
 <span data-ttu-id="7928e-113">**X należy UNIKAĆ** przeładowanie operatorów równości w typach referencyjnych.</span><span class="sxs-lookup"><span data-stu-id="7928e-113">**X AVOID** overloading equality operators on mutable reference types.</span></span>  
  
 <span data-ttu-id="7928e-114">Wiele języków ma operatory wbudowanych równości dla typów odwołań.</span><span class="sxs-lookup"><span data-stu-id="7928e-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="7928e-115">Wbudowane Operatorzy zazwyczaj zaimplementować równości odwołań, a wielu deweloperów są zaskoczeniem, w przypadku zmiany domyślnego zachowania na równości wartości.</span><span class="sxs-lookup"><span data-stu-id="7928e-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>  
  
 <span data-ttu-id="7928e-116">Ten problem jest skorygowane dla typów odwołań niezmienne, ponieważ immutability utrudnia znacznie należy zauważyć różnicę między równości odwołań i o równość wartości.</span><span class="sxs-lookup"><span data-stu-id="7928e-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>  
  
 <span data-ttu-id="7928e-117">**X należy UNIKAĆ** przeładowanie operatorów równości w typach referencyjnych, jeśli implementacja będzie znacznie mniejsza niż w przypadku równości odwołań.</span><span class="sxs-lookup"><span data-stu-id="7928e-117">**X AVOID** overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>  
  
 <span data-ttu-id="7928e-118">*Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*</span><span class="sxs-lookup"><span data-stu-id="7928e-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="7928e-119">*Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*</span><span class="sxs-lookup"><span data-stu-id="7928e-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7928e-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7928e-120">See Also</span></span>  
 [<span data-ttu-id="7928e-121">Wytyczne dotyczące projektowania Framework</span><span class="sxs-lookup"><span data-stu-id="7928e-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="7928e-122">Wskazówki dotyczące użycia</span><span class="sxs-lookup"><span data-stu-id="7928e-122">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)