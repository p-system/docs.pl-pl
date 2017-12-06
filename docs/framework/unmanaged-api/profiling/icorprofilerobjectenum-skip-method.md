---
title: "ICorProfilerObjectEnum::Skip — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerObjectEnum.Skip
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 84960af6e128f3a6aa9e3b45187e282ac7228e0f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="d3880-102">ICorProfilerObjectEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3880-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="d3880-103">Przesuwa kursor tego modułu wyliczającego z jego bieżącym położeniu, dzięki czemu określoną liczbę elementów są pomijane.</span><span class="sxs-lookup"><span data-stu-id="d3880-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3880-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3880-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d3880-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3880-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d3880-106">[in] Liczba elementów do pominięcia.</span><span class="sxs-lookup"><span data-stu-id="d3880-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3880-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3880-107">Remarks</span></span>  
 <span data-ttu-id="d3880-108">Nowa pozycja kursora ten moduł wyliczający jest: (bieżące położenie) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="d3880-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3880-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3880-109">Requirements</span></span>  
 <span data-ttu-id="d3880-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3880-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3880-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d3880-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d3880-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3880-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3880-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3880-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3880-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3880-114">See Also</span></span>  
 [<span data-ttu-id="d3880-115">ICorProfilerObjectEnum — interfejs</span><span class="sxs-lookup"><span data-stu-id="d3880-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)