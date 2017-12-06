---
title: "Równoległe przechowywanie wersji w klasie WorkflowServiceHost"
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
ms.assetid: 60887eed-df40-4412-b812-41e1dd329d15
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f3629778ded2b690f8169223101d89cb551e1449
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="side-by-side-versioning-in-workflowservicehost"></a><span data-ttu-id="17b71-102">Równoległe przechowywanie wersji w klasie WorkflowServiceHost</span><span class="sxs-lookup"><span data-stu-id="17b71-102">Side by Side Versioning in WorkflowServiceHost</span></span>
<span data-ttu-id="17b71-103"><xref:System.ServiceModel.Activities.WorkflowServiceHost> Wprowadzone w systemie kontroli wersji side-by-side [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] oferuje możliwość obsługi wielu wersji usługi przepływu pracy w jednym punkcie końcowym.</span><span class="sxs-lookup"><span data-stu-id="17b71-103">The <xref:System.ServiceModel.Activities.WorkflowServiceHost> side-by-side versioning introduced in [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] provides the capability to host multiple versions of a workflow service on a single endpoint.</span></span> <span data-ttu-id="17b71-104">Funkcjonalność side-by-side umożliwia usłudze przepływu pracy można skonfigurować tak, aby nowe wystąpienia usługi przepływu pracy są tworzone przy użyciu nowych definicji przepływu pracy, podczas uruchamiania wystąpienia pełną przy użyciu istniejącej definicji.</span><span class="sxs-lookup"><span data-stu-id="17b71-104">The side-by-side functionality provided allows a workflow service to be configured so that new instances of the workflow service are created using the new workflow definition, while running instances complete using the existing definition.</span></span> <span data-ttu-id="17b71-105">Ten temat zawiera omówienie sposobu użycia wykonywania side-by-side usługi przepływu pracy <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="17b71-105">This topic provides an overview of workflow service side-by-side execution using <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17b71-106">Aby pobrać przykład i obejrzyj przewodnik wideo dotyczący versioning side-by-side usługi przepływu pracy, zobacz [równoległe przechowywanie wersji usługi przepływu pracy Xamlx Web-Hosted](http://go.microsoft.com/fwlink/?LinkId=393746).</span><span class="sxs-lookup"><span data-stu-id="17b71-106">To download a sample and watch a video walkthrough of workflow service side-by-side versioning, see [Side by Side Versioning with a Web-Hosted Xamlx Workflow Service](http://go.microsoft.com/fwlink/?LinkId=393746).</span></span>  
  
