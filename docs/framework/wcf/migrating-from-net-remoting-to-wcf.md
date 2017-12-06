---
title: Migrowanie z programu .NET Remoting do programu WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16902a42-ef80-40e9-8c4c-90e61ddfdfe5
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8f39a26d52d7002e793935135e0c5d5e8f11c3d8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="migrating-from-net-remoting-to-wcf"></a><span data-ttu-id="023ed-102">Migrowanie z programu .NET Remoting do programu WCF</span><span class="sxs-lookup"><span data-stu-id="023ed-102">Migrating from .NET Remoting to WCF</span></span>
<span data-ttu-id="023ed-103">W tym artykule opisano sposób migracji aplikacji, która używa .NET Remoting do używania usług Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="023ed-103">This article describes how to migrate an application that uses .NET Remoting to use Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="023ed-104">Porównuje podobne pojęcia między tymi produktami, a następnie opisano, jak wykonać kilka typowych scenariuszy komunikacji zdalnej programu WCF.</span><span class="sxs-lookup"><span data-stu-id="023ed-104">It compares similar concepts between these products and then describes how to accomplish several common Remoting scenarios in WCF.</span></span>  
  
 <span data-ttu-id="023ed-105">.NET remoting jest starszy produkt, który jest obsługiwany tylko w przypadku zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="023ed-105">.NET Remoting is a legacy product that is supported only for backward compatibility.</span></span> <span data-ttu-id="023ed-106">Nie jest bezpieczne w środowiskach mieszanych zaufania, ponieważ nie można zachować poziomy zaufania oddzielne między klientem i serwerem.</span><span class="sxs-lookup"><span data-stu-id="023ed-106">It is not secure across mixed-trust environments because it cannot maintain the separate trust levels between client and server.</span></span> <span data-ttu-id="023ed-107">Na przykład nigdy nie powinny ujawniać punkt końcowy .NET Remoting do Internetu lub niezaufanego klientami.</span><span class="sxs-lookup"><span data-stu-id="023ed-107">For example, you should never expose a .NET Remoting endpoint to the Internet or to untrusted clients.</span></span> <span data-ttu-id="023ed-108">Zalecamy Remoting istniejące aplikacje można migrować do nowszej i bezpieczniejsze technologii.</span><span class="sxs-lookup"><span data-stu-id="023ed-108">We recommend existing Remoting applications be migrated to newer and more secure technologies.</span></span> <span data-ttu-id="023ed-109">Jeśli aplikacja — projekt używa tylko protokołu HTTP i RESTful, firma Microsoft zaleca interfejsu API sieci Web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="023ed-109">If the application’s design uses only HTTP and is RESTful, we recommend ASP.NET Web API.</span></span> <span data-ttu-id="023ed-110">Aby uzyskać więcej informacji zobacz interfejsu API sieci Web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="023ed-110">For more information, see ASP.NET Web API.</span></span> <span data-ttu-id="023ed-111">Jeśli aplikacja jest oparta na SOAP lub wymaga protokołów innych niż Http, takie jak protokół TCP, firma Microsoft zaleca WCF.</span><span class="sxs-lookup"><span data-stu-id="023ed-111">If the application is based on SOAP or requires non-Http protocols such as TCP, we recommend WCF.</span></span>  

## <a name="comparing-net-remoting-to-wcf"></a><span data-ttu-id="023ed-112">Porównywanie .NET Remoting do programu WCF</span><span class="sxs-lookup"><span data-stu-id="023ed-112">Comparing .NET Remoting to WCF</span></span>  
 <span data-ttu-id="023ed-113">Ta sekcja porównuje podstawowe bloki konstrukcyjne .NET Remoting z ich odpowiedniki WCF.</span><span class="sxs-lookup"><span data-stu-id="023ed-113">This section compares the basic building blocks of .NET Remoting with their WCF equivalents.</span></span> <span data-ttu-id="023ed-114">Te bloki konstrukcyjne zostanie wykorzystany później można utworzyć niektórych typowych scenariuszy klient serwer programu WCF. Poniższy schemat zawiera podsumowanie głównych podobieństwa i różnice funkcji zdalnych .NET i WCF.</span><span class="sxs-lookup"><span data-stu-id="023ed-114">We will use these building blocks later to create some common client-server scenarios in WCF.The following chart summarizes the main similarities and differences between .NET Remoting and WCF.</span></span>  
  
||<span data-ttu-id="023ed-115">Wywołaniem funkcji zdalnych .NET</span><span class="sxs-lookup"><span data-stu-id="023ed-115">.NET Remoting</span></span>|<span data-ttu-id="023ed-116">WCF</span><span class="sxs-lookup"><span data-stu-id="023ed-116">WCF</span></span>|  
|-|-------------------|---------|  
|<span data-ttu-id="023ed-117">Typ serwera</span><span class="sxs-lookup"><span data-stu-id="023ed-117">Server type</span></span>|<span data-ttu-id="023ed-118">Podklasy elementu MarshalByRefObject</span><span class="sxs-lookup"><span data-stu-id="023ed-118">Subclass MarshalByRefObject</span></span>|<span data-ttu-id="023ed-119">Oznacz z atrybutem [ServiceContract]</span><span class="sxs-lookup"><span data-stu-id="023ed-119">Mark with [ServiceContract] attribute</span></span>|  
|<span data-ttu-id="023ed-120">Operacje usługi</span><span class="sxs-lookup"><span data-stu-id="023ed-120">Service operations</span></span>|<span data-ttu-id="023ed-121">Metody publiczne na typ serwera</span><span class="sxs-lookup"><span data-stu-id="023ed-121">Public methods on server type</span></span>|<span data-ttu-id="023ed-122">Oznacz z atrybutem [OperationContract]</span><span class="sxs-lookup"><span data-stu-id="023ed-122">Mark with [OperationContract] attribute</span></span>|  
|<span data-ttu-id="023ed-123">Serializacja</span><span class="sxs-lookup"><span data-stu-id="023ed-123">Serialization</span></span>|<span data-ttu-id="023ed-124">ISerializable lub [Serializable]</span><span class="sxs-lookup"><span data-stu-id="023ed-124">ISerializable or [Serializable]</span></span>|<span data-ttu-id="023ed-125">DataContractSerializer, lub XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="023ed-125">DataContractSerializer or XmlSerializer</span></span>|  
|<span data-ttu-id="023ed-126">Obiekty przekazany</span><span class="sxs-lookup"><span data-stu-id="023ed-126">Objects passed</span></span>|<span data-ttu-id="023ed-127">Przez wartości lub według odwołania</span><span class="sxs-lookup"><span data-stu-id="023ed-127">By-value or by-reference</span></span>|<span data-ttu-id="023ed-128">Przez wartość tylko</span><span class="sxs-lookup"><span data-stu-id="023ed-128">By-value only</span></span>|  
|<span data-ttu-id="023ed-129">Błędy/wyjątków</span><span class="sxs-lookup"><span data-stu-id="023ed-129">Errors/exceptions</span></span>|<span data-ttu-id="023ed-130">Można serializować wyjątku</span><span class="sxs-lookup"><span data-stu-id="023ed-130">Any serializable exception</span></span>|<span data-ttu-id="023ed-131">Obiekcie FaultContract\<TDetail ></span><span class="sxs-lookup"><span data-stu-id="023ed-131">FaultContract\<TDetail></span></span>|  
|<span data-ttu-id="023ed-132">Obiekty serwera proxy klienta</span><span class="sxs-lookup"><span data-stu-id="023ed-132">Client proxy objects</span></span>|<span data-ttu-id="023ed-133">Jednoznacznie przezroczysty serwery proxy są tworzone automatycznie na podstawie elementów MarshalByRefObjects</span><span class="sxs-lookup"><span data-stu-id="023ed-133">Strongly typed transparent proxies are created automatically from MarshalByRefObjects</span></span>|<span data-ttu-id="023ed-134">Jednoznacznie serwery proxy są generowane na żądanie przy użyciu elementu ChannelFactory\<TChannel ></span><span class="sxs-lookup"><span data-stu-id="023ed-134">Strongly typed proxies are generated on-demand using ChannelFactory\<TChannel></span></span>|  
|<span data-ttu-id="023ed-135">Platforma wymagane</span><span class="sxs-lookup"><span data-stu-id="023ed-135">Platform required</span></span>|<span data-ttu-id="023ed-136">Klienta i serwera, należy użyć programu Microsoft OS i .NET</span><span class="sxs-lookup"><span data-stu-id="023ed-136">Both client and server must use Microsoft OS and .NET</span></span>|<span data-ttu-id="023ed-137">Obsługujący wiele platform</span><span class="sxs-lookup"><span data-stu-id="023ed-137">Cross-platform</span></span>|  
|<span data-ttu-id="023ed-138">Format komunikatu</span><span class="sxs-lookup"><span data-stu-id="023ed-138">Message format</span></span>|<span data-ttu-id="023ed-139">Private</span><span class="sxs-lookup"><span data-stu-id="023ed-139">Private</span></span>|<span data-ttu-id="023ed-140">Standardy branżowe (SOAP, WS-* itp.)</span><span class="sxs-lookup"><span data-stu-id="023ed-140">Industry standards (SOAP, WS-*, etc.)</span></span>|  
  
### <a name="server-implementation-comparison"></a><span data-ttu-id="023ed-141">Porównanie implementacji serwera</span><span class="sxs-lookup"><span data-stu-id="023ed-141">Server Implementation Comparison</span></span>  
  
#### <a name="creating-a-server-in-net-remoting"></a><span data-ttu-id="023ed-142">Tworzenie serwera w funkcji zdalnych .NET</span><span class="sxs-lookup"><span data-stu-id="023ed-142">Creating a Server in .NET Remoting</span></span>  
 <span data-ttu-id="023ed-143">Typy serwerów .NET remoting musi pochodzić od elementu MarshalByRefObject i definiowanie metod, które klient może wywoływać podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="023ed-143">.NET Remoting server types must derive from MarshalByRefObject and define methods the client can call, like the following:</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="023ed-144">Metody publiczne tego typu serwera stają się publicznego kontraktu dostępne dla klientów.</span><span class="sxs-lookup"><span data-stu-id="023ed-144">The public methods of this server type become the public contract available to clients.</span></span>  <span data-ttu-id="023ed-145">Brak rozdzielenie interfejsu publicznego serwera i jego wdrożenie — jeden typ obsługuje zarówno.</span><span class="sxs-lookup"><span data-stu-id="023ed-145">There is no separation between the server’s public interface and its implementation – one type handles both.</span></span>  
  
 <span data-ttu-id="023ed-146">Po zdefiniowaniu typu serwera, można go było dostępne dla klientów, takie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="023ed-146">Once the server type has been defined, it can be made available to clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel(8080);  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingConfiguration.RegisterWellKnownServiceType(  
    typeof(RemotingServer),   
    "RemotingServer",   
    WellKnownObjectMode.Singleton);  
