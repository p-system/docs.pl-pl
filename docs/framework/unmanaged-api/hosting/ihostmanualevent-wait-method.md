---
title: "IHostManualEvent::Wait — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostManualEvent.Wait
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostManualEvent::Wait
helpviewer_keywords:
- IHostManualEvent::Wait method [.NET Framework hosting]
- Wait method, IHostManualEvent interface [.NET Framework hosting]
ms.assetid: 1fbb7d8b-8a23-4c2b-8376-1a70cd2d6030
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a2bd584e1ada69adca7f8ef77f98533ef7a1ba16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmanualeventwait-method"></a><span data-ttu-id="be8f1-102">IHostManualEvent::Wait — Metoda</span><span class="sxs-lookup"><span data-stu-id="be8f1-102">IHostManualEvent::Wait Method</span></span>
<span data-ttu-id="be8f1-103">Powoduje, że bieżący [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) wystąpienia poczekać, aż należy on do lub z określoną ilością pamięci upłynie czas.</span><span class="sxs-lookup"><span data-stu-id="be8f1-103">Causes the current [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance to wait until it is owned, or a specified amount of time elapses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be8f1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="be8f1-104">Syntax</span></span>  
  
```  
HRESULT Wait (  
    [in] DWORD dwMilliseconds,  
    [in] DWORD option  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="be8f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be8f1-105">Parameters</span></span>  
 `dwMilliseconds`  
 <span data-ttu-id="be8f1-106">[in] Wyrażony w milisekundach czas oczekiwania przed zwróceniem, jeśli bieżący `IHostManualEvent` wystąpienia nie jest właścicielem.</span><span class="sxs-lookup"><span data-stu-id="be8f1-106">[in] The number of milliseconds to wait before returning, if the current `IHostManualEvent` instance is not owned.</span></span>  
  
 `option`  
 <span data-ttu-id="be8f1-107">[in] Jeden z [wait_option —](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) wartości i wskazujący akcję hosta powinien wykonać, jeśli ta operacja bloków.</span><span class="sxs-lookup"><span data-stu-id="be8f1-107">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating the action the host should take if this operation blocks.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be8f1-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="be8f1-108">Return Value</span></span>  
  
|<span data-ttu-id="be8f1-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="be8f1-109">HRESULT</span></span>|<span data-ttu-id="be8f1-110">Opis</span><span class="sxs-lookup"><span data-stu-id="be8f1-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="be8f1-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="be8f1-111">S_OK</span></span>|<span data-ttu-id="be8f1-112">`Wait`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="be8f1-112">`Wait` returned successfully.</span></span>|  
|<span data-ttu-id="be8f1-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="be8f1-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="be8f1-114">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="be8f1-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="be8f1-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="be8f1-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="be8f1-116">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="be8f1-116">The call timed out.</span></span>|  
|<span data-ttu-id="be8f1-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="be8f1-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="be8f1-118">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="be8f1-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="be8f1-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="be8f1-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="be8f1-120">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="be8f1-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="be8f1-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="be8f1-121">E_FAIL</span></span>|<span data-ttu-id="be8f1-122">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="be8f1-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="be8f1-123">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="be8f1-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="be8f1-124">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="be8f1-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="be8f1-125">HOST_E_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="be8f1-125">HOST_E_DEADLOCK</span></span>|<span data-ttu-id="be8f1-126">Host wykrył zakleszczenie w interwale oczekiwania, a wybrano bieżącego `IHostManualEvent` wystąpienia jako ofiara zakleszczenia.</span><span class="sxs-lookup"><span data-stu-id="be8f1-126">The host detected a deadlock during the wait interval, and chose the current `IHostManualEvent` instance as the deadlock victim.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be8f1-127">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be8f1-127">Requirements</span></span>  
 <span data-ttu-id="be8f1-128">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be8f1-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be8f1-129">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="be8f1-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="be8f1-130">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="be8f1-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="be8f1-131">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be8f1-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be8f1-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="be8f1-132">See Also</span></span>  
 [<span data-ttu-id="be8f1-133">ICLRSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="be8f1-133">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="be8f1-134">IHostAutoEvent — interfejs</span><span class="sxs-lookup"><span data-stu-id="be8f1-134">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="be8f1-135">IHostManualEvent — interfejs</span><span class="sxs-lookup"><span data-stu-id="be8f1-135">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="be8f1-136">IHostSemaphore — interfejs</span><span class="sxs-lookup"><span data-stu-id="be8f1-136">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="be8f1-137">IHostSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="be8f1-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)