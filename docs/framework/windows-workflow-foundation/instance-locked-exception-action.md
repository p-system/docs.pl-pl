---
title: "Wystąpienie zablokowane wyjątku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 164a5419-315c-4987-ad72-54cbdb88d402
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f3a52550624e93fb9d262f7df2d2e922369c90a8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="instance-locked-exception-action"></a><span data-ttu-id="e1c8f-102">Wystąpienie zablokowane wyjątku</span><span class="sxs-lookup"><span data-stu-id="e1c8f-102">Instance Locked Exception Action</span></span>
<span data-ttu-id="e1c8f-103"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> Właściwość w magazynie wystąpień przepływu pracy SQL pozwala określić akcję dostawca trwałości SQL powinien wykonać, gdy odbierze <xref:System.Runtime.DurableInstancing.InstanceLockedException>.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-103">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> property of the SQL Workflow Instance Store lets you specify what action the SQL persistence provider should take when it receives an <xref:System.Runtime.DurableInstancing.InstanceLockedException>.</span></span> <span data-ttu-id="e1c8f-104">Dostawca trwałości odbiera ten wyjątek podczas próby blokady wystąpienia usługi przepływu pracy, który jest zablokowany przez innego hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-104">The persistence provider receives this exception when it tries to lock a workflow service instance that is currently locked by another service host.</span></span> <span data-ttu-id="e1c8f-105">Wartości dla tej właściwości to <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>, <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>, i <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-105">The values for this property are <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>, <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>, and <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>.</span></span> <span data-ttu-id="e1c8f-106">Wartość domyślna to <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-106">The default value is <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>.</span></span> <span data-ttu-id="e1c8f-107">Na poniższej liście opisano trzy opcje:</span><span class="sxs-lookup"><span data-stu-id="e1c8f-107">The following list describes the three options:</span></span>  
  
-   <span data-ttu-id="e1c8f-108"><xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-108"><xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>.</span></span> <span data-ttu-id="e1c8f-109">Host usługi nie jest podejmowana próba blokady wystąpienia usługi przepływu pracy i przekazuje <xref:System.Runtime.DurableInstancing.InstanceLockedException> do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-109">The service host does not attempt to lock the workflow service instance and passes the <xref:System.Runtime.DurableInstancing.InstanceLockedException> to the caller.</span></span>  <span data-ttu-id="e1c8f-110">Jeśli przepływ pracy pozostaje w pamięci na okres przekraczający 60 sekund, użyj <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry> jako ponów próbę.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-110">If your workflow stays in memory for a period exceeding 60 seconds, use <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry> as the retry.</span></span> <span data-ttu-id="e1c8f-111">Wartość domyślna to <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-111">The default value is <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>.</span></span>  
  
-   <span data-ttu-id="e1c8f-112"><xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-112"><xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>.</span></span> <span data-ttu-id="e1c8f-113">Host usługi reattempts do zablokowania wystąpienia usługi przepływu pracy o liniowej interwał ponawiania prób i przekazuje <xref:System.Runtime.DurableInstancing.InstanceLockedException> do wywołującego na końcu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-113">The service host reattempts to lock the workflow service instance with a linear interval between retry attempts and passes the <xref:System.Runtime.DurableInstancing.InstanceLockedException> to the caller at the end of the sequence.</span></span> <span data-ttu-id="e1c8f-114">Jeśli przepływ pracy zostanie pozostaje w pamięci około od 5 do 60 sekund i nadchodzą komunikaty w partiach gdzie jest bardziej prawdopodobne dla komunikatów są wysyłane do tego samego wystąpienia na tym samym hoście, aby przetworzyć wszystkie komunikaty przed zwolnieniem przepływu pracy, użyj <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> do osiągnąć najlepsze opóźnienia bez marnować zasobów.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-114">If you workflow stays in memory approximately between 5-60 seconds, and messages arrive in batches where it is more likely for messages being sent to the same instance on the same host to process all messages before unloading the workflow, use <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> to achieve the best latency without wasting resources.</span></span>  
  
-   <span data-ttu-id="e1c8f-115"><xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-115"><xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>.</span></span> <span data-ttu-id="e1c8f-116">Host usługi reattempts do zablokowania wystąpienia usługi przepływu pracy wykładniczego wycofywania interwał między ponownymi próbami i przekazuje wyjątek do wywołującego na końcu sekwencji.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-116">The service host reattempts to lock the workflow service instance with an exponential backoff interval between retry attempts, and passes the exception to the caller at the end of the sequence.</span></span> <span data-ttu-id="e1c8f-117">Jeśli przepływ pracy pozostaje w pamięci na bardzo krótkim czasie (mniej niż 5 sekund) lub sieci Web farmy jest duży i nie jest bardzo duże ryzyko kolejną wiadomość dostarczona do tego samego hosta, należy użyć <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry> do osiągnięcia najlepsze opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-117">If your workflow stays in memory for a very short time (less than 5 seconds), or a Web farm is large and the chance of another message being delivered to the same host is not very high, use <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry> to achieve the best latency.</span></span>  
  
 <span data-ttu-id="e1c8f-118">Funkcja akcji wyjątek zablokowane wystąpienie obsługuje następujące scenariusze.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-118">The Instance Locked Exception Action feature supports the following scenarios.</span></span> <span data-ttu-id="e1c8f-119">We wszystkich scenariuszach, jeśli ustawiono właściwość instanceLockedExceptionAction obiekt SqlWorkflowInstanceStore <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> lub <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>, host niewidocznie ponawia próbę uzyskania blokady wystąpienia okresowo.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-119">In all scenarios, if the instanceLockedExceptionAction property of the SqlWorkflowInstanceStore is set to <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> or <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>, the host transparently retries to acquire the lock on instances periodically.</span></span>  
  