## <a name="hosting-multiple-versions-in-a-workflow-service"></a><span data-ttu-id="17b71-107">Obsługa wielu wersji w usłudze przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="17b71-107">Hosting Multiple Versions in a Workflow Service</span></span>  
 <span data-ttu-id="17b71-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost>zawiera dwie właściwości, które można skonfigurować tak, aby umożliwić wiele wersji przepływu pracy można wykonać side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> i <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="17b71-108"><xref:System.ServiceModel.Activities.WorkflowServiceHost> contains two properties that can be configured to allow multiple versions of a workflow to execute side-by-side: <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="17b71-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A>zawiera obsługiwane wersje usługi przepływu pracy i <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> jest używany do jednoznacznego identyfikowania poszczególnych usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="17b71-109"><xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> contains the supported versions of the workflow service, and <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is used to uniquely identify each workflow service.</span></span> <span data-ttu-id="17b71-110">Odbywa się przez skojarzenie <xref:System.Activities.WorkflowIdentity> w usłudze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="17b71-110">This is done by associating a <xref:System.Activities.WorkflowIdentity> with the workflow service.</span></span> <span data-ttu-id="17b71-111">A <xref:System.Activities.WorkflowIdentity> zawiera trzy identyfikujące informacje.</span><span class="sxs-lookup"><span data-stu-id="17b71-111">A <xref:System.Activities.WorkflowIdentity> contains three identifying pieces of information.</span></span> <span data-ttu-id="17b71-112"><xref:System.Activities.WorkflowIdentity.Name%2A>i <xref:System.Activities.WorkflowIdentity.Version%2A> zawiera nazwy i <xref:System.Version> i są wymagane, i <xref:System.Activities.WorkflowIdentity.Package%2A> jest opcjonalna i może służyć do określenia dodatkowych ciąg zawierający informacje, takie jak nazwa zestawu lub inne potrzebne informacje.</span><span class="sxs-lookup"><span data-stu-id="17b71-112"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="17b71-113">Każda usługa przepływu pracy zawarte w <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> , Kolekcja musi mieć unikatową <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="17b71-113">Each workflow service contained in the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection must have a unique <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="17b71-114">A <xref:System.Activities.WorkflowIdentity> jest unikatowa, jeśli żadnego z trzech właściwości różnią się od siebie <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="17b71-114">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="17b71-115">A `null` <xref:System.Activities.WorkflowIdentity> jest dozwolona wartość dla <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale mogą mieć tylko jeden z poprzedniej wersji usługi przepływu pracy `null` <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="17b71-115">A `null` <xref:System.Activities.WorkflowIdentity> is an allowable value for <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but only one previous version of a workflow service may have a `null` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="17b71-116">A <xref:System.Activities.WorkflowIdentity> nie powinna zawierać żadnych informacji osobistych (dane osobowe).</span><span class="sxs-lookup"><span data-stu-id="17b71-116">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="17b71-117"><xref:System.Activities.WorkflowIdentity>składa się z trzech części: <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span><span class="sxs-lookup"><span data-stu-id="17b71-117"><xref:System.Activities.WorkflowIdentity> is composed of three parts: a <xref:System.Activities.WorkflowIdentity.Name%2A> (<xref:System.String>), a <xref:System.Activities.WorkflowIdentity.Version%2A> (<xref:System.Version>), and a <xref:System.Activities.WorkflowIdentity.Package%2A> (<xref:System.String>).</span></span> <span data-ttu-id="17b71-118">Informacje o <xref:System.Activities.WorkflowIdentity> użyty do utworzenia wystąpienia jest emitowany do żadnych skonfigurowanych śledzenia cyklu życia usług w wielu różnych punktach działania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="17b71-118">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="17b71-119">WF śledzenia nie ma żadnych mechanizmu, aby ukryć dane osobowe (poufne dane użytkowników).</span><span class="sxs-lookup"><span data-stu-id="17b71-119">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="17b71-120">W związku z tym <xref:System.Activities.WorkflowIdentity> wystąpienia nie powinna zawierać żadnych danych dane osobowe, ponieważ zostanie wyemitowany przez środowisko uruchomieniowe w śledzenia rekordów i mogą być widoczne dla każda osoba mająca dostęp do wyświetlania rekordów śledzenia.</span><span class="sxs-lookup"><span data-stu-id="17b71-120">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
### <a name="rules-for-hosting-multiple-versions-of-a-workflow-service"></a><span data-ttu-id="17b71-121">Reguły do obsługi wielu wersji usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="17b71-121">Rules for Hosting Multiple Versions of a Workflow Service</span></span>  
 <span data-ttu-id="17b71-122">Gdy użytkownik dodaje dodatkowe wersji do <xref:System.ServiceModel.Activities.WorkflowServiceHost>, istnieje kilka warunków, które muszą zostać spełnione, usługi przepływu pracy ma być obsługiwana z tego samego zestawu punktów końcowych i opis.</span><span class="sxs-lookup"><span data-stu-id="17b71-122">When a user adds an additional version to the <xref:System.ServiceModel.Activities.WorkflowServiceHost>, there are several conditions that must be met in order for a workflow service to be hosted with the same set of endpoints and description.</span></span> <span data-ttu-id="17b71-123">Jeśli dodatkowe wersje nie spełniają tych warunków <xref:System.ServiceModel.Activities.WorkflowServiceHost> zgłasza wyjątek podczas `Open` jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="17b71-123">If any of the additional versions fail to meet these conditions, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> throws an exception when `Open` is called.</span></span> <span data-ttu-id="17b71-124">Każdej definicji przepływu pracy do hosta jako dodatkową wersję musi spełniać następujące wymagania (gdzie głównej wersji jest definicji usługi przepływu pracy, który został dostarczony do konstruktora hosta).</span><span class="sxs-lookup"><span data-stu-id="17b71-124">Each workflow definition provided to the host as an additional version must meet the following requirements (where the primary version is the workflow service definition that is provided to the host constructor).</span></span> <span data-ttu-id="17b71-125">Wersja dodatkowe przepływu pracy musi:</span><span class="sxs-lookup"><span data-stu-id="17b71-125">The additional workflow version must:</span></span>  
  
-   <span data-ttu-id="17b71-126">Tej samej <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> jako głównej wersji usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="17b71-126">Have the same the <xref:System.ServiceModel.Activities.WorkflowService.Name%2A> as the primary version of the workflow service.</span></span>  
  
