---
title: MessageQueueDuplicatedPipeLeak
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 743db7f1-32cc-4a3b-8d1a-5d1cf25e439c
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd1b006d735c5b8bc140efe095adeb74aef387db
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="messagequeueduplicatedpipeleak"></a><span data-ttu-id="3e298-102">MessageQueueDuplicatedPipeLeak</span><span class="sxs-lookup"><span data-stu-id="3e298-102">MessageQueueDuplicatedPipeLeak</span></span>
<span data-ttu-id="3e298-103">Identyfikator: 166</span><span class="sxs-lookup"><span data-stu-id="3e298-103">Id: 166</span></span>  
  
 <span data-ttu-id="3e298-104">Ważność: błąd</span><span class="sxs-lookup"><span data-stu-id="3e298-104">Severity: Error</span></span>  
  
 <span data-ttu-id="3e298-105">Kategoria: SMSvcHost</span><span class="sxs-lookup"><span data-stu-id="3e298-105">Category: SMSvcHost</span></span>  
  
## <a name="description"></a><span data-ttu-id="3e298-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3e298-106">Description</span></span>  
 <span data-ttu-id="3e298-107">To zdarzenie oznacza, że wystąpił błąd podczas wysyłania zduplikowanego potoku.</span><span class="sxs-lookup"><span data-stu-id="3e298-107">This event indicates that an error occurred while dispatching a duplicated named pipe.</span></span> <span data-ttu-id="3e298-108">Ta dojścia jest teraz ujawnione w procesie.</span><span class="sxs-lookup"><span data-stu-id="3e298-108">This handle is now leaked in the process.</span></span> <span data-ttu-id="3e298-109">Zdarzenie zawiera źródła, wyjątek, nazwa procesu i identyfikatora procesu.</span><span class="sxs-lookup"><span data-stu-id="3e298-109">The event lists the source, exception, process name and process ID.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e298-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e298-110">See Also</span></span>  
 [<span data-ttu-id="3e298-111">Rejestrowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="3e298-111">Event Logging</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [<span data-ttu-id="3e298-112">Informacje ogólne o zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="3e298-112">Events General Reference</span></span>](../../../../../docs/framework/wcf/diagnostics/event-logging/events-general-reference.md)