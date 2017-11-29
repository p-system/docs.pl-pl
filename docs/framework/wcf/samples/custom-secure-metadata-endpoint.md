---
title: "Niestandardowy bezpieczny punkt końcowy metadanych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9e369e99-ea4a-49ff-aed2-9fdf61091a48
caps.latest.revision: "19"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 78fbde5f83d4a24594e06b787756c7ab3762d75a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="custom-secure-metadata-endpoint"></a><span data-ttu-id="31139-102">Niestandardowy bezpieczny punkt końcowy metadanych</span><span class="sxs-lookup"><span data-stu-id="31139-102">Custom Secure Metadata Endpoint</span></span>
<span data-ttu-id="31139-103">Przykładzie pokazano, jak wdrożyć usługę z punktem końcowym metadanych bezpieczny, jednym z powiązań wymiany metadanych z systemem innym niż i konfigurowanie [narzędzie narzędzia metadanych elementu ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) lub klientów do pobrania metadane z punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="31139-103">This sample demonstrates how to implement a service with a secure metadata endpoint that uses one of the non-metadata exchange bindings, and how to configure [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) or clients to fetch the metadata from such a metadata endpoint.</span></span> <span data-ttu-id="31139-104">Dostępne są dwa powiązania dostarczane przez system dla udostępnianie punkty końcowe metadanych: mexHttpBinding i mexHttpsBinding.</span><span class="sxs-lookup"><span data-stu-id="31139-104">There are two system-provided bindings available for exposing metadata endpoints: mexHttpBinding and mexHttpsBinding.</span></span> <span data-ttu-id="31139-105">mexHttpBinding jest używany do udostępnienia punktu końcowego metadanych za pośrednictwem protokołu HTTP w sposób, które nie są bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="31139-105">mexHttpBinding is used to expose a metadata endpoint over HTTP in a non-secure manner.</span></span> <span data-ttu-id="31139-106">mexHttpsBinding jest używany do udostępnienia punktu końcowego metadanych za pośrednictwem protokołu HTTPS w bezpieczny sposób.</span><span class="sxs-lookup"><span data-stu-id="31139-106">mexHttpsBinding is used to expose a metadata endpoint over HTTPS in a secure manner.</span></span> <span data-ttu-id="31139-107">W tym przykładzie przedstawiono sposób ujawniać punkt końcowy metadanych bezpiecznego przy użyciu <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="31139-107">This sample illustrates how to expose a secure metadata endpoint using the <xref:System.ServiceModel.WSHttpBinding>.</span></span> <span data-ttu-id="31139-108">Czy chcesz to zrobić, jeśli chcesz zmienić ustawienia zabezpieczeń dla powiązania, ale nie chcesz używać protokołu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="31139-108">You would want to do this when you want to change the security settings on the binding, but you do not want to use HTTPS.</span></span> <span data-ttu-id="31139-109">Jeśli używasz mexHttpsBinding punktu końcowego metadanych będzie bezpieczna, ale nie istnieje sposób zmodyfikować ustawienia powiązania.</span><span class="sxs-lookup"><span data-stu-id="31139-109">If you use the mexHttpsBinding your metadata endpoint will be secure, but there is no way to modify the binding settings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="31139-110">Procedury i kompilacji instrukcje dotyczące instalacji dla tego przykładu znajdują się na końcu tego tematu.</span><span class="sxs-lookup"><span data-stu-id="31139-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="31139-111">Usługa</span><span class="sxs-lookup"><span data-stu-id="31139-111">Service</span></span>  
 <span data-ttu-id="31139-112">Usługi w tym przykładzie ma dwa punkty końcowe.</span><span class="sxs-lookup"><span data-stu-id="31139-112">The service in this sample has two endpoints.</span></span> <span data-ttu-id="31139-113">Punkt końcowy aplikacji służy `ICalculator` kontraktu na `WSHttpBinding` z `ReliableSession` włączone i `Message` zabezpieczeń za pomocą certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="31139-113">The application endpoint serves the `ICalculator` contract on a `WSHttpBinding` with `ReliableSession` enabled and `Message` security using certificates.</span></span> <span data-ttu-id="31139-114">Punkt końcowy metadanych używa również `WSHttpBinding`, z tymi samymi ustawieniami zabezpieczeń, ale bez `ReliableSession`.</span><span class="sxs-lookup"><span data-stu-id="31139-114">The metadata endpoint also uses `WSHttpBinding`, with the same security settings but with no `ReliableSession`.</span></span> <span data-ttu-id="31139-115">Poniżej przedstawiono istotne konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="31139-115">Here is the relevant configuration:</span></span>  
  
