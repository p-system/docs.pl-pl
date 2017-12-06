---
title: ManualResetEvent i ManualResetEventSlim
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f663dd17b063f77e2f9ce6bd4bbd0f8859ba4116
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="manualresetevent-and-manualreseteventslim"></a><span data-ttu-id="275cc-102">ManualResetEvent i ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="275cc-102">ManualResetEvent and ManualResetEventSlim</span></span>
<span data-ttu-id="275cc-103"><xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Klasa reprezentuje zdarzenie dojścia oczekiwania lokalnych, które można ręcznie zresetować po zostanie zasygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="275cc-103">The <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class represents a local wait handle event that must be reset manually after it is signaled.</span></span> <span data-ttu-id="275cc-104">Ta klasa reprezentuje szczególnych przypadkach klasy podstawowej, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="275cc-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span></span> <span data-ttu-id="275cc-105">Zobacz [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) dokumentacja koncepcyjna wykorzystania i funkcje ręczne Resetowanie zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="275cc-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of manual reset events.</span></span>  
  
 <span data-ttu-id="275cc-106">A <xref:System.Threading.ManualResetEvent> obiekt pozostaje sygnałowego aż do jego <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="275cc-106">A <xref:System.Threading.ManualResetEvent> object remains signaled until its <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="275cc-107">Liczba wątków lub wątków oczekiwania na zdarzenie po zostały sygnalizuje, może być zwolnione, gdy stan obiektu jest sygnalizowane.</span><span class="sxs-lookup"><span data-stu-id="275cc-107">Any number of waiting threads, or threads that wait on the event after it has been signaled, can be released while the object's state is signaled.</span></span> <span data-ttu-id="275cc-108"><xref:System.Threading.ManualResetEvent>odpowiada Win32 `CreateEvent` wywołać, określając `true` dla `bManualReset` argumentu.</span><span class="sxs-lookup"><span data-stu-id="275cc-108"><xref:System.Threading.ManualResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `true` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="275cc-109">W [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], można użyć <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> klasy w celu poprawy wydajności podczas powinny być bardzo krótkie czasy oczekiwania i zdarzenia nie przecina granicę procesu.</span><span class="sxs-lookup"><span data-stu-id="275cc-109">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use the <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> class for better performance when wait times are expected to be very short, and when the event does not cross a process boundary.</span></span> <span data-ttu-id="275cc-110"><xref:System.Threading.ManualResetEventSlim>używa wirowania przez krótki czas podczas oczekiwania na zdarzenia stają się sygnalizowane zajęty.</span><span class="sxs-lookup"><span data-stu-id="275cc-110"><xref:System.Threading.ManualResetEventSlim> uses busy spinning for a short time while it waits for the event to become signaled.</span></span> <span data-ttu-id="275cc-111">W przypadku krótki czas oczekiwania Obracająca może być znacznie mniej kosztowne niż czekanie przy użyciu uchwyty oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="275cc-111">When wait times are short, spinning can be much less expensive than waiting by using wait handles.</span></span> <span data-ttu-id="275cc-112">Jednak jeśli zdarzenia stają się nie sygnalizowano w przedziale czasu, <xref:System.Threading.ManualResetEventSlim> uporządkowana do regularnego zdarzenia dojścia oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="275cc-112">However, if the event does not become signaled within a certain period of time, <xref:System.Threading.ManualResetEventSlim> resorts to a regular event handle wait.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="275cc-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="275cc-113">See Also</span></span>  
 [<span data-ttu-id="275cc-114">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="275cc-114">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="275cc-115">Wątkowość obiektów i funkcji</span><span class="sxs-lookup"><span data-stu-id="275cc-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="275cc-116">Uchwyty oczekiwania</span><span class="sxs-lookup"><span data-stu-id="275cc-116">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [<span data-ttu-id="275cc-117">Autoresetevent —</span><span class="sxs-lookup"><span data-stu-id="275cc-117">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 [<span data-ttu-id="275cc-118">Metody SpinWait</span><span class="sxs-lookup"><span data-stu-id="275cc-118">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 [<span data-ttu-id="275cc-119">Semafor i klasa SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="275cc-119">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)