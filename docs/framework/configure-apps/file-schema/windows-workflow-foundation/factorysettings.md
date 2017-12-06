---
title: '&lt;factorySettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 202aad17-1b8b-4c87-ad57-4ca5de18ed35
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b0df9a6bd4da9131961e0ca35ab75109053b97c3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltfactorysettingsgt"></a><span data-ttu-id="947b6-102">&lt;factorySettings&gt;</span><span class="sxs-lookup"><span data-stu-id="947b6-102">&lt;factorySettings&gt;</span></span>
<span data-ttu-id="947b6-103">Określa ustawienia pamięci podręcznej fabryki kanału.</span><span class="sxs-lookup"><span data-stu-id="947b6-103">Specifies the settings of the channel factory cache.</span></span>  
  
<span data-ttu-id="947b6-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="947b6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="947b6-105">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="947b6-105">\<behaviors></span></span>  
<span data-ttu-id="947b6-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="947b6-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="947b6-107">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="947b6-107">\<behavior></span></span>  
<span data-ttu-id="947b6-108">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="947b6-108">\<sendMessageChannelCache></span></span>  
<span data-ttu-id="947b6-109">\<factorySettings ></span><span class="sxs-lookup"><span data-stu-id="947b6-109">\<factorySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="947b6-110">Składnia</span><span class="sxs-lookup"><span data-stu-id="947b6-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean" >
        <factorySettings idleTimeout="TimeSpan" 
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="947b6-111">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="947b6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="947b6-112">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="947b6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="947b6-113">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="947b6-113">Attributes</span></span>  
  
|<span data-ttu-id="947b6-114">Atrybut</span><span class="sxs-lookup"><span data-stu-id="947b6-114">Attribute</span></span>|<span data-ttu-id="947b6-115">Opis</span><span class="sxs-lookup"><span data-stu-id="947b6-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="947b6-116">idleTimeout</span><span class="sxs-lookup"><span data-stu-id="947b6-116">idleTimeout</span></span>|<span data-ttu-id="947b6-117">Wartość przedziału czasu, która określa maksymalny interwał czasu, dla którego obiekt może być nieaktywna w pamięci podręcznej zanim zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="947b6-117">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="947b6-118">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="947b6-118">leaseTimeout</span></span>|<span data-ttu-id="947b6-119">Wartość TimeSpan określający okres czasu, po którym obiekt zostanie usunięty z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="947b6-119">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="947b6-120">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="947b6-120">maxItemsInCache</span></span>|<span data-ttu-id="947b6-121">Liczba całkowita określająca maksymalną liczbę obiektów, które mogą być w pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="947b6-121">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="947b6-122">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="947b6-122">Child Elements</span></span>  
 <span data-ttu-id="947b6-123">Brak.</span><span class="sxs-lookup"><span data-stu-id="947b6-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="947b6-124">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="947b6-124">Parent Elements</span></span>  
  
|<span data-ttu-id="947b6-125">Element</span><span class="sxs-lookup"><span data-stu-id="947b6-125">Element</span></span>|<span data-ttu-id="947b6-126">Opis</span><span class="sxs-lookup"><span data-stu-id="947b6-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="947b6-127">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="947b6-127">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="947b6-128">Zachowanie usługi umożliwiające dostosowywanie udostępnianie poziomy, ustawienia pamięci podręcznej fabryki kanału i ustawienia pamięci podręcznej kanału dla przepływów pracy, który wysyła wiadomości do punktów końcowych usługi przy użyciu działań dotyczących komunikatów wysyłania pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="947b6-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="947b6-129">Uwagi</span><span class="sxs-lookup"><span data-stu-id="947b6-129">Remarks</span></span>  
 <span data-ttu-id="947b6-130">To zachowanie usługi jest przeznaczony do wysyłania wiadomości do punktów końcowych usługi przepływami pracy.</span><span class="sxs-lookup"><span data-stu-id="947b6-130">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="947b6-131">Te przepływy pracy są zwykle przepływy pracy klienta, ale mogą być również usługi przepływu pracy, które znajdują się w <xref:System.ServiceModel.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="947b6-131">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="947b6-132">Domyślnie w przepływie pracy pracujących na <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej używane przez <xref:System.ServiceModel.Activities.Send> wiadomości działania jest udostępniane dla całego wszystkich wystąpień przepływu pracy w <xref:System.ServiceModel.WorkflowServiceHost> (host poziomie buforowania).</span><span class="sxs-lookup"><span data-stu-id="947b6-132">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="947b6-133">Klient przepływu pracy, który nie jest obsługiwany przez <xref:System.ServiceModel.WorkflowServiceHost>, pamięci podręcznej jest dostępna tylko dla wystąpienia przepływu pracy (buforowanie poziomie wystąpienia).</span><span class="sxs-lookup"><span data-stu-id="947b6-133">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="947b6-134">Buforowanie jest domyślnie wyłączony dla dowolnego działania wysyłania w zawierającej punktów końcowych zdefiniowanych w konfiguracji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="947b6-134">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="947b6-135">jak zmienić domyślne pamięci podręcznej udostępnianie poziomów i ustawienia dla fabryki kanałów i pamięci podręcznej kanału pamięci podręcznej, zobacz [Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span><span class="sxs-lookup"><span data-stu-id="947b6-135"> how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="947b6-136">Przykład</span><span class="sxs-lookup"><span data-stu-id="947b6-136">Example</span></span>  
 <span data-ttu-id="947b6-137">W usłudze hostowanej przepływu pracy można określić fabrykę pamięci podręcznej i kanał ustawienia pamięci podręcznej w pliku konfiguracyjnym aplikacji.</span><span class="sxs-lookup"><span data-stu-id="947b6-137">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="947b6-138">W tym celu należy dodać zachowanie usługi, które zawiera ustawienia pamięci podręcznej pamięci podręcznej fabryki i kanał i dodać to zachowanie usługi z usługą.</span><span class="sxs-lookup"><span data-stu-id="947b6-138">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="947b6-139">W poniższym przykładzie pokazano zawartość pliku konfiguracji, który zawiera **MyChannelCacheBehavior** zachowania usługi przy użyciu ustawień pamięci podręcznej pamięci podręcznej i kanał fabrycznej.</span><span class="sxs-lookup"><span data-stu-id="947b6-139">The following example shows the contents of a configuration file that contains the **MyChannelCacheBehavior**  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="947b6-140">To zachowanie usługi zostanie dodany do usługi za pośrednictwem **behaviorConfiguarion** atrybutu.</span><span class="sxs-lookup"><span data-stu-id="947b6-140">This service behavior is added to the service through the **behaviorConfiguarion** attribute.</span></span>  
  
```xml  
<configuration>    
  <system.serviceModel>  
    <!-- List of other config sections here -->   
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->   
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="947b6-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="947b6-141">See Also</span></span>  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache>  
 <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>  
 <xref:System.ServiceModel.Activities.Send>  
 <xref:System.ServiceModel.Activities.ChannelCacheSettings>  
 [<span data-ttu-id="947b6-142">Poziomy zmiana współużytkowania pamięci podręcznej dla działań wysyłania</span><span class="sxs-lookup"><span data-stu-id="947b6-142">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)