Console.WriteLine("RemotingServer is running.  Press ENTER to terminate...");  
Console.ReadLine();  
```  
  
 <span data-ttu-id="023ed-147">Istnieje wiele sposobów, aby udostępnić typ usług zdalnych jako serwer, w tym za pomocą plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="023ed-147">There are many ways to make the Remoting type available as a server, including using configuration files.</span></span> <span data-ttu-id="023ed-148">To jest tylko jeden przykład.</span><span class="sxs-lookup"><span data-stu-id="023ed-148">This is just one example.</span></span>  
  
#### <a name="creating-a-server-in-wcf"></a><span data-ttu-id="023ed-149">Tworzenie serwera w programie WCF</span><span class="sxs-lookup"><span data-stu-id="023ed-149">Creating a Server in WCF</span></span>  
 <span data-ttu-id="023ed-150">Odpowiednik etapem WCF obejmuje tworzenie dwa typy — publiczny "kontraktu usługi" i konkretną implementację.</span><span class="sxs-lookup"><span data-stu-id="023ed-150">The equivalent step in WCF involves creating two types -- the public "service contract" and the concrete implementation.</span></span> <span data-ttu-id="023ed-151">Pierwszy jest zadeklarowany jako interfejs oznaczony atrybutem [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="023ed-151">The first is declared as an interface marked with [ServiceContract].</span></span> <span data-ttu-id="023ed-152">Metody dostępne dla klientów są oznaczone ikoną z elementu [OperationContract]:</span><span class="sxs-lookup"><span data-stu-id="023ed-152">Methods available to clients are marked with [OperationContract]:</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="023ed-153">Implementacji serwera jest zdefiniowany w oddzielnych klasą, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="023ed-153">The server’s implementation is defined in a separate concrete class, like in the following example:</span></span>  
  
```csharp
public class WCFServer : IWCFServer  
{  
    public Customer GetCustomer(int customerId) { … }  
}  
```  
  
 <span data-ttu-id="023ed-154">Po zdefiniowaniu tych typów serwera WCF można udostępnić klientom, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="023ed-154">Once these types have been defined, the WCF server can be made available to clients, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
Uri baseAddress = new Uri("net.tcp://localhost:8000/wcfserver");  
  
using (ServiceHost serviceHost = new ServiceHost(typeof(WCFServer), baseAddress))  
{  
    serviceHost.AddServiceEndpoint(typeof(IWCFServer), binding, baseAddress);  
    serviceHost.Open();  
  
    Console.WriteLine(String.Format("The WCF server is ready at {0}.",  
                                    baseAddress));  
    Console.WriteLine("Press <ENTER> to terminate service...");  
    Console.WriteLine();  
    Console.ReadLine();  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="023ed-155">TCP jest używany w obu przykładach, aby były jak najbardziej podobna.</span><span class="sxs-lookup"><span data-stu-id="023ed-155">TCP is used in both examples to keep them as similar as possible.</span></span> <span data-ttu-id="023ed-156">Zapoznaj się z przewodników scenariusz w dalszej części tego tematu, aby uzyskać przykłady pokazujące, przy użyciu protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="023ed-156">Refer to the scenario walk-throughs later in this topic for examples using HTTP.</span></span>  
  
 <span data-ttu-id="023ed-157">Istnieje wiele sposobów, aby skonfigurować i do obsługi usług WCF.</span><span class="sxs-lookup"><span data-stu-id="023ed-157">There are many ways to configure and to host WCF services.</span></span> <span data-ttu-id="023ed-158">To jest tylko jeden przykład, nazywany "hosta samodzielnego".</span><span class="sxs-lookup"><span data-stu-id="023ed-158">This is just one example, known as "self-hosted".</span></span> <span data-ttu-id="023ed-159">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="023ed-159">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="023ed-160">Porady: definiowanie kontraktu usługi</span><span class="sxs-lookup"><span data-stu-id="023ed-160">How to: Define a Service Contract</span></span>](how-to-define-a-wcf-service-contract.md)  
  
-   [<span data-ttu-id="023ed-161">Konfigurowanie usług za pomocą plików konfiguracji</span><span class="sxs-lookup"><span data-stu-id="023ed-161">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)  
  
-   [<span data-ttu-id="023ed-162">Usługi hostingowe</span><span class="sxs-lookup"><span data-stu-id="023ed-162">Hosting Services</span></span>](hosting-services.md)  
  
### <a name="client-implementation-comparison"></a><span data-ttu-id="023ed-163">Porównanie wdrożenia klienta</span><span class="sxs-lookup"><span data-stu-id="023ed-163">Client Implementation Comparison</span></span>  
  
#### <a name="creating-a-client-in-net-remoting"></a><span data-ttu-id="023ed-164">Tworzenie klienta w funkcji zdalnych .NET</span><span class="sxs-lookup"><span data-stu-id="023ed-164">Creating a Client in .NET Remoting</span></span>  
 <span data-ttu-id="023ed-165">Gdy obiekt serwera funkcji zdalnych .NET została udostępniona, mogą być używane przez klientów, takie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="023ed-165">Once a .NET Remoting server object has been made available, it can be consumed by clients, like in the following example:</span></span>  
  
```csharp
TcpChannel channel = new TcpChannel();  
ChannelServices.RegisterChannel(channel, ensureSecurity : true);  
RemotingServer server = (RemotingServer)Activator.GetObject(  
                            typeof(RemotingServer),   
                            "tcp://localhost:8080/RemotingServer");  
  
RemotingCustomer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("Customer {0} {1} received.",   
                                 customer.FirstName, customer.LastName));  
```  
  
 <span data-ttu-id="023ed-166">Wystąpienie RemotingServer zwrócony z Activator.GetObject() nazywa się "przezroczystego obiektu pośredniczącego."</span><span class="sxs-lookup"><span data-stu-id="023ed-166">The RemotingServer instance returned from Activator.GetObject() is known as a "transparent proxy."</span></span> <span data-ttu-id="023ed-167">Implementuje publiczny interfejs API dla typu RemotingServer na kliencie, ale wszystkie metody wywołania obiektu serwera uruchomione na inny proces lub komputera.</span><span class="sxs-lookup"><span data-stu-id="023ed-167">It implements the public API for the RemotingServer type on the client, but all the methods call the server object running in a different process or machine.</span></span>  
  
#### <a name="creating-a-client-in-wcf"></a><span data-ttu-id="023ed-168">Tworzenie klienta w programie WCF</span><span class="sxs-lookup"><span data-stu-id="023ed-168">Creating a Client in WCF</span></span>  
 <span data-ttu-id="023ed-169">Odpowiednik etapem WCF polega na użyciu fabryki kanałów można jawnie utworzyć serwer proxy.</span><span class="sxs-lookup"><span data-stu-id="023ed-169">The equivalent step in WCF involves using a channel factory to create the proxy explicitly.</span></span> <span data-ttu-id="023ed-170">Podobnie jak Remoting obiekt serwera proxy może służyć do wywołania operacji na serwerze, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="023ed-170">Like Remoting, the proxy object can be used to invoke operations on the server, like in the following example:</span></span>  
  
```csharp
NetTcpBinding binding = new NetTcpBinding();  
String url = "net.tcp://localhost:8000/wcfserver";  
EndpointAddress address = new EndpointAddress(url);  
ChannelFactory<IWCFServer> channelFactory =   
    new ChannelFactory<IWCFServer>(binding, address);  
IWCFServer server = channelFactory.CreateChannel();  
  
Customer customer = server.GetCustomer(42);  
Console.WriteLine(String.Format("  Customer {0} {1} received.",  
                    customer.FirstName, customer.LastName));  