-   <span data-ttu-id="17b71-127">Nie może mieć <xref:System.ServiceModel.Activities.Receive> lub <xref:System.ServiceModel.Activities.SendReply> działania w jego <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> nie znajdują się w wersji podstawowej i muszą one odpowiadać kontrakt operacji.</span><span class="sxs-lookup"><span data-stu-id="17b71-127">Must not have any <xref:System.ServiceModel.Activities.Receive> or <xref:System.ServiceModel.Activities.SendReply> activities in its <xref:System.ServiceModel.Activities.WorkflowService.Body%2A> that are not in the primary version, and they must match the operation contract.</span></span>  
  
-   <span data-ttu-id="17b71-128">Ma unikatową <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="17b71-128">Have a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span> <span data-ttu-id="17b71-129">Może mieć tylko jeden definicji przepływu pracy `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="17b71-129">One and only one workflow definition may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
 <span data-ttu-id="17b71-130">Niektóre zmiany są dozwolone.</span><span class="sxs-lookup"><span data-stu-id="17b71-130">Some changes are permitted.</span></span> <span data-ttu-id="17b71-131">Następujące elementy mogą się różnić między wersjami:</span><span class="sxs-lookup"><span data-stu-id="17b71-131">The following items may be different between the versions:</span></span>  
  
-   <span data-ttu-id="17b71-132"><xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> Może mieć różne nazwy i pakietu od wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="17b71-132">The <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> may have a different Name and Package than the primary version.</span></span>  
  
-   <span data-ttu-id="17b71-133"><xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> Wartość mogą różnić się od wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="17b71-133">The <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> value may be different than the primary version.</span></span>  
  
-   <span data-ttu-id="17b71-134"><xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> Mogą różnić się od wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="17b71-134">The <xref:System.ServiceModel.Activities.WorkflowService.ConfigurationName%2A> may be different than the primary version.</span></span>  
  
-   <span data-ttu-id="17b71-135"><xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> Mogą różnić się od wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="17b71-135">The <xref:System.ServiceModel.Activities.WorkflowService.ImplementedContracts%2A> may be different than the primary version.</span></span>  
  
### <a name="configuring-the-definitionidentity"></a><span data-ttu-id="17b71-136">Konfigurowanie właściwością definitionidentity o wartości</span><span class="sxs-lookup"><span data-stu-id="17b71-136">Configuring the DefinitionIdentity</span></span>  
 <span data-ttu-id="17b71-137">Podczas tworzenia usługi przepływu pracy za pomocą projektanta przepływów pracy <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> jest ustawiany za pomocą **właściwości** okna.</span><span class="sxs-lookup"><span data-stu-id="17b71-137">When a workflow service is created using the workflow designer, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is set using the **Properties** window.</span></span> <span data-ttu-id="17b71-138">Kliknij przycisk poza działania głównego usługi w projektancie, aby wybrać usługi przepływu pracy, a następnie wybierz **okna właściwości** z **widoku** menu.</span><span class="sxs-lookup"><span data-stu-id="17b71-138">Click outside of the service’s root activity in the designer to select the workflow service, and choose **Properties Window** from the **View** menu.</span></span> <span data-ttu-id="17b71-139">Wybierz **właściwości WorkflowIdentity** z listy rozwijanej obok **właściwością definitionidentity o wartości** właściwości, a następnie rozwiń węzeł i określić żądaną <xref:System.Activities.WorkflowIdentity> właściwości.</span><span class="sxs-lookup"><span data-stu-id="17b71-139">Select **WorkflowIdentity** from the drop-down list that appears beside the **DefinitionIdentity** property, and then expand and specify the desired <xref:System.Activities.WorkflowIdentity> properties.</span></span> <span data-ttu-id="17b71-140">W poniższym przykładzie <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> skonfigurowano <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` i <xref:System.Activities.WorkflowIdentity.Version%2A> z `1.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="17b71-140">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `1.0.0.0`.</span></span> <span data-ttu-id="17b71-141"><xref:System.Activities.WorkflowIdentity.Package%2A>jest opcjonalna i w tym przykładzie `null`.</span><span class="sxs-lookup"><span data-stu-id="17b71-141"><xref:System.Activities.WorkflowIdentity.Package%2A> is optional and in this example is `null`.</span></span>  
  
 <span data-ttu-id="17b71-142">![Właściwością definitionidentity o wartości](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv1.bmp "WorkflowServiceDefinitionIdentityv1")</span><span class="sxs-lookup"><span data-stu-id="17b71-142">![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv1.bmp "WorkflowServiceDefinitionIdentityv1")</span></span>  
  
 <span data-ttu-id="17b71-143">Gdy usługi przepływu pracy jest samodzielnie hostowana, <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> jest skonfigurowana, gdy jest tworzony usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="17b71-143">When a workflow service is self-hosted, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured when the workflow service is constructed.</span></span> <span data-ttu-id="17b71-144">W poniższym przykładzie <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> jest konfigurowana przy użyciu tej samej wartości, co w poprzednim przykładzie <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` i <xref:System.Activities.WorkflowIdentity.Name%2A> z `1.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="17b71-144">In the following example, the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is configured with the same values as the previous example, with the <xref:System.Activities.WorkflowIdentity.Name%2A> `MortgageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Name%2A> of `1.0.0.0`.</span></span>  
  
