---
title: '&lt;x509SecurityTokenHandlerRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 66d4e0d6a121f807f5f372b3f39577b0bb3c4ca6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltx509securitytokenhandlerrequirementgt"></a><span data-ttu-id="d7b75-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="d7b75-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="d7b75-103">Zapewnia opcjonalne konfigurację <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> klasy lub klas pochodnych.</span><span class="sxs-lookup"><span data-stu-id="d7b75-103">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="d7b75-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="d7b75-104">\<system.identityModel></span></span>  
<span data-ttu-id="d7b75-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d7b75-105">\<identityConfiguration></span></span>  
<span data-ttu-id="d7b75-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="d7b75-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d7b75-107">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="d7b75-107">\<add></span></span>  
<span data-ttu-id="d7b75-108">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="d7b75-108">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7b75-109">Składnia</span><span class="sxs-lookup"><span data-stu-id="d7b75-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7b75-110">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d7b75-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d7b75-111">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d7b75-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7b75-112">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d7b75-112">Attributes</span></span>  
  
|<span data-ttu-id="d7b75-113">Atrybut</span><span class="sxs-lookup"><span data-stu-id="d7b75-113">Attribute</span></span>|<span data-ttu-id="d7b75-114">Opis</span><span class="sxs-lookup"><span data-stu-id="d7b75-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d7b75-115">tryb certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="d7b75-115">certificateValidationMode</span></span>|<span data-ttu-id="d7b75-116"><xref:System.ServiceModel.Security.X509CertificateValidationMode> Wartość, która określa tryb walidacji do użycia na potrzeby certyfikatów X.509.</span><span class="sxs-lookup"><span data-stu-id="d7b75-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="d7b75-117">Wartość domyślna to "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="d7b75-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="d7b75-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="d7b75-118">mapToWindows</span></span>|<span data-ttu-id="d7b75-119">Określa, czy programu obsługi tokenów należy mapować sprawdzania poprawności tokenu konto systemu Windows przy użyciu nazwy UPN oświadczenia przychodzącego.</span><span class="sxs-lookup"><span data-stu-id="d7b75-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="d7b75-120">Wartość domyślna to "false".</span><span class="sxs-lookup"><span data-stu-id="d7b75-120">The default is "false".</span></span>|  
|<span data-ttu-id="d7b75-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="d7b75-121">revocationMode</span></span>|<span data-ttu-id="d7b75-122"><xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Wartość, która określa tryb odwołania dla certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="d7b75-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="d7b75-123">Wartość domyślna to "Online".</span><span class="sxs-lookup"><span data-stu-id="d7b75-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="d7b75-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="d7b75-124">trustedStoreLocation</span></span>|<span data-ttu-id="d7b75-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> wartość, która określa magazynu certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="d7b75-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="d7b75-126">Wartością domyślną jest "Komputer lokalny".</span><span class="sxs-lookup"><span data-stu-id="d7b75-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="d7b75-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="d7b75-127">certificateValidator</span></span>|<span data-ttu-id="d7b75-128">Typ niestandardowy, która jest pochodną <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="d7b75-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="d7b75-129">Jeśli `certificateValidationMode` atrybutu jest "Custom", wystąpienie tego typu jest używany do sprawdzania poprawności wystawcy certyfikatu.</span><span class="sxs-lookup"><span data-stu-id="d7b75-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7b75-130">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d7b75-130">Child Elements</span></span>  
 <span data-ttu-id="d7b75-131">Brak</span><span class="sxs-lookup"><span data-stu-id="d7b75-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7b75-132">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d7b75-132">Parent Elements</span></span>  
  
|<span data-ttu-id="d7b75-133">Element</span><span class="sxs-lookup"><span data-stu-id="d7b75-133">Element</span></span>|<span data-ttu-id="d7b75-134">Opis</span><span class="sxs-lookup"><span data-stu-id="d7b75-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7b75-135">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="d7b75-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="d7b75-136">Dodaje określony zabezpieczenia programu obsługi tokenów do kolekcji programu obsługi tokenów.</span><span class="sxs-lookup"><span data-stu-id="d7b75-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d7b75-137">Przykład</span><span class="sxs-lookup"><span data-stu-id="d7b75-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```