```  
  
 <span data-ttu-id="023ed-171">Ten przykład przedstawia programowania na poziomie kanału, ponieważ jest najbardziej podobny do komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="023ed-171">This example shows programming at the channel level because it is most similar to the Remoting example.</span></span> <span data-ttu-id="023ed-172">Jest dostępna również **Dodaj odwołanie do usługi** podejście w programie Visual Studio, który generuje kod, aby uprościć klienta programowania.</span><span class="sxs-lookup"><span data-stu-id="023ed-172">Also available is the **Add Service Reference** approach in Visual Studio that generates code to simplify client programming.</span></span> <span data-ttu-id="023ed-173">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="023ed-173">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="023ed-174">Programowanie na poziomie kanału klienta</span><span class="sxs-lookup"><span data-stu-id="023ed-174">Client Channel-Level Programming</span></span>](./extending/client-channel-level-programming.md)  
  
-   [<span data-ttu-id="023ed-175">Porady: Dodawanie, aktualizowanie lub usuwanie odwołań usługi</span><span class="sxs-lookup"><span data-stu-id="023ed-175">How to: Add, Update, or Remove a Service Reference</span></span>](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference)  
  
### <a name="serialization-usage"></a><span data-ttu-id="023ed-176">Użycie serializacji</span><span class="sxs-lookup"><span data-stu-id="023ed-176">Serialization Usage</span></span>  
 <span data-ttu-id="023ed-177">Zarówno funkcji zdalnych .NET, jak i WCF umożliwia wysyłanie obiektów między klientem i serwerem serializacji, ale różnią się one w tych sposobów:</span><span class="sxs-lookup"><span data-stu-id="023ed-177">Both .NET Remoting and WCF use serialization to send objects between client and server, but they differ in these important ways:</span></span>  
  
1.  <span data-ttu-id="023ed-178">Różnych serializatorów i konwencje związane z nich służy do wskazywania co do serializacji.</span><span class="sxs-lookup"><span data-stu-id="023ed-178">They use different serializers and conventions to indicate what to serialize.</span></span>  
  
2.  <span data-ttu-id="023ed-179">Funkcji zdalnych .NET obsługuje serializacji "przez odwołanie", umożliwiająca dostęp do metody lub właściwości na jedną warstwę na wykonanie kodu na inne warstwy, która jest poza granicami zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="023ed-179">.NET Remoting supports "by reference" serialization that allows method or property access on one tier to execute code on the other tier, which is across security boundaries.</span></span> <span data-ttu-id="023ed-180">Ta funkcja udostępnia luk w zabezpieczeniach i jest jednym z głównych powodów dlaczego punktów końcowych usług zdalnych nigdy nie powinny zostać ujawnione klientom niezaufanych.</span><span class="sxs-lookup"><span data-stu-id="023ed-180">This capability exposes security vulnerabilities and is one of the main reasons why Remoting endpoints should never be exposed to untrusted clients.</span></span>  
  
3.  <span data-ttu-id="023ed-181">Wypisz jest używane przez usługi zdalne serializacji (jawnie wykluczyć jakie nie można serializować) i serializacja WCF jest opcjonalnych (Oznacz jawnie członków do serializacji).</span><span class="sxs-lookup"><span data-stu-id="023ed-181">Serialization used by Remoting is opt-out (explicitly exclude what not to serialize) and WCF serialization is opt-in (explicitly mark which members to serialize).</span></span>  
  
#### <a name="serialization-in-net-remoting"></a><span data-ttu-id="023ed-182">Serializacja w funkcji zdalnych .NET</span><span class="sxs-lookup"><span data-stu-id="023ed-182">Serialization in .NET Remoting</span></span>  
 <span data-ttu-id="023ed-183">Funkcji zdalnych .NET obsługuje dwa sposoby serializacji i deserializacji obiektów między klientem i serwerem:</span><span class="sxs-lookup"><span data-stu-id="023ed-183">.NET Remoting supports two ways to serialize and deserialize objects between the client and server:</span></span>  
  
-   <span data-ttu-id="023ed-184">*Według wartości* — wartości obiektu są serializowane w granicach warstwy, a nowe wystąpienie tego obiektu jest tworzony na innej warstwie.</span><span class="sxs-lookup"><span data-stu-id="023ed-184">*By value* – the values of the object are serialized across tier boundaries, and a new instance of that object is created on the other tier.</span></span> <span data-ttu-id="023ed-185">Wszystkie wywołania metody lub właściwości tego nowego wystąpienia wykonanie tylko lokalnie i nie wpływają na oryginalny obiekt lub warstwy.</span><span class="sxs-lookup"><span data-stu-id="023ed-185">Any calls to methods or properties of that new instance execute only locally and do not affect the original object or tier.</span></span>  
  
-   <span data-ttu-id="023ed-186">*Przez odwołanie* — specjalnego "odwołanie do obiektu" jest serializowany w granicach warstwy.</span><span class="sxs-lookup"><span data-stu-id="023ed-186">*By reference* – a special "object reference" is serialized across tier boundaries.</span></span> <span data-ttu-id="023ed-187">Gdy jedną warstwę użyje metody lub właściwości tego obiektu, komunikuje się wstecz do oryginalnego obiektu na warstwie oryginalnej.</span><span class="sxs-lookup"><span data-stu-id="023ed-187">When one tier interacts with methods or properties of that object, it communicates back to the original object on the original tier.</span></span> <span data-ttu-id="023ed-188">Obiekty-reference może przepływać w obu kierunkach — od serwera do klienta lub od klienta do serwera.</span><span class="sxs-lookup"><span data-stu-id="023ed-188">By-reference objects can flow in either direction – server to client, or client to server.</span></span>  
  
 <span data-ttu-id="023ed-189">Typy według wartości w zdalnych są oznaczone atrybutem [Serializable] lub zaimplementuj element ISerializable, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="023ed-189">By-value types in Remoting are marked with the [Serializable] attribute or implement ISerializable, like in the following example:</span></span>  
  
```csharp
[Serializable]  
public class RemotingCustomer  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="023ed-190">Typów przez odwołanie pochodzi od klasy MarshalByRefObject, podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="023ed-190">By-reference types derive from the MarshalByRefObject class, like in the following example:</span></span>  
  
```csharp
public class RemotingCustomerReference : MarshalByRefObject  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="023ed-191">Jest bardzo ważne, aby zrozumienie wpływu na zdalnych obiektów przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="023ed-191">It is extremely important to understand the implications of Remoting’s by-reference objects.</span></span> <span data-ttu-id="023ed-192">Każda warstwa (klienta lub serwera) wysyła obiektu przez odwołania do innych warstwy, wszystkie wywołania metody wykonywania do warstwy będący właścicielem obiektu.</span><span class="sxs-lookup"><span data-stu-id="023ed-192">If either tier (client or server) sends a by-reference object to the other tier, all method calls execute back on the tier owning the object.</span></span> <span data-ttu-id="023ed-193">Na przykład klient wywoływania metod dla obiekt przez odwołanie zwrócone przez serwer będzie wykonanie kodu na serwerze.</span><span class="sxs-lookup"><span data-stu-id="023ed-193">For example, a client calling methods on a by-reference object returned by the server will execute code on the server.</span></span> <span data-ttu-id="023ed-194">Podobnie serwer wywoływania metod dla obiekt przez odwołanie dostarczonych przez klienta będzie wykonywał kodu ponownie na kliencie.</span><span class="sxs-lookup"><span data-stu-id="023ed-194">Similarly, a server calling methods on a by-reference object provided by the client will execute code back on the client.</span></span> <span data-ttu-id="023ed-195">Z tego powodu zaleca się korzystanie z funkcji zdalnych .NET tylko w pełni zaufanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="023ed-195">For this reason, the use of .NET Remoting is recommended only within fully-trusted environments.</span></span> <span data-ttu-id="023ed-196">Udostępnianie publiczny punkt końcowy .NET Remoting do niezaufani Klienci spowoduje, że serwer usług zdalnych narażony na ataki.</span><span class="sxs-lookup"><span data-stu-id="023ed-196">Exposing a public .NET Remoting endpoint to untrusted clients will make a Remoting server vulnerable to attack.</span></span>  
  
#### <a name="serialization-in-wcf"></a><span data-ttu-id="023ed-197">Serializacja w programie WCF</span><span class="sxs-lookup"><span data-stu-id="023ed-197">Serialization in WCF</span></span>  
 <span data-ttu-id="023ed-198">Usługi WCF obsługuje tylko przez wartość serializacji.</span><span class="sxs-lookup"><span data-stu-id="023ed-198">WCF supports only by-value serialization.</span></span> <span data-ttu-id="023ed-199">Najczęściej do zdefiniowania typu do wymiany między klientem a serwerem jest podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="023ed-199">The most common way to define a type to exchange between client and server is like in the following example:</span></span>  
  
```csharp
[DataContract]  
public class WCFCustomer  
{  
    [DataMember]  
    public string FirstName { get; set; }  
  
    [DataMember]  
    public string LastName { get; set; }  
  
    [DataMember]  
    public int CustomerId { get; set; }  
}  
```  
  
 <span data-ttu-id="023ed-200">Atrybut [DataContract] określa tego typu jako jeden serializacji i deserializacji między klientem i serwerem.</span><span class="sxs-lookup"><span data-stu-id="023ed-200">The [DataContract] attribute identifies this type as one that can be serialized and deserialized between client and server.</span></span> <span data-ttu-id="023ed-201">Atrybut [DataMember] określa poszczególne właściwości lub pola do serializacji.</span><span class="sxs-lookup"><span data-stu-id="023ed-201">The [DataMember] attribute identifies the individual properties or fields to serialize.</span></span>  
  
 <span data-ttu-id="023ed-202">Gdy WCF wysyła obiektu między warstwami, serializuje tylko wartości i tworzy nowe wystąpienie obiektu na innej warstwie.</span><span class="sxs-lookup"><span data-stu-id="023ed-202">When WCF sends an object across tiers, it serializes only the values and creates a new instance of the object on the other tier.</span></span> <span data-ttu-id="023ed-203">Wszystkie interakcje z wartościami obiektu występują tylko lokalnie — nie komunikują się z warstwą obiektów przez odwołanie funkcji zdalnych .NET, jak.</span><span class="sxs-lookup"><span data-stu-id="023ed-203">Any interactions with the values of the object occur only locally – they do not communicate with the other tier the way .NET Remoting by-reference objects do.</span></span> <span data-ttu-id="023ed-204">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="023ed-204">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="023ed-205">Serializacja i deserializacja</span><span class="sxs-lookup"><span data-stu-id="023ed-205">Serialization and Deserialization</span></span>](./feature-details/serialization-and-deserialization.md)  
  
-   [<span data-ttu-id="023ed-206">Serializacja programu Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="023ed-206">Serialization in Windows Communication Foundation</span></span>](http://msdn.microsoft.com/magazine/cc163569.aspx)  
  
### <a name="exception-handling-capabilities"></a><span data-ttu-id="023ed-207">Możliwości obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="023ed-207">Exception Handling Capabilities</span></span>  
  
#### <a name="exceptions-in-net-remoting"></a><span data-ttu-id="023ed-208">Wyjątki w funkcji zdalnych .NET</span><span class="sxs-lookup"><span data-stu-id="023ed-208">Exceptions in .NET Remoting</span></span>  
 <span data-ttu-id="023ed-209">Wyjątki generowane przez serwer usług zdalnych są serializowane, wysłane do klienta i generowany lokalnie na komputerze klienckim, podobnie jak inne wyjątek.</span><span class="sxs-lookup"><span data-stu-id="023ed-209">Exceptions thrown by a Remoting server are serialized, sent to the client, and thrown locally on the client like any other exception.</span></span> <span data-ttu-id="023ed-210">Niestandardowymi wyjątkami mogą być tworzone przez podrzędna classing typ wyjątku i oznaczenie go [SERIALIZABLE].</span><span class="sxs-lookup"><span data-stu-id="023ed-210">Custom exceptions can be created by sub-classing the Exception type and marking it with [Serializable].</span></span>   <span data-ttu-id="023ed-211">Większość wyjątków framework już zostały oznaczone w ten sposób, dzięki czemu większość zostanie wygenerowany przez serwer serializowane i zgłoszony ponownie na kliencie.</span><span class="sxs-lookup"><span data-stu-id="023ed-211">Most framework exceptions are already marked in this way, allowing most to be thrown by the server, serialized, and re-thrown on the client.</span></span> <span data-ttu-id="023ed-212">Chociaż ten projekt jest wygodne podczas tworzenia, informacje po stronie serwera może przypadkowo ujawniane do klienta.</span><span class="sxs-lookup"><span data-stu-id="023ed-212">Though this design is convenient during development, server-side information can inadvertently be disclosed to the client.</span></span> <span data-ttu-id="023ed-213">Jest to jedna z wielu powodów zdalnych należy używać tylko w pełni zaufanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="023ed-213">This is one of many reasons Remoting should be used only in fully-trusted environments.</span></span>  
  
#### <a name="exceptions-and-faults-in-wcf"></a><span data-ttu-id="023ed-214">Wyjątków i błędów w programie WCF</span><span class="sxs-lookup"><span data-stu-id="023ed-214">Exceptions and Faults in WCF</span></span>  
 <span data-ttu-id="023ed-215">Usługi WCF nie zezwala na typy wyjątków dowolnego ma zostać zwrócona z serwera do klienta, ponieważ połączenie może prowadzić do przypadkowym ujawnieniem.</span><span class="sxs-lookup"><span data-stu-id="023ed-215">WCF does not allow arbitrary exception types to be returned from the server to the client because it could lead to inadvertent information disclosure.</span></span> <span data-ttu-id="023ed-216">Jeśli operacja usługi zgłasza nieoczekiwany wyjątek, powoduje ogólnego przeznaczenia FaultException zostanie wygenerowany na kliencie.</span><span class="sxs-lookup"><span data-stu-id="023ed-216">If a service operation throws an unexpected exception, it causes a general purpose FaultException to be thrown on the client.</span></span> <span data-ttu-id="023ed-217">Tego wyjątku nie zawiera żadnych informacji, dlaczego gdzie wystąpił problem i dla niektórych aplikacji jest wystarczająca.</span><span class="sxs-lookup"><span data-stu-id="023ed-217">This exception does not carry any information why or where the problem occurred, and for some applications this is sufficient.</span></span> <span data-ttu-id="023ed-218">Aplikacje, które muszą komunikować się bardziej rozbudowane informacje o błędzie, czy klient to definiując kontrakt błędu.</span><span class="sxs-lookup"><span data-stu-id="023ed-218">Applications that need to communicate richer error information to the client do this by defining a fault contract.</span></span>  
  
 <span data-ttu-id="023ed-219">Aby to zrobić, należy najpierw utworzyć typu [DataContract] do przenoszenia informacje o błędzie.</span><span class="sxs-lookup"><span data-stu-id="023ed-219">To do this, first create a [DataContract] type to carry the fault information.</span></span>  
  
```csharp
[DataContract]  
public class CustomerServiceFault  
{  
    [DataMember]  
    public string ErrorMessage { get; set; }  
  
