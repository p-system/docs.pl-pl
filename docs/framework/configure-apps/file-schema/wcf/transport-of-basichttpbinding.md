---
title: '&lt;transport&gt; w &lt;basicHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c5ba293-3d7e-47a6-b84e-e9022857b7e5
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c08e4c8b1008fa6e2625cdb9cd22672daf691a4a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltbasichttpbindinggt"></a><span data-ttu-id="92442-102">&lt;transport&gt; w &lt;basicHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="92442-102">&lt;transport&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="92442-103">Definiuje właściwości sterujące parametrami uwierzytelniania dla transportu HTTP.</span><span class="sxs-lookup"><span data-stu-id="92442-103">Defines properties that control authentication parameters for the HTTP transport.</span></span>  
  
 <span data-ttu-id="92442-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="92442-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="92442-105">\<powiązania ></span><span class="sxs-lookup"><span data-stu-id="92442-105">\<bindings></span></span>  
<span data-ttu-id="92442-106">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="92442-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="92442-107">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="92442-107">\<binding></span></span>  
<span data-ttu-id="92442-108">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="92442-108">\<security></span></span>  
<span data-ttu-id="92442-109">\<transport ></span><span class="sxs-lookup"><span data-stu-id="92442-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92442-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="92442-110">Syntax</span></span>  
  
