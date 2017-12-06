---
title: "Porady: tworzenie właściwości (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, properties
- properties [Visual Basic]
ms.assetid: 4d229712-6be8-4c5c-bac5-06995ce9185a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d140e6a10061f7fabe3d12c6cce5d0c201e103d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-property-visual-basic"></a><span data-ttu-id="d105d-102">Porady: tworzenie właściwości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d105d-102">How to: Create a Property (Visual Basic)</span></span>
<span data-ttu-id="d105d-103">Umieść definicji właściwości między `Property` instrukcji i `End Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d105d-103">You enclose a property definition between a `Property` statement and an `End Property` statement.</span></span> <span data-ttu-id="d105d-104">W ramach tej definicji zdefiniujesz `Get` procedury `Set` procedury lub oba.</span><span class="sxs-lookup"><span data-stu-id="d105d-104">Within this definition you define a `Get` procedure, a `Set` procedure, or both.</span></span> <span data-ttu-id="d105d-105">Wszystkie właściwości kod znajduje się w ramach tych procedur.</span><span class="sxs-lookup"><span data-stu-id="d105d-105">All the property's code lies within these procedures.</span></span>  
  
 <span data-ttu-id="d105d-106">`Get` Procedury pobiera wartość właściwości oraz `Set` procedura przechowywana wartość.</span><span class="sxs-lookup"><span data-stu-id="d105d-106">The `Get` procedure retrieves the property's value, and the `Set` procedure stores a value.</span></span> <span data-ttu-id="d105d-107">Jeśli chcesz, aby właściwość mają dostęp do odczytu/zapisu, należy zdefiniować obu tych procedur.</span><span class="sxs-lookup"><span data-stu-id="d105d-107">If you want the property to have read/write access, you must define both procedures.</span></span> <span data-ttu-id="d105d-108">Dla właściwości tylko do odczytu, możesz określić, tylko `Get`, dla właściwości tylko do zapisu, można określić tylko `Set`.</span><span class="sxs-lookup"><span data-stu-id="d105d-108">For a read-only property, you define only `Get`, and for a write-only property, you define only `Set`.</span></span>  
  
### <a name="to-create-a-property"></a><span data-ttu-id="d105d-109">Aby utworzyć właściwość</span><span class="sxs-lookup"><span data-stu-id="d105d-109">To create a property</span></span>  
  
1.  <span data-ttu-id="d105d-110">Poza właściwość lub procedura, użyj [Property — instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md), a następnie `End Property` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d105d-110">Outside any property or procedure, use a [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md), followed by an `End Property` statement.</span></span>  
  
2.  <span data-ttu-id="d105d-111">Jeśli właściwość pobiera parametry, wykonaj `Property` — słowo kluczowe z nazwą procedury ponownie z listą parametrów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="d105d-111">If the property takes parameters, follow the `Property` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3.  <span data-ttu-id="d105d-112">Postępuj zgodnie z nawiasy `As` klauzuli, aby określić typ danych wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="d105d-112">Follow the parentheses with an `As` clause to specify the data type of the property's value.</span></span> <span data-ttu-id="d105d-113">Należy określić typ danych, nawet w przypadku właściwości tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="d105d-113">You must specify the data type even for a write-only property.</span></span>  
  
4.  <span data-ttu-id="d105d-114">Dodaj `Get` i `Set` procedur, zależnie od potrzeb.</span><span class="sxs-lookup"><span data-stu-id="d105d-114">Add `Get` and `Set` procedures, as appropriate.</span></span> <span data-ttu-id="d105d-115">Zobacz poniższe wskazówki.</span><span class="sxs-lookup"><span data-stu-id="d105d-115">See the following directions.</span></span>  
  
### <a name="to-create-a-get-procedure-that-retrieves-a-property-value"></a><span data-ttu-id="d105d-116">Aby utworzyć procedura Get, który pobiera wartość właściwości</span><span class="sxs-lookup"><span data-stu-id="d105d-116">To create a Get procedure that retrieves a property value</span></span>  
  
1.  <span data-ttu-id="d105d-117">Między `Property` i `End Property` pisanie instrukcji [instrukcja Get](../../../../visual-basic/language-reference/statements/get-statement.md), a następnie `End Get` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d105d-117">Between the `Property` and `End Property` statements, write a [Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md), followed by an `End Get` statement.</span></span> <span data-ttu-id="d105d-118">Nie trzeba definiować wszystkie parametry `Get` procedury.</span><span class="sxs-lookup"><span data-stu-id="d105d-118">You do not need to define any parameters for the `Get` procedure.</span></span>  
  
2.  <span data-ttu-id="d105d-119">Umieść instrukcje kodu można pobrać wartości właściwości między `Get` i `End Get` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="d105d-119">Place the code statements to retrieve the property's value between the `Get` and `End Get` statements.</span></span> <span data-ttu-id="d105d-120">Ten kod może zawierać inne obliczenia i manipulacji danych oprócz generowania i zwraca wartość właściwości.</span><span class="sxs-lookup"><span data-stu-id="d105d-120">This code can include other calculations and data manipulations in addition to generating and returning the property's value.</span></span>  
  
3.  <span data-ttu-id="d105d-121">Użyj `Return` instrukcji, aby zwrócić wartość właściwości do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="d105d-121">Use a `Return` statement to return the property's value to the calling code.</span></span>  
  
 <span data-ttu-id="d105d-122">Musisz zapisać `Get` procedury dla właściwości odczytu / zapisu, a dla właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="d105d-122">You must write a `Get` procedure for a read-write property and for a read-only property.</span></span> <span data-ttu-id="d105d-123">Nie można zdefiniować `Get` procedury dla właściwości tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="d105d-123">You must not define a `Get` procedure for a write-only property.</span></span>  
  
### <a name="to-create-a-set-procedure-that-writes-a-propertys-value"></a><span data-ttu-id="d105d-124">Można utworzyć procedury zestawu, który zapisuje wartości właściwości</span><span class="sxs-lookup"><span data-stu-id="d105d-124">To create a Set procedure that writes a property's value</span></span>  
  
1.  <span data-ttu-id="d105d-125">Między `Property` i `End Property` pisanie instrukcji [Instrukcja Set](../../../../visual-basic/language-reference/statements/set-statement.md), a następnie `End Set` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d105d-125">Between the `Property` and `End Property` statements, write a [Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md), followed by an `End Set` statement.</span></span>  
  
2.  <span data-ttu-id="d105d-126">W `Set` instrukcji, wykonaj `Set` — słowo kluczowe z listą parametrów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="d105d-126">In the `Set` statement, follow the `Set` keyword with a parameter list in parentheses.</span></span> <span data-ttu-id="d105d-127">Ta lista parametrów musi zawierać co najmniej wartość parametru wartość przekazany przez wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="d105d-127">This parameter list must include at least a value parameter for the value passed by the calling code.</span></span> <span data-ttu-id="d105d-128">Domyślna nazwa dla tego parametru wartość to `Value`, ale w razie potrzeby można użyć innej nazwy.</span><span class="sxs-lookup"><span data-stu-id="d105d-128">The default name for this value parameter is `Value`, but you can use a different name if appropriate.</span></span> <span data-ttu-id="d105d-129">Wartość parametru musi mieć taki sam typ jak samej właściwości danych.</span><span class="sxs-lookup"><span data-stu-id="d105d-129">The value parameter must have the same data type as the property itself.</span></span>  
  
3.  <span data-ttu-id="d105d-130">Umieść instrukcje kodu do przechowywania wartości właściwości między `Set` i `End Set` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="d105d-130">Place the code statements to store a value in the property between the `Set` and `End Set` statements.</span></span> <span data-ttu-id="d105d-131">Ten kod może zawierać inne obliczenia i manipulacji danych oprócz sprawdzania poprawności i przechowywanie wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="d105d-131">This code can include other calculations and data manipulations in addition to validating and storing the property's value.</span></span>  
  
4.  <span data-ttu-id="d105d-132">Aby zaakceptować wartości dostarczone przez kod wywołujący, użyj parametru wartości.</span><span class="sxs-lookup"><span data-stu-id="d105d-132">Use the value parameter to accept the value supplied by the calling code.</span></span> <span data-ttu-id="d105d-133">Możesz zapisać tę wartość bezpośrednio w instrukcji przypisania lub używany w wyrażenie do obliczenia wartości wewnętrznego mają być przechowywane.</span><span class="sxs-lookup"><span data-stu-id="d105d-133">You can either store this value directly in an assignment statement, or use it in an expression to calculate the internal value to be stored.</span></span>  
  
 <span data-ttu-id="d105d-134">Musisz zapisać `Set` procedury dla właściwości odczytu / zapisu, a dla właściwości tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="d105d-134">You must write a `Set` procedure for a read-write property and for a write-only property.</span></span> <span data-ttu-id="d105d-135">Nie można zdefiniować `Set` procedury dla właściwości tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="d105d-135">You must not define a `Set` procedure for a read-only property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d105d-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="d105d-136">Example</span></span>  
 <span data-ttu-id="d105d-137">Poniższy przykład tworzy właściwości odczytu/zapisu, która przechowuje pełną nazwę w postaci dwóch nazw składników, imię i nazwisko.</span><span class="sxs-lookup"><span data-stu-id="d105d-137">The following example creates a read/write property that stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="d105d-138">Gdy odczytuje kod wywołujący `fullName`, `Get` procedura łączy dwie nazwy składników i zwraca pełną nazwę.</span><span class="sxs-lookup"><span data-stu-id="d105d-138">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="d105d-139">Gdy kod wywołujący przypisuje nową pełną nazwę, `Set` procedury próbuje podzielić dwie nazwy składowych.</span><span class="sxs-lookup"><span data-stu-id="d105d-139">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="d105d-140">Jeśli nie znajdzie spację, przechowuje on wszystkie jako pierwszej nazwy.</span><span class="sxs-lookup"><span data-stu-id="d105d-140">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/how-to-create-a-property_1.vb)]  
  
 <span data-ttu-id="d105d-141">W poniższym przykładzie przedstawiono typowe wywołania procedury właściwości `fullName`.</span><span class="sxs-lookup"><span data-stu-id="d105d-141">The following example shows typical calls to the property procedures of `fullName`.</span></span> <span data-ttu-id="d105d-142">Pierwsze wywołanie ustawia wartości właściwości, a drugie wywołanie pobiera go.</span><span class="sxs-lookup"><span data-stu-id="d105d-142">The first call sets the property value and the second call retrieves it.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/how-to-create-a-property_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d105d-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d105d-143">See Also</span></span>  
 [<span data-ttu-id="d105d-144">Procedury</span><span class="sxs-lookup"><span data-stu-id="d105d-144">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="d105d-145">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="d105d-145">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="d105d-146">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="d105d-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="d105d-147">Różnice pomiędzy właściwościami i zmiennymi w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d105d-147">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="d105d-148">Porady: deklarowanie właściwości z mieszanymi poziomami dostępu</span><span class="sxs-lookup"><span data-stu-id="d105d-148">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="d105d-149">Porady: wywoływanie procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="d105d-149">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="d105d-150">Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d105d-150">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="d105d-151">Porady: umieszczanie wartości we właściwości</span><span class="sxs-lookup"><span data-stu-id="d105d-151">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="d105d-152">Porady: pobieranie wartości z właściwości</span><span class="sxs-lookup"><span data-stu-id="d105d-152">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)