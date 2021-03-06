---
title: Anulowanie zadania
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, cancellation
- asynchronous task cancellation
ms.assetid: 3ecf1ea9-e399-4a6a-a0d6-8475f48dcb28
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4b9a9331f62ba9655c20a2e27b3a94dac1903472
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582691"
---
# <a name="task-cancellation"></a>Anulowanie zadania
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> i <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> klasy obsługuje anulowania przy użyciu anulowanie tokenów w programie .NET Framework. Aby uzyskać więcej informacji, zobacz [anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md). W klasach Task anulowanie pociąga za sobą współpracę pełnomocnika użytkownika, który reprezentuje możliwości anulowania operacji i kodu, który zażądał anulowania.  Pomyślne anulowania obejmuje żądania wywołania kodu <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> — metoda i delegowanie użytkownika zakończenie operacji w odpowiednim czasie. Można zakończyć operację przy użyciu jednej z następujących opcji:  
  
-   Powracając po prostu od pełnomocnika. W wielu scenariuszach jest wystarczające; Jednak wystąpienie zadania, które zostało anulowane w ten sposób przejścia do <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> stanu, aby nie <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> stanu.  
  
-   Przez zgłaszanie <xref:System.OperationCanceledException> i przekazanie jej przez token, na których zażądano anulowania. Preferowaną metodą w tym celu jest użycie <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> metody. Zadanie, które zostało anulowane w ten sposób, przechodzi do stanu Canceled, którego kod wywołujący może użyć do sprawdzenia, czy zadanie odpowiedziało na żądanie anulowania.  
  
 Poniższy przykład przedstawia podstawowy wzorzec anulowania zadania ze zgłoszeniem wyjątku. Należy zauważyć, że token jest przekazywany do pełnomocnika użytkownika i do samego wystąpienia zadania.  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 Aby uzyskać bardziej szczegółowy przykład, zobacz [porady: anulowanie zadania i jego elementy podrzędne](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md).  
  
 Gdy wystąpienie zadania przestrzega <xref:System.OperationCanceledException> zgłoszone przez kod użytkownika, porównuje token wyjątek do jego skojarzony tokenu (jeden, który został przekazany do interfejsu API, który utworzył zadanie). Jeśli są one takie same i tokenu <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość zwraca wartość true, interpretuje jako potwierdzeniem anulowania i przechodzi w stan Anulowane zadania. Jeśli nie używasz <xref:System.Threading.Tasks.Task.Wait%2A> lub <xref:System.Threading.Tasks.Task.WaitAll%2A> metody oczekiwania zadania, a następnie zadanie tylko ustawia jego stan na <xref:System.Threading.Tasks.TaskStatus.Canceled>.  
  
 Jeśli są oczekiwanie na zadanie, które przechodzi w stan Anulowane <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> wyjątek (ujęte w <xref:System.AggregateException> wyjątek) zostanie zgłoszony. Należy zauważyć, że ten wyjątek wskazuje pomyślne anulowanie, a nie błędną sytuację. W związku z tym zadania <xref:System.Threading.Tasks.Task.Exception%2A> zwraca właściwość `null`.  
  
 Jeśli token <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> właściwość zwraca wartość false lub token wyjątek niezgodny zadania obiektu tokenu, <xref:System.OperationCanceledException> jest traktowany jak normalne wyjątek, powodując zadań, aby przejść w stan końcowy: Faulted. Należy także zauważyć, że obecność innych wyjątków także spowoduje przejście zadania do stanu Faulted. Można pobrać stanu ukończonego zadania w <xref:System.Threading.Tasks.Task.Status%2A> właściwości.  
  
 Możliwe jest, że zadanie będzie kontynuować przetwarzanie niektórych elementy po żądania anulowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Anulowanie w zarządzanych wątkach](../../../docs/standard/threading/cancellation-in-managed-threads.md)  
 [Instrukcje: anulowanie zadania i jego elementów podrzędnych](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
