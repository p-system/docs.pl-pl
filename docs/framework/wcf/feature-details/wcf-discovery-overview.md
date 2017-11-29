---
title: "Omówienie odnajdywania WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
caps.latest.revision: "21"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1afd3d94ceb3389a7d87528371925120f3c92764
ms.sourcegitcommit: e99dfadbca1992c187179b6a3b42bef44534ebb6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2017
---
# <a name="wcf-discovery-overview"></a><span data-ttu-id="742b2-102">Omówienie odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="742b2-102">WCF Discovery Overview</span></span>
<span data-ttu-id="742b2-103">Interfejsy API wykrywania zapewnienia ujednoliconego modelu programowania dynamiczne publikacji i odnajdywania usług sieci Web za pomocą protokołu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="742b2-103">The Discovery APIs provide a unified programming model for the dynamic publication and discovery of Web services using the WS-Discovery protocol.</span></span> <span data-ttu-id="742b2-104">Te interfejsy API umożliwiają usług do publikowania się i klientom znalezienie usług opublikowanych.</span><span class="sxs-lookup"><span data-stu-id="742b2-104">These APIs allow services to publish themselves and clients to find published services.</span></span> <span data-ttu-id="742b2-105">Gdy usługa następuje wykrywalny, usługa ma możliwość wysyłać powiadomienia, a także nasłuchiwania i odpowiadać na żądania odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="742b2-105">Once a service is made discoverable, the service has the ability to send announcement messages as well as listen for and respond to discovery requests.</span></span> <span data-ttu-id="742b2-106">Wykrywalny usług można wysyłać wiadomości powitania ogłaszamy przybyciu w sieci i komunikaty Bye poinformować ich wyjścia z sieci.</span><span class="sxs-lookup"><span data-stu-id="742b2-106">Discoverable services can send Hello messages to announce their arrival on a network and Bye messages to announce their departure from a network.</span></span> <span data-ttu-id="742b2-107">Aby znaleźć usługi, klienci wysyłają `Probe` żądania, która zawiera określone kryteria, takie jak typ kontraktu usługi, słowa kluczowe i zakresem w sieci.</span><span class="sxs-lookup"><span data-stu-id="742b2-107">To find a service, clients send a `Probe` request that contains specific criteria such as service contract type, keywords, and scope on the network.</span></span> <span data-ttu-id="742b2-108">Odbieranie usług `Probe` żądania i ustalić, czy odpowiadają one kryteriom.</span><span class="sxs-lookup"><span data-stu-id="742b2-108">Services receive the `Probe` request and determine whether they match the criteria.</span></span> <span data-ttu-id="742b2-109">Usługa zgodna, odpowiadały wysyłając `ProbeMatch` wiadomość do klienta informacje niezbędne do kontaktu z usługą.</span><span class="sxs-lookup"><span data-stu-id="742b2-109">If a service matches, it responds by sending a `ProbeMatch` message back to the client with the information necessary to contact the service.</span></span> <span data-ttu-id="742b2-110">Klienci mogą również wysyłać `Resolve` żądania, dzięki czemu można znaleźć usługi, które mogą zmienić swój adres punktu końcowego.</span><span class="sxs-lookup"><span data-stu-id="742b2-110">Clients can also send `Resolve` requests that allow them to find services that may have changed their endpoint address.</span></span> <span data-ttu-id="742b2-111">Usługi pasującego odpowiadanie na `Resolve` żądań wysyłając `ResolveMatch` wiadomość do klienta.</span><span class="sxs-lookup"><span data-stu-id="742b2-111">Matching services respond to `Resolve` requests by sending a `ResolveMatch` message back to the client.</span></span>  
  
