---
title: "Niestandardowy dyspozytor kanału"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 81512576e1d26b63cf65b3a0c9992c2d273d2779
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="custom-channel-dispatcher"></a><span data-ttu-id="87278-102">Niestandardowy dyspozytor kanału</span><span class="sxs-lookup"><span data-stu-id="87278-102">Custom Channel Dispatcher</span></span>
<span data-ttu-id="87278-103">Ten przykład demonstruje sposób tworzenia kanału stosu w niestandardowy sposób zaimplementowanie <xref:System.ServiceModel.ServiceHostBase> bezpośrednio oraz sposobu tworzenia dyspozytora niestandardowym kanale w środowisku hosta sieci Web.</span><span class="sxs-lookup"><span data-stu-id="87278-103">This sample demonstrates how to build the channel stack in a custom way by implementing <xref:System.ServiceModel.ServiceHostBase> directly and how to create a custom channel dispatcher in Web host environment.</span></span> <span data-ttu-id="87278-104">Dyspozytor kanału współdziała z <xref:System.ServiceModel.Channels.IChannelListener> ma akceptować komunikaty kanałów i pobiera ze stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="87278-104">The channel dispatcher interacts with <xref:System.ServiceModel.Channels.IChannelListener> to accept channels and retrieves messages from the channel stack.</span></span> <span data-ttu-id="87278-105">W tym przykładzie przedstawiono również podstawowy przykład demonstrujące sposób tworzenia kanału stosu w środowisku hosta sieci Web przy użyciu <xref:System.ServiceModel.Activation.VirtualPathExtension>.</span><span class="sxs-lookup"><span data-stu-id="87278-105">This sample also provides a basic sample to show how to build a channel stack in a Web host environment by using <xref:System.ServiceModel.Activation.VirtualPathExtension>.</span></span>  
  
## <a name="custom-servicehostbase"></a><span data-ttu-id="87278-106">Niestandardowe obiektu ServiceHostBase.</span><span class="sxs-lookup"><span data-stu-id="87278-106">Custom ServiceHostBase</span></span>  
 <span data-ttu-id="87278-107">W tym przykładzie implementuje typ podstawowy <xref:System.ServiceModel.ServiceHostBase> zamiast <xref:System.ServiceModel.ServiceHost> do pokazują, jak zastąpić [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] stosu implementacji z wiadomością niestandardową obsługę warstwy na szczycie stosu kanału.</span><span class="sxs-lookup"><span data-stu-id="87278-107">This sample implements the base type <xref:System.ServiceModel.ServiceHostBase> instead of <xref:System.ServiceModel.ServiceHost> to demonstrate how to replace the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] stack implementation with a custom message handling layer on top of the channel stack.</span></span> <span data-ttu-id="87278-108">Należy przesłonić metodę wirtualną <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> tworzenie odbiorniki kanałów i dyspozytora kanału.</span><span class="sxs-lookup"><span data-stu-id="87278-108">You override the virtual method <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> to build channel listeners and the channel dispatcher.</span></span>  
  
 <span data-ttu-id="87278-109">Do wdrożenia usługi sieci Web hostowanych, pobierz rozszerzenie usługi <xref:System.ServiceModel.Activation.VirtualPathExtension> z <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> kolekcji i dodaj go do <xref:System.ServiceModel.Channels.BindingParameterCollection> tak, aby warstwy transportowej wie, jak skonfigurować odbiornika kanałów na podstawie ustawień środowiska hostingu, który jest Internet Information Services (IIS) / ustawienia usługi aktywacji procesów systemu Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="87278-109">To implement a Web-hosted service, get the service extension <xref:System.ServiceModel.Activation.VirtualPathExtension> from the <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> collection and add it to the <xref:System.ServiceModel.Channels.BindingParameterCollection> so that the transport layer knows how to configure the channel listener based on the hosting environment settings, that is, the Internet Information Services (IIS)/Windows Process Activation Service (WAS) settings.</span></span>  
  
## <a name="custom-channel-dispatcher"></a><span data-ttu-id="87278-110">Niestandardowy dyspozytor kanału</span><span class="sxs-lookup"><span data-stu-id="87278-110">Custom Channel Dispatcher</span></span>  
 <span data-ttu-id="87278-111">Dyspozytor niestandardowym kanale rozszerza typ <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>.</span><span class="sxs-lookup"><span data-stu-id="87278-111">The custom channel dispatcher extends the type <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase>.</span></span> <span data-ttu-id="87278-112">Ten typ implementuje logiki programowania warstwie kanału.</span><span class="sxs-lookup"><span data-stu-id="87278-112">This type implements the channel-layer programming logic.</span></span> <span data-ttu-id="87278-113">W tym przykładzie, tylko <xref:System.ServiceModel.Channels.IReplyChannel> jest obsługiwane w przypadku wymiany komunikatów żądanie odpowiedź, ale dyspozytora kanału niestandardowych można łatwo rozszerzyć innych typów kanałów.</span><span class="sxs-lookup"><span data-stu-id="87278-113">In this sample, only <xref:System.ServiceModel.Channels.IReplyChannel> is supported for request-reply message exchange pattern, but the custom channel dispatcher can be easily extended to other channel types.</span></span>  
  
 <span data-ttu-id="87278-114">Dyspozytor otwierania odbiornika kanałów i następnie akceptuje pojedyncze kanału odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="87278-114">The dispatcher first opens the channel listener and then accepts the singleton reply channel.</span></span> <span data-ttu-id="87278-115">Z kanału rozpoczyna się do wysyłania wiadomości (liczba żądań) w pętli nieskończonej.</span><span class="sxs-lookup"><span data-stu-id="87278-115">With the channel, it starts to send messages (requests) in an infinite loop.</span></span> <span data-ttu-id="87278-116">Dla każdego żądania tworzy komunikat odpowiedzi i wysyła je z powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="87278-116">For each request, it creates a reply message and sends it back to the client.</span></span>  
  