    [DataMember]  
    public int CustomerId {get;set;}  
}  
```  
  
 <span data-ttu-id="023ed-220">Określ kontrakt błędu dla każdej operacji usługi.</span><span class="sxs-lookup"><span data-stu-id="023ed-220">Specify the fault contract to use for each service operation.</span></span>  
  
```csharp
[ServiceContract]  
public interface IWCFServer  
{  
    [OperationContract]  
    [FaultContract(typeof(CustomerServiceFault))]  
    Customer GetCustomer(int customerId);  
}  
```  
  
 <span data-ttu-id="023ed-221">Serwer raportów błędów przez zgłaszanie zgłoszenie wyjątku FaultException.</span><span class="sxs-lookup"><span data-stu-id="023ed-221">The server reports error conditions by throwing a FaultException.</span></span>  
  
```csharp
throw new FaultException<CustomerServiceFault>(  
    new CustomerServiceFault() {   
        CustomerId = customerId,   
        ErrorMessage = "Illegal customer Id"   
    });  
```  
  
 <span data-ttu-id="023ed-222">I zawsze, gdy klient wysyła żądanie do serwera, może przechwycić błędy jako wyjątki normalnego.</span><span class="sxs-lookup"><span data-stu-id="023ed-222">And whenever the client makes a request to the server, it can catch faults as normal exceptions.</span></span>  
  
```csharp
try  
{  
    Customer customer = server.GetCustomer(-1);  
}  
catch (FaultException<CustomerServiceFault> fault)  
{  
    Console.WriteLine(String.Format("Fault received: {0}",  
    fault.Detail.ErrorMessage));  
}  
```  
  
 <span data-ttu-id="023ed-223">Aby uzyskać więcej informacji na temat kontraktów błędów zobacz <xref:System.ServiceModel.FaultException>.</span><span class="sxs-lookup"><span data-stu-id="023ed-223">For more information about fault contracts, see <xref:System.ServiceModel.FaultException>.</span></span>  
  
### <a name="security-considerations"></a><span data-ttu-id="023ed-224">Zagadnienia dotyczące zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="023ed-224">Security Considerations</span></span>  
  
#### <a name="security-in-net-remoting"></a><span data-ttu-id="023ed-225">Zabezpieczenia w funkcji zdalnych .NET</span><span class="sxs-lookup"><span data-stu-id="023ed-225">Security in .NET Remoting</span></span>  
 <span data-ttu-id="023ed-226">Niektórych funkcji zdalnych .NET kanały obsługuje funkcje zabezpieczeń, takich jak uwierzytelnianie i szyfrowanie w warstwie kanału (IPC i TCP).</span><span class="sxs-lookup"><span data-stu-id="023ed-226">Some .NET Remoting channels support security features such as authentication and encryption at the channel layer (IPC and TCP).</span></span> <span data-ttu-id="023ed-227">Kanał HTTP polega na Internet Information Services (IIS) dla uwierzytelniania i szyfrowania.</span><span class="sxs-lookup"><span data-stu-id="023ed-227">The HTTP channel relies on Internet Information Services (IIS) for both authentication and encryption.</span></span> <span data-ttu-id="023ed-228">Pomimo ta obsługa należy wziąć pod uwagę .NET Remoting protokołu komunikacyjnego niezabezpieczone i używać go tylko w pełni zaufanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="023ed-228">Despite this support, you should consider .NET Remoting an unsecure communication protocol and use it only within fully-trusted environments.</span></span> <span data-ttu-id="023ed-229">Nigdy nie uwidacznia publiczny punkt końcowy usług zdalnych do Internetu lub niezaufanego klientów.</span><span class="sxs-lookup"><span data-stu-id="023ed-229">Never expose a public Remoting endpoint to the Internet or untrusted clients.</span></span>  
  
#### <a name="security-in-wcf"></a><span data-ttu-id="023ed-230">Zabezpieczenia w programie WCF</span><span class="sxs-lookup"><span data-stu-id="023ed-230">Security in WCF</span></span>  
 <span data-ttu-id="023ed-231">WCF został opracowany z zabezpieczeniami, pamiętając, w części adresu rodzaje luk w zabezpieczeniach w funkcji zdalnych .NET.</span><span class="sxs-lookup"><span data-stu-id="023ed-231">WCF was designed with security in mind, in part to address the kinds of vulnerabilities found in .NET Remoting.</span></span> <span data-ttu-id="023ed-232">Usługi WCF oferuje zabezpieczeń na poziomie komunikatu i transportu i oferuje wiele opcji uwierzytelniania, autoryzacji, szyfrowania i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="023ed-232">WCF offers security at both the transport and message level, and offers many options for authentication, authorization, encryption, and so on.</span></span> <span data-ttu-id="023ed-233">Więcej informacji znajduje się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="023ed-233">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="023ed-234">Zabezpieczeń</span><span class="sxs-lookup"><span data-stu-id="023ed-234">Security</span></span>](./feature-details/security.md)  
  
-   [<span data-ttu-id="023ed-235">Wskazówki dotyczące zabezpieczeń programu WCF</span><span class="sxs-lookup"><span data-stu-id="023ed-235">WCF Security Guidance</span></span>](./feature-details/security-guidance-and-best-practices.md)  
  
## <a name="migrating-to-wcf"></a><span data-ttu-id="023ed-236">Migracja do programu WCF</span><span class="sxs-lookup"><span data-stu-id="023ed-236">Migrating to WCF</span></span>  
  
### <a name="why-migrate-from-remoting-to-wcf"></a><span data-ttu-id="023ed-237">Dlaczego migrację z usług zdalnych WCF?</span><span class="sxs-lookup"><span data-stu-id="023ed-237">Why Migrate from Remoting to WCF?</span></span>  
  
-   <span data-ttu-id="023ed-238">**.NET remoting jest starszej wersji produktu.**</span><span class="sxs-lookup"><span data-stu-id="023ed-238">**.NET Remoting is a legacy product.**</span></span> <span data-ttu-id="023ed-239">Zgodnie z opisem w [.NET Remoting](http://msdn.microsoft.com/library/vstudio/72x4h507\(v=vs.100\).aspx), jest uznawane za starszej wersji produktu i nie jest zalecane w przypadku nowych wdrożeń.</span><span class="sxs-lookup"><span data-stu-id="023ed-239">As described in [.NET Remoting](http://msdn.microsoft.com/library/vstudio/72x4h507\(v=vs.100\).aspx), it is considered a legacy product and is not recommended for new development.</span></span> <span data-ttu-id="023ed-240">Usługi WCF lub interfejsu API sieci Web platformy ASP.NET są zalecane w przypadku nowych i istniejących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="023ed-240">WCF or ASP.NET Web API are recommended for new and existing applications.</span></span>  
  
-   <span data-ttu-id="023ed-241">**Usługi WCF używa standardów i platform.**</span><span class="sxs-lookup"><span data-stu-id="023ed-241">**WCF uses cross-platform standards.**</span></span> <span data-ttu-id="023ed-242">WCF została zaprojektowana współdziałanie między platformami pamiętać i obsługuje wiele standardy branżowe (SOAP, WS-Security WS-Trust, itp.).</span><span class="sxs-lookup"><span data-stu-id="023ed-242">WCF was designed with cross-platform interoperability in mind and supports many industry standards (SOAP, WS-Security, WS-Trust, etc.).</span></span> <span data-ttu-id="023ed-243">Usługi WCF może współdziałać z klientów z systemem innym niż Windows w systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="023ed-243">A WCF service can interoperate with clients running on operating systems other than Windows.</span></span> <span data-ttu-id="023ed-244">Usług zdalnych został zaprojektowany głównie dla środowisk, w którym aplikacje klienta i serwera uruchamiane przy użyciu programu .NET framework w systemie operacyjnym Windows.</span><span class="sxs-lookup"><span data-stu-id="023ed-244">Remoting was designed primarily for environments where both the server and client applications run using the .NET framework on a Windows operating system.</span></span>  
  
-   <span data-ttu-id="023ed-245">**Usługi WCF ma wbudowane zabezpieczenia.**</span><span class="sxs-lookup"><span data-stu-id="023ed-245">**WCF has built-in security.**</span></span> <span data-ttu-id="023ed-246">Usługi WCF została zaprojektowana z myślą o bezpieczeństwie i oferuje wiele opcji uwierzytelniania zabezpieczeń na poziomie transportu, zabezpieczeniami na poziomie wiadomości itp. Komunikację zdalną zaprojektowano tak, aby ułatwić aplikacji współdziałanie, ale nie został zaprojektowany do zabezpieczenia w środowiskach niezaufanej.</span><span class="sxs-lookup"><span data-stu-id="023ed-246">WCF was designed with security in mind and offers many options for authentication, transport level security, message level security, etc. Remoting was designed to make it easy for applications to interoperate but was not designed to be secure in non-trusted environments.</span></span> <span data-ttu-id="023ed-247">Usługi WCF został zaprojektowany do pracy w środowiskach zaufanej i niezaufanej.</span><span class="sxs-lookup"><span data-stu-id="023ed-247">WCF was designed to work in both trusted and non-trusted environments.</span></span>  
  
### <a name="migration-recommendations"></a><span data-ttu-id="023ed-248">Zalecenia dotyczące migracji</span><span class="sxs-lookup"><span data-stu-id="023ed-248">Migration Recommendations</span></span>  
 <span data-ttu-id="023ed-249">Poniżej przedstawiono zalecane kroki, aby przeprowadzić migrację z programu .NET Remoting do programu WCF:</span><span class="sxs-lookup"><span data-stu-id="023ed-249">The following are the recommended steps to migrate from .NET Remoting to WCF:</span></span>  
  
-   <span data-ttu-id="023ed-250">**Tworzenie kontraktu usługi.**</span><span class="sxs-lookup"><span data-stu-id="023ed-250">**Create the service contract.**</span></span> <span data-ttu-id="023ed-251">Definiowanie typów interfejsu użytkownika usługi i oznacz je za pomocą atrybutu [ServiceContract]. Oznacz wszystkie metody, których klienci będą mogli wywołana za pomocą elementu [OperationContract].</span><span class="sxs-lookup"><span data-stu-id="023ed-251">Define your service interface types, and mark them with the [ServiceContract] attribute.Mark all the methods the clients will be allowed to call with [OperationContract].</span></span>  
  
-   <span data-ttu-id="023ed-252">**Tworzenie kontraktu danych.**</span><span class="sxs-lookup"><span data-stu-id="023ed-252">**Create the data contract.**</span></span> <span data-ttu-id="023ed-253">Definiowanie typów danych, które będą wymieniane między serwerem a klientem i oznacz je za pomocą atrybutu [DataContract].</span><span class="sxs-lookup"><span data-stu-id="023ed-253">Define the data types that will be exchanged between server and client, and mark them with the [DataContract] attribute.</span></span> <span data-ttu-id="023ed-254">Oznacz wszystkie pola i właściwości, które klient będzie mogła korzystać z [DataMember].</span><span class="sxs-lookup"><span data-stu-id="023ed-254">Mark all the fields and properties the client will be allowed to use with [DataMember].</span></span>  
  
-   <span data-ttu-id="023ed-255">**Utwórz kontrakt błędu (opcjonalnie).**</span><span class="sxs-lookup"><span data-stu-id="023ed-255">**Create the fault contract (optional).**</span></span> <span data-ttu-id="023ed-256">Tworzenie typów, które będą wymieniane między serwerem a klientem, gdy wystąpią błędy.</span><span class="sxs-lookup"><span data-stu-id="023ed-256">Create the types that will be exchanged between server and client when errors are encountered.</span></span> <span data-ttu-id="023ed-257">Oznacz te typy z [DataContract] i [DataMember], aby je do serializacji.</span><span class="sxs-lookup"><span data-stu-id="023ed-257">Mark these types with [DataContract] and [DataMember] to make them serializable.</span></span> <span data-ttu-id="023ed-258">Dla wszystkich operacji usługi, które oznaczona atrybutem [OperationContract] również oznacz je za pomocą [obiekcie FaultContract], aby wskazać, które zwracają może błędy.</span><span class="sxs-lookup"><span data-stu-id="023ed-258">For all service operations you marked with [OperationContract], also mark them with [FaultContract] to indicate which errors they may return.</span></span>  
  
-   <span data-ttu-id="023ed-259">**Konfigurowanie i obsługi usługi.**</span><span class="sxs-lookup"><span data-stu-id="023ed-259">**Configure and host the service.**</span></span> <span data-ttu-id="023ed-260">Po utworzeniu kontraktu usługi, następnym krokiem jest skonfigurować powiązanie do udostępnienia usługi w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="023ed-260">Once the service contract has been created, the next step is to configure a binding to expose the service at an endpoint.</span></span> <span data-ttu-id="023ed-261">Aby uzyskać więcej informacji, zobacz [punkty końcowe: adresy, wiązania i kontrakty](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="023ed-261">For more information, see [Endpoints: Addresses, Bindings, and Contracts](./feature-details/endpoints-addresses-bindings-and-contracts.md).</span></span>  
  
 <span data-ttu-id="023ed-262">Po aplikacji usług zdalnych przeprowadzono migrację do programu WCF, należy nadal usuń zależności funkcji zdalnych .NET.</span><span class="sxs-lookup"><span data-stu-id="023ed-262">Once a Remoting application has been migrated to WCF, it is still important to remove dependencies on .NET Remoting.</span></span> <span data-ttu-id="023ed-263">Dzięki temu, że żadnych luk Remoting zostaną usunięte z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="023ed-263">This ensures that any Remoting vulnerabilities are removed from the application.</span></span> <span data-ttu-id="023ed-264">Kroki te obejmują następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="023ed-264">These steps include the following:</span></span>  
  
-   <span data-ttu-id="023ed-265">**Zaprzestanie stosowania programu MarshalByRefObject.**</span><span class="sxs-lookup"><span data-stu-id="023ed-265">**Discontinue use of MarshalByRefObject.**</span></span> <span data-ttu-id="023ed-266">Typ elementu MarshalByRefObject istnieje tylko w przypadku usług zdalnych i nie jest używany przez usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="023ed-266">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="023ed-267">Wszystkie typy aplikacji, które częściowej klasy MarshalByRefObject zostaje usunięty lub zmieniony.</span><span class="sxs-lookup"><span data-stu-id="023ed-267">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span> <span data-ttu-id="023ed-268">Typ elementu MarshalByRefObject istnieje tylko w przypadku usług zdalnych i nie jest używany przez usługę WCF.</span><span class="sxs-lookup"><span data-stu-id="023ed-268">The MarshalByRefObject type exists only for Remoting and is not used by WCF.</span></span> <span data-ttu-id="023ed-269">Wszystkie typy aplikacji, które częściowej klasy MarshalByRefObject zostaje usunięty lub zmieniony.</span><span class="sxs-lookup"><span data-stu-id="023ed-269">Any application types that sub-class MarshalByRefObject should be removed or changed.</span></span>  
  
-   <span data-ttu-id="023ed-270">**Zaprzestanie stosowania [Serializable] i interfejs ISerializable.**</span><span class="sxs-lookup"><span data-stu-id="023ed-270">**Discontinue use of [Serializable] and ISerializable.**</span></span> <span data-ttu-id="023ed-271">Atrybut [Serializable] i interfejsu ISerializable pierwotnie zostały zaprojektowane do serializacji typów w środowiskach zaufanych i są one używane w komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="023ed-271">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="023ed-272">Serializacja WCF polega na typy są oznaczonej jako [DataContract] i [DataMember].</span><span class="sxs-lookup"><span data-stu-id="023ed-272">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="023ed-273">Typy danych używany przez aplikację powinno zostać zmodyfikowane, aby użyć [DataContract] i nie należy używać interfejs ISerializable lub [Serializable].</span><span class="sxs-lookup"><span data-stu-id="023ed-273">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span> <span data-ttu-id="023ed-274">Atrybut [Serializable] i interfejsu ISerializable pierwotnie zostały zaprojektowane do serializacji typów w środowiskach zaufanych i są one używane w komunikacji zdalnej.</span><span class="sxs-lookup"><span data-stu-id="023ed-274">The [Serializable] attribute and ISerializable interface were originally designed to serialize types within trusted environments, and they are used by Remoting.</span></span> <span data-ttu-id="023ed-275">Serializacja WCF polega na typy są oznaczonej jako [DataContract] i [DataMember].</span><span class="sxs-lookup"><span data-stu-id="023ed-275">WCF serialization relies on types being marked with [DataContract] and [DataMember].</span></span> <span data-ttu-id="023ed-276">Typy danych używany przez aplikację powinno zostać zmodyfikowane, aby użyć [DataContract] i nie należy używać interfejs ISerializable lub [Serializable].</span><span class="sxs-lookup"><span data-stu-id="023ed-276">Data types used by an application should be modified to use [DataContract] and not to use ISerializable or [Serializable].</span></span>  
  
### <a name="migration-scenarios"></a><span data-ttu-id="023ed-277">Scenariusze migracji</span><span class="sxs-lookup"><span data-stu-id="023ed-277">Migration Scenarios</span></span>  
 <span data-ttu-id="023ed-278">Teraz zobaczmy, jak wykonywać następujące typowe scenariusze komunikacji zdalnej programu WCF:</span><span class="sxs-lookup"><span data-stu-id="023ed-278">Now let’s see how to accomplish the following common Remoting scenarios in WCF:</span></span>  
  
1.  <span data-ttu-id="023ed-279">Serwer zwraca obiekt przez wartość do klienta</span><span class="sxs-lookup"><span data-stu-id="023ed-279">Server returns an object by-value to the client</span></span>  
  
2.  <span data-ttu-id="023ed-280">Serwer zwraca obiekt przez odwołanie do klienta</span><span class="sxs-lookup"><span data-stu-id="023ed-280">Server returns an object by-reference to the client</span></span>  
  
3.  <span data-ttu-id="023ed-281">Klient wysyła obiektu przez wartość do serwera</span><span class="sxs-lookup"><span data-stu-id="023ed-281">Client sends an object by-value to the server</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="023ed-282">Wysyłanie przez — odwołanie do obiektu z klienta do serwera w programie WCF jest niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="023ed-282">Sending an object by-reference from the client to the server is not allowed in WCF.</span></span>  
  
 <span data-ttu-id="023ed-283">Podczas odczytu za pomocą tych scenariuszy, przyjęto założenie, że naszych interfejsów linii bazowej dla funkcji zdalnych .NET wyglądać jak w następującym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="023ed-283">When reading through these scenarios, assume our baseline interfaces for .NET Remoting look like the following example.</span></span> <span data-ttu-id="023ed-284">Implementacja funkcji zdalnych .NET nie jest ważna w tym miejscu ponieważ chcemy, aby zilustrować tylko używają WCF do zaimplementowania równoważne funkcje.</span><span class="sxs-lookup"><span data-stu-id="023ed-284">The .NET Remoting implementation is not important here because we want to illustrate only how to use WCF to implement equivalent functionality.</span></span>  
  
```csharp
public class RemotingServer : MarshalByRefObject  
{  
    // Demonstrates server returning object by-value  
    public Customer GetCustomer(int customerId) {…}  
  