## <a name="ad-hoc-and-managed-modes"></a><span data-ttu-id="742b2-112">Tryby zarządzanych i Ad Hoc</span><span class="sxs-lookup"><span data-stu-id="742b2-112">Ad-Hoc and Managed Modes</span></span>  
 <span data-ttu-id="742b2-113">Interfejs API Discovery obsługuje dwa różne tryby: zarządzane i Ad Hoc.</span><span class="sxs-lookup"><span data-stu-id="742b2-113">The Discovery API supports two different modes: Managed and Ad-Hoc.</span></span> <span data-ttu-id="742b2-114">Zarządzany tryb jest centralny serwer o nazwie serwera proxy odnajdywania, która zawiera informacje o dostępnych usług.</span><span class="sxs-lookup"><span data-stu-id="742b2-114">In Managed mode there is a centralized server called a discovery proxy that maintains information about available services.</span></span> <span data-ttu-id="742b2-115">Serwera proxy odnajdywania można wypełniać za pomocą informacji o usługach na różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="742b2-115">The discovery proxy can be populated with information about services in a variety of ways.</span></span> <span data-ttu-id="742b2-116">Na przykład usługi może wysyłać komunikaty anonsów podczas uruchamiania serwera proxy odnajdywania lub serwer proxy może odczytywać dane z bazy danych lub plik konfiguracji w celu ustalenia, jakie usługi są dostępne.</span><span class="sxs-lookup"><span data-stu-id="742b2-116">For example, services can send announcement messages during start up to the discovery proxy or the proxy may read data from a database or a configuration file to determine what services are available.</span></span> <span data-ttu-id="742b2-117">Jak jest wypełniana serwera proxy odnajdywania zależy całkowicie dewelopera.</span><span class="sxs-lookup"><span data-stu-id="742b2-117">How the discovery proxy is populated is completely up to the developer.</span></span> <span data-ttu-id="742b2-118">Klienci używają serwera proxy odnajdywania można pobrać informacji o dostępnych usług.</span><span class="sxs-lookup"><span data-stu-id="742b2-118">Clients use the discovery proxy to retrieve information about available services.</span></span> <span data-ttu-id="742b2-119">Gdy klient szuka usługi go wysyła `Probe` wiadomość do serwera proxy odnajdywania i serwer proxy Określa, czy którakolwiek z nich bez informacji o zgodne Usługa klienta jest wyszukiwanie.</span><span class="sxs-lookup"><span data-stu-id="742b2-119">When a client searches for a service it sends a `Probe` message to the discovery proxy and the proxy determines whether any of the services it knows about match the service the client is searching for.</span></span> <span data-ttu-id="742b2-120">Jeśli ma dopasowania wysyła serwera proxy odnajdywania `ProbeMatch` odpowiedź z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="742b2-120">If there are matches the discovery proxy sends a `ProbeMatch` response back to the client.</span></span> <span data-ttu-id="742b2-121">Klient może następnie skontaktować się z usługą, bezpośrednio za pomocą usługi informacje zwrócone z serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="742b2-121">The client can then contact the service directly using the service information returned from the proxy.</span></span> <span data-ttu-id="742b2-122">Zasada klucza za zarządzany tryb jest, że żądania odnajdywania są wysyłane w sposób emisji pojedynczej do jednego urzędu certyfikacji, serwera proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="742b2-122">The key principle behind Managed mode is that the discovery requests are sent in a unicast manner to one authority, the discovery proxy.</span></span> <span data-ttu-id="742b2-123">.NET Framework zawiera najważniejsze składniki, które pozwalają na tworzenie własnego serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="742b2-123">The .NET Framework contains key components that allow you to build your own proxy.</span></span> <span data-ttu-id="742b2-124">Klienci i usługi można zlokalizować serwera proxy przez wiele metod:</span><span class="sxs-lookup"><span data-stu-id="742b2-124">Clients and services can locate the proxy by multiple methods:</span></span>  
  
-   <span data-ttu-id="742b2-125">Serwer proxy może odpowiadać na komunikaty ad hoc.</span><span class="sxs-lookup"><span data-stu-id="742b2-125">The proxy can respond to ad-hoc messages.</span></span>  
  
-   <span data-ttu-id="742b2-126">Serwer proxy można Wyślij anonse podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="742b2-126">The proxy can send an announcement message during start up.</span></span>  
  
