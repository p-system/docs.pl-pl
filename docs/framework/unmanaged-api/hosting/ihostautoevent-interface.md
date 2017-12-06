---
title: "IHostAutoEvent — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostAutoEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostAutoEvent
helpviewer_keywords: IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8c99bde7641ee640df06be71fc43a7f8774f7ff3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="3db8e-102">IHostAutoEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3db8e-102">IHostAutoEvent Interface</span></span>
<span data-ttu-id="3db8e-103">Udostępnia reprezentację implementacji hosta zdarzenie z resetowaniem automatycznym.</span><span class="sxs-lookup"><span data-stu-id="3db8e-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3db8e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3db8e-104">Methods</span></span>  
  
|<span data-ttu-id="3db8e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3db8e-105">Method</span></span>|<span data-ttu-id="3db8e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3db8e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3db8e-107">Set — metoda</span><span class="sxs-lookup"><span data-stu-id="3db8e-107">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-set-method.md)|<span data-ttu-id="3db8e-108">Ustawia bieżący `IHostAutoEvent` wystąpienia sygnałowego stanu.</span><span class="sxs-lookup"><span data-stu-id="3db8e-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="3db8e-109">WAIT — metoda</span><span class="sxs-lookup"><span data-stu-id="3db8e-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-wait-method.md)|<span data-ttu-id="3db8e-110">Powoduje, że bieżący `IHostAutoEvent` wystąpienia poczekać, aż zdarzenia jest właścicielem lub określoną ilość czasu upłynie.</span><span class="sxs-lookup"><span data-stu-id="3db8e-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3db8e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3db8e-111">Requirements</span></span>  
 <span data-ttu-id="3db8e-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3db8e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3db8e-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3db8e-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3db8e-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3db8e-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3db8e-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3db8e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3db8e-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3db8e-116">See Also</span></span>  
 [<span data-ttu-id="3db8e-117">ICLRSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="3db8e-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="3db8e-118">IHostManualEvent — interfejs</span><span class="sxs-lookup"><span data-stu-id="3db8e-118">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="3db8e-119">IHostSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="3db8e-119">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="3db8e-120">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="3db8e-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)