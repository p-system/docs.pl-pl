---
title: 100 - WorkflowInstanceRecord
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed4d1851-b378-489b-a22d-c1db09571fb4
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e60b972c015bd7f3ec304c83e03812e2460b8ca3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="100---workflowinstancerecord"></a><span data-ttu-id="b0728-102">100 - WorkflowInstanceRecord</span><span class="sxs-lookup"><span data-stu-id="b0728-102">100 - WorkflowInstanceRecord</span></span>
## <a name="properties"></a><span data-ttu-id="b0728-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="b0728-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b0728-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="b0728-104">Id</span></span>|<span data-ttu-id="b0728-105">100</span><span class="sxs-lookup"><span data-stu-id="b0728-105">100</span></span>|  
|<span data-ttu-id="b0728-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="b0728-106">Keywords</span></span>|<span data-ttu-id="b0728-107">EndToEndMonitoring rozwiązywania problemów, HealthMonitoring, WFTracking</span><span class="sxs-lookup"><span data-stu-id="b0728-107">EndToEndMonitoring, Troubleshooting, HealthMonitoring, WFTracking</span></span>|  
|<span data-ttu-id="b0728-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="b0728-108">Level</span></span>|<span data-ttu-id="b0728-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="b0728-109">Information</span></span>|  
|<span data-ttu-id="b0728-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="b0728-110">Channel</span></span>|<span data-ttu-id="b0728-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="b0728-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="b0728-112">Opis</span><span class="sxs-lookup"><span data-stu-id="b0728-112">Description</span></span>  
 <span data-ttu-id="b0728-113">To zdarzenie jest emitowane przez uczestnika śledzenia zdarzeń systemu Windows, gdy wystąpienia przepływu pracy emituje WorkflowInstanceRecord dla stanów przepływu pracy: rozpoczęto wznowione, utrwalone, w stanie bezczynności, usunięty, zakończona, anulowana, zwalnianie, Anulowano.</span><span class="sxs-lookup"><span data-stu-id="b0728-113">This event is emitted by the ETW tracking participant when a workflow instance emits WorkflowInstanceRecord for workflow states : Started, Resumed, Persisted, Idle, Deleted, Completed, Canceled, Unloaded, Unsuspended.</span></span>  
  
## <a name="message"></a><span data-ttu-id="b0728-114">Komunikat</span><span class="sxs-lookup"><span data-stu-id="b0728-114">Message</span></span>  
 <span data-ttu-id="b0728-115">TrackRecord = WorkflowInstanceRecord, identyfikator wystąpienia = %1, RecordNumber = %2, EventTime = %3, obiekt ActivityDefinitionId = %4, stan = %5, adnotacje = %6, ProfileName = %7</span><span class="sxs-lookup"><span data-stu-id="b0728-115">TrackRecord= WorkflowInstanceRecord, InstanceID = %1, RecordNumber = %2, EventTime = %3, ActivityDefinitionId = %4, State = %5, Annotations = %6, ProfileName = %7</span></span>  
  
## <a name="details"></a><span data-ttu-id="b0728-116">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="b0728-116">Details</span></span>  
  