    // Demonstrates server returning object by-reference  
    public CustomerReference GetCustomerReference(int customerId) {…}  
  
    // Demonstrates client passing object to server by-value  
    public bool UpdateCustomer(Customer customer) {…}  
}  
```  
  
#### <a name="scenario-1-service-returns-an-object-by-value"></a><span data-ttu-id="023ed-285">Scenariusz 1: Usługa zwraca obiekt przez wartość</span><span class="sxs-lookup"><span data-stu-id="023ed-285">Scenario 1: Service Returns an Object by Value</span></span>  
 <span data-ttu-id="023ed-286">W tym scenariuszu pokazano, serwer, zwracając obiekt do klienta przez wartość.</span><span class="sxs-lookup"><span data-stu-id="023ed-286">This scenario demonstrates a server returning an object to the client by value.</span></span> <span data-ttu-id="023ed-287">WCF zawsze zwraca obiekty z serwera wg wartości, więc w poniższych krokach opisano tylko sposób tworzenia normalnej usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="023ed-287">WCF always returns objects from the server by value, so the following steps simply describe how to build a normal WCF service.</span></span>  
  
1.  <span data-ttu-id="023ed-288">Rozpocznij od zdefiniowania publiczny interfejs dla usługi WCF i oznacz ją atrybutem [ServiceContract].</span><span class="sxs-lookup"><span data-stu-id="023ed-288">Start by defining a public interface for the WCF service and mark it with the [ServiceContract] attribute.</span></span> <span data-ttu-id="023ed-289">Używamy [OperationContract] do identyfikowania metod po stronie serwera, który wywoła naszych klientów.</span><span class="sxs-lookup"><span data-stu-id="023ed-289">We use [OperationContract] to identify the server-side methods our client will call.</span></span>  
  
   ```csharp
   [ServiceContract]  
   public interface ICustomerService  
   {  
       [OperationContract]  
       Customer GetCustomer(int customerId);  
  
       [OperationContract]  
       bool UpdateCustomer(Customer customer);  
   }  
   ```  
  
2.  <span data-ttu-id="023ed-290">Następnym krokiem jest tworzenie kontraktu danych dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="023ed-290">The next step is to create the data contract for this service.</span></span> <span data-ttu-id="023ed-291">Firma Microsoft to zrobić, tworząc klasy (nie interfejsy) oznaczonej przez atrybut [DataContract].</span><span class="sxs-lookup"><span data-stu-id="023ed-291">We do this by creating classes (not interfaces) marked with the [DataContract] attribute.</span></span> <span data-ttu-id="023ed-292">Indywidualne właściwości lub pola, które chcemy się widoczne dla klienta i serwera są oznaczone [DataMember].</span><span class="sxs-lookup"><span data-stu-id="023ed-292">The individual properties or fields we want visible to both client and server are marked with [DataMember].</span></span> <span data-ttu-id="023ed-293">Jeśli chcemy typy pochodne mogą być możemy Użyj atrybutu [KnownType] w celu ich identyfikacji.</span><span class="sxs-lookup"><span data-stu-id="023ed-293">If we want derived types to be allowed, we must use the [KnownType] attribute to identify them.</span></span> <span data-ttu-id="023ed-294">Tylko typy WCF umożliwi serializacji lub deserializacji dla tej usługi, są lokalizacje w interfejsie usługi i te "znane typy".</span><span class="sxs-lookup"><span data-stu-id="023ed-294">The only types WCF will allow to be serialized or deserialized for this service are those in the service interface and these "known types".</span></span> <span data-ttu-id="023ed-295">Podjęto próbę wymiany innego typu spoza tej listy zostaną odrzucone.</span><span class="sxs-lookup"><span data-stu-id="023ed-295">Attempting to exchange any other type not in this list will be rejected.</span></span>  
  
   ```csharp
   [DataContract]  
   [KnownType(typeof(PremiumCustomer))]  
   public class Customer  
   {  
       [DataMember]  
       public string FirstName { get; set; }  
  
       [DataMember]  
       public string LastName { get; set; }  
  
       [DataMember]  
       public int CustomerId { get; set; }  
   }  
  
   [DataContract]  
   public class PremiumCustomer : Customer   
   {  
       [DataMember]  
       public int AccountId { get; set; }  
   }  
   ```  
  
3.  <span data-ttu-id="023ed-296">Następnie firma Microsoft udostępnia implementację interfejsu usługi.</span><span class="sxs-lookup"><span data-stu-id="023ed-296">Next, we provide the implementation for the service interface.</span></span>  
  
   ```csharp  
   public class CustomerService : ICustomerService  
   {  
       public Customer GetCustomer(int customerId)  
       {  
           // read from database  
       }  
  
       public bool UpdateCustomer(Customer customer)  
       {  
           // write to database  
       }  
   }  
   ```  
  
4.  <span data-ttu-id="023ed-297">Aby uruchomić usługę WCF, należy zadeklarować punktu końcowego, który uwidacznia interfejs tej usługi pod określonym adresem URL używa określonego powiązania WCF.</span><span class="sxs-lookup"><span data-stu-id="023ed-297">To run the WCF service, we need to declare an endpoint that exposes that service interface at a specific URL using a specific WCF binding.</span></span> <span data-ttu-id="023ed-298">Jest to zazwyczaj wykonywane przez dodanie sekcje do pliku web.config Projekt serwera.</span><span class="sxs-lookup"><span data-stu-id="023ed-298">This is typically done by adding the following sections to the server project’s web.config file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
5.  <span data-ttu-id="023ed-299">Następnie można uruchomić usługi WCF z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="023ed-299">The WCF service can then be started with the following code:</span></span>  
  
   ```csharp
   ServiceHost customerServiceHost = new ServiceHost(typeof(CustomerService));  
       customerServiceHost.Open();  
   ```  
  
     <span data-ttu-id="023ed-300">Po uruchomieniu tego elementu ServiceHost używa pliku web.config ustanowienie właściwego kontraktu, powiązania i punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="023ed-300">When this ServiceHost is started, it uses the web.config file to establish the proper contract, binding and endpoint.</span></span> <span data-ttu-id="023ed-301">Aby uzyskać więcej informacji o plikach konfiguracji, zobacz [Konfigurowanie usług za pomocą plików konfiguracji](./configuring-services-using-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="023ed-301">For more information about configuration files, see [Configuring Services Using Configuration Files](./configuring-services-using-configuration-files.md).</span></span> <span data-ttu-id="023ed-302">Ten styl uruchamiania serwera jest określany jako hostingu samodzielnego.</span><span class="sxs-lookup"><span data-stu-id="023ed-302">This style of starting the server is known as self-hosting.</span></span> <span data-ttu-id="023ed-303">Aby dowiedzieć się więcej na temat inne opcje hostingu usług WCF, zobacz [Hosting usług](./hosting-services.md).</span><span class="sxs-lookup"><span data-stu-id="023ed-303">To learn more about other choices for hosting WCF services, see [Hosting Services](./hosting-services.md).</span></span>  
  
6.  <span data-ttu-id="023ed-304">App.config projektu klienta należy zadeklarować pasujące informacje o powiązaniu dla punktu końcowego usługi.</span><span class="sxs-lookup"><span data-stu-id="023ed-304">The client project’s app.config must declare matching binding information for the service’s endpoint.</span></span> <span data-ttu-id="023ed-305">Najprostszym sposobem, aby to zrobić w programie Visual Studio jest użycie **Dodaj odwołanie do usługi**, które będą automatycznie zaktualizować pliku app.config.</span><span class="sxs-lookup"><span data-stu-id="023ed-305">The easiest way to do this in Visual Studio is to use **Add Service Reference**, which will automatically update the app.config file.</span></span> <span data-ttu-id="023ed-306">Alternatywnie te same zmiany mogą być dodawane ręcznie.</span><span class="sxs-lookup"><span data-stu-id="023ed-306">Alternatively, these same changes can be added manually.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="023ed-307">Aby uzyskać więcej informacji o korzystaniu z **Dodaj odwołanie do usługi**, zobacz [porady: Dodawanie, aktualizowanie lub usuwanie odwołań usługi](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span><span class="sxs-lookup"><span data-stu-id="023ed-307">For more information about using **Add Service Reference**, see [How to: Add, Update, or Remove a Service Reference](/visualstudio/data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference).</span></span>  
  
7.  <span data-ttu-id="023ed-308">Teraz można nazywamy usługi WCF z klienta.</span><span class="sxs-lookup"><span data-stu-id="023ed-308">Now we can call the WCF service from the client.</span></span> <span data-ttu-id="023ed-309">Firma Microsoft to zrobić przez tworzenie fabryki kanałów dla tej usługi, podanie kanału i bezpośrednio wywołać metodę, którą chcemy udostępnić w tym kanale.</span><span class="sxs-lookup"><span data-stu-id="023ed-309">We do this by creating a channel factory for that service, asking it for a channel, and directly calling the method we want on that channel.</span></span> <span data-ttu-id="023ed-310">Firma Microsoft może to zrobić, ponieważ kanału implementuje interfejs usługi i obsługuje podstawowej logiki żądania/odpowiedzi firmie Microsoft.</span><span class="sxs-lookup"><span data-stu-id="023ed-310">We can do this because the channel implements the service’s interface and handles the underlying request/reply logic for us.</span></span> <span data-ttu-id="023ed-311">Wartość zwrócona przez wywołanie tej metody jest zdeserializowany kopię odpowiedzi serwera.</span><span class="sxs-lookup"><span data-stu-id="023ed-311">The return value from that method call is the deserialized copy of the server’s response.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   Customer customer = service.GetCustomer(42);  
   Console.WriteLine(String.Format("  Customer {0} {1} received.",  
           customer.FirstName, customer.LastName));  
   ```  
  
 <span data-ttu-id="023ed-312">Obiekty zwrócone przez usługi WCF z serwera do klienta są zawsze przez wartość.</span><span class="sxs-lookup"><span data-stu-id="023ed-312">Objects returned by WCF from the server to the client are always by value.</span></span> <span data-ttu-id="023ed-313">Obiekty są zdeserializowany kopie danych wysłanych przez serwer.</span><span class="sxs-lookup"><span data-stu-id="023ed-313">The objects are deserialized copies of the data sent by the server.</span></span> <span data-ttu-id="023ed-314">Klienta można wywoływać metod tych kopiami lokalnymi bez zagrożenia wywoływania kod serwera za pośrednictwem wywołania zwrotne.</span><span class="sxs-lookup"><span data-stu-id="023ed-314">The client can call methods on these local copies without any danger of invoking server code through callbacks.</span></span>  
  