-   <span data-ttu-id="742b2-127">Aby wyszukać określonego dobrze znanego punktu końcowego można pisać klientów i usług.</span><span class="sxs-lookup"><span data-stu-id="742b2-127">Clients and services can be written to look for a specific well-known endpoint.</span></span>  
  
 <span data-ttu-id="742b2-128">W trybie Ad-Hoc serwer nie jest scentralizowane.</span><span class="sxs-lookup"><span data-stu-id="742b2-128">In Ad-Hoc mode, there is no centralized server.</span></span> <span data-ttu-id="742b2-129">Wszystkie komunikaty odnajdywania, takie jak Anonse usługi i żądania klientów są wysyłane w sposób multiemisji.</span><span class="sxs-lookup"><span data-stu-id="742b2-129">All discovery messages such as service announcements and client requests are sent in a multicast fashion.</span></span> <span data-ttu-id="742b2-130">Domyślnie programu .NET Framework obsługuje odnajdywania Ad Hoc za pośrednictwem protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="742b2-130">By default the .NET Framework contains support for Ad-Hoc discovery over the UDP protocol.</span></span> <span data-ttu-id="742b2-131">Na przykład jeśli usługa jest skonfigurowana do wysłania powiadomienia Hello przy uruchamianiu, wysyła on za pośrednictwem adresu dobrze znane, multiemisji przy użyciu protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="742b2-131">For example, if a service is configured to send out a Hello announcement on start up, it sends it out over a well-known, multicast address using the UDP protocol.</span></span> <span data-ttu-id="742b2-132">Klienci muszą aktywnie nasłuchiwania ogłoszenia i odpowiednio je przetworzyć.</span><span class="sxs-lookup"><span data-stu-id="742b2-132">Clients have to actively listen for these announcements and process them accordingly.</span></span> <span data-ttu-id="742b2-133">Gdy klient wyśle `Probe` komunikatu dla usługi są wysyłane za pośrednictwem sieci przy użyciu multiemisji protokołu.</span><span class="sxs-lookup"><span data-stu-id="742b2-133">When a client sends a `Probe` message for a service it is sent over the network using a multicast protocol.</span></span> <span data-ttu-id="742b2-134">Każda usługa, która odbiera żądanie określa, czy spełnia on kryteria `Probe` wiadomości i odpowiada bezpośrednio do klienta z `ProbeMatch` komunikatów, jeśli usługa jest zgodna z kryteriami `Probe` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="742b2-134">Each service that receives the request determines whether it matches the criteria in the `Probe` message and responds directly to the client with a `ProbeMatch` message if the service matches the criteria specified in the `Probe` message.</span></span>  
  