```xml  
<services>   
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- use base address provided by host -->  
     <endpoint address=""  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding2"  
       contract="Microsoft.ServiceModel.Samples.ICalculator" />  
     <endpoint address="mex"  
       binding="wsHttpBinding"  
       bindingConfiguration="Binding1"  
       contract="IMetadataExchange" />  
     </service>  
 </services>  
 <bindings>  
   <wsHttpBinding>  
     <binding name="Binding1">  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
     <binding name="Binding2">  
       <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
       <security mode="Message">  
         <message clientCredentialType="Certificate" />  
       </security>  
     </binding>  
   </wsHttpBinding>  
 </bindings>  
```  
  
 <span data-ttu-id="31139-116">W wielu innych próbek punktu końcowego metadanych używa domyślnej `mexHttpBinding`, która nie jest bezpieczne.</span><span class="sxs-lookup"><span data-stu-id="31139-116">In many of the other samples, the metadata endpoint uses the default `mexHttpBinding`, which is not secure.</span></span> <span data-ttu-id="31139-117">W tym miejscu metadanych jest zabezpieczone przy użyciu `WSHttpBinding` z `Message` zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="31139-117">Here the metadata is secured using `WSHttpBinding` with `Message` security.</span></span> <span data-ttu-id="31139-118">Aby klienci metadanych można pobrać metadanych musi być skonfigurowany z pasującego powiązania.</span><span class="sxs-lookup"><span data-stu-id="31139-118">In order for metadata clients to retrieve this metadata, they must be configured with a matching binding.</span></span> <span data-ttu-id="31139-119">W tym przykładzie przedstawiono dwóch takich klientów.</span><span class="sxs-lookup"><span data-stu-id="31139-119">This sample demonstrates two such clients.</span></span>  
  
 <span data-ttu-id="31139-120">Pierwszy klient używa Svcutil.exe do pobierania metadanych i generowanie kodu klienta i konfiguracji w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="31139-120">The first client uses Svcutil.exe to fetch the metadata and generate client code and configuration at design time.</span></span> <span data-ttu-id="31139-121">Ponieważ usługa korzysta z metadanych powiązania innych niż domyślne, z narzędzia Svcutil.exe muszą zostać skonfigurowane specjalnie, aby ją pobrać metadanych usługi za pomocą tego powiązania.</span><span class="sxs-lookup"><span data-stu-id="31139-121">Because the service uses a non-default binding for the metadata, the Svcutil.exe tool must be specifically configured so that it can get the metadata from the service using that binding.</span></span>  
  
 <span data-ttu-id="31139-122">Drugi klient używa `MetadataResolver` dynamicznie pobrać metadanych dla znanych kontraktu i następnie wywoływać operacje na dynamicznie generowanym klienta.</span><span class="sxs-lookup"><span data-stu-id="31139-122">The second client uses the `MetadataResolver` to dynamically fetch the metadata for a known contract and then invoke operations on the dynamically generated client.</span></span>  
  
## <a name="svcutil-client"></a><span data-ttu-id="31139-123">Svcutil klienta</span><span class="sxs-lookup"><span data-stu-id="31139-123">Svcutil client</span></span>  
 <span data-ttu-id="31139-124">Korzystając z powiązania domyślnego hosta z `IMetadataExchange` punkt końcowy, można uruchomić Svcutil.exe adres tego punktu końcowego:</span><span class="sxs-lookup"><span data-stu-id="31139-124">When using the default binding to host your `IMetadataExchange` endpoint, you can run Svcutil.exe with the address of that endpoint:</span></span>  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="31139-125">i działa.</span><span class="sxs-lookup"><span data-stu-id="31139-125">and it works.</span></span> <span data-ttu-id="31139-126">Jednak w tym przykładzie serwer używa punktu końcowego innych niż domyślne do obsługi metadanych.</span><span class="sxs-lookup"><span data-stu-id="31139-126">But in this sample, the server uses a non-default endpoint to host the metadata.</span></span> <span data-ttu-id="31139-127">Dlatego Svcutil.exe musi być zalecane jest używanie poprawne powiązanie.</span><span class="sxs-lookup"><span data-stu-id="31139-127">So Svcutil.exe must be instructed to use the correct binding.</span></span> <span data-ttu-id="31139-128">Można to zrobić przy użyciu pliku Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="31139-128">This can be done using a Svcutil.exe.config file.</span></span>  
  
 <span data-ttu-id="31139-129">Plik Svcutil.exe.config wygląda jak plik konfiguracji normalne klienta.</span><span class="sxs-lookup"><span data-stu-id="31139-129">The Svcutil.exe.config file looks like a normal client configuration file.</span></span> <span data-ttu-id="31139-130">Tylko nietypowe aspekty są nazwa punktu końcowego klienta i kontraktu:</span><span class="sxs-lookup"><span data-stu-id="31139-130">The only unusual aspects are the client endpoint name and contract:</span></span>  
  