## <a name="creating-a-response-message"></a><span data-ttu-id="87278-117">Tworzenie komunikatu odpowiedzi</span><span class="sxs-lookup"><span data-stu-id="87278-117">Creating a Response Message</span></span>  
 <span data-ttu-id="87278-118">Przetwarzanie komunikatów jest zaimplementowany w typie `MyServiceManager`.</span><span class="sxs-lookup"><span data-stu-id="87278-118">The message processing is implemented in the type `MyServiceManager`.</span></span> <span data-ttu-id="87278-119">W `HandleRequest` metody `Action` nagłówka wiadomości jest najpierw sprawdzane w celu sprawdzenia, czy żądanie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="87278-119">In the `HandleRequest` method, the `Action` header of the message is first checked to see whether the request is supported.</span></span> <span data-ttu-id="87278-120">Wstępnie zdefiniowane akcji SOAP "http://tempuri.org/HelloWorld/Hello" zdefiniowano zapewnienie filtrowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="87278-120">A predefined SOAP action "http://tempuri.org/HelloWorld/Hello" is defined to provide message filtering.</span></span> <span data-ttu-id="87278-121">To jest podobny do koncepcji kontraktu usługi w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementacja <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="87278-121">This is similar to the service contract concept in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementation of <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
 <span data-ttu-id="87278-122">W przypadku poprawne akcji SOAP próbki pobiera dane żądanej wiadomości i generuje odpowiadająca mu reakcja na żądanie, podobnie jak co jest widoczne w <xref:System.ServiceModel.ServiceHost> przypadku.</span><span class="sxs-lookup"><span data-stu-id="87278-122">For the correct SOAP action case, the sample retrieves the requested message data and generates a corresponding response to the request similar to what is seen in the <xref:System.ServiceModel.ServiceHost> case.</span></span>  
  
 <span data-ttu-id="87278-123">Specjalnie zlecenia HTTP GET są obsługiwane przez zwrócenie niestandardowe wiadomości w formacie HTML, w tym przypadku tak, aby przeglądać usługi z przeglądarki, aby zobaczyć, że jest on niepoprawnie skompilowany.</span><span class="sxs-lookup"><span data-stu-id="87278-123">You specially handled the HTTP-GET verb by returning a custom HTML message, in this, case so that you can browse the service from a browser to see that it is compiled correctly.</span></span> <span data-ttu-id="87278-124">Jeśli Akcja SOAP są niezgodne, Błąd wysyłania wiadomości Wstecz, aby wskazać, że żądanie nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="87278-124">If the SOAP action does not match, send a fault message back to indicate that the request is not supported.</span></span>  
  
 <span data-ttu-id="87278-125">Klient w tym przykładzie jest zwykłym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta, który nie przyjmuje żadnych z usługi.</span><span class="sxs-lookup"><span data-stu-id="87278-125">The client of this sample is a normal [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client that does not assume anything from the service.</span></span> <span data-ttu-id="87278-126">Usługa jest specjalnie zaprojektowane do dopasowania, otrzymasz od zwykłym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.ServiceHost> implementacji.</span><span class="sxs-lookup"><span data-stu-id="87278-126">So, the service is specially designed to match what you get from a normal [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.ServiceModel.ServiceHost> implementation.</span></span> <span data-ttu-id="87278-127">W związku z tym kontraktu usługi jest wymagany na kliencie.</span><span class="sxs-lookup"><span data-stu-id="87278-127">As a result, only a service contract is required on the client.</span></span>  
  
## <a name="using-the-sample"></a><span data-ttu-id="87278-128">Przy użyciu próbki</span><span class="sxs-lookup"><span data-stu-id="87278-128">Using the sample</span></span>  
 <span data-ttu-id="87278-129">Uruchomienie aplikacji klienckiej bezpośrednio tworzy następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="87278-129">Running the client application directly produces the following output.</span></span>  
  
```Output  
Client is talking to a request/reply WCF service.   
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 <span data-ttu-id="87278-130">Możesz również przejść usługi z przeglądarki, aby na serwerze pobiera przetworzyć komunikatu HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="87278-130">You can also browse the service from a browser so that an HTTP-GET message gets processed on the server.</span></span> <span data-ttu-id="87278-131">Należy dobrze sformatowany tekst HTML to pobiera ponownie.</span><span class="sxs-lookup"><span data-stu-id="87278-131">This gets you well-formatted HTML text back.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="87278-132">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="87278-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="87278-133">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="87278-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="87278-134">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="87278-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="87278-135">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="87278-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`