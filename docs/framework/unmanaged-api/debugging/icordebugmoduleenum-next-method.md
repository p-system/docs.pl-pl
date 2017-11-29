---
title: "ICorDebugModuleEnum::Next — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModuleEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 917707135f2159b020d9d3c7afb7d70ae466e3e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="73f6d-102">ICorDebugModuleEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="73f6d-102">ICorDebugModuleEnum::Next Method</span></span>
<span data-ttu-id="73f6d-103">Pobiera liczbę wystąpień "ICorDebugModule" określony przez `celt` z wyliczenia, zaczynając od bieżącego położenia.</span><span class="sxs-lookup"><span data-stu-id="73f6d-103">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73f6d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73f6d-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="73f6d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73f6d-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="73f6d-106">[in] Liczba `ICorDebugModule` wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="73f6d-106">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="73f6d-107">[out] Tablicy wskaźników, z których każdy wskazuje `ICorDebugModule` obiektu.</span><span class="sxs-lookup"><span data-stu-id="73f6d-107">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="73f6d-108">[out] Wskaźnik do liczby `ICorDebugModule` wystąpienia faktycznie zwracane.</span><span class="sxs-lookup"><span data-stu-id="73f6d-108">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="73f6d-109">Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="73f6d-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73f6d-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73f6d-110">Requirements</span></span>  
 <span data-ttu-id="73f6d-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73f6d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73f6d-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73f6d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73f6d-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73f6d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73f6d-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73f6d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f6d-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73f6d-115">See Also</span></span>  
 