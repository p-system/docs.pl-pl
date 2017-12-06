---
title: '&lt;Parametry&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bbb67714a58df0c5ccec86c7eac85a5194d780a5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="ltcommonparametersgt"></a><span data-ttu-id="96f7c-102">&lt;Parametry&gt;</span><span class="sxs-lookup"><span data-stu-id="96f7c-102">&lt;commonParameters&gt;</span></span>
<span data-ttu-id="96f7c-103">Reprezentuje kolekcję parametrów, które są globalnie używane w wielu usługach.</span><span class="sxs-lookup"><span data-stu-id="96f7c-103">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="96f7c-104">Ta kolekcja zazwyczaj uwzględnia parametry połączenia bazy danych, które mogą być współużytkowane przez usługi trwałe.</span><span class="sxs-lookup"><span data-stu-id="96f7c-104">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="96f7c-105">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="96f7c-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="96f7c-106">\<zachowania ></span><span class="sxs-lookup"><span data-stu-id="96f7c-106">\<behaviors></span></span>  
<span data-ttu-id="96f7c-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="96f7c-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="96f7c-108">\<zachowanie ></span><span class="sxs-lookup"><span data-stu-id="96f7c-108">\<behavior></span></span>  
<span data-ttu-id="96f7c-109">\<Obiekt workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="96f7c-109">\<workflowRuntime></span></span>  
<span data-ttu-id="96f7c-110">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="96f7c-110">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96f7c-111">Składnia</span><span class="sxs-lookup"><span data-stu-id="96f7c-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96f7c-112">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="96f7c-112">Attributes and Elements</span></span>  
 <span data-ttu-id="96f7c-113">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="96f7c-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96f7c-114">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="96f7c-114">Attributes</span></span>  
 <span data-ttu-id="96f7c-115">Brak.</span><span class="sxs-lookup"><span data-stu-id="96f7c-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="96f7c-116">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="96f7c-116">Child Elements</span></span>  
  
|<span data-ttu-id="96f7c-117">Element</span><span class="sxs-lookup"><span data-stu-id="96f7c-117">Element</span></span>|<span data-ttu-id="96f7c-118">Opis</span><span class="sxs-lookup"><span data-stu-id="96f7c-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96f7c-119">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="96f7c-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)|<span data-ttu-id="96f7c-120">Dodaje pary nazwa wartość wspólnych parametrów używane przez usługi do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="96f7c-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96f7c-121">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="96f7c-121">Parent Elements</span></span>  
  
|<span data-ttu-id="96f7c-122">Element</span><span class="sxs-lookup"><span data-stu-id="96f7c-122">Element</span></span>|<span data-ttu-id="96f7c-123">Opis</span><span class="sxs-lookup"><span data-stu-id="96f7c-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96f7c-124">\<Obiekt workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="96f7c-124">\<workflowRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|<span data-ttu-id="96f7c-125">Określa ustawienia dla wystąpienia <xref:System.Workflow.Runtime.WorkflowRuntime> hostingu opartego o przepływ pracy [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usług.</span><span class="sxs-lookup"><span data-stu-id="96f7c-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96f7c-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="96f7c-126">Remarks</span></span>  
 <span data-ttu-id="96f7c-127">`<commonParameters>` Element definiuje żadnych parametrów, które są globalnie używane w wielu usługach, na przykład `ConnectionString` przy użyciu <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="96f7c-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96f7c-128">Usługa śledzenia programu SQL nie zawsze używa `ConnectionString` wartość, jeśli został określony w `<commonParameters>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="96f7c-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="96f7c-129">Niektóre z jego operacji, takich jak pobieranie `StateMachineWorkflowInstance.StateHistory` właściwości może się nie powieść.</span><span class="sxs-lookup"><span data-stu-id="96f7c-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="96f7c-130">Aby obejść, określ `ConnectionString` atrybutu w sekcji konfiguracji dla dostawcy śledzenia, jak wskazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="96f7c-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="96f7c-131">Dla usług, które zatwierdzania pracy wsadów magazynów trwałości, takich jak <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> i <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, można włączyć je ponowić próbę ich transakcji przy użyciu `EnableRetries` parametru, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="96f7c-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<WorkflowRuntime Name="SampleApplication" UnloadOnIdle="false">  
    <commonParameters>  
        <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />  
        <add name="EnableRetries" value="True" />  
    </commonParameters>  
    <Services>  
        <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" EnableRetries="False" />   
     </Services>  
</WorkflowRuntime>  
```  
  
 <span data-ttu-id="96f7c-132">Zwróć uwagę, że `EnableRetries` parametr może być ustawiony na poziomie globalnym (jak pokazano w *CommonParameters* sekcji) lub dla poszczególnych usług obsługujące `EnableRetries` (jak pokazano w *usług*sekcji).</span><span class="sxs-lookup"><span data-stu-id="96f7c-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="96f7c-133">Następujący przykładowy kod przedstawia sposób programowo zmienić typowych parametrów.</span><span class="sxs-lookup"><span data-stu-id="96f7c-133">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="96f7c-134">Aby uzyskać więcej informacji o używaniu plik konfiguracji do kontrolowania zachowania <xref:System.Workflow.Runtime.WorkflowRuntime> obiektu aplikacji hosta Windows Workflow Foundation, zobacz [pliki konfiguracji przepływu pracy](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span><span class="sxs-lookup"><span data-stu-id="96f7c-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span></span>  
  
## <a name="example"></a><span data-ttu-id="96f7c-135">Przykład</span><span class="sxs-lookup"><span data-stu-id="96f7c-135">Example</span></span>  
  
```xml  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## <a name="see-also"></a><span data-ttu-id="96f7c-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="96f7c-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 [<span data-ttu-id="96f7c-137">Pliki konfiguracji przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="96f7c-137">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)  
 [<span data-ttu-id="96f7c-138">\<Dodaj ></span><span class="sxs-lookup"><span data-stu-id="96f7c-138">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)