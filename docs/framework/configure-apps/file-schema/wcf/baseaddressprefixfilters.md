---
title: '&lt;baseAddressPrefixFilters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 39ceaf3377f1da7f3f953024e1207618df84bf1d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltbaseaddressprefixfiltersgt"></a><span data-ttu-id="861ab-102">&lt;baseAddressPrefixFilters&gt;</span><span class="sxs-lookup"><span data-stu-id="861ab-102">&lt;baseAddressPrefixFilters&gt;</span></span>
<span data-ttu-id="861ab-103">Reprezentuje kolekcję elementów konfiguracji, określających przebiegu filtry, które zawierają mechanizm wyboru odpowiednich powiązań usług Internet Information Services (IIS), odnośnie do hostowania [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aplikacji w usługach IIS.</span><span class="sxs-lookup"><span data-stu-id="861ab-103">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] application in IIS.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="861ab-104">\<baseAddressPrefixFilters > nie rozpoznano "localhost", zamiast tego użyj nazwy FQDN komputera.</span><span class="sxs-lookup"><span data-stu-id="861ab-104">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="861ab-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="861ab-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="861ab-106">\<ServiceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="861ab-106">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="861ab-107">Składnia</span><span class="sxs-lookup"><span data-stu-id="861ab-107">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>  
     <baseAddressPrefixFilters>  
        <add prefix="string"/>  
     </baseAddressPrefixFilters>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="861ab-108">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="861ab-108">Attributes and Elements</span></span>  
 <span data-ttu-id="861ab-109">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="861ab-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="861ab-110">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="861ab-110">Attributes</span></span>  
 <span data-ttu-id="861ab-111">Brak.</span><span class="sxs-lookup"><span data-stu-id="861ab-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="861ab-112">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="861ab-112">Child Elements</span></span>  
  
|<span data-ttu-id="861ab-113">Element</span><span class="sxs-lookup"><span data-stu-id="861ab-113">Element</span></span>|<span data-ttu-id="861ab-114">Opis</span><span class="sxs-lookup"><span data-stu-id="861ab-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="861ab-115">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="861ab-115">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddressprefixfilter.md)|<span data-ttu-id="861ab-116">Dodaje element konfiguracji, który określa filtr prefiks dla adres podstawowy używany przez hosta usługi.</span><span class="sxs-lookup"><span data-stu-id="861ab-116">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="861ab-117">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="861ab-117">Parent Elements</span></span>  
  
|<span data-ttu-id="861ab-118">Element</span><span class="sxs-lookup"><span data-stu-id="861ab-118">Element</span></span>|<span data-ttu-id="861ab-119">Opis</span><span class="sxs-lookup"><span data-stu-id="861ab-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="861ab-120">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="861ab-120">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="861ab-121">Definiuje typ, który usługę hostingu środowiskowego dla danego transportu.</span><span class="sxs-lookup"><span data-stu-id="861ab-121">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="861ab-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="861ab-122">Remarks</span></span>  
 <span data-ttu-id="861ab-123">Filtr prefiks umożliwia udostępnionego dostawcy hostingu określić, które identyfikatory URI są używane przez usługę.</span><span class="sxs-lookup"><span data-stu-id="861ab-123">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="861ab-124">Umożliwia on udostępniony hostów do obsługi wielu aplikacji za pomocą innego adresu podstawowego dla tego samego schematu w tej samej lokacji.</span><span class="sxs-lookup"><span data-stu-id="861ab-124">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="861ab-125">Witryn sieci Web IIS są kontenerami dla aplikacji wirtualnych, które zawierają katalogów wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="861ab-125">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="861ab-126">Za pomocą co najmniej jednego powiązania usługi IIS można uzyskać dostępu do aplikacji w lokacji.</span><span class="sxs-lookup"><span data-stu-id="861ab-126">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="861ab-127">Informacje Podaj powiązania usługi IIS: Protokół powiązania i informacje o wiązaniu.</span><span class="sxs-lookup"><span data-stu-id="861ab-127">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="861ab-128">Powiązanie protokół (na przykład HTTP) definiuje schemat, przez który dane są przesyłane i powiązanie informacji (na przykład adres IP, portu, nagłówka hosta) zawiera dane używane do uzyskania dostępu do witryny.</span><span class="sxs-lookup"><span data-stu-id="861ab-128">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="861ab-129">Usługi IIS obsługują określania wielokrotne powiązania usługi IIS dla każdej lokacji, co prowadzi do wielu adresu podstawowego dla każdego schematu.</span><span class="sxs-lookup"><span data-stu-id="861ab-129">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="861ab-130">Ponieważ [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] usługi hostowanej przez witrynę umożliwia powiązanie tylko jeden adres podstawowy dla każdego schematu, możesz użyć funkcji filtrowania prefiks wybierz wymagany adres podstawowy usługi hostowanej.</span><span class="sxs-lookup"><span data-stu-id="861ab-130">Because a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="861ab-131">Przychodzące adres podstawowy, dostarczone przez usługi IIS, są filtrowane z filtru listy opcjonalny prefiks.</span><span class="sxs-lookup"><span data-stu-id="861ab-131">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="861ab-132">Na przykład witryna może zawierać następujący adres podstawowy.</span><span class="sxs-lookup"><span data-stu-id="861ab-132">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="861ab-133">Można użyć następującego pliku konfiguracji do określenia filtru prefiks na poziomie elementu appdomain.</span><span class="sxs-lookup"><span data-stu-id="861ab-133">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="861ab-134">W tym przykładzie `net.tcp://test1.fabrikam.com:8000` i `http://test2.fabrikam.com:9000` są tylko podstawowy adres ich systemów, które mogą być przekazywane.</span><span class="sxs-lookup"><span data-stu-id="861ab-134">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="861ab-135">Domyślnie jeśli nie określono prefiksu, wszystkie adresy są przekazywane.</span><span class="sxs-lookup"><span data-stu-id="861ab-135">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="861ab-136">Określenie prefiksu umożliwia tylko pasujących adres podstawowy schemat przekazywane.</span><span class="sxs-lookup"><span data-stu-id="861ab-136">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="861ab-137">Filtr nie obsługuje żadnych symboli wieloznacznych.</span><span class="sxs-lookup"><span data-stu-id="861ab-137">The filter does not support any wildcards.</span></span> <span data-ttu-id="861ab-138">Ponadto baseAddresses dostarczonych przez usługi IIS może być adresy powiązany z innych systemów, które nie znajduje się w `baseAddressPrefixFilters` listy.</span><span class="sxs-lookup"><span data-stu-id="861ab-138">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="861ab-139">Tych adresów nie są odfiltrowywane.</span><span class="sxs-lookup"><span data-stu-id="861ab-139">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="861ab-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="861ab-140">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>  
 [<span data-ttu-id="861ab-141">Hosting</span><span class="sxs-lookup"><span data-stu-id="861ab-141">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)