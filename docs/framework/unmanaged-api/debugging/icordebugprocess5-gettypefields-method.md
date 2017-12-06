---
title: "ICorDebugProcess5::GetTypeFields — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetTypeFields
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7a64e754a77c7d730d921f8a8c1547dd18b66d77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="e639c-102">ICorDebugProcess5::GetTypeFields — Metoda</span><span class="sxs-lookup"><span data-stu-id="e639c-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="e639c-103">Zawiera informacje o polach, które należą do typu.</span><span class="sxs-lookup"><span data-stu-id="e639c-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e639c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e639c-104">Syntax</span></span>  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e639c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e639c-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="e639c-106">[in] Identyfikator typu, których pola informacje są pobierane.</span><span class="sxs-lookup"><span data-stu-id="e639c-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="e639c-107">[in] Liczba [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) obiektów, których informacje pole ma być pobrana.</span><span class="sxs-lookup"><span data-stu-id="e639c-107">[in] The number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="e639c-108">[out] Tablica [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) obiektów, które dostarczają informacji o polach, które należą do tego typu.</span><span class="sxs-lookup"><span data-stu-id="e639c-108">[out] An array of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="e639c-109">[out] Wskaźnik do liczby [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) obiektów uwzględnionych w `fields`.</span><span class="sxs-lookup"><span data-stu-id="e639c-109">[out] A pointer to the number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e639c-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e639c-110">Remarks</span></span>  
 <span data-ttu-id="e639c-111">`celt` Parametr, który określa numer pola, którego metoda używa do wypełniania informacji o polu `fields`, powinna być zgodna z wartością `COR_TYPE_LAYOUT::numFields` pola.</span><span class="sxs-lookup"><span data-stu-id="e639c-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e639c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e639c-112">Requirements</span></span>  
 <span data-ttu-id="e639c-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e639c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e639c-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e639c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e639c-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e639c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e639c-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e639c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e639c-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e639c-117">See Also</span></span>  
 [<span data-ttu-id="e639c-118">ICorDebugProcess5 — interfejs</span><span class="sxs-lookup"><span data-stu-id="e639c-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="e639c-119">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="e639c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)