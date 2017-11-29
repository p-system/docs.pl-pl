---
title: "ICLRGCManager2::SetGCStartupLimitsEx — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager2.SetGCStartupLimitsEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 73f5678008354b312964f0cb32d768d36a641fd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="65b24-102">ICLRGCManager2::SetGCStartupLimitsEx — Metoda</span><span class="sxs-lookup"><span data-stu-id="65b24-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="65b24-103">Ustawia rozmiar segmentu kolekcji pamięci i maksymalny rozmiar pamięci systemu kolekcji generacji 0.</span><span class="sxs-lookup"><span data-stu-id="65b24-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65b24-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="65b24-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,   
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65b24-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65b24-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="65b24-106">[in] Określony rozmiar pamięci segment kolekcji.</span><span class="sxs-lookup"><span data-stu-id="65b24-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="65b24-107">Rozmiar segmentu minimalna wynosi 4 MB.</span><span class="sxs-lookup"><span data-stu-id="65b24-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="65b24-108">Segmenty może być większa w krokach 1 MB lub większy.</span><span class="sxs-lookup"><span data-stu-id="65b24-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="65b24-109">[in] Określony maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="65b24-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="65b24-110">Rozmiar minimalny generacji 0 to 64 KB.</span><span class="sxs-lookup"><span data-stu-id="65b24-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65b24-111">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="65b24-111">Return Value</span></span>  
  
|<span data-ttu-id="65b24-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="65b24-112">HRESULT</span></span>|<span data-ttu-id="65b24-113">Opis</span><span class="sxs-lookup"><span data-stu-id="65b24-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="65b24-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="65b24-114">S_OK</span></span>|<span data-ttu-id="65b24-115">`SetGCStartupLimitsEx`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="65b24-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="65b24-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="65b24-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="65b24-117">Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.</span><span class="sxs-lookup"><span data-stu-id="65b24-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="65b24-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="65b24-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="65b24-119">Upłynął limit czasu wywołania.</span><span class="sxs-lookup"><span data-stu-id="65b24-119">The call timed out.</span></span>|  
|<span data-ttu-id="65b24-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="65b24-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="65b24-121">Obiekt wywołujący nie jest właścicielem blokady.</span><span class="sxs-lookup"><span data-stu-id="65b24-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="65b24-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="65b24-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="65b24-123">Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.</span><span class="sxs-lookup"><span data-stu-id="65b24-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="65b24-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="65b24-124">E_FAIL</span></span>|<span data-ttu-id="65b24-125">Wystąpił nieznany błąd krytyczny.</span><span class="sxs-lookup"><span data-stu-id="65b24-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="65b24-126">Po powrocie z metody E_FAIL CLR nie jest już możliwe w ramach procesu.</span><span class="sxs-lookup"><span data-stu-id="65b24-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="65b24-127">Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="65b24-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65b24-128">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65b24-128">Remarks</span></span>  
 <span data-ttu-id="65b24-129">Wartości który `SetGCStartupLimitsEx` zestawy można określić jedynie, aby uruchomić hosta.</span><span class="sxs-lookup"><span data-stu-id="65b24-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="65b24-130">Później wywołań `SetGCStartupLimitsEx` są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="65b24-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="65b24-131">Aby ustawić albo parametr bez wpływu na innych, należy określić 0 (zero) dla parametru, których nie chcesz, aby zmienić.</span><span class="sxs-lookup"><span data-stu-id="65b24-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65b24-132">Wymagania</span><span class="sxs-lookup"><span data-stu-id="65b24-132">Requirements</span></span>  
 <span data-ttu-id="65b24-133">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65b24-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65b24-134">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="65b24-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65b24-135">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65b24-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65b24-136">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65b24-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65b24-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65b24-137">See Also</span></span>  
 [<span data-ttu-id="65b24-138">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="65b24-138">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="65b24-139">Wyrzucanie elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="65b24-139">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="65b24-140">ICLRControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="65b24-140">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="65b24-141">ICLRGCManager2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="65b24-141">ICLRGCManager2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)