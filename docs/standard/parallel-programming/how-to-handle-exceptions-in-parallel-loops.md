---
title: 'Porady: obsługa wyjątków w pętlach równoległych'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11ba240d71287be91bd0b4b40a2cb69f6e2808d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580552"
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a>Porady: obsługa wyjątków w pętlach równoległych
<xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> przeciążenia nie ma żadnych specjalnych mechanizm obsługi wyjątków, które może zostać zgłoszony. W związku z tym są podobne do zwykłych `for` i `foreach` pętli (`For` i `For Each` w języku Visual Basic); wystąpił nieobsługiwany wyjątek powoduje pętli zakończenie natychmiast.  
  
 Po dodaniu własną logikę obsługi wyjątków, aby pętle równoległe, obsługiwać przypadek, w którym podobne wyjątki może zostać zgłoszone na wiele wątków jednocześnie i przypadków, w którym wyjątek w wątku, co powoduje, że kolejny wyjątek zostanie wygenerowany na innym Wątek. Może obsługiwać obu przypadkach zawijania wszystkie wyjątki pętlę w <xref:System.AggregateException?displayProperty=nameWithType>. W poniższym przykładzie przedstawiono jeden ze sposobów możliwe.  
  
> [!NOTE]
>  Po włączeniu "Tylko mój kod" programu Visual Studio w niektórych przypadkach będzie podział wiersza, która zgłasza wyjątek i wyświetlony komunikat o błędzie stwierdzający "wyjątek nie obsłużony przez kod użytkownika." Ten błąd jest niegroźne. Naciśnij klawisz F5, aby nadal z niego i zachowanie obsługi wyjątków, które przedstawiono w poniższym przykładzie. Aby zapobiec dzieleniu pierwszego błędu w Visual Studio, wystarczy usunąć zaznaczenie pola wyboru "Tylko mój kod" w obszarze **narzędzia, opcje, debugowanie, ogólne**.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wszystkie wyjątki są przechwycony i następnie otoczona <xref:System.AggregateException?displayProperty=nameWithType> który jest generowany. Obiekt wywołujący można zdecydować, które wyjątki, aby obsłużyć.  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a>Zobacz też  
 [Równoległość danych](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Wyrażenia Lambda w PLINQ i TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
