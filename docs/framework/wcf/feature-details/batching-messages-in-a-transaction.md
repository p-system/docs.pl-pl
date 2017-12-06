---
title: "Tworzenie partii komunikatów w ramach transakcji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d9effe9b44a8e6f786103162930852de80ab4f8d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="batching-messages-in-a-transaction"></a><span data-ttu-id="09399-102">Tworzenie partii komunikatów w ramach transakcji</span><span class="sxs-lookup"><span data-stu-id="09399-102">Batching Messages in a Transaction</span></span>
<span data-ttu-id="09399-103">Aplikacje umieszczonych w kolejce używać transakcji, aby zapewnić poprawność i niezawodne dostarczanie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="09399-103">Queued applications use transactions to ensure correctness and reliable delivery of messages.</span></span> <span data-ttu-id="09399-104">Transakcje, jednak operacje kosztowne i może znacznie zmniejszyć wydajność obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="09399-104">Transactions, however, are expensive operations and can dramatically reduce message throughput.</span></span> <span data-ttu-id="09399-105">Jednym ze sposobów poprawy wydajności przesyłania wiadomości jest używana aplikacja odczytywać i przetwarzać wiele komunikatów w ramach jednej transakcji.</span><span class="sxs-lookup"><span data-stu-id="09399-105">One way to improve message throughput is to have an application read and process multiple messages within a single transaction.</span></span> <span data-ttu-id="09399-106">Jest kompromis między wydajnością i odzyskiwanie: jak zwiększa liczbę komunikatów w partii, co powoduje ilość pracy odzyskiwania, który wymagany, jeśli wycofywania transakcji.</span><span class="sxs-lookup"><span data-stu-id="09399-106">The trade-off is between performance and recovery: as the number of messages in a batch increases, so does the amount of recovery work that required if transactions are rolled back.</span></span> <span data-ttu-id="09399-107">Należy zauważyć różnicę między tworzenie partii komunikatów w transakcji i sesje.</span><span class="sxs-lookup"><span data-stu-id="09399-107">It is important to note the difference between batching messages in a transaction and sessions.</span></span> <span data-ttu-id="09399-108">A *sesji* jest grupowanie powiązanych wiadomości, które są przetwarzane przez pojedynczą aplikacją i zatwierdzona jako pojedyncza jednostka.</span><span class="sxs-lookup"><span data-stu-id="09399-108">A *session* is a grouping of related messages that are processed by a single application and committed as a single unit.</span></span> <span data-ttu-id="09399-109">Sesje są zazwyczaj stosowane, gdy grupy powiązane komunikaty, które muszą zostać przetworzone jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="09399-109">Sessions are generally used when a group of related messages must be processed together.</span></span> <span data-ttu-id="09399-110">Na przykład jest online zakupów witryna sieci Web.</span><span class="sxs-lookup"><span data-stu-id="09399-110">An example of this is an online shopping Web site.</span></span> <span data-ttu-id="09399-111">*Partie* są używane do przetwarzania wielu, niepowiązanych wiadomości w taki sposób, że zwiększa komunikatu przepływności.</span><span class="sxs-lookup"><span data-stu-id="09399-111">*Batches* are used to process multiple, unrelated messages in a way that increases message throughput.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="09399-112">sesje, zobacz [grupowania w kolejce wiadomości w sesji](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md).</span><span class="sxs-lookup"><span data-stu-id="09399-112"> sessions, see [Grouping Queued Messages in a Session](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md).</span></span> <span data-ttu-id="09399-113">Komunikaty w partii są również przetwarzane przez pojedynczą aplikacją i zatwierdzone jako pojedyncza jednostka, ale może być Brak relacji między komunikatami w partii.</span><span class="sxs-lookup"><span data-stu-id="09399-113">Messages in a batch are also processed by a single application and committed as a single unit, but there may be no relationship between the messages in the batch.</span></span> <span data-ttu-id="09399-114">Tworzenie partii komunikatów w ramach transakcji jest optymalizacji, która nie zmienia sposób uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="09399-114">Batching messages in a transaction is an optimization that does not change how the application runs.</span></span>  
  