```csharp  
WorkflowService service = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflow(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
```  
  
```vb  
Dim service As New WorkflowService  
With service  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflow  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
```  
  
 <span data-ttu-id="17b71-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> nie jest wymagana, chociaż może mieć tylko jedną wersję usługi przepływu pracy **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="17b71-145">A <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> is not required, although only one version of the workflow service may have a **null**<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="17b71-146">Jest to przydatne, jeśli usługa została wdrożona początkowo bez <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> skonfigurowany, a tworzona jest zaktualizowana wersja.</span><span class="sxs-lookup"><span data-stu-id="17b71-146">This is useful if the service was deployed initially without a <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> configured, and then an updated version is created.</span></span>  
  
### <a name="adding-a-new-version-to-a-web-hosted-workflow-service"></a><span data-ttu-id="17b71-147">Dodawanie nowej wersji do usługi sieci Web hostowanych przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="17b71-147">Adding a New Version to a Web-hosted Workflow Service</span></span>  
 <span data-ttu-id="17b71-148">Pierwszym etapem konfigurowania nowej wersji usługi przepływu pracy za pośrednictwem usługi sieci web hostowanych jest można utworzyć nowego folderu w `App_Code` folderu, który ma taką samą nazwę jak plik usługi.</span><span class="sxs-lookup"><span data-stu-id="17b71-148">The first step in configuring a new version of a workflow service in a web-hosted service is to create a new folder in the `App_Code` folder that has the same name as the service file.</span></span> <span data-ttu-id="17b71-149">Jeśli usługi `xamlx` nosi nazwę pliku `MortgageWorkflow.xamlx`, a następnie folder musi mieć nazwę `MortgageWorkflow`.</span><span class="sxs-lookup"><span data-stu-id="17b71-149">If the service’s `xamlx` file is named `MortgageWorkflow.xamlx`, then the folder must be named `MortgageWorkflow`.</span></span> <span data-ttu-id="17b71-150">Umieść kopię oryginalnej usługi `xamlx` pliku do tego folderu i zmień jego nazwę na nową nazwę, taką jak `MortgageWorkflowV1.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="17b71-150">Place a copy of the original service’s `xamlx` file into this folder and rename it to a new name, such as `MortgageWorkflowV1.xamlx`.</span></span> <span data-ttu-id="17b71-151">Wprowadź żądane zmiany do głównej usługi, zaktualizuj jego <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, a następnie wdrożyć usługę.</span><span class="sxs-lookup"><span data-stu-id="17b71-151">Make the desired changes to the primary service, update its <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, and then deploy the service.</span></span> <span data-ttu-id="17b71-152">W poniższym przykładzie <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> został zaktualizowany o <xref:System.Activities.WorkflowIdentity.Name%2A> z `MortageWorkflow` i <xref:System.Activities.WorkflowIdentity.Version%2A> z `2.0.0.0`.</span><span class="sxs-lookup"><span data-stu-id="17b71-152">In the following example the <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> has been updated with a <xref:System.Activities.WorkflowIdentity.Name%2A> of `MortageWorkflow` and a <xref:System.Activities.WorkflowIdentity.Version%2A> of `2.0.0.0`.</span></span>  
  
 <span data-ttu-id="17b71-153">![Właściwością definitionidentity o wartości](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv2.bmp "WorkflowServiceDefinitionIdentityv2")</span><span class="sxs-lookup"><span data-stu-id="17b71-153">![DefinitionIdentity](../../../../docs/framework/wcf/feature-details/media/workflowservicedefinitionidentityv2.bmp "WorkflowServiceDefinitionIdentityv2")</span></span>  
  
 <span data-ttu-id="17b71-154">Po ponownym uruchomieniu usługi poprzedniej wersji zostanie automatycznie dodany do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji, ponieważ znajduje się w wyznaczonym `App_Code` podfolderu.</span><span class="sxs-lookup"><span data-stu-id="17b71-154">When the service restarts, the previous version will automatically be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection because it is located in the designated `App_Code` subfolder.</span></span> <span data-ttu-id="17b71-155">Należy pamiętać, że jeśli głównej wersji usługi przepływu pracy `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> poprzednie wersje nie zostaną dodane.</span><span class="sxs-lookup"><span data-stu-id="17b71-155">Note that if the primary version of the workflow service has a `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> the previous versions will not be added.</span></span> <span data-ttu-id="17b71-156">Może mieć jedną wersję `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, ale jeśli istnieje wiele wersji głównej wersji nie może być jednym z `null` <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> lub #else poprzednich wersji, nie zostanie dodany do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="17b71-156">One version may have a `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A>, but if there are multiple versions the primary version must not be the one with the `null`<xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> or else the previous versions will not be added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span>  
  
