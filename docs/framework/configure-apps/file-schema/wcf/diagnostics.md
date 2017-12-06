---
title: '&lt;Diagnostyka&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0c2f95c4-cc12-4fb5-a70c-7fc6fa95db58
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d558bf6ac71a3a19fb8c28989fd9262e7a13f0f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiagnosticsgt"></a><span data-ttu-id="95902-102">&lt;Diagnostyka&gt;</span><span class="sxs-lookup"><span data-stu-id="95902-102">&lt;diagnostics&gt;</span></span>
<span data-ttu-id="95902-103">`diagnostics` Element definiuje ustawienia używane przez administratora w czasie wykonywania inspekcji i kontroli.</span><span class="sxs-lookup"><span data-stu-id="95902-103">The `diagnostics` element defines settings that can be used by an administrator for run-time inspection and control.</span></span>  
  
 <span data-ttu-id="95902-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="95902-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="95902-105">\<Diagnostyka ></span><span class="sxs-lookup"><span data-stu-id="95902-105">\<diagnostics></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95902-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="95902-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics etwProviderId="String"       performanceCounters="Off/ServiceOnly/All/Default"              wmiProviderEnabled="Boolean" >       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
       <messageLogging logEntireMessage="Boolean"  
          logMalformedMessages="Boolean"  
          logMessagesAtServiceLevel="Boolean"  
          logMessagesAtTransportLevel="Boolean"  
          maxMessagesToLog="Integer"  
          maxSizeOfMessageToLog="Integer" >  
          <filters>  
             <clear />  
          </filters>  
       </messageLogging>  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="95902-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="95902-107">Attributes and Elements</span></span>  
 <span data-ttu-id="95902-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="95902-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="95902-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="95902-109">Attributes</span></span>  
  
|<span data-ttu-id="95902-110">Atrybut</span><span class="sxs-lookup"><span data-stu-id="95902-110">Attribute</span></span>|<span data-ttu-id="95902-111">Opis</span><span class="sxs-lookup"><span data-stu-id="95902-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="95902-112">etwProviderId</span><span class="sxs-lookup"><span data-stu-id="95902-112">etwProviderId</span></span>|<span data-ttu-id="95902-113">Ciąg określający identyfikator dostawcy śledzenia zdarzeń, która zapisuje zdarzenia do sesji ETW.</span><span class="sxs-lookup"><span data-stu-id="95902-113">A string that specifies the identifier for the Event-Tracing provider, which writes events to ETW sessions.</span></span>|  
|<span data-ttu-id="95902-114">liczniki wydajności</span><span class="sxs-lookup"><span data-stu-id="95902-114">performanceCounters</span></span>|<span data-ttu-id="95902-115">Określa, czy są włączone liczniki wydajności dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="95902-115">Specifies whether performance counters for the assembly are enabled.</span></span> <span data-ttu-id="95902-116">Prawidłowe wartości to</span><span class="sxs-lookup"><span data-stu-id="95902-116">Valid values are</span></span><br /><br /> <span data-ttu-id="95902-117">-Off: Liczniki wydajności są wyłączone.</span><span class="sxs-lookup"><span data-stu-id="95902-117">-   Off: Performance counters are disabled.</span></span><br /><span data-ttu-id="95902-118">-ServiceOnly: Jest włączona tylko liczniki wydajności istotne dla tej usługi.</span><span class="sxs-lookup"><span data-stu-id="95902-118">-   ServiceOnly: Only performance counters relevant to this service is enabled.</span></span><br /><span data-ttu-id="95902-119">-Wszystkie: Wydajności liczniki można wyświetlać w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="95902-119">-   All: Performance counters can be viewed at runtime.</span></span><br /><span data-ttu-id="95902-120">— Wartość domyślna: _WCF_Admin wystąpienia licznika wydajności pojedynczego jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="95902-120">-   Default: A single performance counter instance _WCF_Admin is created.</span></span> <span data-ttu-id="95902-121">To wystąpienie jest używane umożliwia zbieranie danych SQM używane przez infrastrukturę.</span><span class="sxs-lookup"><span data-stu-id="95902-121">This instance is used to enable the collection of SQM data for used by the infrastructure.</span></span> <span data-ttu-id="95902-122">Brak wartości liczników dla tego wystąpienia są aktualizowane i w związku z tym pozostanie od zera.</span><span class="sxs-lookup"><span data-stu-id="95902-122">None of the counter values for this instance are updated and therefore will remain at zero.</span></span> <span data-ttu-id="95902-123">Jest to wartość domyślna, jeśli konfiguracja nie jest stosowany w przypadku usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="95902-123">This is the default value if no configuration is present for WCF.</span></span>|  
|<span data-ttu-id="95902-124">wmiProviderEnabled</span><span class="sxs-lookup"><span data-stu-id="95902-124">wmiProviderEnabled</span></span>|<span data-ttu-id="95902-125">Wartość logiczna określająca czy włączone jest dostawca WMI dla zestawu.</span><span class="sxs-lookup"><span data-stu-id="95902-125">A Boolean value that specifies whether the WMI provider for the assembly is enabled.</span></span> <span data-ttu-id="95902-126">Dostawca WMI jest wymagany dla użytkownik może uzyskać dostępu do środowiska wykonawczego do inspekcji i kontroli funkcji Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="95902-126">The WMI provider is required for user to gain run-time access to the inspection and control features of Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="95902-127">Wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="95902-127">The default is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="95902-128">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="95902-128">Child Elements</span></span>  
  