#### <a name="scenario-2-server-returns-an-object-by-reference"></a><span data-ttu-id="023ed-315">Scenariusz 2: Serwer zwraca obiekt przez odwołanie</span><span class="sxs-lookup"><span data-stu-id="023ed-315">Scenario 2: Server Returns an Object By Reference</span></span>  
 <span data-ttu-id="023ed-316">W tym scenariuszu pokazano serwera podajesz obiekt do klienta przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="023ed-316">This scenario demonstrates the server providing an object to the client by reference.</span></span> <span data-ttu-id="023ed-317">W funkcji zdalnych .NET, to odbywa się automatycznie dla dowolnego typu pochodnego od elementu MarshalByRefObject, która jest serializowany przez odwołanie.</span><span class="sxs-lookup"><span data-stu-id="023ed-317">In .NET Remoting, this is handled automatically for any type derived from MarshalByRefObject, which is serialized by-reference.</span></span> <span data-ttu-id="023ed-318">Przykładem tego scenariusza jest stosowanie wielu klientów niezależne obiekty zamykania po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="023ed-318">An example of this scenario is allowing multiple clients to have independent sessionful server-side objects.</span></span> <span data-ttu-id="023ed-319">Jak wcześniej wspomniano, obiekty zwrócone przez usługę WCF są zawsze wg wartości, więc ma bezpośredniego odpowiednika obiektu przez odwołanie, ale można osiągnąć podobny do przy użyciu semantyki przez odwołanie <xref:System.ServiceModel.EndpointAddress10> obiektu.</span><span class="sxs-lookup"><span data-stu-id="023ed-319">As previously mentioned, objects returned by a WCF service are always by value, so there is no direct equivalent of a by-reference object, but it is possible to achieve something similar to by-reference semantics using an <xref:System.ServiceModel.EndpointAddress10> object.</span></span> <span data-ttu-id="023ed-320">Jest to obiekt możliwy do serializacji przez wartość używaną przez klienta można uzyskać obiektu sesyjnych przez odwołania na serwerze.</span><span class="sxs-lookup"><span data-stu-id="023ed-320">This is a serializable by-value object that can be used by the client to obtain a sessionful by-reference object on the server.</span></span> <span data-ttu-id="023ed-321">Dzięki temu scenariusz o wielu klientów obiektami niezależne zamykania po stronie serwera.</span><span class="sxs-lookup"><span data-stu-id="023ed-321">This enables the scenario of having multiple clients with independent sessionful server-side objects.</span></span>  
  
