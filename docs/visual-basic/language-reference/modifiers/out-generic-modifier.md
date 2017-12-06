---
title: "Out (modyfikator ogólny) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94d18200e6d7ce0ad63a229223ae77d99302e0e6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="out-generic-modifier-visual-basic"></a><span data-ttu-id="50fdd-102">Out (modyfikator ogólny) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50fdd-102">Out (Generic Modifier) (Visual Basic)</span></span>
<span data-ttu-id="50fdd-103">Parametry typu ogólnego `Out` — słowo kluczowe Określa, że typ jest kowariantny.</span><span class="sxs-lookup"><span data-stu-id="50fdd-103">For generic type parameters, the `Out` keyword specifies that the type is covariant.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50fdd-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50fdd-104">Remarks</span></span>  
 <span data-ttu-id="50fdd-105">Kowariancja pozwala na użycie typu bardziej pochodnego od określonej przez parametr ogólny.</span><span class="sxs-lookup"><span data-stu-id="50fdd-105">Covariance enables you to use a more derived type than that specified by the generic parameter.</span></span> <span data-ttu-id="50fdd-106">Dzięki temu niejawna konwersja klas implementujących interfejsów typu variant i niejawna konwersja typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="50fdd-106">This allows for implicit conversion of classes that implement variant interfaces and implicit conversion of delegate types.</span></span>  
  
 <span data-ttu-id="50fdd-107">Aby uzyskać więcej informacji, zobacz [Kowariancja i Kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).</span><span class="sxs-lookup"><span data-stu-id="50fdd-107">For more information, see [Covariance and Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="50fdd-108">Reguły</span><span class="sxs-lookup"><span data-stu-id="50fdd-108">Rules</span></span>  
 <span data-ttu-id="50fdd-109">Można użyć `Out` — słowo kluczowe w interfejsach i delegatów.</span><span class="sxs-lookup"><span data-stu-id="50fdd-109">You can use the `Out` keyword in generic interfaces and delegates.</span></span>  
  
 <span data-ttu-id="50fdd-110">W interfejsie ogólny parametru typu mogą być deklarowane jako kowariantnego, spełnia następujące warunki:</span><span class="sxs-lookup"><span data-stu-id="50fdd-110">In a generic interface, a type parameter can be declared covariant if it satisfies the following conditions:</span></span>  
  
-   <span data-ttu-id="50fdd-111">Parametr typu jest używany tylko jako typ zwracany metody interfejsu i nie jest używany jako typ argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="50fdd-111">The type parameter is used only as a return type of interface methods and not used as a type of method arguments.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="50fdd-112">Istnieje jeden wyjątek od tej reguły.</span><span class="sxs-lookup"><span data-stu-id="50fdd-112">There is one exception to this rule.</span></span> <span data-ttu-id="50fdd-113">Jeśli w interfejsie kowariantnego to delegat generyczny kontrawariantnego jako parametr metody, można użyć typu kowariantnego jako parametr typu ogólnego dla tego obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="50fdd-113">If in a covariant interface you have a contravariant generic delegate as a method parameter, you can use the covariant type as a generic type parameter for this delegate.</span></span> <span data-ttu-id="50fdd-114">Aby uzyskać więcej informacji na temat kowariantnego i kontrawariantnego delegatów, zobacz [wariancji w Delegatach](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca) i [przy użyciu wariancję Func i delegatów akcji](http://msdn.microsoft.com/library/e69c4f39-09aa-4c6d-a752-08cc767d8290).</span><span class="sxs-lookup"><span data-stu-id="50fdd-114">For more information about covariant and contravariant generic delegates, see [Variance in Delegates](http://msdn.microsoft.com/library/e3b98197-6c5b-4e55-9c6e-9739b60645ca) and [Using Variance for Func and Action Generic Delegates](http://msdn.microsoft.com/library/e69c4f39-09aa-4c6d-a752-08cc767d8290).</span></span>  
  
-   <span data-ttu-id="50fdd-115">Parametr typu nie jest używany jako ogólne ograniczenia dla metod interfejsu.</span><span class="sxs-lookup"><span data-stu-id="50fdd-115">The type parameter is not used as a generic constraint for the interface methods.</span></span>  
  
 <span data-ttu-id="50fdd-116">Delegat ogólny parametru typu mogą być deklarowane kowariantnego Jeśli jest używany tylko jako typ zwracany metody i nie są używane dla argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="50fdd-116">In a generic delegate, a type parameter can be declared covariant if it is used only as a method return type and not used for method arguments.</span></span>  
  
 <span data-ttu-id="50fdd-117">Kowariancja i kontrawariancja są obsługiwane dla typów odwołań, ale nie są obsługiwane dla typów wartości.</span><span class="sxs-lookup"><span data-stu-id="50fdd-117">Covariance and contravariance are supported for reference types, but they are not supported for value types.</span></span>  
  
 <span data-ttu-id="50fdd-118">W języku Visual Basic nie można zadeklarować zdarzenia w interfejsach kowariantnego bez określania typu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="50fdd-118">In Visual Basic, you cannot declare events in covariant interfaces without specifying the delegate type.</span></span> <span data-ttu-id="50fdd-119">Ponadto kowariantnego interfejsów nie mogą mieć zagnieżdżonych klas, wyliczeń lub struktury, ale można mieć zagnieżdżonych interfejsów.</span><span class="sxs-lookup"><span data-stu-id="50fdd-119">Also, covariant interfaces cannot have nested classes, enums, or structures, but they can have nested interfaces.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="50fdd-120">Zachowanie</span><span class="sxs-lookup"><span data-stu-id="50fdd-120">Behavior</span></span>  
 <span data-ttu-id="50fdd-121">Interfejs, który ma parametr typu kowariantnego umożliwia sposobów niż określony przez parametr typu bardziej pochodnego typy zwracane.</span><span class="sxs-lookup"><span data-stu-id="50fdd-121">An interface that has a covariant type parameter enables its methods to return more derived types than those specified by the type parameter.</span></span> <span data-ttu-id="50fdd-122">Na przykład ponieważ w .NET Framework 4 w <xref:System.Collections.Generic.IEnumerable%601>typu T jest kowariantny, można przypisać obiektu `IEnumerabe(Of String)` typu do obiektu `IEnumerable(Of Object)` typu bez korzystania z żadnych metod konwersji specjalnych.</span><span class="sxs-lookup"><span data-stu-id="50fdd-122">For example, because in .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601>, type T is covariant, you can assign an object of the `IEnumerabe(Of String)` type to an object of the `IEnumerable(Of Object)` type without using any special conversion methods.</span></span>  
  
 <span data-ttu-id="50fdd-123">Kowariantnego delegata można przypisać inną delegata tego samego typu, ale także z bardziej pochodny parametr typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="50fdd-123">A covariant delegate can be assigned another delegate of the same type, but with a more derived generic type parameter.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50fdd-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="50fdd-124">Example</span></span>  
 <span data-ttu-id="50fdd-125">Poniższy przykład pokazuje, jak zadeklarować, rozszerzać i implementacji kowariantnego interfejs generyczny.</span><span class="sxs-lookup"><span data-stu-id="50fdd-125">The following example shows how to declare, extend, and implement a covariant generic interface.</span></span> <span data-ttu-id="50fdd-126">On również przedstawia użycie niejawna konwersja dla klas implementujących interfejs kowariantny.</span><span class="sxs-lookup"><span data-stu-id="50fdd-126">It also shows how to use implicit conversion for classes that implement a covariant interface.</span></span>  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="50fdd-127">Przykład</span><span class="sxs-lookup"><span data-stu-id="50fdd-127">Example</span></span>  
 <span data-ttu-id="50fdd-128">Poniższy przykład pokazuje, jak zadeklarować, wystąpienia i wywoływać kowariantnego Delegat ogólny.</span><span class="sxs-lookup"><span data-stu-id="50fdd-128">The following example shows how to declare, instantiate, and invoke a covariant generic delegate.</span></span> <span data-ttu-id="50fdd-129">Pokazuje też, używania niejawna konwersja typów delegata.</span><span class="sxs-lookup"><span data-stu-id="50fdd-129">It also shows how you can use implicit conversion for delegate types.</span></span>  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="50fdd-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50fdd-130">See Also</span></span>  
 [<span data-ttu-id="50fdd-131">Wariancje w interfejsach</span><span class="sxs-lookup"><span data-stu-id="50fdd-131">Variance in Generic Interfaces</span></span>](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [<span data-ttu-id="50fdd-132">W</span><span class="sxs-lookup"><span data-stu-id="50fdd-132">In</span></span>](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)