|<span data-ttu-id="b0728-117">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="b0728-117">Data Item Name</span></span>|<span data-ttu-id="b0728-118">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="b0728-118">Data Item Type</span></span>|<span data-ttu-id="b0728-119">Opis</span><span class="sxs-lookup"><span data-stu-id="b0728-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="b0728-120">Identyfikator wystąpienia</span><span class="sxs-lookup"><span data-stu-id="b0728-120">InstanceId</span></span>|<span data-ttu-id="b0728-121">xs:GUID</span><span class="sxs-lookup"><span data-stu-id="b0728-121">xs:GUID</span></span>|<span data-ttu-id="b0728-122">Identyfikator wystąpienia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b0728-122">The instance id for the workflow</span></span>|  
|<span data-ttu-id="b0728-123">RecordNumber</span><span class="sxs-lookup"><span data-stu-id="b0728-123">RecordNumber</span></span>|<span data-ttu-id="b0728-124">xs:Long</span><span class="sxs-lookup"><span data-stu-id="b0728-124">xs:long</span></span>|<span data-ttu-id="b0728-125">Numer sekwencyjny emitowany rekordu</span><span class="sxs-lookup"><span data-stu-id="b0728-125">The sequence number of the emitted record</span></span>|  
|<span data-ttu-id="b0728-126">eventTime</span><span class="sxs-lookup"><span data-stu-id="b0728-126">EventTime</span></span>|<span data-ttu-id="b0728-127">xs: DateTime</span><span class="sxs-lookup"><span data-stu-id="b0728-127">xs:dateTime</span></span>|<span data-ttu-id="b0728-128">Godzina w formacie UTC podczas zdarzenia zostały wyemitowane</span><span class="sxs-lookup"><span data-stu-id="b0728-128">The time in UTC when the event was emitted</span></span>|  
|<span data-ttu-id="b0728-129">Obiekt ActivityDefinitionId</span><span class="sxs-lookup"><span data-stu-id="b0728-129">ActivityDefinitionId</span></span>|<span data-ttu-id="b0728-130">xs:String</span><span class="sxs-lookup"><span data-stu-id="b0728-130">xs:string</span></span>|<span data-ttu-id="b0728-131">Nazwa działania głównego w przepływie pracy</span><span class="sxs-lookup"><span data-stu-id="b0728-131">The name of the root activity in the workflow</span></span>|  
|<span data-ttu-id="b0728-132">Stan</span><span class="sxs-lookup"><span data-stu-id="b0728-132">State</span></span>|<span data-ttu-id="b0728-133">xs:String</span><span class="sxs-lookup"><span data-stu-id="b0728-133">xs:string</span></span>|<span data-ttu-id="b0728-134">Bieżący stan przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b0728-134">The current state of the Workflow.</span></span>|  
|<span data-ttu-id="b0728-135">Adnotacje</span><span class="sxs-lookup"><span data-stu-id="b0728-135">Annotations</span></span>|<span data-ttu-id="b0728-136">xs:String</span><span class="sxs-lookup"><span data-stu-id="b0728-136">xs:string</span></span>|<span data-ttu-id="b0728-137">Adnotacje, które zostały dodane do tego zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="b0728-137">The annotations that were added to this event.</span></span>  <span data-ttu-id="b0728-138">Wartości są przechowywane w elemencie xml w formacie \<elementy >\< nazwa elementu = "annotationName" type="System.String" > annotationValue\</elementu > \< /elementy >.</span><span class="sxs-lookup"><span data-stu-id="b0728-138">The values are stored in an xml element in the format \<items>\< item  name = "annotationName" type="System.String">annotationValue\</item>\</items>.</span></span>  <span data-ttu-id="b0728-139">Jeśli nie określono bez adnotacji, a następnie ciąg zawiera \<elementów / >.</span><span class="sxs-lookup"><span data-stu-id="b0728-139">If no annotations are specified then the string contains \<items/>.</span></span> <span data-ttu-id="b0728-140">Rozmiar zdarzenia ETW jest ograniczona przez rozmiar bufora ETW lub max ładunku zdarzenia ETW.</span><span class="sxs-lookup"><span data-stu-id="b0728-140">The ETW event size is limited by the ETW buffer size or the max payload for an ETW event.</span></span> <span data-ttu-id="b0728-141">Jeśli limity ETW przekracza rozmiar zdarzenia, a następnie zdarzenia został obcięty przez usunięcie adnotacje i zastąpienie wartości adnotacji z \<elementy >...  \< /elementy >.</span><span class="sxs-lookup"><span data-stu-id="b0728-141">If the size of the event exceeds the ETW limits, then the event is truncated by dropping the annotations and replacing the annotation value with \<items>...\</items>.</span></span>|  
|<span data-ttu-id="b0728-142">ProfileName</span><span class="sxs-lookup"><span data-stu-id="b0728-142">ProfileName</span></span>|<span data-ttu-id="b0728-143">xs:String</span><span class="sxs-lookup"><span data-stu-id="b0728-143">xs:string</span></span>|<span data-ttu-id="b0728-144">Nazwa lub profilu śledzenia, które spowodowały to zdarzenie jest emitowany</span><span class="sxs-lookup"><span data-stu-id="b0728-144">The name or the tracking profile that resulted in this event being emitted</span></span>|  
|<span data-ttu-id="b0728-145">HostReference</span><span class="sxs-lookup"><span data-stu-id="b0728-145">HostReference</span></span>|<span data-ttu-id="b0728-146">xs:String</span><span class="sxs-lookup"><span data-stu-id="b0728-146">xs:string</span></span>|<span data-ttu-id="b0728-147">Dla usług sieci web hostowanych w tym polu unikatowo identyfikuje usługę w hierarchii sieci web.</span><span class="sxs-lookup"><span data-stu-id="b0728-147">For web hosted services, this field uniquely identifies the service in the web hierarchy.</span></span>  <span data-ttu-id="b0728-148">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName "przykład:" Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService "</span><span class="sxs-lookup"><span data-stu-id="b0728-148">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName' Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'</span></span>|  
|<span data-ttu-id="b0728-149">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="b0728-149">AppDomain</span></span>|<span data-ttu-id="b0728-150">xs:String</span><span class="sxs-lookup"><span data-stu-id="b0728-150">xs:string</span></span>|<span data-ttu-id="b0728-151">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="b0728-151">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|