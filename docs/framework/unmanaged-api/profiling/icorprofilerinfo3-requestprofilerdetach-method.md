---
title: "ICorProfilerInfo3::RequestProfilerDetach — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.RequestProfilerDetach Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::RequestProfilerDetach
helpviewer_keywords:
- RequestProfilerDetach method [.NET Framework profiling]
- ICorProfilerInfo3::RequestProfilerDetach method [.NET Framework profiling]
ms.assetid: ea102e62-0454-4477-bcf3-126773acd184
topic_type: apiref
caps.latest.revision: "20"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4d155c68f1b7743e0a888c78f6eeecf967c16570
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a><span data-ttu-id="278af-102">ICorProfilerInfo3::RequestProfilerDetach — Metoda</span><span class="sxs-lookup"><span data-stu-id="278af-102">ICorProfilerInfo3::RequestProfilerDetach Method</span></span>
<span data-ttu-id="278af-103">Powoduje, że środowisko uruchomieniowe można odłączyć profilera.</span><span class="sxs-lookup"><span data-stu-id="278af-103">Instructs the runtime to detach the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="278af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="278af-104">Syntax</span></span>  
  
```  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="278af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="278af-105">Parameters</span></span>  
 `dwExpectedCompletionMilliseconds`  
 <span data-ttu-id="278af-106">[in] Czas (w milisekundach), środowisko uruchomieniowe języka wspólnego (CLR) ma odczekać przed sprawdzanie, czy jest bezpieczne zwolnić profilera.</span><span class="sxs-lookup"><span data-stu-id="278af-106">[in] The length of time, in milliseconds, the common language runtime (CLR) should wait before checking to see whether it is safe to unload the profiler.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="278af-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="278af-107">Return Value</span></span>  
 <span data-ttu-id="278af-108">Ta metoda zwraca następujące określonych wyników HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="278af-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="278af-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="278af-109">HRESULT</span></span>|<span data-ttu-id="278af-110">Opis</span><span class="sxs-lookup"><span data-stu-id="278af-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="278af-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="278af-111">S_OK</span></span>|<span data-ttu-id="278af-112">Odłącz żądanie jest prawidłowe, i procedury odłączeń jest teraz kontynuowane w innym wątku.</span><span class="sxs-lookup"><span data-stu-id="278af-112">The detach request is valid, and the detach procedure is now continuing on another thread.</span></span> <span data-ttu-id="278af-113">W przypadku odłączenia zostanie całkowicie zakończona, `ProfilerDetachSucceeded` zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="278af-113">When the detach is fully complete, a `ProfilerDetachSucceeded` event is issued.</span></span>|  
|<span data-ttu-id="278af-114">E_ CORPROF_E_CALLBACK3_REQUIRED</span><span class="sxs-lookup"><span data-stu-id="278af-114">E_ CORPROF_E_CALLBACK3_REQUIRED</span></span>|<span data-ttu-id="278af-115">Wystąpił błąd [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) podejmować dla [ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md) interfejs, który musi implementować do obsługi operacji odłączania.</span><span class="sxs-lookup"><span data-stu-id="278af-115">The profiler failed an [IUnknown::QueryInterface](http://go.microsoft.com/fwlink/?LinkID=144867) attempt for the [ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md) interface, which it must implement to support the detach operation.</span></span> <span data-ttu-id="278af-116">Odłączanie nie podjęto próby.</span><span class="sxs-lookup"><span data-stu-id="278af-116">Detach was not attempted.</span></span>|  
|<span data-ttu-id="278af-117">CORPROF_E_IMMUTABLE_FLAGS_SET</span><span class="sxs-lookup"><span data-stu-id="278af-117">CORPROF_E_IMMUTABLE_FLAGS_SET</span></span>|<span data-ttu-id="278af-118">Oderwania jest niemożliwe, ponieważ profiler Ustaw flagi niezmienne podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="278af-118">Detachment is impossible because the profiler set immutable flags at startup.</span></span> <span data-ttu-id="278af-119">Nie podjęto próby oderwania; profiler nadal pełni jest dołączony.</span><span class="sxs-lookup"><span data-stu-id="278af-119">Detachment was not attempted; the profiler is still fully attached.</span></span>|  
|<span data-ttu-id="278af-120">CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT</span><span class="sxs-lookup"><span data-stu-id="278af-120">CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT</span></span>|<span data-ttu-id="278af-121">Oderwania jest niemożliwe, ponieważ profiler używane zinstrumentowane kod języka pośredniego (MSIL) firmy Microsoft lub wstawionego `enter` / `leave` punkty zaczepienia.</span><span class="sxs-lookup"><span data-stu-id="278af-121">Detachment is impossible because the profiler used instrumented Microsoft intermediate language (MSIL) code, or inserted `enter`/`leave` hooks.</span></span> <span data-ttu-id="278af-122">Nie podjęto próby oderwania; profiler nadal pełni jest dołączony.</span><span class="sxs-lookup"><span data-stu-id="278af-122">Detachment was not attempted; the profiler is still fully attached.</span></span><br /><br /> <span data-ttu-id="278af-123">**Uwaga** Zinstrumentowane MSIL jest kod jest kod, który odbywa się przy użyciu profilera [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="278af-123">**Note** Instrumented MSIL is code is code that is provided by the profiler using the [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md) method.</span></span>|  
|<span data-ttu-id="278af-124">CORPROF_E_RUNTIME_UNINITIALIZED</span><span class="sxs-lookup"><span data-stu-id="278af-124">CORPROF_E_RUNTIME_UNINITIALIZED</span></span>|<span data-ttu-id="278af-125">Środowisko uruchomieniowe nie zostały jeszcze zainicjowane w zarządzanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="278af-125">The runtime has not been initialized yet in the managed application.</span></span> <span data-ttu-id="278af-126">(To znaczy środowiska uruchomieniowego nie został całkowicie załadowany.) Tego kodu błędu mogą być zwrócone zleconą oderwania wewnątrz wywołania zwrotnego profilera [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="278af-126">(That is, the runtime has not been fully loaded.) This error code may be returned when detachment is requested inside the profiler callback's [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) method.</span></span>|  
|<span data-ttu-id="278af-127">WYNIK CORPROF_E_UNSUPPORTED_CALL_SEQUENCE</span><span class="sxs-lookup"><span data-stu-id="278af-127">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE</span></span>|<span data-ttu-id="278af-128">`RequestProfilerDetach`została wywołana w czasie nieobsługiwany.</span><span class="sxs-lookup"><span data-stu-id="278af-128">`RequestProfilerDetach` was called at an unsupported time.</span></span> <span data-ttu-id="278af-129">Dzieje się tak, jeśli metoda jest wywoływana w wątku zarządzanego, ale nie za pomocą [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metody lub z poziomu [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metody, które nie tolerują wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="278af-129">This occurs if the method is called on a managed thread but not from within an [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) method or from within an [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) method that cannot tolerate a garbage collection.</span></span> <span data-ttu-id="278af-130">Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span><span class="sxs-lookup"><span data-stu-id="278af-130">For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="278af-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="278af-131">Remarks</span></span>  
 <span data-ttu-id="278af-132">Podczas wykonywania procedury detach detach wątku (Wątek utworzony specjalnie z myślą o odłączanie profilera) od czasu do czasu sprawdza, czy wszystkie wątki zamknięciu kodu profilera.</span><span class="sxs-lookup"><span data-stu-id="278af-132">During the detach procedure, the detach thread (the thread created specifically for detaching the profiler) occasionally checks whether all threads have exited the profiler’s code.</span></span> <span data-ttu-id="278af-133">Profilera powinien podać prognozę, jak długo powinien zostać za pośrednictwem `dwExpectedCompletionMilliseconds` parametru.</span><span class="sxs-lookup"><span data-stu-id="278af-133">The profiler should provide an estimate of how long this should take through the `dwExpectedCompletionMilliseconds` parameter.</span></span> <span data-ttu-id="278af-134">Dobrym wartości do użycia to typowe ilość czasu profilera zużywa wewnątrz żadnej podanej `ICorProfilerCallback*` metody; ta wartość nie powinna być mniejsza niż połowy maksymalną ilość czasu profilera oczekuje poświęcić.</span><span class="sxs-lookup"><span data-stu-id="278af-134">A good value to use is the typical amount of time the profiler spends inside any given `ICorProfilerCallback*` method; this value should not be less than half of the maximum amount of time the profiler expects to spend.</span></span>  
  
 <span data-ttu-id="278af-135">Wątek detach używa `dwExpectedCompletionMilliseconds` decyzji o tym, jak długo do stanu uśpienia przed sprawdzeniem, czy kod wywołania zwrotnego profilera ma zostały zdjęte ze stosu Wyłącz wszystkie stosy.</span><span class="sxs-lookup"><span data-stu-id="278af-135">The detach thread uses `dwExpectedCompletionMilliseconds` to decide how long to sleep before checking whether profiler callback code has been popped off all stacks.</span></span> <span data-ttu-id="278af-136">Mimo że szczegóły następującego algorytmu mogą ulec zmianie w przyszłych wersjach środowiska CLR, zastosowano jeden ze sposobów `dwExpectedCompletionMilliseconds` może być używana podczas ustalania, kiedy jest bezpieczne zwolnić profilera.</span><span class="sxs-lookup"><span data-stu-id="278af-136">Although the details of the following algorithm may change in future releases of the CLR, it illustrates one way `dwExpectedCompletionMilliseconds` can be used when determining when it is safe to unload the profiler.</span></span> <span data-ttu-id="278af-137">Wątek Odłącz najpierw zostanie uśpiony na `dwExpectedCompletionMilliseconds` milisekund.</span><span class="sxs-lookup"><span data-stu-id="278af-137">The detach thread first sleeps for `dwExpectedCompletionMilliseconds` milliseconds.</span></span> <span data-ttu-id="278af-138">Jeśli po aktywności ze stanu uśpienia, CLR stwierdzi, że profiler wywołania zwrotnego kodu jest nadal się tam, odłącz wątek jest w stanie uśpienia ponownie, czas dwa razy `dwExpectedCompletionMilliseconds` milisekund.</span><span class="sxs-lookup"><span data-stu-id="278af-138">If, after awakening from the sleep, the CLR finds that profiler callback code is still present, the detach thread sleeps again, this time for two times `dwExpectedCompletionMilliseconds` milliseconds.</span></span> <span data-ttu-id="278af-139">Jeśli po aktywności z tego drugiego uśpienia, odłącz wątku stwierdzi, że profiler wywołania zwrotnego kodu nadal się tam, zostanie uśpiony na 10 minut przed ponownym sprawdzeniem.</span><span class="sxs-lookup"><span data-stu-id="278af-139">If, after awakening from this second sleep, the detach thread finds that profiler callback code is still present, it sleeps for 10 minutes before checking again.</span></span> <span data-ttu-id="278af-140">Odłącz wątku w dalszym ciągu ponownie co 10 minut.</span><span class="sxs-lookup"><span data-stu-id="278af-140">The detach thread continues to recheck every 10 minutes.</span></span>  
  
 <span data-ttu-id="278af-141">Jeśli określa profilera `dwExpectedCompletionMilliseconds` jako 0 (zero), korzysta z wartości domyślnej 5000, co oznacza, że zostanie przeprowadzone sprawdzanie po 5 sekund, ponownie za 10 sekund, a następnie co 10 minut, następnie środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="278af-141">If the profiler specifies `dwExpectedCompletionMilliseconds` as 0 (zero), the CLR uses a default value of 5000, which means that it will perform a check after 5 seconds, again after 10 seconds, and then every 10 minutes thereafter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="278af-142">Wymagania</span><span class="sxs-lookup"><span data-stu-id="278af-142">Requirements</span></span>  
 <span data-ttu-id="278af-143">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="278af-143">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="278af-144">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="278af-144">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="278af-145">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="278af-145">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="278af-146">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="278af-146">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="278af-147">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="278af-147">See Also</span></span>  
 [<span data-ttu-id="278af-148">ICorProfilerInfo3 — interfejs</span><span class="sxs-lookup"><span data-stu-id="278af-148">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="278af-149">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="278af-149">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="278af-150">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="278af-150">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)