1.  <span data-ttu-id="023ed-322">Najpierw musimy definiowanie kontraktu usługi WCF, która odpowiada obiekt sesyjnych.</span><span class="sxs-lookup"><span data-stu-id="023ed-322">First, we need to define a WCF service contract that corresponds to the sessionful object itself.</span></span>  
  
   ```csharp
   [ServiceContract(SessionMode = SessionMode.Allowed)]  
       public interface ISessionBoundObject  
       {  
           [OperationContract]  
           string GetCurrentValue();  
  
           [OperationContract]  
           void SetCurrentValue(string value);  
       }  
   ```  
  
    > [!TIP]
    >  <span data-ttu-id="023ed-323">Zwróć uwagę, że sesyjnych obiekt jest oznaczony atrybutem [ServiceContract], dzięki czemu zwykłym usługi WCF interfejs.</span><span class="sxs-lookup"><span data-stu-id="023ed-323">Notice that the sessionful object is marked with [ServiceContract], making it a normal WCF service interface.</span></span> <span data-ttu-id="023ed-324">Ustawienie wartość właściwości SessionMode właściwość wskazuje, że będzie on zamykania usługi.</span><span class="sxs-lookup"><span data-stu-id="023ed-324">Setting the SessionMode property indicates it will be a sessionful service.</span></span> <span data-ttu-id="023ed-325">W programie WCF sesja jest sposób korelacji wiele komunikatów przesyłanych między dwoma punktami końcowymi.</span><span class="sxs-lookup"><span data-stu-id="023ed-325">In WCF, a session is a way of correlating multiple messages sent between two endpoints.</span></span> <span data-ttu-id="023ed-326">Oznacza to, że gdy klient uzyskuje połączenie z tą usługą, sesja zostanie nawiązane między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="023ed-326">This means that once a client obtains a connection to this service, a session will be established between the client and the server.</span></span> <span data-ttu-id="023ed-327">Klient będzie używać jednego wystąpienia unikatowy obiektu po stronie serwera dla wszystkich jego interakcji w tym jednej sesji.</span><span class="sxs-lookup"><span data-stu-id="023ed-327">The client will use a single unique instance of the server-side object for all its interactions within this single session.</span></span>  
  
2.  <span data-ttu-id="023ed-328">Następnie należy udostępnić implementację tego interfejsu usługi.</span><span class="sxs-lookup"><span data-stu-id="023ed-328">Next, we need to provide the implementation of this service interface.</span></span> <span data-ttu-id="023ed-329">Określające, o [ServiceBehavior] i ustawiając właściwość InstanceContextMode, możemy stwierdzić WCF, chcemy użyć unikatowego wystąpienia tego typu dla każdej sesji.</span><span class="sxs-lookup"><span data-stu-id="023ed-329">By denoting it with [ServiceBehavior] and setting the InstanceContextMode, we tell WCF we want to use a unique instance of this type for an each session.</span></span>  
  
   ```csharp
   [ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
       public class MySessionBoundObject : ISessionBoundObject  
       {  
           private string _value;  
  
           public string GetCurrentValue()  
           {  
               return _value;  
           }  
  
           public void SetCurrentValue(string val)  
           {  
               _value = val;  
           }  
  
       }  
   ```  
  
3.  <span data-ttu-id="023ed-330">Teraz potrzebujemy sposób uzyskanie wystąpienia obiektu sesyjnych.</span><span class="sxs-lookup"><span data-stu-id="023ed-330">Now we need a way to obtain an instance of this sessionful object.</span></span> <span data-ttu-id="023ed-331">Firma Microsoft to zrobić, tworząc inny interfejs usługi WCF zwraca obiekt EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="023ed-331">We do this by creating another WCF service interface that returns an EndpointAddress10 object.</span></span> <span data-ttu-id="023ed-332">Jest to format możliwy do serializacji elementu punktu końcowego, który klient może używać do tworzenia obiektu sesyjnych.</span><span class="sxs-lookup"><span data-stu-id="023ed-332">This is a serializable form of an endpoint that the client can use to create the sessionful object.</span></span>  
  
   ```csharp
   [ServiceContract]  
       public interface ISessionBoundFactory  
       {  
           [OperationContract]  
           EndpointAddress10 GetInstanceAddress();  
       }  
   ```  
  
     <span data-ttu-id="023ed-333">I wdrożymy tę usługę WCF:</span><span class="sxs-lookup"><span data-stu-id="023ed-333">And we implement this WCF service:</span></span>  
  
   ```csharp
   public class SessionBoundFactory : ISessionBoundFactory  
       {  
           public static ChannelFactory<ISessionBoundObject> _factory =   
               new ChannelFactory<ISessionBoundObject>("sessionbound");  
 
           public SessionBoundFactory()  
           {  
           }  
  
           public EndpointAddress10 GetInstanceAddress()  
           {  
               IClientChannel channel = (IClientChannel)_factory.CreateChannel();  
               return EndpointAddress10.FromEndpointAddress(channel.RemoteAddress);  
           }  
       }  
   ```  
  
     <span data-ttu-id="023ed-334">Ta implementacja obsługuje pojedyncze fabryki kanałów do tworzenia obiektów sesyjnych.</span><span class="sxs-lookup"><span data-stu-id="023ed-334">This implementation maintains a singleton channel factory to create sessionful objects.</span></span> <span data-ttu-id="023ed-335">Po wywołaniu GetInstanceAddress() tworzy kanału i tworzy obiekt EndpointAddress10 skutecznie wskazujące zdalny adres skojarzony z tym kanale.</span><span class="sxs-lookup"><span data-stu-id="023ed-335">When GetInstanceAddress() is called, it creates a channel and creates an EndpointAddress10 object that effectively points to the remote address associated with this channel.</span></span> <span data-ttu-id="023ed-336">EndpointAddress10 jest po prostu typu danych, który może być zwracany do klienta przez wartość.</span><span class="sxs-lookup"><span data-stu-id="023ed-336">EndpointAddress10 is simply a data type that can be returned to the client by-value.</span></span>  
  
4.  <span data-ttu-id="023ed-337">Należy zmodyfikować pliku konfiguracji serwera, wykonując następujące dwie czynności, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="023ed-337">We need to modify the server’s configuration file by doing the following two things as shown in the example below:</span></span>  
  
    1.  <span data-ttu-id="023ed-338">Deklarowanie \<klienta > sekcji, która opisuje punktu końcowego dla obiektu sesyjnych.</span><span class="sxs-lookup"><span data-stu-id="023ed-338">Declare a \<client> section that describes the endpoint for the sessionful object.</span></span> <span data-ttu-id="023ed-339">Jest to konieczne, ponieważ serwer działa również jako klient w tej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="023ed-339">This is necessary because the server also acts as a client in this situation.</span></span>  
  
    2.  <span data-ttu-id="023ed-340">Deklarowanie punktów końcowych dla obiekt fabryki i sessionful.</span><span class="sxs-lookup"><span data-stu-id="023ed-340">Declare endpoints for the factory and sessionful object.</span></span> <span data-ttu-id="023ed-341">Jest to konieczne umożliwić klientom komunikowanie się z punktami końcowymi usługi, aby uzyskać EndpointAddress10 i utworzyć podczas zamykania kanału sesji.</span><span class="sxs-lookup"><span data-stu-id="023ed-341">This is necessary to allow the client to communicate with the service endpoints to acquire the EndpointAddress10 and to create the sessionful channel.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
         <client>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
        </client>  
        <services>  
          <service name="Server.CustomerService">  
            <endpoint address="http://localhost:8083/CustomerService"  
                      binding="basicHttpBinding"  
                      contract="Shared.ICustomerService" />  
          </service>  
          <service name="Server.MySessionBoundObject">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundObject"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundObject" />  
          </service>  
          <service name="Server.SessionBoundFactory">  
            <endpoint address="net.tcp://localhost:8081/SessionBoundFactory"  
                      binding="netTcpBinding"  
                      contract="Shared.ISessionBoundFactory" />  
          </service>  
        </services>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="023ed-342">A następnie można uruchomić następujące usługi:</span><span class="sxs-lookup"><span data-stu-id="023ed-342">And then we can start these services:</span></span>  
  
   ```csharp
   ServiceHost factoryHost = new ServiceHost(typeof(SessionBoundFactory));  
   factoryHost.Open();  
  
   ServiceHost sessionHost = new ServiceHost(typeof(MySessionBoundObject));  
   sessionHost.Open();  
   ```  
  