## <a name="entering-batching-mode"></a><span data-ttu-id="09399-115">Wprowadzanie przetwarzanie wsadowe tryb</span><span class="sxs-lookup"><span data-stu-id="09399-115">Entering Batching Mode</span></span>  
 <span data-ttu-id="09399-116"><xref:System.ServiceModel.Description.TransactedBatchingBehavior> Kontroli zachowania punktu końcowego przetwarzania wsadowego.</span><span class="sxs-lookup"><span data-stu-id="09399-116">The <xref:System.ServiceModel.Description.TransactedBatchingBehavior> endpoint behavior controls batching.</span></span> <span data-ttu-id="09399-117">Dodawanie tego zachowania punktu końcowego na punkt końcowy usługi określa, że [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] do partii komunikatów w ramach transakcji.</span><span class="sxs-lookup"><span data-stu-id="09399-117">Adding this endpoint behavior to a service endpoint tells [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to batch messages in a transaction.</span></span> <span data-ttu-id="09399-118">Nie wszystkie wiadomości wymaga transakcji, dzięki czemu można tylko komunikaty, które wymagają transakcji są umieszczane w partii i oznaczone wyłącznie wiadomości wysyłane z operacji `TransactionScopeRequired`  =  `true` i `TransactionAutoComplete`  =  `true` są uwzględnione w partii.</span><span class="sxs-lookup"><span data-stu-id="09399-118">Not all messages require a transaction, so only messages that require a transaction are placed in a batch, and only messages sent from operations marked with `TransactionScopeRequired` = `true` and `TransactionAutoComplete` = `true` are considered for a batch.</span></span> <span data-ttu-id="09399-119">Jeśli wszystkie operacje w kontrakcie usługi są oznaczone ikoną z `TransactionScopeRequired`  =  `false` i `TransactionAutoComplete`  =  `false`, a następnie przetwarzanie wsadowe tryb nigdy nie wprowadzono.</span><span class="sxs-lookup"><span data-stu-id="09399-119">If all operations on the service contract are marked with `TransactionScopeRequired` = `false` and `TransactionAutoComplete` = `false`, then batching mode is never entered.</span></span>  
  
## <a name="committing-a-transaction"></a><span data-ttu-id="09399-120">Zatwierdzanie transakcji</span><span class="sxs-lookup"><span data-stu-id="09399-120">Committing a Transaction</span></span>  
 <span data-ttu-id="09399-121">Transakcji wsadowej dba oparte na następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="09399-121">A batched transaction is committed based on the following:</span></span>  
  
-   <span data-ttu-id="09399-122">`MaxBatchSize`.</span><span class="sxs-lookup"><span data-stu-id="09399-122">`MaxBatchSize`.</span></span> <span data-ttu-id="09399-123">Właściwość <xref:System.ServiceModel.Description.TransactedBatchingBehavior> zachowania.</span><span class="sxs-lookup"><span data-stu-id="09399-123">A property of the <xref:System.ServiceModel.Description.TransactedBatchingBehavior> behavior.</span></span> <span data-ttu-id="09399-124">Ta właściwość określa maksymalną liczbę wiadomości, które są umieszczane w partii.</span><span class="sxs-lookup"><span data-stu-id="09399-124">This property determines the maximum number of messages that are placed into a batch.</span></span> <span data-ttu-id="09399-125">Po osiągnięciu tej liczby dba partii.</span><span class="sxs-lookup"><span data-stu-id="09399-125">When this number is reached, the batch is committed.</span></span> <span data-ttu-id="09399-126">Jest to wartość nie jest ścisłym limit, można przekazać partii przed otrzymaniem to liczba komunikatów.</span><span class="sxs-lookup"><span data-stu-id="09399-126">This is value is not a strict limit, it is possible to commit a batch before receiving this number of messages.</span></span>  
  
-   <span data-ttu-id="09399-127">`Transaction Timeout`.</span><span class="sxs-lookup"><span data-stu-id="09399-127">`Transaction Timeout`.</span></span> <span data-ttu-id="09399-128">Po upływie limitu czasu transakcji 80 procent, dba partii i utworzeniu nowej instancji.</span><span class="sxs-lookup"><span data-stu-id="09399-128">After 80 percent of the transaction's time-out has elapsed, the batch is committed and a new batch is created.</span></span> <span data-ttu-id="09399-129">Oznacza to, że jeśli 20% lub mniej czasu dla transakcji ukończyć pozostaje, dba partii.</span><span class="sxs-lookup"><span data-stu-id="09399-129">This means that if 20 percent or less of the time given for a transaction to complete remains, the batch is committed.</span></span>  
  
-   <span data-ttu-id="09399-130">`TransactionScopeRequired`.</span><span class="sxs-lookup"><span data-stu-id="09399-130">`TransactionScopeRequired`.</span></span> <span data-ttu-id="09399-131">Podczas przetwarzania wsadowego komunikatów, jeśli [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] znalezienia punktu, który ma `TransactionScopeRequired`  =  `false`, zatwierdza partii i ponownie otwiera nową instancję po otrzymaniu pierwszego komunikatu z `TransactionScopeRequired`  =  `true` i `TransactionAutoComplete` = `true`.</span><span class="sxs-lookup"><span data-stu-id="09399-131">When processing a batch of messages, if [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] finds one that has `TransactionScopeRequired` = `false`, it commits the batch and reopens a new batch on receipt of the first message with `TransactionScopeRequired` = `true` and `TransactionAutoComplete` = `true`.</span></span>  
  
-   <span data-ttu-id="09399-132">Jeśli nie więcej istnieją wiadomości w kolejce, a następnie bieżącej partii został przekazany, nawet jeśli `MaxBatchSize` nie został osiągnięty lub nie upłynął limit czasu transakcji 80 procent.</span><span class="sxs-lookup"><span data-stu-id="09399-132">If no more messages exist in the queue, then the current batch is committed, even if the `MaxBatchSize` has not been reached or 80 percent of the transaction's time-out has not elapsed.</span></span>  
  
## <a name="leaving-batching-mode"></a><span data-ttu-id="09399-133">Pozostawienie przetwarzanie wsadowe tryb</span><span class="sxs-lookup"><span data-stu-id="09399-133">Leaving Batching Mode</span></span>  
 <span data-ttu-id="09399-134">Jeśli komunikat w partii powoduje przerwanie transakcji, zostaną wykonane następujące kroki:</span><span class="sxs-lookup"><span data-stu-id="09399-134">If a message in a batch causes the transaction to abort, the following steps occur:</span></span>  
  
1.  <span data-ttu-id="09399-135">Całą partię komunikatów zostanie wycofana.</span><span class="sxs-lookup"><span data-stu-id="09399-135">The entire batch of messages is rolled back.</span></span>  
  
2.  <span data-ttu-id="09399-136">Wiadomości są odczytywane pojedynczo, dopóki liczba wiadomości przekracza dwukrotnie maksymalny rozmiar wsadu.</span><span class="sxs-lookup"><span data-stu-id="09399-136">Messages are read one at a time until the number of messages read exceeds twice the maximum batch size.</span></span>  
  
3.  <span data-ttu-id="09399-137">Tryb partii jest ponowne wprowadzenie.</span><span class="sxs-lookup"><span data-stu-id="09399-137">Batch mode is re-entered.</span></span>  
  
## <a name="choosing-the-batch-size"></a><span data-ttu-id="09399-138">Wybieranie rozmiaru partii</span><span class="sxs-lookup"><span data-stu-id="09399-138">Choosing the Batch Size</span></span>  
 <span data-ttu-id="09399-139">Rozmiar partii jest zależny od aplikacji.</span><span class="sxs-lookup"><span data-stu-id="09399-139">The size of a batch is application-dependent.</span></span> <span data-ttu-id="09399-140">Metoda empiryczne jest najlepszym sposobem na rozmiar partii optymalne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="09399-140">The empirical method is the best way to arrive at an optimal batch size for the application.</span></span> <span data-ttu-id="09399-141">Należy pamiętać, wybierając rozmiar partii, aby wybrać rozmiar zgodnie z modelu rzeczywiste wdrożenie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="09399-141">It is important to remember when choosing a batch size to choose the size according to your application's actual deployment model.</span></span> <span data-ttu-id="09399-142">Na przykład w przypadku wdrażania aplikacji, jeśli potrzebujesz programu SQL server na komputerze zdalnym i transakcji obejmującej kolejki i SQL server, następnie rozmiar partii najlepiej zależy, uruchamiając tego dokładnej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="09399-142">For example, when deploying the application, if you need an SQL server on a remote machine and a transaction that spans the queue and the SQL server, then the batch size is best determined by running this exact configuration.</span></span>  
  
## <a name="concurrency-and-batching"></a><span data-ttu-id="09399-143">Współbieżność i przetwarzanie wsadowe</span><span class="sxs-lookup"><span data-stu-id="09399-143">Concurrency and Batching</span></span>  
 <span data-ttu-id="09399-144">W celu zwiększenia przepływności, może również mieć wiele instancji uruchamiać jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="09399-144">To increase throughput, you can also have many batches run concurrently.</span></span> <span data-ttu-id="09399-145">Przez ustawienie `ConcurrencyMode.Multiple` w `ServiceBehaviorAttribute`, możesz włączyć równoczesnych przetwarzanie wsadowe.</span><span class="sxs-lookup"><span data-stu-id="09399-145">By setting `ConcurrencyMode.Multiple` in `ServiceBehaviorAttribute`, you enable concurrent batching.</span></span>  
  
 <span data-ttu-id="09399-146">*Usługa ograniczania* jest zachowanie usługi, który jest używany do określania, ile maksymalna współbieżnych wywołań w usłudze.</span><span class="sxs-lookup"><span data-stu-id="09399-146">*Service throttling* is a service behavior that is used to indicate how many maximum concurrent calls can be made on the service.</span></span> <span data-ttu-id="09399-147">W przypadku użycia z przetwarzanie wsadowe, jest interpretowany jak można uruchomić wiele równoczesnych partie.</span><span class="sxs-lookup"><span data-stu-id="09399-147">When used with batching, this is interpreted as how many concurrent batches can be run.</span></span> <span data-ttu-id="09399-148">Jeśli nie ustawiono ograniczenie usługi, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] domyślnie maksymalna równoczesnych wywołań 16.</span><span class="sxs-lookup"><span data-stu-id="09399-148">If the service throttling is not set, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] defaults the maximum concurrent calls to 16.</span></span> <span data-ttu-id="09399-149">W związku z tym Jeśli przetwarzanie wsadowe zachowanie dodano domyślnie, maksymalnie 16 partii zadań mogą być aktywne w tym samym czasie.</span><span class="sxs-lookup"><span data-stu-id="09399-149">Thus, if batching behavior were added by default, a maximum of 16 batches can be active at the same time.</span></span> <span data-ttu-id="09399-150">Najlepiej dostroić ograniczania usługi i przetwarzanie wsadowe oparte na wydajność.</span><span class="sxs-lookup"><span data-stu-id="09399-150">It is best to tune the service throttling and batching based on your capacity.</span></span> <span data-ttu-id="09399-151">Na przykład jeśli kolejki jest 100 wiadomości i wymagane jest partii 20, o maksymalnej równoczesnych wywołań ustawioną 16 nie jest przydatne ponieważ w zależności od przepustowości, 16 transakcji może być aktywne, podobnie jak nie posiadają przetwarzanie wsadowe włączona.</span><span class="sxs-lookup"><span data-stu-id="09399-151">For example, if the queue has 100 messages and a batch of 20 is desired, having the maximum concurrent calls set to 16 is not useful because, depending on throughput, 16 transactions could be active, similar to not having batching turned on.</span></span> <span data-ttu-id="09399-152">W związku z tym podczas dostosowywania wydajności, nie ma równoczesnych przetwarzanie wsadowe lub mieć równoczesnych przetwarzanie wsadowe o rozmiarze ograniczania prawidłowe usługi.</span><span class="sxs-lookup"><span data-stu-id="09399-152">Therefore, when fine-tuning for performance, either do not have concurrent batching or have concurrent batching with the correct service throttle size.</span></span>  
  
