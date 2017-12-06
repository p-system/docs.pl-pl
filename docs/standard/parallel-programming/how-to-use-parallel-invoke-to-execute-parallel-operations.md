---
title: "Porady: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8a51f180a394c1baa2ecb0620279ea15c62e1edc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a><span data-ttu-id="5a5ba-102">Porady: korzystanie z parallel_invoke podczas przeprowadzania operacji równoległych</span><span class="sxs-lookup"><span data-stu-id="5a5ba-102">How to: Use Parallel.Invoke to Execute Parallel Operations</span></span>
<span data-ttu-id="5a5ba-103">W tym przykładzie pokazano, jak parallelize operacje przy użyciu <xref:System.Threading.Tasks.Parallel.Invoke%2A> w bibliotece równoległych zadań.</span><span class="sxs-lookup"><span data-stu-id="5a5ba-103">This example shows how to parallelize operations by using <xref:System.Threading.Tasks.Parallel.Invoke%2A> in the Task Parallel Library.</span></span> <span data-ttu-id="5a5ba-104">Trzy operacje są wykonywane na udostępnione źródło danych.</span><span class="sxs-lookup"><span data-stu-id="5a5ba-104">Three operations are performed on a shared data source.</span></span> <span data-ttu-id="5a5ba-105">Ponieważ żadna z operacji modyfikuje źródło, mogą być wykonywane równolegle w sposób proste.</span><span class="sxs-lookup"><span data-stu-id="5a5ba-105">Because none of the operations modifies the source, they can be executed in parallel in a straightforward manner.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a5ba-106">Ta dokumentacja używa wyrażeń lambda do definiowania delegatów w TPL.</span><span class="sxs-lookup"><span data-stu-id="5a5ba-106">This documentation uses lambda expressions to define delegates in TPL.</span></span> <span data-ttu-id="5a5ba-107">Jeśli nie masz doświadczenia z wyrażenia lambda w języku C# lub Visual Basic, zobacz [wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="5a5ba-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda Expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a5ba-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="5a5ba-108">Example</span></span>  
 [!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
 [!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]  
  
 <span data-ttu-id="5a5ba-109">Należy pamiętać, że z <xref:System.Threading.Tasks.Parallel.Invoke%2A>, po prostu express akcje, które chcesz uruchamiać jednocześnie i środowiska uruchomieniowego obsługuje wszystkie wątku planowania szczegółów, takich jak automatycznie skalować liczbę rdzeni na komputerze hosta.</span><span class="sxs-lookup"><span data-stu-id="5a5ba-109">Note that with <xref:System.Threading.Tasks.Parallel.Invoke%2A>, you simply express which actions you want to run concurrently, and the runtime handles all thread scheduling details, including scaling automatically to the number of cores on the host computer.</span></span>  
  
 <span data-ttu-id="5a5ba-110">W tym przykładzie parallelizes operacji, a nie dane.</span><span class="sxs-lookup"><span data-stu-id="5a5ba-110">This example parallelizes the operations, not the data.</span></span> <span data-ttu-id="5a5ba-111">Jako alternatywne podejście możesz parallelize zapytań LINQ za pomocą PLINQ i zapytania są wykonywane sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="5a5ba-111">As an alternate approach, you can parallelize the LINQ queries by using PLINQ and run the queries sequentially.</span></span> <span data-ttu-id="5a5ba-112">Alternatywnie można parallelize danych przy użyciu PLINQ.</span><span class="sxs-lookup"><span data-stu-id="5a5ba-112">Alternatively, you could parallelize the data by using PLINQ.</span></span> <span data-ttu-id="5a5ba-113">Innym rozwiązaniem jest parallelize zarówno zapytania i zadania.</span><span class="sxs-lookup"><span data-stu-id="5a5ba-113">Another option is to parallelize both the queries and the tasks.</span></span> <span data-ttu-id="5a5ba-114">Mimo że powstałe w ten sposób obciążenie może zmniejszyć wydajność na komputerach hostów mają względnie mało procesory, go będzie skalować znacznie poprawia na komputerach z wielu procesorów.</span><span class="sxs-lookup"><span data-stu-id="5a5ba-114">Although the resulting overhead might degrade performance on host computers with relatively few processors, it would scale much better on computers with many processors.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5a5ba-115">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="5a5ba-115">Compiling the Code</span></span>  
  
-   <span data-ttu-id="5a5ba-116">Skopiuj i Wklej cały przykład do projektu Microsoft Visual Studio 2010 i naciśnij klawisz F5.</span><span class="sxs-lookup"><span data-stu-id="5a5ba-116">Copy and paste the entire example into a Microsoft Visual Studio 2010 project and press F5.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a5ba-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5a5ba-117">See Also</span></span>  
 [<span data-ttu-id="5a5ba-118">Programowanie równoległe</span><span class="sxs-lookup"><span data-stu-id="5a5ba-118">Parallel Programming</span></span>](../../../docs/standard/parallel-programming/index.md)  
 [<span data-ttu-id="5a5ba-119">Porady: anulowanie zadania i jego elementów podrzędnych</span><span class="sxs-lookup"><span data-stu-id="5a5ba-119">How to: Cancel a Task and Its Children</span></span>](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)  
 [<span data-ttu-id="5a5ba-120">Równoległe LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="5a5ba-120">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)