---
title: "Emitowanie danych śledzenia elementu User-Code"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa54186a-8ffa-4332-b0e7-63867126fd49
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2162377fbe8f8329c12dfd88a55d893d26f5b2bf
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="emitting-user-code-traces"></a><span data-ttu-id="c0ff2-102">Emitowanie danych śledzenia elementu User-Code</span><span class="sxs-lookup"><span data-stu-id="c0ff2-102">Emitting User-Code Traces</span></span>
<span data-ttu-id="c0ff2-103">Oprócz włączenia śledzenia w konfiguracji, aby zbieranie danych Instrumentacji generowanych przez [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], można również wysyłać dane śledzenia w kodzie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-103">In addition to enabling tracing in configuration to collect instrumentation data generated by [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)], you can also emit traces programmatically in user code.</span></span> <span data-ttu-id="c0ff2-104">W ten sposób można utworzyć aktywne dane instrumentacji, który można przejrzeć później w celu diagnostyki.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-104">In this way, you can proactively create instrumentation data that you can peruse later for diagnostic purpose.</span></span> <span data-ttu-id="c0ff2-105">W tym temacie opisano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-105">This topic discusses how you can do this.</span></span>  
  
 <span data-ttu-id="c0ff2-106">Ponadto [rozszerzanie śledzenia](../../../../../docs/framework/wcf/samples/extending-tracing.md) próbki obejmuje całego kodu pokazano w poniższych sekcjach.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-106">In addition, the [Extending Tracing](../../../../../docs/framework/wcf/samples/extending-tracing.md) sample includes all the code demonstrated in the following sections.</span></span>  
  
## <a name="creating-a-trace-source"></a><span data-ttu-id="c0ff2-107">Tworzenie źródła śledzenia</span><span class="sxs-lookup"><span data-stu-id="c0ff2-107">Creating a Trace Source</span></span>  
 <span data-ttu-id="c0ff2-108">Poniższy kod umożliwia utworzenie źródła śledzenia użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-108">You can use the following code to create a user trace source.</span></span>  
  
```  
TraceSource ts = new TraceSource("myUserTraceSource");  
```  
  
## <a name="creating-activities"></a><span data-ttu-id="c0ff2-109">Tworzenie działania</span><span class="sxs-lookup"><span data-stu-id="c0ff2-109">Creating Activities</span></span>  
 <span data-ttu-id="c0ff2-110">Działania są jednostki logicznej przetwarzania.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-110">Activities are logical unit of processing.</span></span> <span data-ttu-id="c0ff2-111">Dla każdej jednostki przetwarzania głównych, w której ma zostać śladów do można grupować można utworzyć jedno działanie.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-111">You can create one activity for each major processing unit in which you want traces to be grouped together.</span></span> <span data-ttu-id="c0ff2-112">Na przykład można utworzyć jedno działanie dla każdego żądania do usługi.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-112">For example, you can create one activity for each request to the service.</span></span> <span data-ttu-id="c0ff2-113">Aby to zrobić, wykonaj następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-113">To do so, perform the following steps.</span></span>  
  
1.  <span data-ttu-id="c0ff2-114">Zapisz identyfikator działania w zakresie.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-114">Save the activity ID in scope.</span></span>  
  
2.  <span data-ttu-id="c0ff2-115">Utwórz nowy identyfikator działania.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-115">Create a new activity ID.</span></span>  
  
3.  <span data-ttu-id="c0ff2-116">Transfer z działania w zakresie do nowego, Ustaw nowe działanie w zakresie a emisją Rozpocznij śledzenie dla tego działania.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-116">Transfer from the activity in scope to the new one, set the new activity in scope and emit a start trace for that activity.</span></span>  
  
 <span data-ttu-id="c0ff2-117">Poniższy kod przedstawia, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-117">The following code demonstrates how to do this.</span></span>  
  
```  
Guid oldID = Trace.CorrelationManager.ActivityId;  
Guid traceID = Guid.NewGuid();  
ts.TraceTransfer(0, "transfer", traceID);  
Trace.CorrelationManager.ActivityId = traceID; // Trace is static  
ts.TraceEvent(TraceEventType.Start, 0, "Add request");  
```  
  