|<span data-ttu-id="95902-129">Element</span><span class="sxs-lookup"><span data-stu-id="95902-129">Element</span></span>|<span data-ttu-id="95902-130">Opis</span><span class="sxs-lookup"><span data-stu-id="95902-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="95902-131">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="95902-131">\<endToEndTracing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endtoendtracing.md)|<span data-ttu-id="95902-132">Element konfiguracji, który umożliwia włączanie i wyłączanie różnych aspektów śledzenia end-to-end podczas uruchamiania aplikacji usługi.</span><span class="sxs-lookup"><span data-stu-id="95902-132">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>|  
|[<span data-ttu-id="95902-133">\<messageLogging ></span><span class="sxs-lookup"><span data-stu-id="95902-133">\<messageLogging></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)|<span data-ttu-id="95902-134">Opisuje ustawienia rejestrowania komunikatów usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="95902-134">Describes the settings for WCF message logging.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="95902-135">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="95902-135">Parent Elements</span></span>  
  
|<span data-ttu-id="95902-136">Element</span><span class="sxs-lookup"><span data-stu-id="95902-136">Element</span></span>|<span data-ttu-id="95902-137">Opis</span><span class="sxs-lookup"><span data-stu-id="95902-137">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="95902-138">ServiceModel</span><span class="sxs-lookup"><span data-stu-id="95902-138">serviceModel</span></span>|<span data-ttu-id="95902-139">Element główny wszystkich elementów konfiguracji usługi WCF.</span><span class="sxs-lookup"><span data-stu-id="95902-139">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95902-140">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95902-140">Remarks</span></span>  
 <span data-ttu-id="95902-141">`diagnostics` Sekcja definiuje ustawień diagnostycznych dla wszystkich usług znajduje się w zestawie.</span><span class="sxs-lookup"><span data-stu-id="95902-141">The `diagnostics` section defines the diagnostics settings for all services located in an assembly.</span></span> <span data-ttu-id="95902-142">Nie jest możliwe do definiowania ustawień diagnostyki oddzielne na poziomie usługi, chyba że istnieje tylko jedna usługa w zestawie.</span><span class="sxs-lookup"><span data-stu-id="95902-142">It is not possible to define separate diagnostics settings at the service level unless there is only one service in the assembly.</span></span> <span data-ttu-id="95902-143">Atrybuty są ustawione zgodnie z wymaganiami sekcji.</span><span class="sxs-lookup"><span data-stu-id="95902-143">Attributes are set according to the requirements of the section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95902-144">Przykład</span><span class="sxs-lookup"><span data-stu-id="95902-144">Example</span></span>  
  
```xml  
<diagnostics wmiProviderEnabled="false"  
       performanceCounters="all">  
       <messageLogging logEntireMessage="true"  
          logMalformedMessages="true"  
          logMessagesAtServiceLevel="true"  
          logMessagesAtTransportLevel="true"  
          maxMessagesToLog="42"  
          maxSizeOfMessageToLog="42">  
         <filters>  
         <clear />  
    </filters>  
       </messageLogging>  
</diagnostics>  
```  
  
## <a name="see-also"></a><span data-ttu-id="95902-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95902-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>