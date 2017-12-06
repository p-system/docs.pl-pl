---
title: "Porady: wywoływanie Windows API (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a219e031cdd36c713db8dcee6cc1da3849c9cf93
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-windows-apis-visual-basic"></a><span data-ttu-id="e943b-102">Porady: wywoływanie Windows API (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e943b-102">How to: Call Windows APIs (Visual Basic)</span></span>
<span data-ttu-id="e943b-103">W tym przykładzie definiuje i wywołuje `MessageBox` funkcji w user32.dll, a następnie przekazuje ciąg do niego.</span><span class="sxs-lookup"><span data-stu-id="e943b-103">This example defines and calls the `MessageBox` function in user32.dll and then passes a string to it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e943b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e943b-104">Example</span></span>  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e943b-105">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e943b-105">Compiling the Code</span></span>  
 <span data-ttu-id="e943b-106">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e943b-106">This example requires:</span></span>  
  
-   <span data-ttu-id="e943b-107">Odwołanie do <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="e943b-107">A reference to the <xref:System> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e943b-108">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="e943b-108">Robust Programming</span></span>  
 <span data-ttu-id="e943b-109">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="e943b-109">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="e943b-110">Metoda nie jest statyczny, jest abstrakcyjna lub został wcześniej zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="e943b-110">The method is not static, is abstract, or has been previously defined.</span></span> <span data-ttu-id="e943b-111">Typ nadrzędny jest interfejsem lub długość *nazwa* lub *dllName* wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="e943b-111">The parent type is an interface, or the length of *name* or *dllName* is zero.</span></span> <span data-ttu-id="e943b-112">(<xref:System.ArgumentException>)</span><span class="sxs-lookup"><span data-stu-id="e943b-112">(<xref:System.ArgumentException>)</span></span>  
  
-   <span data-ttu-id="e943b-113">*Nazwa* lub *dllName* jest `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="e943b-113">The *name* or *dllName* is `Nothing`.</span></span> <span data-ttu-id="e943b-114">(<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="e943b-114">(<xref:System.ArgumentNullException>)</span></span>  
  
-   <span data-ttu-id="e943b-115">Typ zawierający wcześniej utworzono za pomocą `CreateType`.</span><span class="sxs-lookup"><span data-stu-id="e943b-115">The containing type has been previously created using `CreateType`.</span></span> <span data-ttu-id="e943b-116">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="e943b-116">(<xref:System.InvalidOperationException>)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e943b-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e943b-117">See Also</span></span>  
 [<span data-ttu-id="e943b-118">Bliższe spojrzenie na platformie wywołania</span><span class="sxs-lookup"><span data-stu-id="e943b-118">A Closer Look at Platform Invoke</span></span>](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [<span data-ttu-id="e943b-119">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="e943b-119">Platform Invoke Examples</span></span>](../../../framework/interop/platform-invoke-examples.md)  
 [<span data-ttu-id="e943b-120">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="e943b-120">Consuming Unmanaged DLL Functions</span></span>](../../../framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="e943b-121">Emituj definiowanie metody za pomocą odbicia</span><span class="sxs-lookup"><span data-stu-id="e943b-121">Defining a Method with Reflection Emit</span></span>](http://msdn.microsoft.com/en-us/84fd3bf6-628f-41aa-83d9-b990cf926e81)  
 [<span data-ttu-id="e943b-122">Wskazówki: Wywoływanie Windows API</span><span class="sxs-lookup"><span data-stu-id="e943b-122">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [<span data-ttu-id="e943b-123">Współdziałanie z COM</span><span class="sxs-lookup"><span data-stu-id="e943b-123">COM Interop</span></span>](../../../visual-basic/programming-guide/com-interop/index.md)