1.  <span data-ttu-id="e1c8f-120">**Włączanie bezpiecznego zamknięcia i nachodzące odtwarzania domen aplikacji.**</span><span class="sxs-lookup"><span data-stu-id="e1c8f-120">**Enabling graceful shutdown and overlapped recycling of application domains.**</span></span> <span data-ttu-id="e1c8f-121">Załóżmy, że **elementu AppDomain** z hostem usługi uruchamiania przepływu pracy wystąpień usługi jest w trakcie odtwarzania i nowy **elementu AppDomain** jest włączane do obsługi nowych żądań równolegle równocześnie z  **Elementu AppDomain** obniżył jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-121">Suppose an **AppDomain** with a service host running workflow service instances is being recycled and a new **AppDomain** is brought up to handle new requests in parallel while the old **AppDomain** is brought down gracefully.</span></span> <span data-ttu-id="e1c8f-122">Zamknięcie czeka, aż wystąpienie usługi przepływu pracy są w stanie bezczynności, a następnie będzie się powtarzać i zwalnia wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-122">The shutdown waits until workflow service instances are idle, and then persists and unloads the instances.</span></span> <span data-ttu-id="e1c8f-123">Wszystkie próby dostępu hosty w nowym **elementu AppDomain** do zablokowania wystąpienia spowoduje, że <xref:System.Runtime.DurableInstancing.InstanceLockedException>.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-123">Any attempts by hosts in the new **AppDomain** to lock an instance will cause an <xref:System.Runtime.DurableInstancing.InstanceLockedException>.</span></span>  
  
2.  <span data-ttu-id="e1c8f-124">**Poziomo skalowanie trwałe przepływy pracy jednorodnych farmie serwerów.**</span><span class="sxs-lookup"><span data-stu-id="e1c8f-124">**Horizontally scaling durable workflows across a homogeneous farm of servers.**</span></span> <span data-ttu-id="e1c8f-125">Załóżmy, że węzeł farmy serwerów, na którym działa wystąpienie przepływu pracy awarii (Crash) i hosta przepływu pracy nie można usunąć blokady wystąpienia, który jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-125">Suppose a node of a server farm on which a workflow instance is running crashes and the workflow host cannot remove locks on the instance it is running.</span></span> <span data-ttu-id="e1c8f-126">Gdy hosta usługi uruchomione w innym węźle farmy odbiera komunikat dla tego wystąpienia przepływu pracy, próbuje uzyskać blokad w tych wystąpieniach odbieranie <xref:System.Runtime.DurableInstancing.InstanceLockedException>.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-126">When a service host running on another node of the farm receives a message for that workflow instance, it tries to acquire locks on these instances it will receive the <xref:System.Runtime.DurableInstancing.InstanceLockedException>.</span></span> <span data-ttu-id="e1c8f-127">Blokad wygaśnie po pewnym czasie, ponieważ hosta, który miał odnawiania blokady już istnieje.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-127">The locks will expire after some time because the host that was supposed to renew the lock no longer exists.</span></span>  
  
     <span data-ttu-id="e1c8f-128">**Poziomo skalowanie trwałe przepływy pracy jednorodnych farmie serwerów.**</span><span class="sxs-lookup"><span data-stu-id="e1c8f-128">**Horizontally scaling durable workflows across a homogeneous farm of servers.**</span></span>  <span data-ttu-id="e1c8f-129">Załóżmy, że ma być skalowana w poziomie trwałe przepływu pracy przy użyciu wielu hostach za równoważenia obciążenia Sieciowego (Usługa równoważenia obciążenia sieciowego), hosta przepływów pracy uruchomionych na jednym węźle farmy ładuje wystąpienia przepływu pracy i przetwarza komunikat i następny komunikat do wystąpienia jest kierowany do hosta, który jest uruchomiona w innym węźle, ponieważ Równoważenie obciążenia Sieciowego nie ma algorytmu routingu na dostarczenie wiadomości do hosta, który jest już uruchomione wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-129">Suppose you want to horizontally scale a durable workflow using multiple hosts behind a NLB (Network Load Balancer), the workflow host running on one node of the farm loads a workflow instance and is processing a message, and the next message to the instance is routed to the host that is running on another node because the NLB does not have routing algorithm to deliver messages to the host that is already running the instance.</span></span> <span data-ttu-id="e1c8f-130">Po otrzymaniu komunikatu, drugi host próbuje załadować wystąpienia przepływu pracy i odbiera <xref:System.Runtime.DurableInstancing.InstanceLockedException> ponieważ pierwszego hosta jest zablokowany w wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-130">Upon receiving the message, the second host attempts to load the workflow instance and receives the <xref:System.Runtime.DurableInstancing.InstanceLockedException> because the first host has a lock on the instance.</span></span> <span data-ttu-id="e1c8f-131">Po zakończeniu przy użyciu przetwarzania do pierwszej wiadomości i drugim hoście uzyskuje blokadę ponawia próbę po następnym, ładuje wystąpienie, a drugi komunikat przetwarza pierwszego hosta umożliwia odblokowanie wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="e1c8f-131">The first host unlocks the instance when it is finished with processing the first message and the second host acquires the lock when it retries the next time, loads the instance, and processes the second message.</span></span>