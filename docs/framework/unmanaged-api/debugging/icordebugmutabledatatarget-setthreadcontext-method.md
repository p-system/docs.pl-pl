---
title: "ICorDebugMutableDataTarget::SetThreadContext — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8c43ef5405ed582cc55af69d7f41887c0615965f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a><span data-ttu-id="05b1d-102">ICorDebugMutableDataTarget::SetThreadContext — metoda</span><span class="sxs-lookup"><span data-stu-id="05b1d-102">ICorDebugMutableDataTarget::SetThreadContext Method</span></span>
<span data-ttu-id="05b1d-103">Ustawia kontekst wątku (wartości rejestru).</span><span class="sxs-lookup"><span data-stu-id="05b1d-103">Sets the context (register values) for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05b1d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="05b1d-104">Syntax</span></span>  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="05b1d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="05b1d-105">Parameters</span></span>  
 `dwThreadID`  
 <span data-ttu-id="05b1d-106">[in] Identyfikator wątku zdefiniowane przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="05b1d-106">[in] The operating system-defined thread identifier.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="05b1d-107">[in] Rozmiar `pContext` buforu do zapisania.</span><span class="sxs-lookup"><span data-stu-id="05b1d-107">[in] The size of the `pContext` buffer to be written.</span></span>  
  
 `pContext`  
 <span data-ttu-id="05b1d-108">[in] Wskaźnik do bajtów do zapisania.</span><span class="sxs-lookup"><span data-stu-id="05b1d-108">[in] A pointer to the bytes to be written.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="05b1d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="05b1d-109">Remarks</span></span>  
 <span data-ttu-id="05b1d-110">`SetThreadContext` Metody aktualizacji bieżący kontekst wątku określony przez system operacyjny zdefiniowane `dwThreadID` argumentu.</span><span class="sxs-lookup"><span data-stu-id="05b1d-110">The `SetThreadContext` method updates the current context for the thread specified by the operating system-defined `dwThreadID` argument.</span></span> <span data-ttu-id="05b1d-111">Format rekordu kontekstu jest określany przez platformy wskazywaną przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="05b1d-111">The format of the context record is determined by the platform indicated by the [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) method.</span></span> <span data-ttu-id="05b1d-112">W systemie Windows, to [KONTEKSTU](http://msdn.microsoft.com/library/windows/desktop/ms679284.aspx) struktury.</span><span class="sxs-lookup"><span data-stu-id="05b1d-112">On Windows, this is a [CONTEXT](http://msdn.microsoft.com/library/windows/desktop/ms679284.aspx) structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05b1d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="05b1d-113">Requirements</span></span>  
 <span data-ttu-id="05b1d-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05b1d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05b1d-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05b1d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05b1d-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05b1d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05b1d-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05b1d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05b1d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05b1d-118">See Also</span></span>  
 [<span data-ttu-id="05b1d-119">Interfejs ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="05b1d-119">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="05b1d-120">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="05b1d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)