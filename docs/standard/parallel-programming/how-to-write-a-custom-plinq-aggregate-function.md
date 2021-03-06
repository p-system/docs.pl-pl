---
title: 'Porady: pisanie niestandardowej funkcji agregowania w PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a7aa2a8e5d9695c08d1c98e05cdd1eaa4d9a5318
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580913"
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a>Porady: pisanie niestandardowej funkcji agregowania w PLINQ
Ten przykład przedstawia sposób użycia <xref:System.Linq.ParallelEnumerable.Aggregate%2A> metody dotyczą funkcji agregacji niestandardowej sekwencji źródłowej.  
  
> [!WARNING]
>  W tym przykładzie jest jedynie do zademonstrowania użycia i mogą nie działać szybciej niż równoważne sekwencyjnych zapytań LINQ do obiektów zapytania. Aby uzyskać więcej informacji na temat przyspieszenie, zobacz [przyspieszeniach w PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie oblicza odchylenie standardowe sekwencją liczb całkowitych.  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 W tym przykładzie używane jest przeciążenie operatora agregacji standardowej kwerendy, który jest unikatowy dla PLINQ. To przeciążenie zajmuje dodatkowy <xref:System.Func%603?displayProperty=nameWithType> jako trzeci parametr wejściowy. Ten delegat łączy wyniki ze wszystkich wątków przed przesłaniem ostatecznego obliczenia wyników zagregowany. W tym przykładzie dodamy razem sumy ze wszystkich wątków.  
  
 Należy pamiętać, że jeśli treści wyrażenia lambda składa się z samym wyrażeniu, zwracana wartość <xref:System.Func%602?displayProperty=nameWithType> delegat jest wartość wyrażenia.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq.ParallelEnumerable>  
 [Równoległe LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
