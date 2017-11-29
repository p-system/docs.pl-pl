---
title: "ICorDebugAppDomainEnum::Next — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugAppDomainEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugAppDomainEnum::Next method
helpviewer_keywords:
- ICorDebugAppDomainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugAppDomainEnum interface [.NET Framework debugging]
ms.assetid: b8d1def7-0ebc-4314-a3a2-fd36a75973e7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 10d53ebac99942ac9376041f217df53965bdbb2f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugappdomainenumnext-method"></a><span data-ttu-id="7b1c3-102">ICorDebugAppDomainEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="7b1c3-102">ICorDebugAppDomainEnum::Next Method</span></span>
<span data-ttu-id="7b1c3-103">Pobiera określoną liczbę domen aplikacji z kolekcji, począwszy od bieżącej pozycji kursora.</span><span class="sxs-lookup"><span data-stu-id="7b1c3-103">Gets the specified number of application domains from the collection, starting at the current cursor position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b1c3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7b1c3-104">Syntax</span></span>  
  
```  
HRESULT Next (  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
                           ICorDebugAppDomain *values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b1c3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b1c3-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="7b1c3-106">[in] Liczba domen aplikacji, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="7b1c3-106">[in] The number of application domains to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="7b1c3-107">[out] Tablicy wskaźników, z których każdy wskazuje obiekt ICorDebugAppDomain, który reprezentuje domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7b1c3-107">[out] An array of pointers, each of which points to an ICorDebugAppDomain object that represents an application domain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="7b1c3-108">[out] Wskaźnik do liczby domen aplikacji faktycznie zwracane.</span><span class="sxs-lookup"><span data-stu-id="7b1c3-108">[out] A pointer to the number of application domains actually returned.</span></span> <span data-ttu-id="7b1c3-109">Ta wartość może mieć wartości zerowej Jeśli `celt` jeden.</span><span class="sxs-lookup"><span data-stu-id="7b1c3-109">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b1c3-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7b1c3-110">Requirements</span></span>  
 <span data-ttu-id="7b1c3-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b1c3-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b1c3-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b1c3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b1c3-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b1c3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b1c3-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b1c3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>