---
title: 'Instrukcje: Tworzenie bezpiecznej sesji'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: f2393209352f18eb25b9837ca1ad8ca2746b91d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="eff47-102">Instrukcje: Tworzenie bezpiecznej sesji</span><span class="sxs-lookup"><span data-stu-id="eff47-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="eff47-103">Z wyjątkiem produktów [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) powiązanie, powiązania dostarczane przez system w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] automatycznie użyj bezpiecznych sesji po włączeniu zabezpieczeń wiadomości.</span><span class="sxs-lookup"><span data-stu-id="eff47-103">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="eff47-104">Domyślnie bezpiecznej sesji po serwera sieci Web, który zostanie odtworzony.</span><span class="sxs-lookup"><span data-stu-id="eff47-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="eff47-105">Podczas ustanawiania sesji bezpiecznych, klient i usługa pamięci podręcznej klucza, który jest skojarzony z bezpieczną sesję.</span><span class="sxs-lookup"><span data-stu-id="eff47-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="eff47-106">Jak komunikaty są wymieniane, są przekazywane tylko identyfikator, aby klucz pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="eff47-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="eff47-107">Jeśli serwer sieci Web zostanie odtworzony, pamięci podręcznej odtworzeniem również, tak, aby serwer sieci Web nie może pobrać klucz pamięci podręcznej dla identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="eff47-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="eff47-108">W takim przypadku jest zwracany wyjątek powrotem do klienta.</span><span class="sxs-lookup"><span data-stu-id="eff47-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="eff47-109">Serwer sieci Web odtwarzane przełączniki bezpiecznych sesji, które używają token kontekstu zabezpieczeń stanową (SCT).</span><span class="sxs-lookup"><span data-stu-id="eff47-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="eff47-110">w ramach bezpiecznej sesji przy użyciu stanowe SCT zobacz [porady: Tworzenie tokenu kontekstu zabezpieczeń dla bezpiecznej sesji](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span><span class="sxs-lookup"><span data-stu-id="eff47-110"> using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="eff47-111">Aby określić, że usługa używa bezpiecznych sesji przy użyciu jednego powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="eff47-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
-   <span data-ttu-id="eff47-112">Skonfiguruj usługę do używania wiązania dostarczane przez system, które obsługuje zabezpieczenia wiadomości.</span><span class="sxs-lookup"><span data-stu-id="eff47-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="eff47-113">Z wyjątkiem produktów [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) powiązanie, gdy powiązania dostarczane przez system są skonfigurowane do korzystania z zabezpieczeń wiadomości [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatycznie używa bezpiecznych sesji.</span><span class="sxs-lookup"><span data-stu-id="eff47-113">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatically uses secure sessions.</span></span> <span data-ttu-id="eff47-114">W poniższej tabeli wymieniono powiązania dostarczane przez system obsługi zabezpieczeń komunikatów i określa, czy zabezpieczenia wiadomości są domyślnego mechanizmu zabezpieczeń.</span><span class="sxs-lookup"><span data-stu-id="eff47-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="eff47-115">Powiązania dostarczane przez system</span><span class="sxs-lookup"><span data-stu-id="eff47-115">System-provided binding</span></span>|<span data-ttu-id="eff47-116">Element konfiguracji</span><span class="sxs-lookup"><span data-stu-id="eff47-116">Configuration element</span></span>|<span data-ttu-id="eff47-117">Zabezpieczenia komunikatów na domyślnie</span><span class="sxs-lookup"><span data-stu-id="eff47-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[<span data-ttu-id="eff47-118">\<basicHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="eff47-118">\<basicHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="eff47-119">Nie</span><span class="sxs-lookup"><span data-stu-id="eff47-119">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[<span data-ttu-id="eff47-120">\<wsHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="eff47-120">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="eff47-121">Tak</span><span class="sxs-lookup"><span data-stu-id="eff47-121">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[<span data-ttu-id="eff47-122">\<wsDualHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="eff47-122">\<wsDualHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="eff47-123">Tak</span><span class="sxs-lookup"><span data-stu-id="eff47-123">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[<span data-ttu-id="eff47-124">\<wsFederationHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="eff47-124">\<wsFederationHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="eff47-125">Tak</span><span class="sxs-lookup"><span data-stu-id="eff47-125">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[<span data-ttu-id="eff47-126">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="eff47-126">\<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="eff47-127">Nie</span><span class="sxs-lookup"><span data-stu-id="eff47-127">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[<span data-ttu-id="eff47-128">\<netMsmqBinding ></span><span class="sxs-lookup"><span data-stu-id="eff47-128">\<netMsmqBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="eff47-129">Nie</span><span class="sxs-lookup"><span data-stu-id="eff47-129">No</span></span>|  
  
     <span data-ttu-id="eff47-130">Poniższy przykład kodu wykorzystuje konfiguracji, aby określić powiązanie o nazwie `wsHttpBinding_Calculator` używającą [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), zabezpieczenia wiadomości i bezpieczne sesje.</span><span class="sxs-lookup"><span data-stu-id="eff47-130">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
    ```xml  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="eff47-131">Poniższy przykład kodu Określa, że [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), zabezpieczenia wiadomości i bezpieczne sesje są używane do zabezpieczania `secureCalculator` usługi.</span><span class="sxs-lookup"><span data-stu-id="eff47-131">The following code example specifies that the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="eff47-132">Bezpieczne sesje, można wyłączyć dla [ <wsHttpBinding> ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) przez ustawienie `establishSecurityContext` atrybutu `false`.</span><span class="sxs-lookup"><span data-stu-id="eff47-132">Secure sessions can be turned off for the [<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="eff47-133">Dla innych dostarczane przez system powiązań można tylko wyłączyć bezpiecznej sesji przez utworzenie niestandardowego powiązania.</span><span class="sxs-lookup"><span data-stu-id="eff47-133">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="eff47-134">Aby określić, że usługa używa bezpiecznych sesji przy użyciu wiązania niestandardowego</span><span class="sxs-lookup"><span data-stu-id="eff47-134">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
-   <span data-ttu-id="eff47-135">Tworzenie niestandardowego powiązania, który określa, że wiadomości SOAP są chronione przez bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="eff47-135">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="eff47-136">Tworzenie niestandardowego powiązania, zobacz [porady: dostosowywanie powiązania System-Provided](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span><span class="sxs-lookup"><span data-stu-id="eff47-136"> creating a custom binding, see [How to: Customize a System-Provided Binding](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="eff47-137">Poniższy przykład kodu wykorzystuje konfiguracji do określenia niestandardowego powiązania tej wiadomości za pomocą bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="eff47-137">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
    ```xml  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="eff47-138">Poniższy przykład kodu tworzy niestandardowego powiązania, który używa <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> tryb uwierzytelniania do ładowania początkowego bezpiecznej sesji.</span><span class="sxs-lookup"><span data-stu-id="eff47-138">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="eff47-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eff47-139">See Also</span></span>  
 [<span data-ttu-id="eff47-140">Omówienie powiązań WCF</span><span class="sxs-lookup"><span data-stu-id="eff47-140">WCF Bindings Overview</span></span>](../../../../docs/framework/wcf/bindings-overview.md)