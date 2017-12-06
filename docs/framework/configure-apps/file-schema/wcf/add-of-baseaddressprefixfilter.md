---
title: '&lt;add&gt; w &lt;baseAddressPrefixFilter&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd0a0d7fc5a83c78a56df796714e70e2e2a61767
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltbaseaddressprefixfiltergt"></a><span data-ttu-id="3a517-102">&lt;add&gt; w &lt;baseAddressPrefixFilter&gt;</span><span class="sxs-lookup"><span data-stu-id="3a517-102">&lt;add&gt; of &lt;baseAddressPrefixFilter&gt;</span></span>
<span data-ttu-id="3a517-103">Reprezentuje element konfiguracji, który określa przekazujące filtr, który zapewnia mechanizm wyboru odpowiednich powiązań usług Internet Information Services (IIS), odnośnie do hostowania [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aplikacji w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="3a517-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] application in IIS.</span></span>  
  
 <span data-ttu-id="3a517-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3a517-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3a517-105">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="3a517-105">\<ServiceHostingEnvironment></span></span>  
<span data-ttu-id="3a517-106">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="3a517-106">\<baseAddressPrefixFilters></span></span>  
<span data-ttu-id="3a517-107">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="3a517-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a517-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a517-108">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a517-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3a517-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3a517-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3a517-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a517-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3a517-111">Attributes</span></span>  
  
|<span data-ttu-id="3a517-112">Atrybut</span><span class="sxs-lookup"><span data-stu-id="3a517-112">Attribute</span></span>|<span data-ttu-id="3a517-113">Opis</span><span class="sxs-lookup"><span data-stu-id="3a517-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3a517-114">Prefiks</span><span class="sxs-lookup"><span data-stu-id="3a517-114">prefix</span></span>|<span data-ttu-id="3a517-115">Identyfikator URI, który jest używany do dopasowywania część adresu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="3a517-115">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a517-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3a517-116">Child Elements</span></span>  
 <span data-ttu-id="3a517-117">Brak.</span><span class="sxs-lookup"><span data-stu-id="3a517-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a517-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3a517-118">Parent Elements</span></span>  
  
|<span data-ttu-id="3a517-119">Element</span><span class="sxs-lookup"><span data-stu-id="3a517-119">Element</span></span>|<span data-ttu-id="3a517-120">Opis</span><span class="sxs-lookup"><span data-stu-id="3a517-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a517-121">\<baseAddressPrefixFilters ></span><span class="sxs-lookup"><span data-stu-id="3a517-121">\<baseAddressPrefixFilters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md)|<span data-ttu-id="3a517-122">Kolekcja elementów konfiguracji, filtrami przekazujące, które zapewniają mechanizm wyboru odpowiednich powiązań internetowych usług informacyjnych odnośnie do hostowania [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aplikacji w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="3a517-122">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a517-123">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a517-123">Remarks</span></span>  
 <span data-ttu-id="3a517-124">Filtr prefiks umożliwia udostępnionego dostawcy hostingu określić, które identyfikatory URI są używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="3a517-124">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="3a517-125">Umożliwia on udostępniony hostów do obsługi wielu aplikacji za pomocą innego adresu podstawowego dla tego samego schematu w tej samej lokacji.</span><span class="sxs-lookup"><span data-stu-id="3a517-125">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="3a517-126">Witryn sieci Web IIS są kontenerami dla aplikacji wirtualnych, które zawierają katalogów wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="3a517-126">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="3a517-127">Za pomocą co najmniej jednego powiązania usługi IIS można uzyskać dostępu do aplikacji w lokacji.</span><span class="sxs-lookup"><span data-stu-id="3a517-127">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="3a517-128">Informacje Podaj powiązania usługi IIS: Protokół powiązania i informacje o wiązaniu.</span><span class="sxs-lookup"><span data-stu-id="3a517-128">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="3a517-129">Powiązanie protokół (na przykład HTTP) definiuje schemat, przez który dane są przesyłane i powiązanie informacji (na przykład adres IP, portu, nagłówka hosta) zawiera dane używane do uzyskania dostępu do witryny.</span><span class="sxs-lookup"><span data-stu-id="3a517-129">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="3a517-130">Usługi IIS obsługują określania wielokrotne powiązania usługi IIS dla każdej lokacji, co prowadzi do wielu adresu podstawowego dla każdego schematu.</span><span class="sxs-lookup"><span data-stu-id="3a517-130">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="3a517-131">Ponieważ [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usługi hostowanej przez witrynę umożliwia powiązanie tylko jeden adres podstawowy dla każdego schematu, możesz użyć funkcji filtrowania prefiks wybierz wymagany adres podstawowy usługi hostowanej.</span><span class="sxs-lookup"><span data-stu-id="3a517-131">Because a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="3a517-132">Przychodzące adres podstawowy, dostarczone przez usługi IIS, są filtrowane z filtru listy opcjonalny prefiks.</span><span class="sxs-lookup"><span data-stu-id="3a517-132">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="3a517-133">Na przykład witryna może zawierać następujący adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="3a517-133">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="3a517-134">Można użyć następującego pliku konfiguracji do określenia filtru prefiks na poziomie elementu appdomain.</span><span class="sxs-lookup"><span data-stu-id="3a517-134">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="net.tcp://test1.fabrikam.com:8000"/>  
        <add prefix="http://test2.fabrikam.com:9000"/>  
    </baseAddressPrefixFilters>  
  </serviceHostingEnvironment>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="3a517-135">W tym przykładzie `net.tcp://test1.fabrikam.com:8000` i `http://test2.fabrikam.com:9000` są tylko podstawowy adres ich systemów, które mogą być przekazywane.</span><span class="sxs-lookup"><span data-stu-id="3a517-135">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="3a517-136">Domyślnie jeśli nie określono prefiksu, wszystkie adresy są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="3a517-136">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="3a517-137">Określenie prefiksu umożliwia tylko pasujących adres podstawowy schemat przekazywane.</span><span class="sxs-lookup"><span data-stu-id="3a517-137">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3a517-138">Filtr nie obsługuje żadnych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="3a517-138">The filter does not support any wildcards.</span></span> <span data-ttu-id="3a517-139">Ponadto baseAddresses dostarczonych przez usługi IIS może być adresy powiązany z innych systemów, które nie znajduje się w `baseAddressPrefixFilters` listy.</span><span class="sxs-lookup"><span data-stu-id="3a517-139">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="3a517-140">Tych adresów nie są odfiltrowywane.</span><span class="sxs-lookup"><span data-stu-id="3a517-140">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a517-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a517-141">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="3a517-142">Hosting</span><span class="sxs-lookup"><span data-stu-id="3a517-142">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)