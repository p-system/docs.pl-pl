---
title: "Instrukcje: Konfigurowanie zachowania dotyczącego nieobsługiwanego wyjątku przepływu pracy przy użyciu klasy WorkflowServiceHost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 51b25c86-292c-43e4-8d13-273d2badc8ad
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9e85f8010528d18133ccd9d98de8479ea0de343d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-configure-workflow-unhandled-exception-behavior-with-workflowservicehost"></a><span data-ttu-id="946b3-102">Instrukcje: Konfigurowanie zachowania dotyczącego nieobsługiwanego wyjątku przepływu pracy przy użyciu klasy WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="946b3-102">How to: Configure Workflow Unhandled Exception Behavior with WorkflowServiceHost</span></span>
<span data-ttu-id="946b3-103"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> Jest zachowanie, które można określić akcję do wykonania, jeśli wystąpi nieobsługiwany wyjątek w przepływie pracy hostowanych w <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="946b3-103">The <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> is a behavior that enables you to specify the action to take if an unhandled exception occurs within a workflow hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span> <span data-ttu-id="946b3-104">W tym temacie przedstawiono sposób skonfigurowania tego zachowania w pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="946b3-104">This topic shows how to configure this behavior in a configuration file.</span></span>  
  
### <a name="to-configure-workflowunhandledexceptionbehavior"></a><span data-ttu-id="946b3-105">Aby skonfigurować WorkflowUnhandledExceptionBehavior</span><span class="sxs-lookup"><span data-stu-id="946b3-105">To configure WorkflowUnhandledExceptionBehavior</span></span>  
  
1.  <span data-ttu-id="946b3-106">Dodaj <`workflowUnhandledException`> elementu <`behavior`> w elemencie <`serviceBehaviors`> element, przy użyciu `action` atrybutu, aby określić akcję wykonywaną, gdy wystąpi nieobsługiwany wyjątek, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="946b3-106">Add a <`workflowUnhandledException`> element in a <`behavior`> element within a <`serviceBehaviors`> element, using the `action` attribute to specify the action to take when an unhandled exception occurs as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <workflowUnhandledException action="abandonAndSuspend"/>   
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="946b3-107">Uproszczona konfiguracja używa powyższego przykładu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="946b3-107">The preceding configuration sample is using simplified configuration.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="946b3-108">[Uproszczony konfiguracji](../../../../docs/framework/wcf/simplified-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="946b3-108"> [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md).</span></span>  
  
     <span data-ttu-id="946b3-109">To zachowanie można skonfigurować w kodzie, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="946b3-109">This behavior can be configured in code as shown in the following example.</span></span>  
  
    ```csharp  
    host.Description.Behaviors.Add(new WorkflowUnhandledExceptionBehavior { Action = WorkflowUnhandledExceptionAction.AbandonAndSuspend });  
    ```  
  
     <span data-ttu-id="946b3-110">`action` Atrybut <`workflowUnhandledException`> element może być ustawiony na jedną z następujących wartości:</span><span class="sxs-lookup"><span data-stu-id="946b3-110">The `action` attribute of the <`workflowUnhandledException`> element can be set to one of the following values:</span></span>  
  
     <span data-ttu-id="946b3-111">**porzucenia**</span><span class="sxs-lookup"><span data-stu-id="946b3-111">**abandon**</span></span>  
     <span data-ttu-id="946b3-112">Przerywa wystąpienia w pamięci bez modyfikowania stanu trwałego wystąpienia (tj. Przywracanie do ostatniego punktu utrwalanie).</span><span class="sxs-lookup"><span data-stu-id="946b3-112">Aborts the instance in memory without touching the persisted instance state (that is, roll back to the last persist point).</span></span>  
  
     <span data-ttu-id="946b3-113">**abandonAndSuspend**</span><span class="sxs-lookup"><span data-stu-id="946b3-113">**abandonAndSuspend**</span></span>  
     <span data-ttu-id="946b3-114">Przerywa wystąpienia w pamięci i aktualizuje trwałego wystąpienia zostanie zawieszona.</span><span class="sxs-lookup"><span data-stu-id="946b3-114">Aborts the instance in memory and updates the persisted instance to be suspended.</span></span>  
  
     <span data-ttu-id="946b3-115">**Anuluj**</span><span class="sxs-lookup"><span data-stu-id="946b3-115">**cancel**</span></span>  
     <span data-ttu-id="946b3-116">Wywołuje anulowania obsługi dla tego wystąpienia, a następnie kończy wystąpienia w pamięci, co może też spowodować usunięcie go z magazynu wystąpień</span><span class="sxs-lookup"><span data-stu-id="946b3-116">Calls cancellation handlers for the instance and then completes the instance in memory, which may also remove it from the instance store</span></span>  
  
     <span data-ttu-id="946b3-117">**Zakończenie**</span><span class="sxs-lookup"><span data-stu-id="946b3-117">**terminate**</span></span>  
     <span data-ttu-id="946b3-118">Kończy wystąpienia w pamięci i usuwa go z magazynu wystąpień.</span><span class="sxs-lookup"><span data-stu-id="946b3-118">Completes the instance in memory and removes it from the instance store.</span></span>  
  
     [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="946b3-119"><xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, zobacz [rozszerzalność hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span><span class="sxs-lookup"><span data-stu-id="946b3-119"> <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>, see [Workflow Service Host Extensibility](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="946b3-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="946b3-120">See Also</span></span>  
 [<span data-ttu-id="946b3-121">Rozszerzalność hosta usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="946b3-121">Workflow Service Host Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/workflow-service-host-extensibility.md)  
 [<span data-ttu-id="946b3-122">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="946b3-122">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)