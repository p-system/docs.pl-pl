---
title: "ICorProfilerCallback4::ReJITCompilationStarted — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.ReJITCompilationStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::ReJITCompilationStarted
helpviewer_keywords:
- ReJITCompilationStarted method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITCompilationStarted method [.NET Framework profiling]
ms.assetid: 512fdd00-262a-4456-a075-365ef4133c4d
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ddcacf72d21ec076fe74a1c069311ef3f73a20c2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4rejitcompilationstarted-method"></a><span data-ttu-id="d85d6-102">ICorProfilerCallback4::ReJITCompilationStarted — Metoda</span><span class="sxs-lookup"><span data-stu-id="d85d6-102">ICorProfilerCallback4::ReJITCompilationStarted Method</span></span>
<span data-ttu-id="d85d6-103">Powiadamia profilera, czy można ponownie skompilować funkcję została uruchomiona przy użyciu kompilatora just in time (JIT).</span><span class="sxs-lookup"><span data-stu-id="d85d6-103">Notifies the profiler that the just-in-time (JIT) compiler has started to recompile a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d85d6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d85d6-104">Syntax</span></span>  
  
```  
HRESULT ReJITCompilationStarted(    [in] FunctionID functionId,  
    [in] ReJITID    rejitId,  
    [in] BOOL       fIsSafeToBlock);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d85d6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d85d6-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d85d6-106">[in] Identyfikator funkcji rozpoczęcia ponowną kompilację przy użyciu kompilatora JIT.</span><span class="sxs-lookup"><span data-stu-id="d85d6-106">[in] The ID of the function that the JIT compiler has started to recompile.</span></span>  
  
 `rejitId`  
 <span data-ttu-id="d85d6-107">[in] Identyfikator nowej wersji funkcji ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d85d6-107">[in] The recompilation ID of the new version of the function.</span></span>  
  
 `fIsSafeToBlock`  
 <span data-ttu-id="d85d6-108">[in] `true` wskazująca, czy blokowanie może spowodować środowiska uruchomieniowego oczekiwania na wątek wywołujący do zwrócenia z tego wywołania zwrotnego; `false` wskazująca, czy blokowanie nie wpływa na działanie środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="d85d6-108">[in] `true` to indicate that blocking may cause the runtime to wait for the calling thread to return from this callback; `false` to indicate that blocking will not affect the operation of the runtime.</span></span> <span data-ttu-id="d85d6-109">Wartość `true` nie uszkodzić środowiska uruchomieniowego, ale może mieć wpływ na wyniki profilowania.</span><span class="sxs-lookup"><span data-stu-id="d85d6-109">A value of `true` does not harm the runtime, but can affect the profiling results.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d85d6-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d85d6-110">Remarks</span></span>  
 <span data-ttu-id="d85d6-111">Istnieje możliwość odbierania więcej niż jedną parę `ReJITCompilationStarted` i [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) wywołania metod dla każdej funkcji ze względu na sposób środowiska uruchomieniowego konstruktorów klas uchwytów.</span><span class="sxs-lookup"><span data-stu-id="d85d6-111">It is possible to receive more than one pair of `ReJITCompilationStarted` and [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) method calls for each function because of the way the runtime handles class constructors.</span></span> <span data-ttu-id="d85d6-112">Na przykład środowiska uruchomieniowego uruchamia ponowną kompilację metoda, ale konstruktora klasy dla klasy B musi zostać uruchomione.</span><span class="sxs-lookup"><span data-stu-id="d85d6-112">For example, the runtime starts to recompile method A, but the class constructor for class B needs to be run.</span></span> <span data-ttu-id="d85d6-113">W związku z tym środowiska uruchomieniowego rekompiluje konstruktora dla klasy B i uruchamia go.</span><span class="sxs-lookup"><span data-stu-id="d85d6-113">Therefore, the runtime recompiles the constructor for class B and runs it.</span></span> <span data-ttu-id="d85d6-114">Konstruktor jest uruchomiona, powoduje wywołanie do metody A, co powoduje, że metoda A ponownie skompilowana.</span><span class="sxs-lookup"><span data-stu-id="d85d6-114">While the constructor is running, it makes a call to method A, which causes method A to be recompiled again.</span></span> <span data-ttu-id="d85d6-115">W tym scenariuszu pierwszy kompilację metoda jest zatrzymywane.</span><span class="sxs-lookup"><span data-stu-id="d85d6-115">In this scenario, the first recompilation of method A is halted.</span></span> <span data-ttu-id="d85d6-116">Jednak zarówno próbuje ponownie skompilować metody są zgłaszane zdarzenia ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="d85d6-116">However, both attempts to recompile method A are reported with JIT recompilation events.</span></span>  
  
 <span data-ttu-id="d85d6-117">Profilery musi obsługiwać sekwencję wywołań zwrotnych ponownej kompilacji JIT w przypadkach, gdy dwa wątków jednocześnie dokonywania wywołań zwrotnych.</span><span class="sxs-lookup"><span data-stu-id="d85d6-117">Profilers must support the sequence of JIT recompilation callbacks in cases where two threads are simultaneously making callbacks.</span></span> <span data-ttu-id="d85d6-118">Na przykład wywołuje wątku A `ReJITCompilationStarted`; jednak przed wywołania wątku A [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), wywołania wątku B [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) o identyfikatorze — funkcja z `ReJITCompilationStarted` wywołania zwrotnego dla wątku A. Wydaje się, że identyfikator funkcji należy jeszcze być nieprawidłowe ponieważ wywołania [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) nie ma jeszcze odebrane profilera.</span><span class="sxs-lookup"><span data-stu-id="d85d6-118">For example, thread A calls `ReJITCompilationStarted`; however, before thread A calls [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md), thread B calls [ICorProfilerCallback::ExceptionSearchFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md) with the function ID from the `ReJITCompilationStarted` callback for thread A. It might appear that the function ID should not yet be valid because a call to [ReJITCompilationFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md) had not yet been received by the profiler.</span></span> <span data-ttu-id="d85d6-119">Jednak w takim przypadku funkcja identyfikator jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="d85d6-119">However, in this case, the function ID is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d85d6-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d85d6-120">Requirements</span></span>  
 <span data-ttu-id="d85d6-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d85d6-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d85d6-122">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d85d6-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d85d6-123">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d85d6-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d85d6-124">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d85d6-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d85d6-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d85d6-125">See Also</span></span>  
 [<span data-ttu-id="d85d6-126">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="d85d6-126">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="d85d6-127">ICorProfilerCallback4 — interfejs</span><span class="sxs-lookup"><span data-stu-id="d85d6-127">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [<span data-ttu-id="d85d6-128">JITCompilationFinished — metoda</span><span class="sxs-lookup"><span data-stu-id="d85d6-128">JITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)  
 [<span data-ttu-id="d85d6-129">ReJITCompilationFinished — metoda</span><span class="sxs-lookup"><span data-stu-id="d85d6-129">ReJITCompilationFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)