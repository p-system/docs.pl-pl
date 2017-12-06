---
title: 'Porady: definiowanie i wykonywanie metod dynamicznych'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 52f6b425ae4df138a843c6a790f10f78dc5a2b40
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-and-execute-dynamic-methods"></a><span data-ttu-id="7d2c5-102">Porady: definiowanie i wykonywanie metod dynamicznych</span><span class="sxs-lookup"><span data-stu-id="7d2c5-102">How to: Define and Execute Dynamic Methods</span></span>
<span data-ttu-id="7d2c5-103">Poniższe procedury pokazują, jak definiowanie i wykonywanie prosta metoda dynamiczne i dynamiczna metoda powiązany z wystąpieniem klasy.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-103">The following procedures show how to define and execute a simple dynamic method and a dynamic method bound to an instance of a class.</span></span> <span data-ttu-id="7d2c5-104">Więcej informacji na temat metod dynamicznych, zobacz <xref:System.Reflection.Emit.DynamicMethod> klasy i [emisji dynamicznego metody scenariuszami odbicia](http://msdn.microsoft.com/en-us/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).</span><span class="sxs-lookup"><span data-stu-id="7d2c5-104">For more information on dynamic methods, see the <xref:System.Reflection.Emit.DynamicMethod> class and [Reflection Emit Dynamic Method Scenarios](http://msdn.microsoft.com/en-us/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e).</span></span>  
  
### <a name="to-define-and-execute-a-dynamic-method"></a><span data-ttu-id="7d2c5-105">Aby zdefiniować i wykonania metody dynamiczne</span><span class="sxs-lookup"><span data-stu-id="7d2c5-105">To define and execute a dynamic method</span></span>  
  
1.  <span data-ttu-id="7d2c5-106">Należy zadeklarować typ delegata można wykonać metody.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-106">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="7d2c5-107">Należy rozważyć użycie do minimalizacji liczby typów delegatów, które należy zadeklarować to delegat generyczny.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-107">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="7d2c5-108">Poniższy kod deklaruje delegata dwa typy, które mogłyby zostać użyte do `SquareIt` — metoda i jeden z nich jest rodzajowy.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-108">The following code declares two delegate types that could be used for the `SquareIt` method, and one of them is generic.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2.  <span data-ttu-id="7d2c5-109">Utwórz tablicę, która określa typ parametru metody dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-109">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="7d2c5-110">W tym przykładzie jest tylko parametr `int` (`Integer` w języku Visual Basic), przez co tablica zawiera tylko jeden element.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-110">In this example, the only parameter is an `int` (`Integer` in Visual Basic), so the array has only one element.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3.  <span data-ttu-id="7d2c5-111">Utwórz <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-111">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="7d2c5-112">W tym przykładzie metodę o nazwie `SquareIt`.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-112">In this example the method is named `SquareIt`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7d2c5-113">Nie jest konieczne, nadaj nazwę metody dynamiczne i nie można wywołać według nazwy.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-113">It is not necessary to give dynamic methods names, and they cannot be invoked by name.</span></span> <span data-ttu-id="7d2c5-114">Wiele metod dynamicznych może mieć takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-114">Multiple dynamic methods can have the same name.</span></span> <span data-ttu-id="7d2c5-115">Jednak nazwa jest wyświetlana w stosy wywołań i mogą być przydatne do debugowania.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-115">However, the name appears in call stacks and can be useful for debugging.</span></span>  
  
     <span data-ttu-id="7d2c5-116">Typ wartości zwracanej jest określony jako `long`.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-116">The type of the return value is specified as `long`.</span></span> <span data-ttu-id="7d2c5-117">Metoda jest skojarzony z moduł, który zawiera `Example` klasy, która zawiera przykładowy kod.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-117">The method is associated with the module that contains the `Example` class, which contains the example code.</span></span> <span data-ttu-id="7d2c5-118">Każdy moduł załadować może być określony.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-118">Any loaded module could be specified.</span></span> <span data-ttu-id="7d2c5-119">Działa dynamiczna metoda jak poziom modułu `static` — metoda (`Shared` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="7d2c5-119">The dynamic method acts like a module-level `static` method (`Shared` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4.  <span data-ttu-id="7d2c5-120">Emituj treści metody.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-120">Emit the method body.</span></span> <span data-ttu-id="7d2c5-121">W tym przykładzie <xref:System.Reflection.Emit.ILGenerator> obiekt jest używany do wysyłania język pośredni firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="7d2c5-121">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="7d2c5-122">Alternatywnie <xref:System.Reflection.Emit.DynamicILInfo> obiektu można w połączeniu z generatory kodu niezarządzanego Emituj treść metody <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-122">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="7d2c5-123">MSIL w tym przykładzie ładuje argumentu, który jest `int`, na stosie, konwertuje go do `long`, duplikaty `long`i mnoży dwie liczby.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-123">The MSIL in this example loads the argument, which is an `int`, onto the stack, converts it to a `long`, duplicates the `long`, and multiplies the two numbers.</span></span> <span data-ttu-id="7d2c5-124">Wynik kwadratów pozostawione na stosie, a metoda ma robić, jest zwracany.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-124">This leaves the squared result on the stack, and all the method has to do is return.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5.  <span data-ttu-id="7d2c5-125">Utwórz wystąpienie obiektu delegowanego (deklaracja w kroku 1) reprezentuje przez wywołanie metody dynamicznej <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-125">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method.</span></span> <span data-ttu-id="7d2c5-126">Tworzenie obiektu delegowanego ukończeniu metody i wszelkie dodatkowe próbuje zmienić metodę — na przykład dodać więcej MSIL — są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-126">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span> <span data-ttu-id="7d2c5-127">Poniższy kod tworzy delegata i wywołuje, przy użyciu to delegat generyczny.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-127">The following code creates the delegate and invokes it, using a generic delegate.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a><span data-ttu-id="7d2c5-128">Aby zdefiniować i wykonać dynamicznej metodę, która jest powiązana z obiektem</span><span class="sxs-lookup"><span data-stu-id="7d2c5-128">To define and execute a dynamic method that is bound to an object</span></span>  
  