### <a name="adding-a-new-version-to-a-self-hosted-workflow-service"></a><span data-ttu-id="17b71-157">Dodawanie nowej wersji do usługi hostowanej własnym przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="17b71-157">Adding a New Version to a Self-hosted Workflow Service</span></span>  
 <span data-ttu-id="17b71-158">Podczas dodawania nowej wersji do usługi hostowanej własnym przepływu pracy, <xref:System.ServiceModel.Activities.WorkflowServiceHost> jest skonfigurowane przy użyciu głównej wersji usługi przepływu pracy i poprzednich wersjach należy jawnie dodać do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="17b71-158">When adding a new version to a self-hosted workflow service, the <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with the primary version of the workflow service, and previous versions must be explicitly added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="17b71-159">W poniższym przykładzie <xref:System.ServiceModel.Activities.WorkflowServiceHost> jest skonfigurowany z usługą podstawowy przepływ pracy, który używa `MortgageWorkflowV2` definicji przepływu pracy i skonfigurowano usługi przepływu pracy `MortgageWorkflowV1` definicji przepływu pracy jest dodawany do <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="17b71-159">In the following example, a <xref:System.ServiceModel.Activities.WorkflowServiceHost> is configured with a primary workflow service that uses a `MortgageWorkflowV2` workflow definition, and a workflow service configured with a `MortgageWorkflowV1` workflow definition is added to the <xref:System.ServiceModel.Activities.WorkflowServiceHost.SupportedVersions%2A> collection.</span></span> <span data-ttu-id="17b71-160">Każda usługa przepływu pracy jest skonfigurowana przy użyciu unikatowego <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> , które odzwierciedla wersji definicji przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="17b71-160">Each workflow service is configured with a unique <xref:System.ServiceModel.Activities.WorkflowService.DefinitionIdentity%2A> that reflects the version of the workflow definition.</span></span>  
  
```csharp  
// Create the primary version of the workflow service.  
WorkflowService serviceV2 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV2(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(2, 0, 0, 0)  
    }  
};  
  
// Configure the WorkflowServiceHost with the current version  
// of the workflow service. This code requires Administrator  
// privileges to function correctly. If running from Visual  
// Studio, Visual Studio must be run with Administrator privileges.  
WorkflowServiceHost host = new WorkflowServiceHost(serviceV2,   
    new Uri("http://localhost:8080/MortgageWorkflowService"));  
  
// Create the previous version of the workflow service.  
WorkflowService serviceV1 = new WorkflowService  
{  
    Name = "MortgageWorkflowService",  
    Body = new MortgageWorkflowV1(),  
    DefinitionIdentity = new WorkflowIdentity  
    {  
        Name = "MortgageWorkflow",  
        Version = new Version(1, 0, 0, 0)  
    }  
};  
  
// Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1);  
```  
  
```vb  
'Create the primary version of the workflow service  
Dim serviceV2 As New WorkflowService  
With serviceV2  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV2  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(2, 0, 0, 0) _  
    }  
End With  
  
'Configure the WorkflowServiceHost with the current version  
'of the workflow service. This code requires Administrator  
'privileges to function correctly. If running from Visual  
'Studio, Visual Studio must be run with Administrator privileges.  
  
Dim host As New WorkflowServiceHost(serviceV2, _  
    New Uri("http://localhost:8080/MortgageWorkflowService"))  
  
'Create the previous version of the workflow service.  
Dim serviceV1 As New WorkflowService  
With serviceV1  
    .Name = "MortgageWorkflowService"  
    .Body = New MortgageWorkflowV1  
    .DefinitionIdentity = New WorkflowIdentity With _  
    { _  
        .Name = "MortgageWorkflow", _  
        .Version = New Version(1, 0, 0, 0) _  
    }  
End With  
  
'Add the previous version of the service to the SupportedVersions collection.  
host.SupportedVersions.Add(serviceV1)  
```