## <a name="benefits-of-using-wcf-discovery"></a><span data-ttu-id="742b2-135">Zalety używania odnajdywania WCF</span><span class="sxs-lookup"><span data-stu-id="742b2-135">Benefits of Using WCF Discovery</span></span>  
 <span data-ttu-id="742b2-136">Ponieważ odnajdywania WCF jest implementowane za pomocą protokołu WS-Discovery jest współpraca z innymi klientami, usług i serwerów proxy, które również implementują WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="742b2-136">Because WCF Discovery is implemented using the WS-Discovery protocol it is interoperable with other clients, services, and proxies that implement WS-Discovery as well.</span></span> <span data-ttu-id="742b2-137">Odnajdywania WCF jest oparty na istniejących API WCF, która ułatwia dodawanie funkcji odnajdywania do istniejących usług i klientów.</span><span class="sxs-lookup"><span data-stu-id="742b2-137">WCF Discovery is built upon the existing WCF APIs, which makes it easy to add Discovery functionality to your existing services and clients.</span></span> <span data-ttu-id="742b2-138">Odnajdowanie usługi można łatwo dodać za pomocą ustawienia konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="742b2-138">Service discoverability can be easily added through the application configuration settings.</span></span> <span data-ttu-id="742b2-139">Ponadto odnajdywania WCF obsługuje również, przy użyciu protokołu odnajdowania za pośrednictwem innych transportów, takie jak sieci równorzędnej, nazewnictwa nakładce i HTTP.</span><span class="sxs-lookup"><span data-stu-id="742b2-139">In addition, WCF Discovery also supports using the discovery protocol over other transports such as peer net, naming overlay, and HTTP.</span></span> <span data-ttu-id="742b2-140">Odnajdywania WCF zapewnia obsługę zarządzany tryb działania, w których jest używany serwer proxy odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="742b2-140">WCF Discovery provides support for a Managed mode of operation where a discovery proxy is used.</span></span> <span data-ttu-id="742b2-141">To zmniejszenie ruchu w sieci, ponieważ komunikaty są wysyłane bezpośrednio do serwera proxy odnajdywania zamiast wysyłać komunikatów multiemisji do całej sieci.</span><span class="sxs-lookup"><span data-stu-id="742b2-141">This can reduce network traffic as messages are sent directly to the discovery proxy instead of sending multicast messages to the entire network.</span></span> <span data-ttu-id="742b2-142">Odnajdywania WCF umożliwia również większą elastyczność podczas pracy z usługami sieci Web.</span><span class="sxs-lookup"><span data-stu-id="742b2-142">WCF Discovery also allows for more flexibility when working with Web services.</span></span> <span data-ttu-id="742b2-143">Na przykład można zmienić adres usługi bez konieczności ponownej konfiguracji klienta lub usługi.</span><span class="sxs-lookup"><span data-stu-id="742b2-143">For example, you can change the address of a service without having to reconfigure the client or the service.</span></span> <span data-ttu-id="742b2-144">Gdy klient musi uzyskać dostęp do usługi, pozwala na wydawanie `Probe` komunikatu za pośrednictwem `Find` żądania i oczekują usługi z bieżącego adresu.</span><span class="sxs-lookup"><span data-stu-id="742b2-144">When a client must access the service it can issue a `Probe` message through a `Find` request and expect the service to respond with its current address.</span></span> <span data-ttu-id="742b2-145">Odnajdywania WCF umożliwia klientowi wyszukiwania na podstawie różnych kryteriów, takich jak typy kontraktu, elementy powiązania, przestrzeni nazw, zakresu oraz słowa kluczowe i numery wersji usługi.</span><span class="sxs-lookup"><span data-stu-id="742b2-145">WCF Discovery allows a client to search for a service based on different criteria including contract types, binding elements, namespace, scope, and keywords or version numbers.</span></span> <span data-ttu-id="742b2-146">Odnajdywania WCF umożliwia odnajdywanie czasu środowiska uruchomieniowego i projektu.</span><span class="sxs-lookup"><span data-stu-id="742b2-146">WCF Discovery enables runtime and design time discovery.</span></span> <span data-ttu-id="742b2-147">Dodawanie odnajdywania aplikacji można włączyć inne scenariusze, takie jak odporność na uszkodzenia i konfiguracji automatycznej.</span><span class="sxs-lookup"><span data-stu-id="742b2-147">Adding discovery to your application can be used to enable other scenarios such as fault tolerance and auto configuration.</span></span>  
  