```xml  
<basicHttpBinding>  
    <binding>  
        <security  
        mode="None|Transport|Message|TransportWithMessageCredential|TransportCredentialOnly">  
            <transport clientCredentialType="None|Basic|Digest|Ntlm|Windows"  
             proxyCredentialType="None|Basic|Digest|Ntlm|Windows" realm="string" >  
                <extendedProtectionPolicy  
                     policyEnforcement="Never|WhenSupported|Always"  
                     protectionScenario="TransportSelected|TrustedProxy">  
                    <customServiceNames></customServiceNames>  
                        </extendedProtectionPolicy>  
            </transport>  
        </security>  
    </binding>  
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92442-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="92442-111">Attributes and Elements</span></span>  
 <span data-ttu-id="92442-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="92442-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92442-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="92442-113">Attributes</span></span>  
  
|<span data-ttu-id="92442-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="92442-114">Attribute</span></span>|<span data-ttu-id="92442-115">Opis</span><span class="sxs-lookup"><span data-stu-id="92442-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="92442-116">Właściwość clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="92442-116">clientCredentialType</span></span>|<span data-ttu-id="92442-117">— Określa typ poświadczenia, które będą używane podczas uwierzytelniania klienta przy użyciu uwierzytelniania HTTP.</span><span class="sxs-lookup"><span data-stu-id="92442-117">-   Specifies the type of credential to be used when performing client authentication using HTTP authentication.</span></span>  <span data-ttu-id="92442-118">Wartość domyślna to `None`.</span><span class="sxs-lookup"><span data-stu-id="92442-118">The default is `None`.</span></span> <span data-ttu-id="92442-119">Ten atrybut jest typu <xref:System.ServiceModel.HttpClientCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="92442-119">This attribute is of type <xref:System.ServiceModel.HttpClientCredentialType>.</span></span>|  
|<span data-ttu-id="92442-120">proxyCredentialType</span><span class="sxs-lookup"><span data-stu-id="92442-120">proxyCredentialType</span></span>|<span data-ttu-id="92442-121">— Określa typ poświadczenia, które będą używane podczas uwierzytelniania klienta z w obrębie domeny przy użyciu serwera proxy za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="92442-121">-   Specifies the type of credential to be used when performing client authentication from within a domain using a proxy over HTTP.</span></span> <span data-ttu-id="92442-122">Ten atrybut jest stosowane tylko wtedy, gdy `mode` atrybutu nadrzędnego `security` jest element `Transport` lub `TransportCredentialsOnly`.</span><span class="sxs-lookup"><span data-stu-id="92442-122">This attribute is applicable only when the `mode` attribute of the parent `security` element is `Transport` or `TransportCredentialsOnly`.</span></span> <span data-ttu-id="92442-123">Ten atrybut jest typu <xref:System.ServiceModel.HttpProxyCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="92442-123">This attribute is of type <xref:System.ServiceModel.HttpProxyCredentialType>.</span></span>|  
|<span data-ttu-id="92442-124">obszar</span><span class="sxs-lookup"><span data-stu-id="92442-124">realm</span></span>|<span data-ttu-id="92442-125">Ciąg określający obszar, który jest używany przez schemat uwierzytelniania HTTP dla uwierzytelniania podstawowego lub szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="92442-125">A string that specifies the realm that is used by the HTTP authentication scheme for digest or basic authentication.</span></span> <span data-ttu-id="92442-126">Wartość domyślna to ciąg pusty.</span><span class="sxs-lookup"><span data-stu-id="92442-126">The default is an empty string.</span></span>|  
|<span data-ttu-id="92442-127">Właściwość policyEnforcement</span><span class="sxs-lookup"><span data-stu-id="92442-127">policyEnforcement</span></span>|<span data-ttu-id="92442-128">To wyliczenie Określa, kiedy <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> powinny być wymuszane.</span><span class="sxs-lookup"><span data-stu-id="92442-128">This enumeration specifies when the <xref:System.Security.Authentication.ExtendedProtection.ExtendedProtectionPolicy> should be enforced.</span></span><br /><br /> <span data-ttu-id="92442-129">1.  Nigdy nie — zasady nigdy nie są wymuszane (ochrona rozszerzona jest wyłączona).</span><span class="sxs-lookup"><span data-stu-id="92442-129">1.  Never – The policy is never enforced (Extended Protection is disabled).</span></span><br /><span data-ttu-id="92442-130">2.  WhenSupported — zasady są wymuszane tylko wtedy, gdy klient obsługuje ochrony rozszerzonej.</span><span class="sxs-lookup"><span data-stu-id="92442-130">2.  WhenSupported – The policy is enforced only if the client supports Extended Protection.</span></span><br /><span data-ttu-id="92442-131">3.  Zawsze — zasady zawsze są wymuszane.</span><span class="sxs-lookup"><span data-stu-id="92442-131">3.  Always – The policy is always enforced.</span></span> <span data-ttu-id="92442-132">Klienci, którzy nie obsługują ochrony rozszerzonej będzie mogło uwierzytelnić.</span><span class="sxs-lookup"><span data-stu-id="92442-132">Clients which don’t support Extended Protection will fail to authenticate.</span></span>|  
|<span data-ttu-id="92442-133">protectionScenario</span><span class="sxs-lookup"><span data-stu-id="92442-133">protectionScenario</span></span>|<span data-ttu-id="92442-134">To wyliczenie Określa scenariusz ochrony wymuszany przez zasady.</span><span class="sxs-lookup"><span data-stu-id="92442-134">This enumeration specifies the protection scenario enforced by the policy.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="92442-135">właściwości ClientCredentialType o wartości atrybutu</span><span class="sxs-lookup"><span data-stu-id="92442-135">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="92442-136">Wartość</span><span class="sxs-lookup"><span data-stu-id="92442-136">Value</span></span>|<span data-ttu-id="92442-137">Opis</span><span class="sxs-lookup"><span data-stu-id="92442-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="92442-138">Brak</span><span class="sxs-lookup"><span data-stu-id="92442-138">None</span></span>|<span data-ttu-id="92442-139">Komunikaty nie są już zabezpieczone podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="92442-139">Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="92442-140">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="92442-140">Basic</span></span>|<span data-ttu-id="92442-141">Określa uwierzytelnianie podstawowe.</span><span class="sxs-lookup"><span data-stu-id="92442-141">Specifies basic authentication.</span></span>|  
|<span data-ttu-id="92442-142">Skrót</span><span class="sxs-lookup"><span data-stu-id="92442-142">Digest</span></span>|<span data-ttu-id="92442-143">Określa uwierzytelnianie szyfrowane.</span><span class="sxs-lookup"><span data-stu-id="92442-143">Specifies digest authentication.</span></span>|  
|<span data-ttu-id="92442-144">Uwierzytelnianie NTLM</span><span class="sxs-lookup"><span data-stu-id="92442-144">Ntlm</span></span>|<span data-ttu-id="92442-145">Określa uwierzytelniania NTLM, jeśli to możliwe, a w przypadku niepowodzenia uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="92442-145">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="92442-146">Windows</span><span class="sxs-lookup"><span data-stu-id="92442-146">Windows</span></span>|<span data-ttu-id="92442-147">Określa zintegrowane uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="92442-147">Specifies Windows integrated authentication.</span></span>|  
  
## <a name="proxycredentialtype-attribute"></a><span data-ttu-id="92442-148">proxyCredentialType atrybutu</span><span class="sxs-lookup"><span data-stu-id="92442-148">proxyCredentialType Attribute</span></span>  
  
|<span data-ttu-id="92442-149">Wartość</span><span class="sxs-lookup"><span data-stu-id="92442-149">Value</span></span>|<span data-ttu-id="92442-150">Opis</span><span class="sxs-lookup"><span data-stu-id="92442-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="92442-151">Brak</span><span class="sxs-lookup"><span data-stu-id="92442-151">None</span></span>|<span data-ttu-id="92442-152">— Liczba komunikatów nie są już zabezpieczone podczas transferu.</span><span class="sxs-lookup"><span data-stu-id="92442-152">-   Messages are not secured during transfer.</span></span>|  
|<span data-ttu-id="92442-153">Podstawowy</span><span class="sxs-lookup"><span data-stu-id="92442-153">Basic</span></span>|<span data-ttu-id="92442-154">Określa uwierzytelnianie podstawowe, zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: Basic i uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="92442-154">Specifies basic authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="92442-155">Skrót</span><span class="sxs-lookup"><span data-stu-id="92442-155">Digest</span></span>|<span data-ttu-id="92442-156">Określa uwierzytelnianie szyfrowane zgodnie z definicją w dokumencie RFC 2617 — uwierzytelnianie HTTP: Basic i uwierzytelniania szyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="92442-156">Specifies digest authentication as defined by RFC 2617 – HTTP Authentication: Basic and Digest Authentication.</span></span>|  
|<span data-ttu-id="92442-157">Uwierzytelnianie NTLM</span><span class="sxs-lookup"><span data-stu-id="92442-157">Ntlm</span></span>|<span data-ttu-id="92442-158">Określa uwierzytelniania NTLM, jeśli to możliwe, a w przypadku niepowodzenia uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="92442-158">Specifies NTLM authentication when possible, and if Windows authentication fails.</span></span>|  
|<span data-ttu-id="92442-159">Windows</span><span class="sxs-lookup"><span data-stu-id="92442-159">Windows</span></span>|<span data-ttu-id="92442-160">Określa zintegrowane uwierzytelnianie systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="92442-160">Specifies Windows integrated authentication.</span></span>|  
|<span data-ttu-id="92442-161">certyfikat</span><span class="sxs-lookup"><span data-stu-id="92442-161">Certificate</span></span>|<span data-ttu-id="92442-162">Wykonuje uwierzytelnianie klienta przy użyciu certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="92442-162">Performs client authentication using a certificate.</span></span> <span data-ttu-id="92442-163">Ta opcja działa tylko wtedy, gdy `Mode` atrybutu nadrzędnego `security` element ma ustawioną wartość transportu i nie będzie działać, jeśli jest ustawiona wartość TransportCredentialOnly.</span><span class="sxs-lookup"><span data-stu-id="92442-163">This option works only if the `Mode` attribute of the parent `security` element is set to Transport, and will not work if it is set to TransportCredentialOnly.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92442-164">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="92442-164">Child Elements</span></span>  
 <span data-ttu-id="92442-165">Brak</span><span class="sxs-lookup"><span data-stu-id="92442-165">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92442-166">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="92442-166">Parent Elements</span></span>  
  
|<span data-ttu-id="92442-167">Element</span><span class="sxs-lookup"><span data-stu-id="92442-167">Element</span></span>|<span data-ttu-id="92442-168">Opis</span><span class="sxs-lookup"><span data-stu-id="92442-168">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92442-169">\<Zabezpieczenia ></span><span class="sxs-lookup"><span data-stu-id="92442-169">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="92442-170">Definiuje funkcje zabezpieczeń dla [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="92442-170">Defines the security capabilities for the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="92442-171">Przykład</span><span class="sxs-lookup"><span data-stu-id="92442-171">Example</span></span>  
 <span data-ttu-id="92442-172">W poniższym przykładzie pokazano użycie zabezpieczenia transportowe protokołu SSL z powiązaniem podstawowe.</span><span class="sxs-lookup"><span data-stu-id="92442-172">The following example demonstrates the use of SSL transport security with the basic binding.</span></span> <span data-ttu-id="92442-173">Domyślnie podstawowe wiązanie obsługuje komunikację HTTP.</span><span class="sxs-lookup"><span data-stu-id="92442-173">By default, the basic binding supports HTTP communication.</span></span>  
  
```xml  
<system.serviceModel>  
   <services>  
      <service   
          type="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
         <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
      </service>  
   </services>  
    <bindings>  
        <basicHttpBinding>  
        <!-- Configure basicHttpBinding with Transport security -- >  
        <!-- mode and clientCredentialType set to None.-->  
           <binding name="Binding1">  
               <security mode="Transport">  
                   <transport clientCredentialType="None"  
                              proxyCredentialType="None">  
                       <extendedProtectionPolicy  
                          policyEnforcement="WhenSupported"  
                          protectionScenario="TransportSelected">  
                    <customServiceNames></customServiceNames>  
                       </extendedProtectionPolicy>  
               </security>  
           </binding>  
        </basicHttpBinding>  
    </bindings>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="92442-174">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="92442-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.BasicHttpSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.HttpTransportSecurityElement>  
 <xref:System.ServiceModel.HttpTransportSecurity>  
 [<span data-ttu-id="92442-175">Zabezpieczanie usług i klientów</span><span class="sxs-lookup"><span data-stu-id="92442-175">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="92442-176">Powiązania</span><span class="sxs-lookup"><span data-stu-id="92442-176">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="92442-177">Konfigurowanie powiązań dostarczanych przez System</span><span class="sxs-lookup"><span data-stu-id="92442-177">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="92442-178">Konfigurowanie usług Windows Communication Foundation i klientów za pomocą powiązań</span><span class="sxs-lookup"><span data-stu-id="92442-178">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="92442-179">\<Powiązanie ></span><span class="sxs-lookup"><span data-stu-id="92442-179">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)