```xml  
<endpoint name="http"  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"  
          behaviorConfiguration="ClientCertificateBehavior"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="31139-131">Nazwa punktu końcowego musi być nazwą systemu adres, gdzie jest hostowana metadanych i kontraktu punktu końcowego musi być `IMetadataExchange`.</span><span class="sxs-lookup"><span data-stu-id="31139-131">The endpoint name must be the name of the scheme of the address where the metadata is hosted and the endpoint contract must be `IMetadataExchange`.</span></span> <span data-ttu-id="31139-132">W związku z tym, kiedy Svcutil.exe jest uruchamiana z wiersza polecenia takich jak następujące:</span><span class="sxs-lookup"><span data-stu-id="31139-132">Thus, when Svcutil.exe is run with a command-line such as the following:</span></span>  
  
```  
svcutil http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="31139-133">wygląda na to dla punktu końcowego o nazwie "http" i kontraktu `IMetadataExchange` do konfigurowania wiązania i zachowanie programu exchange komunikacji z punktem końcowym metadanych.</span><span class="sxs-lookup"><span data-stu-id="31139-133">it looks for the endpoint named "http" and contract `IMetadataExchange` to configure the binding and behavior of the communication exchange with the metadata endpoint.</span></span> <span data-ttu-id="31139-134">Pozostała część pliku Svcutil.exe.config w próbce określa Konfiguracja powiązania i zachowanie poświadczeń do dopasowania konfiguracji serwera punktu końcowego metadanych.</span><span class="sxs-lookup"><span data-stu-id="31139-134">The rest of the Svcutil.exe.config file in the sample specifies the binding configuration and behavior credentials to match the server's configuration of the metadata endpoint.</span></span>  
  
 <span data-ttu-id="31139-135">Aby Svcutil.exe do pobrania konfiguracji w Svcutil.exe.config Svcutil.exe musi być w tym samym katalogu co plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="31139-135">In order for Svcutil.exe to pick up the configuration in Svcutil.exe.config, Svcutil.exe must be in the same directory as the configuration file.</span></span> <span data-ttu-id="31139-136">W związku z tym należy skopiować Svcutil.exe z lokalizacji instalacji do katalogu zawierającego plik Svcutil.exe.config.</span><span class="sxs-lookup"><span data-stu-id="31139-136">As a result, you must copy Svcutil.exe from its install location to the directory that contains the Svcutil.exe.config file.</span></span> <span data-ttu-id="31139-137">Następnie uruchom następujące polecenie z tego katalogu:</span><span class="sxs-lookup"><span data-stu-id="31139-137">Then from that directory, run the following command:</span></span>  
  
```  
.\svcutil.exe http://localhost/servicemodelsamples/service.svc/mex  
```  
  
 <span data-ttu-id="31139-138">Znaku ". \\"zapewnia, że kopia Svcutil.exe w tym katalogu (taki, który ma odpowiednie Svcutil.exe.config) jest uruchamiane.</span><span class="sxs-lookup"><span data-stu-id="31139-138">The leading ".\\" ensures that the copy of Svcutil.exe in this directory (the one which has a corresponding Svcutil.exe.config) is run.</span></span>  
  
