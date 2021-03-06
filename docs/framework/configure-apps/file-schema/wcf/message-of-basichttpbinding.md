---
title: '&lt;message&gt; w &lt;basicHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: 7f543a91f1d11575df239267a6a8a0b244d99cb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33366050"
---
# <a name="ltmessagegt-of-ltbasichttpbindinggt"></a>&lt;message&gt; w &lt;basicHttpBinding&gt;
Definiuje ustawienia zabezpieczeń na poziomie komunikatu z [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 \<system.ServiceModel>  
\<powiązania >  
\<basicHttpBinding >  
\<Powiązanie >  
\<Zabezpieczenia >  
\<message>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<message   
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="UserName/Certificate"/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty i elementy podrzędne, elementy nadrzędne  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|algorithmSuite|Ustawia komunikat algorytmów szyfrowania i zawijania klucza. Ten atrybut jest typu <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, który określa algorytmy i rozmiary kluczy. Algorytmy te są mapowane na te określone w specyfikacji języka zasad zabezpieczeń (WS-SecurityPolicy).<br /><br /> Wartość domyślna to `Basic256`.|  
|clientCredentialType|Określa typ poświadczenia do użycia podczas przeprowadzania uwierzytelniania klienta za pomocą zabezpieczenia na poziomie wiadomości. Wartość domyślna to `UserName`.|  
  
## <a name="clientcredentialtype-attribute"></a>właściwości ClientCredentialType o wartości atrybutu  
  
|Wartość|Opis|  
|-----------|-----------------|  
|UserName|-Wymaga uwierzytelnienia klienta do serwera o poświadczenie nazwy użytkownika. To poświadczenie musi być określona za pomocą [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).<br />-WCF nie obsługuje wysyłanie skrótu hasła lub wyprowadzanie kluczy przy użyciu hasła i te klucze dla zabezpieczenia wiadomości. W związku z tym WCF wymusza, czy transport można zabezpieczyć, korzystając z poświadczeń UserName. Aby uzyskać `basicHttpBinding`, wymagane jest skonfigurowanie kanału SSL.|  
|certyfikat|Wymaga uwierzytelnienia klienta na serwerze przy użyciu certyfikatu. W takim przypadku poświadczeń klienta należy określić przy użyciu [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) i [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md). Ponadto podczas korzystania z trybu zabezpieczeń wiadomości, klient musi obsługiwane za pomocą certyfikatu usługi. Poświadczenia usługi w takim przypadku należy określić przy użyciu <xref:System.ServiceModel.Description.ClientCredentials> klasy lub `ClientCredentials` element zachowania i określając usługi certyfikatów przy użyciu [ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<Zabezpieczenia >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Definiuje funkcje zabezpieczeń dla [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).|  
  
## <a name="example"></a>Przykład  
 W tym przykładzie pokazano, jak wdrożyć aplikację, która używa zabezpieczeń basicHttpBinding i komunikatów. W poniższym przykładzie konfiguracji dla usługi definicji punktu końcowego określa basicHttpBinding i odwołuje się do konfiguracji powiązania o nazwie `Binding1`. Certyfikat używany przez usługę do samodzielnego uwierzytelnienia klienta znajduje się w `behaviors` sekcji pliku konfiguracji w obszarze `serviceCredentials` elementu. Tryb walidacji, która ma zastosowanie do certyfikatu używanego przez klienta do samodzielnego uwierzytelnienia usługi znajduje się również w `behaviors` w obszarze `clientCertificate` elementu.  
  
 Szczegóły tego samego powiązania i zabezpieczenia są określone w pliku konfiguracji klienta.  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="Binding1"   
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <bindings>  
      <basicHttpBinding>  
        <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1" >  
          <security mode = "Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--  
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by a client to authenticate the service and provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.BasicHttpMessageSecurity>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>  
 <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>  
 [Zabezpieczanie usług i klientów](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Powiązania](../../../../../docs/framework/wcf/bindings.md)  
 [Konfigurowanie powiązań dostarczanych przez system](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<Powiązanie >](../../../../../docs/framework/misc/binding.md)