## <a name="service-publication"></a><span data-ttu-id="742b2-148">Usługa publikacji</span><span class="sxs-lookup"><span data-stu-id="742b2-148">Service Publication</span></span>  
 <span data-ttu-id="742b2-149">Aby usługa wykrywalny, <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> musi zostać dodany do hosta usługi i odnajdywanie punktu końcowego musi zostać dodany do określ, gdzie nasłuchiwać komunikatów odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="742b2-149">To make a service discoverable, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> must be added to the service host and a discovery endpoint must be added to specify where to listen for discovery messages.</span></span> <span data-ttu-id="742b2-150">Poniższy przykład kodu pokazuje, jak samodzielnie hostowana usługa może być modyfikowany w taki sposób, aby był wykrywalny.</span><span class="sxs-lookup"><span data-stu-id="742b2-150">The following code example shows how a self-hosted service can be modified to make it discoverable.</span></span>  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",  
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
 <span data-ttu-id="742b2-151">A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> wystąpienie musi zostać dodany do opisu usługi do być wykrywalny przez usługę.</span><span class="sxs-lookup"><span data-stu-id="742b2-151">A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance must be added to a service description for the service to be discoverable.</span></span> <span data-ttu-id="742b2-152">A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> wystąpienie musi zostać dodany do na informują usługa skąd do nasłuchiwania żądań odnajdywania usługi hosta.</span><span class="sxs-lookup"><span data-stu-id="742b2-152">A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance must be added to the service host to tell the service where to listen for discovery requests.</span></span> <span data-ttu-id="742b2-153">W tym przykładzie <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (która jest pochodną <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) jest dodawany do określenia, czy usługa powinna nasłuchiwać żądań odnajdywania za pośrednictwem protokołu UDP multiemisji transportu.</span><span class="sxs-lookup"><span data-stu-id="742b2-153">In this example, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (which is derived from <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) is added to specify that the service should listen for discovery requests over the UDP multicast transport.</span></span> <span data-ttu-id="742b2-154"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> Służy do odnajdowania Ad-Hoc, ponieważ wszystkie komunikaty są wysyłane w sposób multiemisji.</span><span class="sxs-lookup"><span data-stu-id="742b2-154">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is used for Ad-Hoc discovery because all messages are sent in a multicast fashion.</span></span>  
  