## <a name="metadataresolver-client"></a><span data-ttu-id="31139-139">MetadataResolver klienta</span><span class="sxs-lookup"><span data-stu-id="31139-139">MetadataResolver client</span></span>  
 <span data-ttu-id="31139-140">Jeśli klient zna umowy oraz sposób zwróć się do metadanych w czasie projektowania, klienta można dynamicznie znaleźć powiązanie i adres punktów końcowych aplikacji za pomocą `MetadataResolver`.</span><span class="sxs-lookup"><span data-stu-id="31139-140">If the client knows the contract and how to talk to the metadata at design time, the client can dynamically find out the binding and address of application endpoints using the `MetadataResolver`.</span></span> <span data-ttu-id="31139-141">Ten klient przykładowych pokazano, pokazujący sposób konfigurowania powiązania i poświadczenia używane przez `MetadataResolver` przez tworzenie i konfigurowanie `MetadataExchangeClient`.</span><span class="sxs-lookup"><span data-stu-id="31139-141">This sample client demonstrates this, showing how to configure the binding and credentials used by `MetadataResolver` by creating and configuring a `MetadataExchangeClient`.</span></span>  
  
 <span data-ttu-id="31139-142">Powiązanie i certyfikatu informacje, które znajdowały się w Svcutil.exe.config można określić imperatively na `MetadataExchangeClient`:</span><span class="sxs-lookup"><span data-stu-id="31139-142">The same binding and certificate information that appeared in Svcutil.exe.config can be specified imperatively on the `MetadataExchangeClient`:</span></span>  
  
```  
// Specify the Metadata Exchange binding and its security mode  
WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
// Create a MetadataExchangeClient for retrieving metadata, and set the // certificate details  
MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
mexClient.SoapCredentials.ClientCertificate.SetCertificate(    StoreLocation.CurrentUser, StoreName.My,  
    X509FindType.FindBySubjectName, "client.com");  
mexClient.SoapCredentials.ServiceCertificate.Authentication.    CertificateValidationMode =    X509CertificateValidationMode.PeerOrChainTrust;  
mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(    StoreLocation.CurrentUser, StoreName.TrustedPeople,  
    X509FindType.FindBySubjectName, "localhost");  
```  
  
 <span data-ttu-id="31139-143">Z `mexClient` skonfigurowane, możemy wyliczyć kontrakty firma Microsoft planuje się i użyj `MetadataResolver` można pobrać listy punktów końcowych o tych umów:</span><span class="sxs-lookup"><span data-stu-id="31139-143">With the `mexClient` configured, we can enumerate the contracts we are interested in, and use `MetadataResolver` to fetch a list of endpoints with those contracts:</span></span>  
  
```  
// The contract we want to fetch metadata for  
Collection<ContractDescription> contracts =    new Collection<ContractDescription>();  
ContractDescription contract =    ContractDescription.GetContract(typeof(ICalculator));  
contracts.Add(contract);  
// Find endpoints for that contract  
EndpointAddress mexAddress = new    EndpointAddress(ConfigurationManager.AppSettings["mexAddress"]);  
ServiceEndpointCollection endpoints =    MetadataResolver.Resolve(contracts, mexAddress, mexClient);  
```  
  
 <span data-ttu-id="31139-144">Na koniec możemy użyć informacji z tych punktów końcowych zainicjować powiązania oraz adres `ChannelFactory` używany do tworzenia kanałów do komunikowania się z punktami końcowymi aplikacji.</span><span class="sxs-lookup"><span data-stu-id="31139-144">Finally we can use the information from those endpoints to initialize the binding and address of a `ChannelFactory` used to create channels to communicate with the application endpoints.</span></span>  
  
```  
ChannelFactory<ICalculator> cf = new    ChannelFactory<ICalculator>(endpoint.Binding, endpoint.Address);  
```  
  
 <span data-ttu-id="31139-145">Klucza punkt ten klient próbki jest wykazać, że jeśli używasz `MetadataResolver`i należy określić niestandardowe powiązania lub zachowania dla komunikacji wymiany metadanych, możesz użyć `MetadataExchangeClient` do określenia tych ustawień niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="31139-145">The key point of this sample client is to demonstrate that, if you are using `MetadataResolver`, and you must specify custom bindings or behaviors for the metadata exchange communication, you can use a `MetadataExchangeClient` to specify those custom settings.</span></span>  
  
#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="31139-146">Aby skonfigurować i tworzyć przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="31139-146">To set up and build the sample</span></span>  
  
