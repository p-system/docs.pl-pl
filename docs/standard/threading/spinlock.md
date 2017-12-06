---
title: SpinLock
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: efe9b3126b3c952ab156f9ca40752ad8d3fddcd1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="spinlock"></a><span data-ttu-id="93307-102">SpinLock</span><span class="sxs-lookup"><span data-stu-id="93307-102">SpinLock</span></span>
<span data-ttu-id="93307-103"><xref:System.Threading.SpinLock> Struktura jest niskiego poziomu, wzajemne wykluczenie prymitywu synchronizacji, który obraca podczas oczekiwania na uzyskanie blokady.</span><span class="sxs-lookup"><span data-stu-id="93307-103">The <xref:System.Threading.SpinLock> structure is a low-level, mutual-exclusion synchronization primitive that spins while it waits to acquire a lock.</span></span> <span data-ttu-id="93307-104">W przypadku komputerów wielordzeniowych podczas czasy oczekiwania są powinien być krótki i kiedy rywalizacji jest minimalny <xref:System.Threading.SpinLock> może działać lepiej niż inne rodzaje blokad.</span><span class="sxs-lookup"><span data-stu-id="93307-104">On multicore computers, when wait times are expected to be short and when contention is minimal, <xref:System.Threading.SpinLock> can perform better than other kinds of locks.</span></span> <span data-ttu-id="93307-105">Jednak zaleca się używanie <xref:System.Threading.SpinLock> tylko przy określaniu przez profilowania, która <xref:System.Threading.Monitor?displayProperty=nameWithType> metody lub <xref:System.Threading.Interlocked> metody znacznie spowalniają działanie programu.</span><span class="sxs-lookup"><span data-stu-id="93307-105">However, we recommend that you use <xref:System.Threading.SpinLock> only when you determine by profiling that the <xref:System.Threading.Monitor?displayProperty=nameWithType> method or the <xref:System.Threading.Interlocked> methods are significantly slowing the performance of your program.</span></span>  
  
 <span data-ttu-id="93307-106"><xref:System.Threading.SpinLock>może spowodować przedział czasu w wątku, nawet jeśli nie ma jeszcze uzyskać blokady.</span><span class="sxs-lookup"><span data-stu-id="93307-106"><xref:System.Threading.SpinLock> may yield the time slice of the thread even if it has not yet acquired the lock.</span></span> <span data-ttu-id="93307-107">Jest to, aby uniknąć odwracanie priorytetu wątku i Włącz moduł zbierający elementy bezużyteczne postęp.</span><span class="sxs-lookup"><span data-stu-id="93307-107">It does this to avoid thread-priority inversion, and to enable the garbage collector to make progress.</span></span> <span data-ttu-id="93307-108">Jeśli używasz <xref:System.Threading.SpinLock>, upewnij się, wątku nie może zawierać blokady dla więcej niż bardzo krótki okres oraz że wątku nie można zablokować, gdy posiada blokady.</span><span class="sxs-lookup"><span data-stu-id="93307-108">When you use a <xref:System.Threading.SpinLock>, ensure that no thread can hold the lock for more than a very brief time span, and that no thread can block while it holds the lock.</span></span>  
  
 <span data-ttu-id="93307-109">Ponieważ struktury SpinLock jest typem wartości, należy jawnie przekazujesz ją przez odwołanie, jeśli planujesz obydwie kopie do odwoływania się do tego samego blokady.</span><span class="sxs-lookup"><span data-stu-id="93307-109">Because SpinLock is a value type, you must explicitly pass it by reference if you intend the two copies to refer to the same lock.</span></span>  
  
 <span data-ttu-id="93307-110">Aby uzyskać więcej informacji na temat używania tego typu, zobacz <xref:System.Threading.SpinLock?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="93307-110">For more information about how to use this type, see <xref:System.Threading.SpinLock?displayProperty=nameWithType>.</span></span> <span data-ttu-id="93307-111">Na przykład zobacz [porady: struktury Użyj SpinLock do synchronizacji niższego poziomu](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="93307-111">For an example, see [How to: Use SpinLock for Low-Level Synchronization](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).</span></span>  
  
 <span data-ttu-id="93307-112"><xref:System.Threading.SpinLock>obsługuje *wątku*-*śledzenia* tryb pomocne podczas fazy opracowywania służące do śledzenia w wątku, który jest z blokadą w określonym czasie.</span><span class="sxs-lookup"><span data-stu-id="93307-112"><xref:System.Threading.SpinLock> supports a *thread*-*tracking* mode that you can use during the development phase to help track the thread that is holding the lock at a specific time.</span></span> <span data-ttu-id="93307-113">Tryb śledzenia wątków jest bardzo przydatne w przypadku debugowania, ale firma Microsoft zaleca wyłączenie go w wydanej wersji programu, ponieważ może zmniejszyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="93307-113">Thread-tracking mode is very useful for debugging, but we recommend that you turn it off in the release version of your program because it may slow performance.</span></span> <span data-ttu-id="93307-114">Aby uzyskać więcej informacji, zobacz [porady: tryb włączyć wątku śledzenia w strukturze SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).</span><span class="sxs-lookup"><span data-stu-id="93307-114">For more information, see [How to: Enable Thread-Tracking Mode in SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93307-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93307-115">See Also</span></span>  
 [<span data-ttu-id="93307-116">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="93307-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)