## <a name="emitting-traces-within-a-user-activity"></a><span data-ttu-id="c0ff2-118">Emitowanie danych śledzenia w ramach działania użytkownika</span><span class="sxs-lookup"><span data-stu-id="c0ff2-118">Emitting Traces within a User Activity</span></span>  
 <span data-ttu-id="c0ff2-119">Poniższy kod emituje dane śledzenia w ramach działania użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-119">The following code emits traces within a user activity.</span></span>  
  
```  
double value1 = 100.00D;  
double value2 = 15.99D;  
ts.TraceInformation("Client sends message to Add " + value1 + ", " + value2);  
double result = client.Add(value1, value2);  
ts.TraceInformation("Client receives Add response '" + result + "'");  
```  
  
## <a name="stopping-the-activities"></a><span data-ttu-id="c0ff2-120">Zatrzymywanie działania</span><span class="sxs-lookup"><span data-stu-id="c0ff2-120">Stopping the Activities</span></span>  
 <span data-ttu-id="c0ff2-121">Zatrzymanie działania, transfer do starego działania, Zatrzymaj bieżący identyfikator działania i zresetować stary identyfikator działania w zakresie.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-121">To stop the activities, transfer back to the old activity, stop the current activity id, and reset the old activity id in scope.</span></span>  
  
 <span data-ttu-id="c0ff2-122">Poniższy kod przedstawia, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-122">The following code demonstrates how to do this.</span></span>  
  
```  
ts.TraceTransfer(0, "transfer", oldID);  
ts.TraceEvent(TraceEventType.Stop, 0, "Add request");  
Trace.CorrelationManager.ActivityId = oldID;  
```  
  
## <a name="propagating-the-activity-id-to-a-service"></a><span data-ttu-id="c0ff2-123">Propagowanie identyfikator działania z usługą</span><span class="sxs-lookup"><span data-stu-id="c0ff2-123">Propagating the Activity ID to A Service</span></span>  
 <span data-ttu-id="c0ff2-124">Jeśli ustawisz `propagateActivity` atrybutu `true` dla `System.ServiceModel` pliki źródłowe śledzenia w konfiguracji klienta i usługi, usługi przetwarzanie żądania Dodaj występuje w to samo działanie jak określono w kliencie.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-124">If you set the `propagateActivity` attribute to `true` for the `System.ServiceModel` trace source in both the client and service configuration files, the service processing for the Add request occurs in the same activity as the one defined in the client.</span></span> <span data-ttu-id="c0ff2-125">Jeśli usługa definiuje własne działania i transfery, ślady usługi nie są wyświetlane w działaniu propagowane klienta.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-125">If the service defines its own activities and transfers, the service traces do not appear in the client-propagated activity.</span></span> <span data-ttu-id="c0ff2-126">Zamiast tego pojawią się one w działaniu Skorelowane za transfer śladów do działania, których identyfikator jest propagowana przez klienta.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-126">Instead, they appear in an activity correlated by transfer traces to the activity whose ID is propagated by the client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0ff2-127">Jeśli `propagateActivity` atrybut ma ustawioną `true` na klienta i usługi, otoczenia działania w zakresie operacji usługi jest ustawiana przez [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0ff2-127">If the `propagateActivity` attribute is set to `true` on both the client and service, the ambient activity in the operation scope of the service is set by [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="c0ff2-128">Można użyć poniższego kodu, aby sprawdzić, czy działanie zostało ustawione w zakresie przez [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0ff2-128">You can use the following code to check whether an activity was set in scope by [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)].</span></span>  
  
```  
// Check if an activity was set in scope by WCF, if it was   
// propagated from the client. If not, ( ambient activity is   
// equal to Guid.Empty), create a new one.  
if(Trace.CorrelationManager.ActivityId == Guid.Empty)  
{  
    Guid newGuid = Guid.NewGuid();  
    Trace.CorrelationManager.ActivityId = newGuid;  
}  
// Emit your Start trace.  
ts.TraceEvent(TraceEventType.Start, 0, "Add Activity");  
  
// Emit the processing traces for that request.  
serviceTs.TraceInformation("Service receives Add "   
                            + n1 + ", " + n2);  
// double result = n1 + n2;  
serviceTs.TraceInformation("Service sends Add result" + result);  
  
// Emit the Stop trace and exit the method scope.  
ts.TraceEvent(TraceEventType.Stop, 0, "Add Activity");  
// return result;  
```  
  