1.  <span data-ttu-id="31139-147">Upewnij się, że wykonano procedurę [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="31139-147">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="31139-148">Postępuj zgodnie z instrukcjami w celu skompilowania rozwiązania, [kompilowanie przykładów programu Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="31139-148">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="31139-149">Aby uruchomić przykład na tym samym komputerze</span><span class="sxs-lookup"><span data-stu-id="31139-149">To run the sample on the same machine</span></span>  
  
1.  <span data-ttu-id="31139-150">Uruchamianie pliku Setup.bat z folderu instalacyjnego próbki.</span><span class="sxs-lookup"><span data-stu-id="31139-150">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="31139-151">Spowoduje to zainstalowanie wszystkich certyfikatów, które są wymagane do uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="31139-151">This installs all the certificates required for running the sample.</span></span> <span data-ttu-id="31139-152">Należy pamiętać, że pliku Setup.bat używa narzędzia FindPrivateKey.exe, które jest zainstalowany, uruchamiając setupCertTool.bat z [jednorazowego procedurę instalacji dla przykładów Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="31139-152">Note that Setup.bat uses the FindPrivateKey.exe tool, which is installed by running setupCertTool.bat from [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="31139-153">Uruchom aplikację klienta z \MetadataResolverClient\bin lub \SvcutilClient\bin.</span><span class="sxs-lookup"><span data-stu-id="31139-153">Run the client application from \MetadataResolverClient\bin or \SvcutilClient\bin.</span></span> <span data-ttu-id="31139-154">Aktywność klienta jest wyświetlany w aplikacji konsoli klienta.</span><span class="sxs-lookup"><span data-stu-id="31139-154">Client activity is displayed on the client console application.</span></span>  
  
3.  <span data-ttu-id="31139-155">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="31139-155">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
4.  <span data-ttu-id="31139-156">Usuń certyfikaty, uruchamiając Cleanup.bat po zakończeniu z próbką.</span><span class="sxs-lookup"><span data-stu-id="31139-156">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="31139-157">Inne przykłady zabezpieczeń za pomocą tego samego certyfikatów.</span><span class="sxs-lookup"><span data-stu-id="31139-157">Other security samples use the same certificates.</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="31139-158">Aby uruchomić przykład na komputerach</span><span class="sxs-lookup"><span data-stu-id="31139-158">To run the sample across machines</span></span>  
  
1.  <span data-ttu-id="31139-159">Na serwerze, uruchom `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="31139-159">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="31139-160">Uruchomiona `setup.bat` z `service` argument tworzy certyfikat usługi z nazwą domeny pełni kwalifikowanymi maszyny i wyeksportuj certyfikat usługi do pliku o nazwie Service.cer.</span><span class="sxs-lookup"><span data-stu-id="31139-160">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
2.  <span data-ttu-id="31139-161">Na serwerze należy edytować plik Web.config, aby odzwierciedlić nową nazwę certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="31139-161">On the server, edit Web.config to reflect the new certificate name.</span></span> <span data-ttu-id="31139-162">Oznacza to, zmień `findValue` atrybutu w [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) elementu, aby w pełni kwalifikowaną nazwą domeny maszyny.</span><span class="sxs-lookup"><span data-stu-id="31139-162">That is, change the `findValue` attribute in the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) element to the fully-qualified domain name of the machine.</span></span>  
  
3.  <span data-ttu-id="31139-163">Skopiuj plik Service.cer z katalogu usług do katalogu klienta na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="31139-163">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
4.  <span data-ttu-id="31139-164">Na komputerze klienckim, uruchom `setup.bat client`.</span><span class="sxs-lookup"><span data-stu-id="31139-164">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="31139-165">Uruchomiona `setup.bat` z `client` argument tworzy certyfikat klienta o nazwie Client.com i wyeksportuj certyfikat klienta do pliku o nazwie Client.cer.</span><span class="sxs-lookup"><span data-stu-id="31139-165">Running `setup.bat` with the `client` argument creates a client certificate named Client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
5.  <span data-ttu-id="31139-166">W pliku App.config `MetadataResolverClient` na komputerze klienckim, zmień wartość adresu punktu końcowego mex odpowiadające nowy adres z usługą.</span><span class="sxs-lookup"><span data-stu-id="31139-166">In the App.config file of the `MetadataResolverClient` on the client machine, change the address value of the mex endpoint to match the new address of your service.</span></span> <span data-ttu-id="31139-167">Aby to zrobić, zastępując localhost w pełni kwalifikowaną nazwą domeny serwera.</span><span class="sxs-lookup"><span data-stu-id="31139-167">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="31139-168">Wystąpienie "localhost" w pliku metadataResolverClient.cs należy również zmienić na nową nazwę certyfikatu usługi (nazwa domeny pełni kwalifikowanymi serwera).</span><span class="sxs-lookup"><span data-stu-id="31139-168">Also change the occurrence of "localhost" in the metadataResolverClient.cs file to the new service certificate name (the fully-qualified domain name of the server).</span></span> <span data-ttu-id="31139-169">Tak samo postąpić w pliku App.config projektu SvcutilClient.</span><span class="sxs-lookup"><span data-stu-id="31139-169">Do the same thing for the App.config of the SvcutilClient project.</span></span>  
  
6.  <span data-ttu-id="31139-170">Skopiuj plik Client.cer z katalogu klienta do katalogu usługi na serwerze.</span><span class="sxs-lookup"><span data-stu-id="31139-170">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
7.  <span data-ttu-id="31139-171">Na komputerze klienckim, uruchom `ImportServiceCert.bat`.</span><span class="sxs-lookup"><span data-stu-id="31139-171">On the client, run `ImportServiceCert.bat`.</span></span> <span data-ttu-id="31139-172">Certyfikat usługi to importuje z pliku Service.cer do CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="31139-172">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
8.  <span data-ttu-id="31139-173">Na serwerze, uruchom `ImportClientCert.bat`, certyfikat klienta zostaną zaimportowane z pliku Client.cer do LocalMachine - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="31139-173">On the server, run `ImportClientCert.bat`, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
9. <span data-ttu-id="31139-174">Na komputerze usługi kompilacji projektu usługi w programie Visual Studio i wybierz stronę pomocy w przeglądarce sieci web, aby sprawdzić, czy jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="31139-174">On the service machine, build the service project in Visual Studio and select the help page in a web browser to verify that it is running.</span></span>  
  
10. <span data-ttu-id="31139-175">Na komputerze klienckim należy uruchomić MetadataResolverClient lub SvcutilClient z wersji programu VS.</span><span class="sxs-lookup"><span data-stu-id="31139-175">On the client machine, run the MetadataResolverClient or the SvcutilClient from VS.</span></span>  
  
    1.  <span data-ttu-id="31139-176">Jeśli klient i usługa nie będą mogli komunikować się, zobacz [Rozwiązywanie problemów z porady](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span><span class="sxs-lookup"><span data-stu-id="31139-176">If the client and service are not able to communicate, see [Troubleshooting Tips](http://msdn.microsoft.com/en-us/8787c877-5e96-42da-8214-fa737a38f10b).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="31139-177">Aby wyczyścić po próbki</span><span class="sxs-lookup"><span data-stu-id="31139-177">To clean up after the sample</span></span>  
  
-   <span data-ttu-id="31139-178">Uruchamianie Cleanup.bat w folderze Przykłady po ukończeniu działania próbki.</span><span class="sxs-lookup"><span data-stu-id="31139-178">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="31139-179">Ten skrypt nie powoduje usunięcia certyfikatów usługi na kliencie podczas uruchamiania na komputerach w przykładzie.</span><span class="sxs-lookup"><span data-stu-id="31139-179">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="31139-180">Jeśli uruchomiono [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] przykłady, które korzystają z certyfikatów na komputerach, należy wyczyścić certyfikaty usługi, które zostały zainstalowane w CurrentUser - TrustedPeople magazynu.</span><span class="sxs-lookup"><span data-stu-id="31139-180">If you have run [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="31139-181">Aby to zrobić, użyj następującego polecenia: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span><span class="sxs-lookup"><span data-stu-id="31139-181">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`.</span></span> <span data-ttu-id="31139-182">Na przykład: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="31139-182">For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="31139-183">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="31139-183">The samples may already be installed on your machine.</span></span> <span data-ttu-id="31139-184">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="31139-184">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="31139-185">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="31139-185">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="31139-186">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="31139-186">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Metadata\CustomMexEndpoint`  
  
## <a name="see-also"></a><span data-ttu-id="31139-187">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="31139-187">See Also</span></span>