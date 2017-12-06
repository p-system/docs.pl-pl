---
title: "Zakolejkowane komunikaty porzucone na sekundę"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74540f52-8762-4147-b5ba-e171180515a3
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d97d78ddbf52e821cfff2aac08b41e732b189602
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="queue-dropped-messages-per-second"></a><span data-ttu-id="3c000-102">Zakolejkowane komunikaty porzucone na sekundę</span><span class="sxs-lookup"><span data-stu-id="3c000-102">Queue Dropped Messages Per Second</span></span>
<span data-ttu-id="3c000-103">Nazwa licznika: Zakolejkowane komunikaty porzucone na sekundę.</span><span class="sxs-lookup"><span data-stu-id="3c000-103">Counter Name: Queued Messages Dropped Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="3c000-104">Opis</span><span class="sxs-lookup"><span data-stu-id="3c000-104">Description</span></span>  
 <span data-ttu-id="3c000-105">Liczba komunikatów porzuconych przez transport z kolejką w tej usługi na sekundę.</span><span class="sxs-lookup"><span data-stu-id="3c000-105">Number of messages that are dropped by the queued transport at this service in a second.</span></span>  
  
 <span data-ttu-id="3c000-106">Ten licznik jest typu licznika wydajności [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), którego wartość jest obliczana przy użyciu następującej formuły.</span><span class="sxs-lookup"><span data-stu-id="3c000-106">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="3c000-107">(N 1 - N 0) / ((D 1 - D 0) / F)</span><span class="sxs-lookup"><span data-stu-id="3c000-107">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>