## <a name="tracing-exceptions-thrown-in-code"></a><span data-ttu-id="c0ff2-129">Śledzenie wyjątków zgłoszonych w kodzie</span><span class="sxs-lookup"><span data-stu-id="c0ff2-129">Tracing Exceptions Thrown in Code</span></span>  
 <span data-ttu-id="c0ff2-130">Gdy Zgłoś wyjątek w kodzie, można również śledzenia wyjątków na poziomie ostrzeżenia lub przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-130">When you throw an exception in code, you can also trace the exception at Warning level or up using the following code.</span></span>  
  
```  
ts.TraceEvent(TraceEventType.Warning, 0, "Throwing exception " + "exceptionMessage");  
```  
  
## <a name="viewing-user-traces-in-the-service-trace-viewer-tool"></a><span data-ttu-id="c0ff2-131">Wyświetlanie śladów użytkownika za pomocą narzędzia podglądu śledzenia usługi</span><span class="sxs-lookup"><span data-stu-id="c0ff2-131">Viewing User Traces in the Service Trace Viewer Tool</span></span>  
 <span data-ttu-id="c0ff2-132">Ta sekcja zawiera zrzuty ekranu śladów generowane przez uruchomienie [rozszerzanie śledzenia](../../../../../docs/framework/wcf/samples/extending-tracing.md) próbkowania, podczas wyświetlania przy użyciu [narzędzia podglądu śledzenia usług (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c0ff2-132">This section contains screenshots of traces generated by running the [Extending Tracing](../../../../../docs/framework/wcf/samples/extending-tracing.md) sample, when viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span>  
  
 <span data-ttu-id="c0ff2-133">Na poniższym diagramie działania "Dodaj żądanie" utworzone wcześniej wybrano w lewym panelu.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-133">In the following diagram, the "Add request" activity created previously is selected on the left panel.</span></span> <span data-ttu-id="c0ff2-134">Znajduje się on z trzech innymi matematyczne operacji (dzielenie, różnicowe, mnożenie) wchodzących w skład programu klienta aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-134">It is listed with three other Math operation activities (Divide, Subtract, Multiply) that constitute the application client program.</span></span> <span data-ttu-id="c0ff2-135">Kod użytkownika został zdefiniowany jeden nowe działanie dla każdej operacji do izolowania potencjalnych wystąpienia błędu w różnych żądań.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-135">The user code has defined one new activity for each operation to isolate potential error occurrences in different requests.</span></span>  
  
 <span data-ttu-id="c0ff2-136">Aby zademonstrować stosowania transferów [rozszerzanie śledzenia](../../../../../docs/framework/wcf/samples/extending-tracing.md) próbki, działanie Kalkulator, które hermetyzuje żądania operacji cztery tworzona jest również.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-136">To demonstrate the use of transfers in the [Extending Tracing](../../../../../docs/framework/wcf/samples/extending-tracing.md) sample, a Calculator activity that encapsulates the four operation requests is also created.</span></span> <span data-ttu-id="c0ff2-137">Dla każdego żądania jest transferu i z powrotem z działania Kalkulator do działania żądania (śledzenia zostanie wyróżniona w górnym prawym panelu na rysunku).</span><span class="sxs-lookup"><span data-stu-id="c0ff2-137">For each request, there is a transfer back and forth from the Calculator activity to the request activity (trace is highlighted in the upper right panel in the figure).</span></span>  
  
 <span data-ttu-id="c0ff2-138">Po wybraniu do działania w lewym panelu śladów uwzględnionych tego działania są wyświetlane w górnym prawym panelu.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-138">When you select an activity on the left panel, the traces included by this activity are shown on the upper right panel.</span></span> <span data-ttu-id="c0ff2-139">Jeśli `propagateActivity` jest `true` w każdym punkcie końcowym ścieżka żądania, dane śledzenia w działaniu żądania są od wszystkich procesów, które uczestniczą w żądaniu.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-139">If `propagateActivity` is `true` at every endpoint in the request path, traces in the request activity are from all processes that participate in the request.</span></span> <span data-ttu-id="c0ff2-140">W tym przykładzie widać śladów pochodzących z klienta i usługi, w kolumnie 4. w panelu.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-140">In this example, you can see traces from both the client and service in the 4th column in the panel.</span></span>  
  
 <span data-ttu-id="c0ff2-141">To działanie zawiera następujące kolejność przetwarzania:</span><span class="sxs-lookup"><span data-stu-id="c0ff2-141">This activity shows the following order of processing:</span></span>  
  
1.  <span data-ttu-id="c0ff2-142">Klient wysyła komunikat do dodania.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-142">Client sends message to Add.</span></span>  
  
2.  <span data-ttu-id="c0ff2-143">Usługa odbiera komunikat żądania Dodaj.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-143">Service receives Add request message.</span></span>  
  
3.  <span data-ttu-id="c0ff2-144">Dodaj odpowiedzi wysyłane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-144">Service sends Add response.</span></span>  
  
4.  <span data-ttu-id="c0ff2-145">Klient odbiera odpowiedź Dodaj.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-145">Client receives Add response.</span></span>  
  
 <span data-ttu-id="c0ff2-146">Te operacje śledzenia zostały wyemitowane na poziomie informacji.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-146">All these traces were emitted at Information level.</span></span> <span data-ttu-id="c0ff2-147">Kliknięcie przycisku śledzenia w prawym górnym panelu przedstawia szczegóły tego śladu w prawym dolnym panelu.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-147">Clicking a trace in the upper-right panel shows the details of that trace in the lower-right panel.</span></span>  
  
 <span data-ttu-id="c0ff2-148">Na poniższym diagramie Widzimy również śladów transfer od i do działania Kalkulator, jak również dwie pary uruchomienia i zatrzymania śledzenia na działanie żądania, jeden dla klienta i jeden dla usługi (po jednej dla każdego źródła śledzenia).</span><span class="sxs-lookup"><span data-stu-id="c0ff2-148">In the following diagram, we also see transfer traces from and to the Calculator activity, as well as two pairs of Start and Stop traces per request activity, one for the client and one for the service (one for each trace source).</span></span>  
  
 <span data-ttu-id="c0ff2-149">![Podgląd śledzenia: Emitowanie użytkownika &#45; kod śledzenia](../../../../../docs/framework/wcf/diagnostics/tracing/media/242c9358-475a-4baf-83f3-4227aa942fcd.gif "242c9358-475a-4baf-83f3-4227aa942fcd")</span><span class="sxs-lookup"><span data-stu-id="c0ff2-149">![Trace Viewer: Emitting User&#45;code traces](../../../../../docs/framework/wcf/diagnostics/tracing/media/242c9358-475a-4baf-83f3-4227aa942fcd.gif "242c9358-475a-4baf-83f3-4227aa942fcd")</span></span>  
<span data-ttu-id="c0ff2-150">Lista działań w oparciu o czas utworzenia (lewego panelu) i ich zagnieżdżonych działań (prawym górnym panelu)</span><span class="sxs-lookup"><span data-stu-id="c0ff2-150">List of activities by creation time (left panel) and their nested activities (upper-right panel)</span></span>  
  
 <span data-ttu-id="c0ff2-151">Jeśli kod usługi zgłasza wyjątek, który powoduje, że klient ma zostać zgłoszony, jak również (na przykład, gdy klient nie pobrały odpowiedzi na żądania), zarówno usługa i klient ostrzeżenia lub komunikaty o błędach występować w tym samym działaniu dla korelacji bezpośredniego.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-151">If the service code throws an exception that causes the client to throw as well (for example, when the client did not get the response to its request), both the service and client warning or error messages occur in the same activity for direct correlation.</span></span> <span data-ttu-id="c0ff2-152">Na poniższym diagramie usługa zgłasza wyjątek stwierdzający "Usługa odmówi przetworzyć tego żądania w kodzie użytkownika."</span><span class="sxs-lookup"><span data-stu-id="c0ff2-152">In the following diagram, the service throws an exception that states "The service refuses to process this request in user code."</span></span> <span data-ttu-id="c0ff2-153">Klient również zgłasza wyjątek stwierdzający "serwer nie może przetworzyć żądania z powodu błędu wewnętrznego."</span><span class="sxs-lookup"><span data-stu-id="c0ff2-153">The client also throws an exception that states "The server was unable to process the request due to an internal error."</span></span>  
  
 <span data-ttu-id="c0ff2-154">![Emituj 45; & użytkownika za pomocą podglądu śledzenia śledzi kodu](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace2.gif "e2eTrace2")</span><span class="sxs-lookup"><span data-stu-id="c0ff2-154">![Using Trace Viewer to emit user&#45;code traces](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace2.gif "e2eTrace2")</span></span>  
<span data-ttu-id="c0ff2-155">Błędy w obrębie punktów końcowych dla danego żądania są wyświetlane w tym samym działaniu jeśli pochodzi żądanie identyfikator działania</span><span class="sxs-lookup"><span data-stu-id="c0ff2-155">Errors across endpoints for a given request appear in the same activity if the request activity id was propagated</span></span>  
  
 <span data-ttu-id="c0ff2-156">Dwukrotne kliknięcie mnożenie działania w lewym panelu przedstawia wykres następujących, za pomocą danych śledzenia dla mnożenia działanie dla każdego procesu związane.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-156">Double-clicking the Multiply activity on the left panel shows the following graph, with the traces for the Multiply activity for each process involved.</span></span> <span data-ttu-id="c0ff2-157">Firma Microsoft można zauważyć, że najpierw wystąpiło ostrzeżenie w usług (wystąpienie wyjątku), której następuje ostrzeżeń i błędów na komputerze klienckim, ponieważ nie można przetworzyć żądania.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-157">We can see a warning first occurred at the service (exception thrown), which is followed by warnings and errors on the client because the request could not be processed.</span></span> <span data-ttu-id="c0ff2-158">Firma Microsoft w związku z tym oznacza błąd przyczynowy relacji między punktami końcowymi i pochodzić przyczynę błędu.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-158">Therefore, we can imply the causal error relationship between endpoints and derive the root cause of the error.</span></span>  
  
 <span data-ttu-id="c0ff2-159">![Emituj 45; & użytkownika za pomocą podglądu śledzenia śledzi kodu](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace3.gif "e2eTrace3")</span><span class="sxs-lookup"><span data-stu-id="c0ff2-159">![Using Trace Viewer to emit user&#45;code traces](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace3.gif "e2eTrace3")</span></span>  
<span data-ttu-id="c0ff2-160">Widok wykresu błąd korelacji</span><span class="sxs-lookup"><span data-stu-id="c0ff2-160">Graph view of error correlation</span></span>  
  
 <span data-ttu-id="c0ff2-161">Uzyskanie poprzedniej śladów ustawiliśmy `ActivityTracing` źródeł śledzenia użytkownika i `propagateActivity=true` dla `System.ServiceModel` źródła śledzenia.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-161">To obtain the previous traces, we set `ActivityTracing` for the user trace sources and `propagateActivity=true` for the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="c0ff2-162">Firma Microsoft nie określono `ActivityTracing` dla `System.ServiceModel` źródła śledzenia do kodu użytkownika rozprzestrzenianie działania kodu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-162">We did not set `ActivityTracing` for the `System.ServiceModel` trace source to enable user code to user code activity propagation.</span></span> <span data-ttu-id="c0ff2-163">(Jeśli ServiceModel czynność śledzenia jest włączona, identyfikator działania zdefiniowane na komputerze klienckim nie są propagowane do kodu użytkownika usługi; Transfery, jednak skorelowania działania kodu użytkownika klienta i usługi do pośredniego [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] działania.)</span><span class="sxs-lookup"><span data-stu-id="c0ff2-163">(When ServiceModel activity tracing is on, the activity ID defined in the client is not propagated all the way to the service user code; Transfers, however, correlate the client and service user code activities to the intermediate [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] activities.)</span></span>  
  
 <span data-ttu-id="c0ff2-164">Definiowanie działań i propagowanie identyfikator działania umożliwia firmie Microsoft w celu wykonania bezpośredniego błąd korelacji między punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-164">Defining activities and propagating the activity ID enables us to perform direct error correlation across endpoints.</span></span> <span data-ttu-id="c0ff2-165">W ten sposób można zlokalizować przyczynę błędu szybciej.</span><span class="sxs-lookup"><span data-stu-id="c0ff2-165">In this way, we can locate the root cause of an error more quickly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0ff2-166">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0ff2-166">See Also</span></span>  
 [<span data-ttu-id="c0ff2-167">Rozszerzanie śledzenia</span><span class="sxs-lookup"><span data-stu-id="c0ff2-167">Extending Tracing</span></span>](../../../../../docs/framework/wcf/samples/extending-tracing.md)