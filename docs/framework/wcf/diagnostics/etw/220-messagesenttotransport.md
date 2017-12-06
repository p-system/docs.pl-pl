---
title: "220 — MessageSentToTransport"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aef4e781-240b-45bc-bff8-400053037e71
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7bc3b784dca090ed768711728a054782e06c7b10
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="220---messagesenttotransport"></a><span data-ttu-id="bc944-102">220 — MessageSentToTransport</span><span class="sxs-lookup"><span data-stu-id="bc944-102">220 - MessageSentToTransport</span></span>
## <a name="properties"></a><span data-ttu-id="bc944-103">Właściwości</span><span class="sxs-lookup"><span data-stu-id="bc944-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="bc944-104">Identyfikator</span><span class="sxs-lookup"><span data-stu-id="bc944-104">Id</span></span>|<span data-ttu-id="bc944-105">220</span><span class="sxs-lookup"><span data-stu-id="bc944-105">220</span></span>|  
|<span data-ttu-id="bc944-106">Słowa kluczowe</span><span class="sxs-lookup"><span data-stu-id="bc944-106">Keywords</span></span>|<span data-ttu-id="bc944-107">EndToEndMonitoring rozwiązywania problemów, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="bc944-107">EndToEndMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="bc944-108">Poziom</span><span class="sxs-lookup"><span data-stu-id="bc944-108">Level</span></span>|<span data-ttu-id="bc944-109">Informacje</span><span class="sxs-lookup"><span data-stu-id="bc944-109">Information</span></span>|  
|<span data-ttu-id="bc944-110">Kanał</span><span class="sxs-lookup"><span data-stu-id="bc944-110">Channel</span></span>|<span data-ttu-id="bc944-111">Microsoft-Windows aplikacji Server aplikacje/analityczne</span><span class="sxs-lookup"><span data-stu-id="bc944-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="bc944-112">Opis</span><span class="sxs-lookup"><span data-stu-id="bc944-112">Description</span></span>  
 <span data-ttu-id="bc944-113">To zdarzenie jest emitowany, gdy Model usługi wysyła wiadomość do transportu.</span><span class="sxs-lookup"><span data-stu-id="bc944-113">This event is emitted when the Service Model sends a message to the transport.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc944-114">To zdarzenie nie będzie emitowany dla transportów jednokierunkowe.</span><span class="sxs-lookup"><span data-stu-id="bc944-114">This event will not be emitted for one-way transports.</span></span>  
  
## <a name="message"></a><span data-ttu-id="bc944-115">Komunikat</span><span class="sxs-lookup"><span data-stu-id="bc944-115">Message</span></span>  
 <span data-ttu-id="bc944-116">Dyspozytor wysłał wiadomość do transportu.</span><span class="sxs-lookup"><span data-stu-id="bc944-116">The Dispatcher sent a message to the transport.</span></span> <span data-ttu-id="bc944-117">Identyfikator korelacji == "%1".</span><span class="sxs-lookup"><span data-stu-id="bc944-117">Correlation ID == '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="bc944-118">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="bc944-118">Details</span></span>  
  
|<span data-ttu-id="bc944-119">Nazwa elementu danych</span><span class="sxs-lookup"><span data-stu-id="bc944-119">Data Item Name</span></span>|<span data-ttu-id="bc944-120">Typ elementu danych</span><span class="sxs-lookup"><span data-stu-id="bc944-120">Data Item Type</span></span>|<span data-ttu-id="bc944-121">Opis</span><span class="sxs-lookup"><span data-stu-id="bc944-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="bc944-122">Identyfikator korelacji</span><span class="sxs-lookup"><span data-stu-id="bc944-122">Correlation ID</span></span>|`xs:GUID`|<span data-ttu-id="bc944-123">Aktywności identyfikator używany do skorelowania `MessageSentToTransport` odpowiednie zdarzenia z usługi lub klienta `MessageReceivedFromTransport` w drugim zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="bc944-123">The activity ID used to correlate a `MessageSentToTransport` event from a service or client to its corresponding `MessageReceivedFromTransport` on the other end.</span></span>|  
|<span data-ttu-id="bc944-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="bc944-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="bc944-125">W przypadku usług hostowanych w sieci Web to pole unikatowo identyfikuje usługę w hierarchii sieci Web.</span><span class="sxs-lookup"><span data-stu-id="bc944-125">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="bc944-126">Jego format jest zdefiniowany jako "Ścieżka wirtualna aplikacji Nazwa witryny sieci Web &#124; Ścieżka wirtualna usługi &#124; ServiceName ".</span><span class="sxs-lookup"><span data-stu-id="bc944-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="bc944-127">Przykład: "Default Web Site/CalculatorApplication &#124;/CalculatorService.svc &#124; CalculatorService ".</span><span class="sxs-lookup"><span data-stu-id="bc944-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="bc944-128">Domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="bc944-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="bc944-129">Długość ciągu zwróconego przez AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="bc944-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|