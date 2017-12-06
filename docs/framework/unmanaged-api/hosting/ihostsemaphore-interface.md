---
title: "IHostSemaphore — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSemaphore
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSemaphore
helpviewer_keywords: IHostSemaphore interface [.NET Framework hosting]
ms.assetid: c0765321-656c-441e-bab5-58176292be1e
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 67b3225186f74fceadfb3104145743823ef82fc2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsemaphore-interface"></a><span data-ttu-id="af614-102">IHostSemaphore — Interfejs</span><span class="sxs-lookup"><span data-stu-id="af614-102">IHostSemaphore Interface</span></span>
<span data-ttu-id="af614-103">Reprezentuje implementację hosta semafor dla wątków.</span><span class="sxs-lookup"><span data-stu-id="af614-103">Represents the host's implementation of a semaphore for threading.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="af614-104">Metody</span><span class="sxs-lookup"><span data-stu-id="af614-104">Methods</span></span>  
  
|<span data-ttu-id="af614-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="af614-105">Method</span></span>|<span data-ttu-id="af614-106">Opis</span><span class="sxs-lookup"><span data-stu-id="af614-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="af614-107">ReleaseSemaphore — metoda</span><span class="sxs-lookup"><span data-stu-id="af614-107">ReleaseSemaphore Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-releasesemaphore-method.md)|<span data-ttu-id="af614-108">Zwiększa liczbę bieżącego `IHostSemaphore` wystąpienia o określonej szerokości.</span><span class="sxs-lookup"><span data-stu-id="af614-108">Increases the count of the current `IHostSemaphore` instance by the specified amount.</span></span>|  
|[<span data-ttu-id="af614-109">WAIT — metoda</span><span class="sxs-lookup"><span data-stu-id="af614-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-wait-method.md)|<span data-ttu-id="af614-110">Powoduje, że bieżący `IHostSemaphore` wystąpienia poczekać, aż należy lub określoną ilość czasu upłynie.</span><span class="sxs-lookup"><span data-stu-id="af614-110">Causes the current `IHostSemaphore` instance to wait until it is owned or the specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="af614-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="af614-111">Requirements</span></span>  
 <span data-ttu-id="af614-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af614-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af614-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="af614-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="af614-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="af614-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af614-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af614-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af614-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af614-116">See Also</span></span>  
 [<span data-ttu-id="af614-117">ICLRSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="af614-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="af614-118">IHostAutoEvent — interfejs</span><span class="sxs-lookup"><span data-stu-id="af614-118">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="af614-119">IHostManualEvent — interfejs</span><span class="sxs-lookup"><span data-stu-id="af614-119">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="af614-120">IHostSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="af614-120">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="af614-121">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="af614-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)