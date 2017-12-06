---
title: "Procedury operatorów (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 865695731dd591b0c48f4416814fa97edf4ea42e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="ab1b8-102">Procedury operatorów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab1b8-102">Operator Procedures (Visual Basic)</span></span>
<span data-ttu-id="ab1b8-103">Procedury operatora jest szereg [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] instrukcji, które definiują zachowanie standardowe — operator (takich jak `*`, `<>`, lub `And`) dla klasy lub struktury zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-103">An operator procedure is a series of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="ab1b8-104">Jest to również *przeładowania operatora*.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-104">This is also called *operator overloading*.</span></span>  
  
## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="ab1b8-105">Kiedy należy zdefiniować procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="ab1b8-105">When to Define Operator Procedures</span></span>  
 <span data-ttu-id="ab1b8-106">Po zdefiniowaniu klasy lub struktury, należy zadeklarować zmienne, które mają być typu tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="ab1b8-107">Czasami taki zmiennej musi uczestniczyć w operacji jako część wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="ab1b8-108">Aby to zrobić, musi ona być argumentu operacji operatora.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-108">To do this, it must be an operand of an operator.</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="ab1b8-109">Definiuje operatory tylko na jego typów podstawowych danych.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-109"> defines operators only on its fundamental data types.</span></span> <span data-ttu-id="ab1b8-110">Można określić zachowanie operatora, jeśli jeden lub oba argumenty operacji są typu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="ab1b8-111">Aby uzyskać więcej informacji, zobacz [operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ab1b8-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="types-of-operator-procedure"></a><span data-ttu-id="ab1b8-112">Typy procedury operatora</span><span class="sxs-lookup"><span data-stu-id="ab1b8-112">Types of Operator Procedure</span></span>  
 <span data-ttu-id="ab1b8-113">Procedury operatora może być jedną z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="ab1b8-113">An operator procedure can be one of the following types:</span></span>  
  
-   <span data-ttu-id="ab1b8-114">Definicja operatora jednoargumentowego, gdy argument jest typu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="ab1b8-115">Definicja operatora binarnego, gdzie jest co najmniej jeden z argumentów typu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="ab1b8-116">Definicja operatora konwersji, gdy argument jest typu klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="ab1b8-117">Definicja operatora konwersji, który zwraca typ klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>  
  
 <span data-ttu-id="ab1b8-118">Operatory konwersji są zawsze jednoargumentowy i zawsze używaj `CType` jako operator definiujesz.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="ab1b8-119">Składnia deklaracji</span><span class="sxs-lookup"><span data-stu-id="ab1b8-119">Declaration Syntax</span></span>  
 <span data-ttu-id="ab1b8-120">Składnia deklaracji procedury operatora wygląda następująco:</span><span class="sxs-lookup"><span data-stu-id="ab1b8-120">The syntax for declaring an operator procedure is as follows:</span></span>  
  
 <span data-ttu-id="ab1b8-121">`Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol* `(` *operand1*`[,`*operand2* `]) As` *typu danych* </span><span class="sxs-lookup"><span data-stu-id="ab1b8-121">`Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*</span></span>  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 <span data-ttu-id="ab1b8-122">Możesz użyć `Widening` lub `Narrowing` — słowo kluczowe tylko na operatora konwersji typu.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-122">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="ab1b8-123">Symbol operatora jest zawsze [CType — funkcja](../../../../visual-basic/language-reference/functions/ctype-function.md) dla operatora konwersji typu.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-123">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>  
  
 <span data-ttu-id="ab1b8-124">Deklarowanie dwóch argumentów operacji, aby zdefiniować operator binarny i zadeklarować jeden operand, aby zdefiniować operator Jednoargumentowy operator konwersji typu w tym.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-124">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="ab1b8-125">Należy zadeklarować wszystkie operandy `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-125">All operands must be declared `ByVal`.</span></span>  
  
 <span data-ttu-id="ab1b8-126">Zadeklaruj każdy argument deklarować parametrów tak samo [procedury Sub](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ab1b8-126">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="ab1b8-127">Typ danych</span><span class="sxs-lookup"><span data-stu-id="ab1b8-127">Data Type</span></span>  
 <span data-ttu-id="ab1b8-128">Ponieważ operator są definiowane w klasie lub strukturze zdefiniowanych, co najmniej jeden z argumentów musi być typu danych z tej klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-128">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="ab1b8-129">Dla operatora konwersji typu argument lub typ zwracany musi być typu danych klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-129">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>  
  
 <span data-ttu-id="ab1b8-130">Aby uzyskać więcej informacji, zobacz [operator — instrukcja](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ab1b8-130">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="ab1b8-131">Składnia wywoływania</span><span class="sxs-lookup"><span data-stu-id="ab1b8-131">Calling Syntax</span></span>  
 <span data-ttu-id="ab1b8-132">Wywołanie procedury operatora jest niejawnie za pomocą symbol operatora w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-132">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="ab1b8-133">Argumenty operacji Podaj ten sam sposób jak w przypadku operatorów wstępnie zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-133">You supply the operands the same way you do for predefined operators.</span></span>  
  
 <span data-ttu-id="ab1b8-134">Niejawne wywołanie procedury operatora ma następującą składnię:</span><span class="sxs-lookup"><span data-stu-id="ab1b8-134">The syntax for an implicit call to an operator procedure is as follows:</span></span>  
  
 <span data-ttu-id="ab1b8-135">`Dim testStruct As`  *structurename*</span><span class="sxs-lookup"><span data-stu-id="ab1b8-135">`Dim testStruct As`  *structurename*</span></span>  
  
 <span data-ttu-id="ab1b8-136">`Dim testNewStruct As`  *structurename*`= testStruct`*operatorsymbol*   `10`</span><span class="sxs-lookup"><span data-stu-id="ab1b8-136">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="ab1b8-137">Ilustracja deklaracji i wywołanie</span><span class="sxs-lookup"><span data-stu-id="ab1b8-137">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="ab1b8-138">Następującą strukturę przechowuje wartość całkowita 128-bitowego jako elementy składowe znaczących i znaczącymi bitami.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-138">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="ab1b8-139">Definiuje `+` operatora, aby dodać dwa `veryLong` wartości oraz generowanie wynikowa `veryLong` wartość.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-139">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>  
  
 [!code-vb[VbVbcnProcedures#23](./codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 <span data-ttu-id="ab1b8-140">W poniższym przykładzie przedstawiono typowe wywołania `+` operator zdefiniowany na `veryLong`.</span><span class="sxs-lookup"><span data-stu-id="ab1b8-140">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#24](./codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 <span data-ttu-id="ab1b8-141">Aby uzyskać dodatkowe informacje i przykłady, zobacz [przeciążanie operatora w Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span><span class="sxs-lookup"><span data-stu-id="ab1b8-141">For more information and examples, see [Operator Overloading in Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab1b8-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab1b8-142">See Also</span></span>  
 [<span data-ttu-id="ab1b8-143">Procedury</span><span class="sxs-lookup"><span data-stu-id="ab1b8-143">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="ab1b8-144">Sub — procedury</span><span class="sxs-lookup"><span data-stu-id="ab1b8-144">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="ab1b8-145">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="ab1b8-145">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="ab1b8-146">Procedury własności</span><span class="sxs-lookup"><span data-stu-id="ab1b8-146">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="ab1b8-147">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="ab1b8-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="ab1b8-148">Operator — instrukcja</span><span class="sxs-lookup"><span data-stu-id="ab1b8-148">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="ab1b8-149">Porady: Definiowanie operatora</span><span class="sxs-lookup"><span data-stu-id="ab1b8-149">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="ab1b8-150">Porady: Definiowanie operatora konwersji</span><span class="sxs-lookup"><span data-stu-id="ab1b8-150">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="ab1b8-151">Porady: wywoływanie procedury operatora</span><span class="sxs-lookup"><span data-stu-id="ab1b8-151">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="ab1b8-152">Porady: używanie klasy definiującej operatory</span><span class="sxs-lookup"><span data-stu-id="ab1b8-152">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)