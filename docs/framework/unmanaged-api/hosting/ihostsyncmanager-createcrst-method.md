---
title: "IHostSyncManager::CreateCrst — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateCrst
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateCrst
helpviewer_keywords:
- CreateCrst method [.NET Framework hosting]
- IHostSyncManager::CreateCrst method [.NET Framework hosting]
ms.assetid: ac278cc8-2540-4a6c-b5c6-b90c3970b4f4
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b54abb60b00d071900d3bfdd01c2e5f1807998a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreatecrst-method"></a><span data-ttu-id="1f241-102">IHostSyncManager::CreateCrst — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f241-102">IHostSyncManager::CreateCrst Method</span></span>
<span data-ttu-id="1f241-103">Tworzy obiekt sekcja krytyczna synchronizacji.</span><span class="sxs-lookup"><span data-stu-id="1f241-103">Creates a critical section object for synchronization.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f241-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f241-104">Syntax</span></span>  
  
```  
HRESULT CreateCrst (  
    [out] IHostCrst** ppCrst  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f241-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f241-105">Parameters</span></span>  
 `ppCrst`  
 <span data-ttu-id="1f241-106">[out] Wskaźnik do adresu [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) wystąpienie implementowane przez hosta lub wartość null, jeśli nie można utworzyć sekcji krytycznych.</span><span class="sxs-lookup"><span data-stu-id="1f241-106">[out] A pointer to the address of an [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance implemented by the host, or null if the critical section could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1f241-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1f241-107">Return Value</span></span>  
  
|<span data-ttu-id="1f241-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1f241-108">HRESULT</span></span>|<span data-ttu-id="1f241-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1f241-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1f241-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="1f241-110">S_OK</span></span>|<span data-ttu-id="1f241-111">`CreateCrst`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="1f241-111">`CreateCrst` returned successfully.</span></span>|  
|<span data-ttu-id="1f241-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1f241-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1f241-113">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="1f241-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1f241-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1f241-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1f241-115">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="1f241-115">The call timed out.</span></span>|  
|<span data-ttu-id="1f241-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1f241-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1f241-117">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="1f241-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1f241-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1f241-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1f241-119">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="1f241-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1f241-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1f241-120">E_FAIL</span></span>|<span data-ttu-id="1f241-121">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="1f241-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1f241-122">Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="1f241-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1f241-123">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1f241-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1f241-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="1f241-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="1f241-125">Za mało pamięci nie była dostępna, można utworzyć żądanego sekcja krytyczna.</span><span class="sxs-lookup"><span data-stu-id="1f241-125">Not enough memory was available to create the requested critical section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f241-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f241-126">Remarks</span></span>  
 <span data-ttu-id="1f241-127">Sekcja krytyczna obiektów zapewniają podobne do dostarczony przez obiekt mutex synchronizacji z tą różnicą, że sekcje krytyczne mogą być używane tylko przez wątki jednego procesu.</span><span class="sxs-lookup"><span data-stu-id="1f241-127">Critical section objects provide synchronization similar to that provided by a mutex object, except that critical sections can be used only by the threads of a single process.</span></span> <span data-ttu-id="1f241-128">`CreateCrst`odzwierciedla Win32 `InitializeCriticalSection` funkcji.</span><span class="sxs-lookup"><span data-stu-id="1f241-128">`CreateCrst` mirrors the Win32 `InitializeCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f241-129">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f241-129">Requirements</span></span>  
 <span data-ttu-id="1f241-130">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f241-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f241-131">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1f241-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f241-132">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1f241-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f241-133">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f241-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f241-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f241-134">See Also</span></span>  
 [<span data-ttu-id="1f241-135">ICLRSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="1f241-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="1f241-136">IHostCrst — interfejs</span><span class="sxs-lookup"><span data-stu-id="1f241-136">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="1f241-137">IHostSyncManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="1f241-137">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 [<span data-ttu-id="1f241-138">IHostSemaphore — interfejs</span><span class="sxs-lookup"><span data-stu-id="1f241-138">IHostSemaphore Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 [<span data-ttu-id="1f241-139">Muteksy</span><span class="sxs-lookup"><span data-stu-id="1f241-139">Mutexes</span></span>](../../../../docs/standard/threading/mutexes.md)  
 [<span data-ttu-id="1f241-140">Semafor i klasa SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="1f241-140">Semaphore and SemaphoreSlim</span></span>](../../../../docs/standard/threading/semaphore-and-semaphoreslim.md)