1.  <span data-ttu-id="7d2c5-129">Należy zadeklarować typ delegata można wykonać metody.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-129">Declare a delegate type to execute the method.</span></span> <span data-ttu-id="7d2c5-130">Należy rozważyć użycie do minimalizacji liczby typów delegatów, które należy zadeklarować to delegat generyczny.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-130">Consider using a generic delegate to minimize the number of delegate types you need to declare.</span></span> <span data-ttu-id="7d2c5-131">Poniższy kod deklaruje typ Delegat ogólny, który może służyć do wykonywania dowolnej metody z jednym parametrem i zwracanej wartości, lub metody z dwóch parametrów i wartości zwracanej, jeśli delegat jest powiązana z obiektem.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-131">The following code declares a generic delegate type that can be used to execute any method with one parameter and a return value, or a method with two parameters and a return value if the delegate is bound to an object.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2.  <span data-ttu-id="7d2c5-132">Utwórz tablicę, która określa typ parametru metody dynamicznej.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-132">Create an array that specifies the parameter types for the dynamic method.</span></span> <span data-ttu-id="7d2c5-133">W przypadku delegata reprezentującego metodę powiązać obiektu, pierwszy parametr musi być zgodna z typu obiektu delegowanego jest powiązany z.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-133">If the delegate representing the method is to be bound to an object, the first parameter must match the type the delegate is bound to.</span></span> <span data-ttu-id="7d2c5-134">W tym przykładzie są dwa parametry typu `Example` i typ `int` (`Integer` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="7d2c5-134">In this example, there are two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3.  <span data-ttu-id="7d2c5-135">Utwórz <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-135">Create a <xref:System.Reflection.Emit.DynamicMethod>.</span></span> <span data-ttu-id="7d2c5-136">W tym przykładzie metoda nie ma nazwy.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-136">In this example the method has no name.</span></span> <span data-ttu-id="7d2c5-137">Typ wartości zwracanej jest określony jako `int` (`Integer` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="7d2c5-137">The type of the return value is specified as `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="7d2c5-138">Metoda ma dostęp do członków prywatnych i chronionych `Example` klasy.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-138">The method has access to the private and protected members of the `Example` class.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4.  <span data-ttu-id="7d2c5-139">Emituj treści metody.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-139">Emit the method body.</span></span> <span data-ttu-id="7d2c5-140">W tym przykładzie <xref:System.Reflection.Emit.ILGenerator> obiekt jest używany do wysyłania język pośredni firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="7d2c5-140">In this example, an <xref:System.Reflection.Emit.ILGenerator> object is used to emit the Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="7d2c5-141">Alternatywnie <xref:System.Reflection.Emit.DynamicILInfo> obiektu można w połączeniu z generatory kodu niezarządzanego Emituj treść metody <xref:System.Reflection.Emit.DynamicMethod>.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-141">Alternatively, a <xref:System.Reflection.Emit.DynamicILInfo> object can be used in conjunction with unmanaged code generators to emit the method body for a <xref:System.Reflection.Emit.DynamicMethod>.</span></span>  
  
     <span data-ttu-id="7d2c5-142">Pierwszy argument, który jest wystąpieniem ładuje MSIL w tym przykładzie z `Example` klasy i używa go do załadowania wartości pola prywatne wystąpienia typu `int`.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-142">The MSIL in this example loads the first argument, which is an instance of the `Example` class, and uses it to load the value of a private instance field of type `int`.</span></span> <span data-ttu-id="7d2c5-143">Drugi argument jest załadowany, i są mnożone dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-143">The second argument is loaded, and the two numbers are multiplied.</span></span> <span data-ttu-id="7d2c5-144">Jeśli wynik jest większy niż `int`, wartość zostanie obcięta i najbardziej znaczących bitów zostaną odrzucone.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-144">If the result is larger than `int`, the value is truncated and the most significant bits are discarded.</span></span> <span data-ttu-id="7d2c5-145">Metoda zwraca z wartością zwracaną na stosie.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-145">The method returns, with the return value on the stack.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5.  <span data-ttu-id="7d2c5-146">Utwórz wystąpienie obiektu delegowanego (deklaracja w kroku 1) reprezentuje przez wywołanie metody dynamicznej <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> przeciążenie metody.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-146">Create an instance of the delegate (declared in step 1) that represents the dynamic method by calling the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> method overload.</span></span> <span data-ttu-id="7d2c5-147">Tworzenie obiektu delegowanego ukończeniu metody i wszelkie dodatkowe próbuje zmienić metodę — na przykład dodać więcej MSIL — są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-147">Creating the delegate completes the method, and any further attempts to change the method — for example, adding more MSIL — are ignored.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7d2c5-148">Możesz wywołać <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> metody kilka razy do tworzenia delegatów powiązana z innymi wystąpieniami typu docelowego.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-148">You can call the <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> method multiple times to create delegates bound to other instances of the target type.</span></span>  
  
     <span data-ttu-id="7d2c5-149">Poniższy kod wiąże metody nowe wystąpienie klasy `Example` klasy, których pole prywatne testu ma ustawioną wartość 42.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-149">The following code binds the method to a new instance of the `Example` class whose private test field is set to 42.</span></span> <span data-ttu-id="7d2c5-150">Oznacza to, zawsze jest delegat wywoływany wystąpienie `Example` jest przekazywany do pierwszego parametru metody.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-150">That is, each time the delegate is invoked the instance of `Example` is passed to the first parameter of the method.</span></span>  
  
     <span data-ttu-id="7d2c5-151">Delegat `OneParameter` jest używany, ponieważ pierwszy parametr metody zawsze otrzymuje wystąpienie `Example`.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-151">The delegate `OneParameter` is used because the first parameter of the method always receives the instance of `Example`.</span></span> <span data-ttu-id="7d2c5-152">Po wywołaniu delegat drugi parametr jest wymagany.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-152">When the delegate is invoked, only the second parameter is required.</span></span>  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a><span data-ttu-id="7d2c5-153">Przykład</span><span class="sxs-lookup"><span data-stu-id="7d2c5-153">Example</span></span>  
 <span data-ttu-id="7d2c5-154">W poniższym przykładzie kodu pokazano prostą metodę dynamicznego i dynamiczna metoda powiązany z wystąpieniem klasy.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-154">The following code example demonstrates a simple dynamic method and a dynamic method bound to an instance of a class.</span></span>  
  
 <span data-ttu-id="7d2c5-155">Prosta metoda dynamiczne przyjmuje jeden argument, 32-bitową liczbę całkowitą i zwraca kwadrat 64-bitowych tej liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-155">The simple dynamic method takes one argument, a 32-bit integer, and returns the 64-bit square of that integer.</span></span> <span data-ttu-id="7d2c5-156">Delegat ogólny służy do wywoływania metody.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-156">A generic delegate is used to invoke the method.</span></span>  
  
 <span data-ttu-id="7d2c5-157">Druga metoda dynamiczne ma dwa parametry typu `Example` i typ `int` (`Integer` w języku Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="7d2c5-157">The second dynamic method has two parameters, of type `Example` and type `int` (`Integer` in Visual Basic).</span></span> <span data-ttu-id="7d2c5-158">Podczas tworzenia metody dynamicznej jest on powiązany z wystąpieniem `Example`, przy użyciu Delegat ogólny, który ma jeden argument typu `int`.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-158">When the dynamic method has been created, it is bound to an instance of `Example`, using a generic delegate that has one argument of type `int`.</span></span> <span data-ttu-id="7d2c5-159">Delegat nie ma argumentu typu `Example` ponieważ pierwszy parametr metody otrzymuje zawsze powiązane wystąpienie `Example`.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-159">The delegate does not have an argument of type `Example` because the first parameter of the method always receives the bound instance of `Example`.</span></span> <span data-ttu-id="7d2c5-160">Jeśli delegat jest wywoływany, tylko `int` argumentu.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-160">When the delegate is invoked, only the `int` argument is supplied.</span></span> <span data-ttu-id="7d2c5-161">Pole prywatne uzyskuje dostęp do tej metody dynamicznej `Example` klasy i zwraca iloczyn pole prywatne i `int` argumentu.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-161">This dynamic method accesses a private field of the `Example` class and returns the product of the private field and the `int` argument.</span></span>  
  
 <span data-ttu-id="7d2c5-162">Przykładowy kod definiuje delegatów, które mogą służyć do wykonywania metody.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-162">The code example defines delegates that can be used to execute the methods.</span></span>  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7d2c5-163">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7d2c5-163">Compiling the Code</span></span>  
  
-   <span data-ttu-id="7d2c5-164">Zawiera kod C# `using` instrukcje (`Imports` w języku Visual Basic) niezbędne do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-164">The code contains the C# `using` statements (`Imports` in Visual Basic) necessary for compilation.</span></span>  
  
-   <span data-ttu-id="7d2c5-165">Nie odwołania do zestawów dodatkowe są wymagane.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-165">No additional assembly references are required.</span></span>  
  
-   <span data-ttu-id="7d2c5-166">Kompilowanie kodu w wierszu polecenia przy użyciu csc.exe, vbc.exe lub cl.exe.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-166">Compile the code at the command line using csc.exe, vbc.exe, or cl.exe.</span></span> <span data-ttu-id="7d2c5-167">Aby skompilować kod w programie Visual Studio, należy umieścić w szablonie Projekt aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="7d2c5-167">To compile the code in Visual Studio, place it in a console application project template.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d2c5-168">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7d2c5-168">See Also</span></span>  
 <xref:System.Reflection.Emit.DynamicMethod>  
 [<span data-ttu-id="7d2c5-169">Emituj za pomocą odbicia</span><span class="sxs-lookup"><span data-stu-id="7d2c5-169">Using Reflection Emit</span></span>](http://msdn.microsoft.com/en-us/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)  
 [<span data-ttu-id="7d2c5-170">Emisja odbicia scenariuszy dynamicznej — metoda</span><span class="sxs-lookup"><span data-stu-id="7d2c5-170">Reflection Emit Dynamic Method Scenarios</span></span>](http://msdn.microsoft.com/en-us/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)