## <a name="announcement"></a><span data-ttu-id="742b2-155">Anonsu</span><span class="sxs-lookup"><span data-stu-id="742b2-155">Announcement</span></span>  
 <span data-ttu-id="742b2-156">Domyślnie usługi publikacji nie wysyła wiadomości powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="742b2-156">By default, service publication does not send out announcement messages.</span></span> <span data-ttu-id="742b2-157">Usługa musi być skonfigurowana do wysyłania wiadomości powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="742b2-157">The service must be configured to send out announcement messages.</span></span> <span data-ttu-id="742b2-158">Zapewnia to większą elastyczność moduły zapisujące usługi ponieważ one ogłaszamy usługi niezależnie od nasłuchiwanie komunikatów odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="742b2-158">This provides additional flexibility for service writers because they can announce the service separately from listening for discovery messages.</span></span> <span data-ttu-id="742b2-159">Powiadomienia usługi również może służyć jako mechanizm rejestrowania usług za pomocą serwera proxy odnajdywania lub innych rejestrów usługi.</span><span class="sxs-lookup"><span data-stu-id="742b2-159">Service announcement can also be used as a mechanism for registering services with a discovery proxy or other service registries.</span></span> <span data-ttu-id="742b2-160">Poniższy kod przedstawia sposób konfigurowania usługi do wysłania komunikatów Anons powiązania protokołu UDP.</span><span class="sxs-lookup"><span data-stu-id="742b2-160">The following code shows how to configure a service to send announcement messages over a UDP binding.</span></span>  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // Send announcements on UDP multicast transport
    discoveryBehavior.AnnouncementEndpoints.Add(
      new UdpAnnouncementEndpoint());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.Description.Endpoints.Add(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
## <a name="service-discovery"></a><span data-ttu-id="742b2-161">Odnajdowanie usługi</span><span class="sxs-lookup"><span data-stu-id="742b2-161">Service Discovery</span></span>  
 <span data-ttu-id="742b2-162">Można użyć aplikacji klienckiej <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy można znaleźć usługi.</span><span class="sxs-lookup"><span data-stu-id="742b2-162">A client application can use the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to find services.</span></span> <span data-ttu-id="742b2-163">Deweloper tworzy wystąpienie <xref:System.ServiceModel.Discovery.DiscoveryClient> klasy, która przekazuje w odnajdowania punktu końcowego, który określa, który ma zostać wysłana `Probe` lub `Resolve` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="742b2-163">The developer creates an instance of the <xref:System.ServiceModel.Discovery.DiscoveryClient> class that passes in a discovery endpoint that specifies where to send `Probe` or `Resolve` messages.</span></span> <span data-ttu-id="742b2-164">Klient następnie wywołuje <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> , który określa kryteria wyszukiwania w <xref:System.ServiceModel.Discovery.FindCriteria> wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="742b2-164">The client then calls <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> that specifies search criteria within a <xref:System.ServiceModel.Discovery.FindCriteria> instance.</span></span> <span data-ttu-id="742b2-165">W przypadku znalezienia pasujących usług <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> zwraca kolekcję <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>.</span><span class="sxs-lookup"><span data-stu-id="742b2-165">If matching services are found, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> returns a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>.</span></span> <span data-ttu-id="742b2-166">Poniższy kod przedstawia sposób wywołania `Find` metody, a następnie połączyć się z usługą odnalezione.</span><span class="sxs-lookup"><span data-stu-id="742b2-166">The following code shows how to call the `Find` method and then connect to a discovered service.</span></span>  
  
```csharp  
class Client
{
    static EndpointAddress serviceAddress;
  
    static void Main()
    {  
        if (FindService()) 
        {
            InvokeService();
        }
    }  
  
    // ** DISCOVERY ** //  
    static bool FindService()  
    {  
        Console.WriteLine("\nFinding Calculator Service ..");  
        DiscoveryClient discoveryClient =   
            new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
        Collection<EndpointDiscoveryMetadata> calculatorServices =   
            (Collection<EndpointDiscoveryMetadata>)discoveryClient.Find(new FindCriteria(typeof(ICalculator))).Endpoints;  
  
        discoveryClient.Close();  
  
        if (calculatorServices.Count == 0)  
        {  
            Console.WriteLine("\nNo services are found.");  
            return false;  
        }  
        else  
        {  
            serviceAddress = calculatorServices[0].Address;  
            return true;  
        }  
    }  
  
    static void InvokeService()  
    {  
        Console.WriteLine("\nInvoking Calculator Service at {0}\n", serviceAddress);  
  
        // Create a client  
        CalculatorClient client = new CalculatorClient();  
        client.Endpoint.Address = serviceAddress;  
        client.Add(10,3);  
    }
}  
```  
  
## <a name="discovery-and-message-level-security"></a><span data-ttu-id="742b2-167">Odnajdywanie i zabezpieczeń na poziomie komunikatu</span><span class="sxs-lookup"><span data-stu-id="742b2-167">Discovery and Message Level Security</span></span>  
 <span data-ttu-id="742b2-168">Korzystając z zabezpieczeniami na poziomie wiadomości jest niezbędne do określenia <xref:System.ServiceModel.EndpointIdentity> na punkt końcowy odnajdowania usługi i odpowiadający mu <xref:System.ServiceModel.EndpointIdentity> odnajdywania klienta w punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="742b2-168">When using message level security it is necessary to specify an <xref:System.ServiceModel.EndpointIdentity> on the service discovery endpoint and a matching <xref:System.ServiceModel.EndpointIdentity> on the client discovery endpoint.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="742b2-169">poziom zabezpieczeń, zobacz [zabezpieczenia komunikatów](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="742b2-169"> message level security, see [Message Security](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>  
  
## <a name="discovery-and-web-hosted-services"></a><span data-ttu-id="742b2-170">Odnajdywanie i sieci Web usług hostowanych</span><span class="sxs-lookup"><span data-stu-id="742b2-170">Discovery and Web Hosted Services</span></span>  
 <span data-ttu-id="742b2-171">Aby usługi WCF być wykrywalny musi być uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="742b2-171">In order for WCF services to be discoverable they must be running.</span></span> <span data-ttu-id="742b2-172">Usługi WCF hostowanej przez usługi IIS lub WAS nie uruchamiaj do usług IIS / WAS odbiera komunikat przeznaczony dla usługi, dlatego nie może być wykrywalny domyślnie.</span><span class="sxs-lookup"><span data-stu-id="742b2-172">WCF services hosted under IIS or WAS do not run until IIS/WAS receives a message bound for the service, so they cannot be discoverable by default.</span></span>  <span data-ttu-id="742b2-173">Dostępne są dwie opcje do wprowadzania wykrywalny usług hostowanych w sieci Web:</span><span class="sxs-lookup"><span data-stu-id="742b2-173">There are two options for making Web-Hosted services discoverable:</span></span>  
  
1.  <span data-ttu-id="742b2-174">Funkcja Auto-Start systemu Windows Server AppFabric</span><span class="sxs-lookup"><span data-stu-id="742b2-174">Use the Windows Server AppFabric Auto-Start feature</span></span>  
  
2.  <span data-ttu-id="742b2-175">Użyj serwera proxy odnajdywania do komunikacji w imieniu usługi</span><span class="sxs-lookup"><span data-stu-id="742b2-175">Use a discovery proxy to communicate on behalf of the service</span></span>  
  
 <span data-ttu-id="742b2-176">Windows Server AppFabric ma funkcję automatycznego uruchamiania, która umożliwi usługa ma zostać uruchomiony przed otrzymaniem komunikaty.</span><span class="sxs-lookup"><span data-stu-id="742b2-176">Windows Server AppFabric has an Auto-Start feature that will allow a service to be started before receiving any messages.</span></span> <span data-ttu-id="742b2-177">Auto-Start ustawiona, usługi IIS / WAS hostowanej usługi można skonfigurować w celu być wykrywalny.</span><span class="sxs-lookup"><span data-stu-id="742b2-177">With this Auto-Start set, an IIS/WAS hosted service can be configured to be discoverable.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="742b2-178">Automatyczne uruchamianie funkcji, zobacz [systemu Windows Server AppFabric automatycznego uruchamiania funkcji](http://go.microsoft.com/fwlink/?LinkId=205545).</span><span class="sxs-lookup"><span data-stu-id="742b2-178"> the Auto-Start feature see, [Windows Server AppFabric Auto-Start Feature](http://go.microsoft.com/fwlink/?LinkId=205545).</span></span> <span data-ttu-id="742b2-179">Wraz z włączenie funkcji automatycznego uruchamiania, należy skonfigurować usługę odnajdywania.</span><span class="sxs-lookup"><span data-stu-id="742b2-179">Along with turning on the Auto-Start feature, you must configure the service for discovery.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="742b2-180">[Porady: programowane Dodawanie możliwości odnajdywania do usługi WCF i klienta](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[konfigurowania odnajdywania w pliku konfiguracyjnym](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="742b2-180"> [How to: Programmatically Add Discoverability to a WCF Service and Client](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[Configuring Discovery in a Configuration File](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).</span></span>  
  
 <span data-ttu-id="742b2-181">Serwer proxy odnajdywania może służyć do komunikacji imieniu usług WCF, gdy usługa nie jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="742b2-181">A discovery proxy can be used to communicate on behalf of the WCF service when the service is not running.</span></span> <span data-ttu-id="742b2-182">Serwer proxy można nasłuchiwać sondy lub rozwiązać wiadomości i odpowiedzi do klienta.</span><span class="sxs-lookup"><span data-stu-id="742b2-182">The proxy can listen for probe or resolve messages and respond to the client.</span></span> <span data-ttu-id="742b2-183">Klient następnie może wysyłać komunikaty bezpośrednio do usługi.</span><span class="sxs-lookup"><span data-stu-id="742b2-183">The client can then send messages directly to the service.</span></span> <span data-ttu-id="742b2-184">Gdy klient wysyła komunikat do usługi będzie można wdrożyć odpowiedzieć na wiadomość.</span><span class="sxs-lookup"><span data-stu-id="742b2-184">When the client sends a message to the service it will be instantiated to respond to the message.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="742b2-185">Wdrażanie serwera proxy odnajdywania zobacz [Implementowanie serwera Proxy odnajdywania](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).</span><span class="sxs-lookup"><span data-stu-id="742b2-185"> implementing a discovery proxy see, [Implementing a Discovery Proxy](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="742b2-186">Do odnajdywania WCF działał prawidłowo wszystkie karty sieciowe (kontrolera interfejsu sieciowego) powinien mieć tylko 1 adres IP.</span><span class="sxs-lookup"><span data-stu-id="742b2-186">For WCF Discovery to work correctly, all NICs (Network Interface Controller) should only have 1 IP address.</span></span>