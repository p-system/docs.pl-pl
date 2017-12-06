---
title: "Używanie kontraktów w przepływie pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c13da32e304e54d1826c6dd4ad83d5fbb17702a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="using-contracts-in-workflow"></a><span data-ttu-id="b9980-102">Używanie kontraktów w przepływie pracy</span><span class="sxs-lookup"><span data-stu-id="b9980-102">Using Contracts in Workflow</span></span>
<span data-ttu-id="b9980-103">Podczas wdrażania usługi, należy określić numer kontraktów opisujących usługę i wysyła i odbiera dane.</span><span class="sxs-lookup"><span data-stu-id="b9980-103">When implementing a service, you define a number of contracts that describe the service and the data that it sends and receives.</span></span> <span data-ttu-id="b9980-104">Dane są reprezentowane jako kontraktów danych i kontrakty komunikatu; zarówno [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] i usług przepływu pracy Użyj definicji kontraktu danych kontraktu i komunikatu jako części opisy usług.</span><span class="sxs-lookup"><span data-stu-id="b9980-104">The data is represented as data contracts and message contracts; both [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and workflow services use data contract and message contract definitions as part of service descriptions.</span></span> <span data-ttu-id="b9980-105">Sama usługa przedstawia metadanych (w formie WSDL) w celu opisania działania usługi.</span><span class="sxs-lookup"><span data-stu-id="b9980-105">The service itself exposes metadata (in the form of WSDL) in order to describe the operations of the service.</span></span> <span data-ttu-id="b9980-106">W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], usługa kontrakty i kontrakty operacji usługi i operacje, obsługuje on definiować.</span><span class="sxs-lookup"><span data-stu-id="b9980-106">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], service contracts and operation contracts define the service and the operations it supports.</span></span> <span data-ttu-id="b9980-107">Jednak w usłudze przepływu pracy, umowy te są częścią procesu biznesowego. są one widoczne w metadanych przez proces, nazywany wnioskowania kontraktu.</span><span class="sxs-lookup"><span data-stu-id="b9980-107">However, in a workflow service, these contracts are part of the business process itself; they are exposed in metadata by a process called contract inference.</span></span>  
  
## <a name="contract-inference"></a><span data-ttu-id="b9980-108">Kontrakt wnioskowania</span><span class="sxs-lookup"><span data-stu-id="b9980-108">Contract Inference</span></span>  
 <span data-ttu-id="b9980-109">Gdy usługa przepływu pracy jest obsługiwana przy użyciu <xref:System.ServiceModel.Activities.WorkflowServiceHost>, definicji przepływu pracy się zbadana i kontrakt jest generowany na podstawie zestawu działań w przepływie pracy do obsługi komunikatów.</span><span class="sxs-lookup"><span data-stu-id="b9980-109">When a workflow service is hosted using <xref:System.ServiceModel.Activities.WorkflowServiceHost>, the workflow definition is examined and a contract is generated based on the set of messaging activities found in the workflow.</span></span> <span data-ttu-id="b9980-110">W szczególności następujące działania i właściwości są używane do generowania kontraktu:</span><span class="sxs-lookup"><span data-stu-id="b9980-110">In particular the following activities and properties are used to generate the contract:</span></span>  
  
 <span data-ttu-id="b9980-111"><xref:System.ServiceModel.Activities.Receive>Działanie</span><span class="sxs-lookup"><span data-stu-id="b9980-111"><xref:System.ServiceModel.Activities.Receive> Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <span data-ttu-id="b9980-112"><xref:System.ServiceModel.Activities.SendReply>Działanie</span><span class="sxs-lookup"><span data-stu-id="b9980-112"><xref:System.ServiceModel.Activities.SendReply> Activity</span></span>  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <span data-ttu-id="b9980-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope>Działanie</span><span class="sxs-lookup"><span data-stu-id="b9980-113"><xref:System.ServiceModel.Activities.TransactedReceiveScope> Activity</span></span>  
  
 <span data-ttu-id="b9980-114">W rezultacie wnioskowania kontraktu jest opis usługi przy użyciu tych samych struktur danych jako WCF kontraktów usługi i działania.</span><span class="sxs-lookup"><span data-stu-id="b9980-114">The end result of contract inference is a description of the service using the same data structures as WCF service and operation contracts.</span></span> <span data-ttu-id="b9980-115">Te informacje jest następnie używane do udostępnienia WSDL usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="b9980-115">This information is then used to expose WSDL for the workflow service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9980-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b9980-116">See Also</span></span>  
 [<span data-ttu-id="b9980-117">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="b9980-117">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="b9980-118">Działania dotyczące komunikatów</span><span class="sxs-lookup"><span data-stu-id="b9980-118">Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 [<span data-ttu-id="b9980-119">Porady: Tworzenie usługi przepływu pracy za pomocą działań dotyczących komunikatów</span><span class="sxs-lookup"><span data-stu-id="b9980-119">How to: Create a Workflow Service with Messaging Activities</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [<span data-ttu-id="b9980-120">Porady: Tworzenie usługi przepływu pracy, który wykorzystuje istniejący kontrakt usługi</span><span class="sxs-lookup"><span data-stu-id="b9980-120">How to: Create a workflow service that consumes an existing service contract</span></span>](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)