## <a name="batching-and-multiple-endpoints"></a><span data-ttu-id="09399-153">Przetwarzanie wsadowe i wiele punktów końcowych</span><span class="sxs-lookup"><span data-stu-id="09399-153">Batching and Multiple Endpoints</span></span>  
 <span data-ttu-id="09399-154">Punkt końcowy składa się z adresu i kontrakt.</span><span class="sxs-lookup"><span data-stu-id="09399-154">An endpoint is composed of an address and a contract.</span></span> <span data-ttu-id="09399-155">Może istnieć wiele punktów końcowych, które współużytkują to samo powiązanie.</span><span class="sxs-lookup"><span data-stu-id="09399-155">There may be multiple endpoints that share the same binding.</span></span> <span data-ttu-id="09399-156">Istnieje możliwość dwa punkty końcowe udostępnianie tego samego powiązania do nasłuchiwania identyfikator URI (Uniform Resource) lub adres kolejki.</span><span class="sxs-lookup"><span data-stu-id="09399-156">It is possible for two endpoints to share the same binding and listen Uniform Resource Identifier (URI), or queue address.</span></span> <span data-ttu-id="09399-157">Jeśli dwa punkty końcowe są czytania z tej samej kolejki i transakcyjnego przetwarzania wsadowego zachowanie jest dodawany do konflikt w partii, które mogą pojawić się rozmiary określone oba punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="09399-157">If two endpoints are reading from the same queue, and transacted batching behavior is added to both endpoints, a conflict in the batch sizes specified could arise.</span></span> <span data-ttu-id="09399-158">Jest to rozwiązane przez wdrożenie, przetwarzanie wsadowe przy użyciu podanego rozmiaru partii minimalnego między dwa transakcyjnego łączenia we wsady zachowania.</span><span class="sxs-lookup"><span data-stu-id="09399-158">This is resolved by implementing batching using the minimal batch size specified between the two transacted batching behaviors.</span></span> <span data-ttu-id="09399-159">W tym scenariuszu jeśli jeden z punktów końcowych nie określa transakcyjnego przetwarzania wsadowego, następnie oba punkty końcowe nie użyje przetwarzanie wsadowe.</span><span class="sxs-lookup"><span data-stu-id="09399-159">In this scenario, if one of the endpoints does not specify transacted batching, then both endpoints would not use batching.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09399-160">Przykład</span><span class="sxs-lookup"><span data-stu-id="09399-160">Example</span></span>  
 <span data-ttu-id="09399-161">Poniższy przykład przedstawia sposób określić `TransactedBatchingBehavior` w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="09399-161">The following example shows how to specify the `TransactedBatchingBehavior` in a configuration file.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="TransactedBatchingBehavior"
              maxBatchSize="100" />
  </endpointBehaviors>
</behaviors>
```  
  
 <span data-ttu-id="09399-162">Poniższy przykład przedstawia sposób określić <xref:System.ServiceModel.Description.TransactedBatchingBehavior> w kodzie.</span><span class="sxs-lookup"><span data-stu-id="09399-162">The following example shows how to specify the <xref:System.ServiceModel.Description.TransactedBatchingBehavior> in code.</span></span>  
  
```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
     ServiceEndpoint sep = ServiceHost.AddServiceEndpoint(typeof(IOrderProcessor), new NetMsmqBinding(), "net.msmq://localhost/private/ServiceModelSamplesTransacted");
     sep.Behaviors.Add(new TransactedBatchingBehavior(100));
     
     // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();
  
    // The service can now be accessed.
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.WriteLine();
    Console.ReadLine();
  
    // Close the ServiceHostB to shut down the service.
    serviceHost.Close();
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="09399-163">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09399-163">See Also</span></span>  
 [<span data-ttu-id="09399-164">Omówienie kolejek</span><span class="sxs-lookup"><span data-stu-id="09399-164">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 [<span data-ttu-id="09399-165">Usługi kolejkowania wiadomości w programie WCF</span><span class="sxs-lookup"><span data-stu-id="09399-165">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)