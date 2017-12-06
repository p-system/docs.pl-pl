---
title: "ICorProfilerCallback::ExceptionCatcherEnter — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionCatcherEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b1605fdca3f5aa13ce4e29c0ff2fb42383512e6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="dce59-102">ICorProfilerCallback::ExceptionCatcherEnter — Metoda</span><span class="sxs-lookup"><span data-stu-id="dce59-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="dce59-103">Powiadamia profiler kontrola jest przekazywana do odpowiedniego `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="dce59-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dce59-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dce59-104">Syntax</span></span>  
  
```  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dce59-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dce59-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="dce59-106">[in] Identyfikator zawierający funkcja `catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="dce59-106">[in] The identifier of the function containing the `catch` block.</span></span>  
  
 `objectId`  
 <span data-ttu-id="dce59-107">[in] Identyfikator obsługiwanie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="dce59-107">[in] The identifier of the exception being handled.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dce59-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dce59-108">Remarks</span></span>  
 <span data-ttu-id="dce59-109">`ExceptionCatcherEnter` Metoda jest wywoływana tylko wtedy, gdy punkt catch w kodzie skompilowanym z kompilatora just-in-time (JIT).</span><span class="sxs-lookup"><span data-stu-id="dce59-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="dce59-110">Wyjątek zostanie przechwycony za pomocą kodu niezarządzanego lub w kodzie wewnętrzny środowiska uruchomieniowego nie wywoła tego powiadomienia.</span><span class="sxs-lookup"><span data-stu-id="dce59-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="dce59-111">`objectId` Została przekazana wartość ponownie ponieważ wyrzucania elementów bezużytecznych można przenieść obiektu, ponieważ `ExceptionThrown` powiadomień.</span><span class="sxs-lookup"><span data-stu-id="dce59-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="dce59-112">Profilera nie należy zablokować w jej implementacja tej metody, ponieważ stos nie może być w stanie, który umożliwia odzyskiwanie pamięci i dlatego nie można włączyć cenią sobie wcześniejsze wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="dce59-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="dce59-113">Jeśli profilera blokuje tutaj i nastąpiła wyrzucanie elementów bezużytecznych, środowisko uruchomieniowe zablokuje dopóki zwraca tego wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="dce59-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="dce59-114">Profiler implementacja tej metody nie powinny wywoływać kodu zarządzanego lub w dowolnym Przyczyna sposób alokacji pamięci zarządzane.</span><span class="sxs-lookup"><span data-stu-id="dce59-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dce59-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dce59-115">Requirements</span></span>  
 <span data-ttu-id="dce59-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dce59-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dce59-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dce59-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dce59-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dce59-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dce59-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dce59-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce59-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dce59-120">See Also</span></span>  
 [<span data-ttu-id="dce59-121">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="dce59-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="dce59-122">ExceptionCatcherLeave — metoda</span><span class="sxs-lookup"><span data-stu-id="dce59-122">ExceptionCatcherLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)