5.  <span data-ttu-id="023ed-343">Firma Microsoft Konfigurowanie klienta przez zadeklarowanie tych samym punktów końcowych w pliku app.config jego projektu.</span><span class="sxs-lookup"><span data-stu-id="023ed-343">We configure the client by declaring these same endpoints in its project’s app.config file.</span></span>  
  
    ```xml  
    <configuration>  
      <system.serviceModel>  
        <client>  
          <endpoint name="customerservice"  
                    address="http://localhost:8083/CustomerService"  
                    binding="basicHttpBinding"  
                    contract="Shared.ICustomerService"/>  
          <endpoint name="sessionbound"  
                    address="net.tcp://localhost:8081/SessionBoundObject"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundObject"/>  
          <endpoint name="factory"  
                    address="net.tcp://localhost:8081/SessionBoundFactory"  
                    binding="netTcpBinding"  
                    contract="Shared.ISessionBoundFactory"/>  
        </client>  
      </system.serviceModel>  
    </configuration>  
    ```  
  
6.  <span data-ttu-id="023ed-344">W celu tworzenia i używania tego obiektu zamykania, klienta należy wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="023ed-344">In order to create and use this sessionful object, the client must do the following steps:</span></span>  
  
    1.  <span data-ttu-id="023ed-345">Tworzenie kanału do usługi ISessionBoundFactory.</span><span class="sxs-lookup"><span data-stu-id="023ed-345">Create a channel to the ISessionBoundFactory service.</span></span>  
  
    2.  <span data-ttu-id="023ed-346">Użyj tego kanału do wywołania tej usługi, aby uzyskać EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="023ed-346">Use that channel to invoke that service to obtain an EndpointAddress10.</span></span>  
  
    3.  <span data-ttu-id="023ed-347">EndpointAddress10 umożliwia tworzenie kanału można uzyskać obiektu sesyjnych.</span><span class="sxs-lookup"><span data-stu-id="023ed-347">Use the EndpointAddress10 to create a channel to obtain a sessionful object.</span></span>  
  
    4.  <span data-ttu-id="023ed-348">Interakcje z obiektu sesyjnych wykazanie, że to samo wystąpienie pozostaje w wielu wywołań.</span><span class="sxs-lookup"><span data-stu-id="023ed-348">Interact with the sessionful object to demonstrate it remains the same instance across multiple calls.</span></span>  
  
   ```csharp
   ChannelFactory<ISessionBoundFactory> channelFactory =   
       new ChannelFactory<ISessionBoundFactory>("factory");  
   ISessionBoundFactory sessionFactory = channelFactory.CreateChannel();  
  
   EndpointAddress10 address1 = sessionFactory.GetInstanceAddress();  
   EndpointAddress10 address2 = sessionFactory.GetInstanceAddress();  
  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory1 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address1.ToEndpointAddress());  
   ChannelFactory<ISessionBoundObject> sessionObjectFactory2 =   
       new ChannelFactory<ISessionBoundObject>(new NetTcpBinding(),   
                                               address2.ToEndpointAddress());  
  
   ISessionBoundObject sessionInstance1 = sessionObjectFactory1.CreateChannel();  
   ISessionBoundObject sessionInstance2 = sessionObjectFactory2.CreateChannel();  
  
   sessionInstance1.SetCurrentValue("Hello");  
   sessionInstance2.SetCurrentValue("World");  
  
   if (sessionInstance1.GetCurrentValue() == "Hello" &&  
       sessionInstance2.GetCurrentValue() == "World")  
   {  
       Console.WriteLine("sessionful server object works as expected");  
   }  
   ```  
  
 <span data-ttu-id="023ed-349">Usługi WCF zawsze zwraca obiekty według wartości, ale istnieje możliwość obsługi odpowiednikiem semantyki przez odwołanie za pośrednictwem EndpointAddress10.</span><span class="sxs-lookup"><span data-stu-id="023ed-349">WCF always returns objects by value, but it is possible to support the equivalent of by-reference semantics through the use of EndpointAddress10.</span></span> <span data-ttu-id="023ed-350">Umożliwia klientowi żądanie sesyjnych wystąpienie usługi WCF, po którym może współdziałać z nim podobnie jak inne usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="023ed-350">This permits the client to request a sessionful WCF service instance, after which it can interact with it like any other WCF service.</span></span>  
  
#### <a name="scenario-3-client-sends-server-a-by-value-instance"></a><span data-ttu-id="023ed-351">Scenariusz 3: Klient wysyła serwera wystąpienia przez wartość</span><span class="sxs-lookup"><span data-stu-id="023ed-351">Scenario 3: Client Sends Server a By-Value Instance</span></span>  
 <span data-ttu-id="023ed-352">W tym scenariuszu pokazano klienta, wysyłanie wystąpienia obiektu innego niż pierwotny do serwera przez wartość.</span><span class="sxs-lookup"><span data-stu-id="023ed-352">This scenario demonstrates the client sending a non-primitive object instance to the server by value.</span></span> <span data-ttu-id="023ed-353">Ponieważ WCF wysyła tylko obiekty według wartości, w tym scenariuszu pokazano normalnego użycia WCF.</span><span class="sxs-lookup"><span data-stu-id="023ed-353">Because WCF only sends objects by value, this scenario demonstrates normal WCF usage.</span></span>  
  
1.  <span data-ttu-id="023ed-354">Użyj tej samej usługi WCF z scenariusz 1.</span><span class="sxs-lookup"><span data-stu-id="023ed-354">Use the same WCF Service from Scenario 1.</span></span>  
  
2.  <span data-ttu-id="023ed-355">Aby utworzyć nowy obiekt przez wartość (klienta), tworzenie kanału do komunikacji z usługą ICustomerService i wysłać do niego obiekt, użyj klienta.</span><span class="sxs-lookup"><span data-stu-id="023ed-355">Use the client to create a new by-value object (Customer), create a channel to communicate with the ICustomerService service, and send the object to it.</span></span>  
  
   ```csharp
   ChannelFactory<ICustomerService> factory =  
       new ChannelFactory<ICustomerService>("customerservice");  
   ICustomerService service = factory.CreateChannel();  
   PremiumCustomer customer = new PremiumCustomer {   
   FirstName = "Bob",   
   LastName = "Jones",   
   CustomerId = 43,   
   AccountId = 99};  
   bool success = service.UpdateCustomer(customer);  
   Console.WriteLine(String.Format("  Server returned {0}.", success));  
   ```  
  
     <span data-ttu-id="023ed-356">Obiekt klienta będą serializowane i wysyłane na serwer, gdzie jest ona przeprowadzona deserializacja nową kopię tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="023ed-356">The customer object will be serialized, and sent to the server, where it is deserialized into a new copy of that object.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="023ed-357">Ten kod przedstawia również wysyłanie typu pochodnego (PremiumCustomer).</span><span class="sxs-lookup"><span data-stu-id="023ed-357">This code also illustrates sending a derived type (PremiumCustomer).</span></span> <span data-ttu-id="023ed-358">Interfejs usługi oczekuje obiektu klienta, ale atrybutu [KnownType] do klasy odbiorcy wskazał PremiumCustomer również jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="023ed-358">The service interface expects a Customer object, but the [KnownType] attribute on the Customer class indicated PremiumCustomer was also allowed.</span></span> <span data-ttu-id="023ed-359">Usługi WCF nie powiedzie się próba serializacji lub deserializacji innego typu, za pośrednictwem tego interfejsu usługi.</span><span class="sxs-lookup"><span data-stu-id="023ed-359">WCF will fail any attempt to serialize or deserialize any other type through this service interface.</span></span>  
  
 <span data-ttu-id="023ed-360">Normalny WCF wymiany danych są przez wartość.</span><span class="sxs-lookup"><span data-stu-id="023ed-360">Normal WCF exchanges of data are by value.</span></span> <span data-ttu-id="023ed-361">Gwarantuje to, że wywoływanie metod na jednym z tych obiektów danych jest wykonywana tylko lokalnie — nie wywoła kodu na innej warstwie.</span><span class="sxs-lookup"><span data-stu-id="023ed-361">This guarantees that invoking methods on one of these data objects executes only locally – it will not invoke code on the other tier.</span></span> <span data-ttu-id="023ed-362">Gdy jest możliwość osiągnięcia przypominać zwracanych obiektów przez odwołanie *z* serwera, nie jest możliwe dla klienta w celu przekazania obiektu przez odwołanie *do* serwera.</span><span class="sxs-lookup"><span data-stu-id="023ed-362">While it is possible to achieve something like by-reference objects returned *from* the server, it is not possible for a client to pass a by-reference object *to* the server.</span></span> <span data-ttu-id="023ed-363">Scenariusz, który wymaga konwersacji i z powrotem między klientem i serwerem można osiągnąć w programie WCF, za pomocą usługi duplex.</span><span class="sxs-lookup"><span data-stu-id="023ed-363">A scenario that requires a conversation back and forth between client and server can be achieved in WCF using a duplex service.</span></span> <span data-ttu-id="023ed-364">Aby uzyskać więcej informacji, zobacz [usługi dwukierunkowe](./feature-details/duplex-services.md).</span><span class="sxs-lookup"><span data-stu-id="023ed-364">For more information, see [Duplex Services](./feature-details/duplex-services.md).</span></span>  
  
## <a name="summary"></a><span data-ttu-id="023ed-365">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="023ed-365">Summary</span></span>  
 <span data-ttu-id="023ed-366">.NET remoting to platforma komunikacji przeznaczony do użycia tylko w pełni zaufanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="023ed-366">.NET Remoting is a communication framework intended to be used only within fully-trusted environments.</span></span> <span data-ttu-id="023ed-367">Starszy produkt i jest obsługiwana tylko w przypadku zgodności z poprzednimi wersjami.</span><span class="sxs-lookup"><span data-stu-id="023ed-367">It is a legacy product and supported only for backward compatibility.</span></span> <span data-ttu-id="023ed-368">Nie można stosować do tworzenia nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="023ed-368">It should not be used to build new applications.</span></span> <span data-ttu-id="023ed-369">Z drugiej strony WCF została zaprojektowana z myślą o bezpieczeństwie i jest zalecany dla nowych i istniejących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="023ed-369">Conversely, WCF was designed with security in mind and is recommended for new and existing applications.</span></span> <span data-ttu-id="023ed-370">Firma Microsoft zaleca się, czy istniejące aplikacji usług zdalnych można migrować zamiast tego użyć WCF lub interfejsu API sieci Web platformy ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="023ed-370">Microsoft recommends that existing Remoting applications be migrated to use WCF or ASP.NET Web API instead.</span></span>