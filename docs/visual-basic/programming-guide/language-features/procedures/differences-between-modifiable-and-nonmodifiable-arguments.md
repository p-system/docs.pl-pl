---
title: "Różnice pomiędzy argumentami modyfikowalnymi i niemodyfikowalnymi (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab108d064f5c6740f80328a9b6db4785334550ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="4c8ca-102">Różnice pomiędzy argumentami modyfikowalnymi i niemodyfikowalnymi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4c8ca-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="4c8ca-103">Po wywołaniu procedury, zwykle przekazywania jednego lub więcej argumentów do niej.</span><span class="sxs-lookup"><span data-stu-id="4c8ca-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="4c8ca-104">Każdy argument odnosi się do odpowiedniego elementu programowania.</span><span class="sxs-lookup"><span data-stu-id="4c8ca-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="4c8ca-105">Zarówno elementy źródłowe, jak i argumentów, same może być modyfikowalnymi i niemodyfikowalnymi.</span><span class="sxs-lookup"><span data-stu-id="4c8ca-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="4c8ca-106">Elementy modyfikowalnymi i niemodyfikowalnymi</span><span class="sxs-lookup"><span data-stu-id="4c8ca-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="4c8ca-107">Elementu programistycznego mogą być *można modyfikować elementu*, która może zawierać wartość zmienione, lub *niemodyfikowalnymi elementu*, mającego stałą wartość, po jego utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="4c8ca-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="4c8ca-108">W poniższej tabeli wymieniono modyfikowalnymi i niemodyfikowalnymi elementów programowania.</span><span class="sxs-lookup"><span data-stu-id="4c8ca-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="4c8ca-109">Można modyfikować elementów</span><span class="sxs-lookup"><span data-stu-id="4c8ca-109">Modifiable elements</span></span>|<span data-ttu-id="4c8ca-110">Elementy niemodyfikowalnymi</span><span class="sxs-lookup"><span data-stu-id="4c8ca-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="4c8ca-111">Zmienne lokalne (zadeklarowana wewnątrz procedury), w tym zmiennych obiektu, z wyjątkiem tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4c8ca-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="4c8ca-112">Zmienne tylko do odczytu, pól i właściwości</span><span class="sxs-lookup"><span data-stu-id="4c8ca-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="4c8ca-113">Pola (zmienne Członkowskie modułów, klasy i struktury), z wyjątkiem tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4c8ca-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="4c8ca-114">Literały i stałe</span><span class="sxs-lookup"><span data-stu-id="4c8ca-114">Constants and literals</span></span>|  
|<span data-ttu-id="4c8ca-115">Właściwości, z wyjątkiem tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="4c8ca-115">Properties, except for read-only</span></span>|<span data-ttu-id="4c8ca-116">Elementy członkowskie wyliczenia</span><span class="sxs-lookup"><span data-stu-id="4c8ca-116">Enumeration members</span></span>|  
|<span data-ttu-id="4c8ca-117">Elementy tablicy</span><span class="sxs-lookup"><span data-stu-id="4c8ca-117">Array elements</span></span>|<span data-ttu-id="4c8ca-118">Wyrażenia (nawet jeśli ich elementy są modyfikowane przez)</span><span class="sxs-lookup"><span data-stu-id="4c8ca-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="4c8ca-119">Modyfikowalnymi i niemodyfikowalnymi</span><span class="sxs-lookup"><span data-stu-id="4c8ca-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="4c8ca-120">A *można modyfikować argumentu* jest jednym z elementem podstawowej można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="4c8ca-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="4c8ca-121">Kod wywołujący może przechowywać nową wartość w dowolnym momencie i jeśli zostanie przekazany argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), kod w procedurze można modyfikować również odpowiedniego elementu kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4c8ca-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="4c8ca-122">A *niemodyfikowalnymi argument* ma niemodyfikowalnymi odpowiedniego elementu albo jest przekazywany [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="4c8ca-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="4c8ca-123">Procedury nie można zmodyfikować odpowiedniego elementu kodu wywołującego, nawet jeśli jest on elementem można modyfikować.</span><span class="sxs-lookup"><span data-stu-id="4c8ca-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="4c8ca-124">Jeśli element niemodyfikowalnymi, nie można zmodyfikować kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4c8ca-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="4c8ca-125">Wywoływana procedura może zmodyfikować swojej lokalnej kopii niemodyfikowalnymi argumentu, ale modyfikacji nie ma wpływu na odpowiedniego elementu kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="4c8ca-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c8ca-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4c8ca-126">See Also</span></span>  
 [<span data-ttu-id="4c8ca-127">Procedury</span><span class="sxs-lookup"><span data-stu-id="4c8ca-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="4c8ca-128">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="4c8ca-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="4c8ca-129">Porady: przekazywanie argumentów do procedury</span><span class="sxs-lookup"><span data-stu-id="4c8ca-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="4c8ca-130">Przekazywanie argumentów według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="4c8ca-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="4c8ca-131">Różnice pomiędzy przekazywaniem argumentu według wartości i według odwołania</span><span class="sxs-lookup"><span data-stu-id="4c8ca-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="4c8ca-132">Porady: Zmienianie wartości argumentu procedury</span><span class="sxs-lookup"><span data-stu-id="4c8ca-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="4c8ca-133">Porady: chronienie argumentu procedury przed zmianami wartości</span><span class="sxs-lookup"><span data-stu-id="4c8ca-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="4c8ca-134">Porady: Wymuszanie przekazywania argumentu przez wartość</span><span class="sxs-lookup"><span data-stu-id="4c8ca-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="4c8ca-135">Przekazywanie argumentów według pozycji i według nazwy</span><span class="sxs-lookup"><span data-stu-id="4c8ca-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="4c8ca-136">Typy wartości i typy referencyjne</span><span class="sxs-lookup"><span data-stu-id="4c8ca-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)