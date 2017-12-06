---
title: "ICLRDataTarget3 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget3
api_location: mscordbi.dll
api_type: COM
ms.assetid: d2711bdf-64b3-404c-a0c3-01ba4907f703
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16e2d2aa1a2626f4124e1b43ff85abcdd17f6990
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdatatarget3-interface"></a><span data-ttu-id="e2dab-102">ICLRDataTarget3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e2dab-102">ICLRDataTarget3 Interface</span></span>
<span data-ttu-id="e2dab-103">Podklasa [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) , który zapewnia dostęp do informacji o wyjątku.</span><span class="sxs-lookup"><span data-stu-id="e2dab-103">A subclass of [ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md) that provides access to exception information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e2dab-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e2dab-104">Methods</span></span>  
  
|<span data-ttu-id="e2dab-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e2dab-105">Method</span></span>|<span data-ttu-id="e2dab-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e2dab-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e2dab-107">GetExceptionRecord — metoda</span><span class="sxs-lookup"><span data-stu-id="e2dab-107">GetExceptionRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionrecord-method.md)|<span data-ttu-id="e2dab-108">Wywoływana przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) w celu pobrania rekordu wyjątku skojarzonego z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="e2dab-108">Called by the common language runtime (CLR) data access services to retrieve the exception record associated with the target process.</span></span>|  
|[<span data-ttu-id="e2dab-109">Metoda GetExceptionContextRecord</span><span class="sxs-lookup"><span data-stu-id="e2dab-109">GetExceptionContextRecord Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptioncontextrecord-method.md)|<span data-ttu-id="e2dab-110">Wywoływana przez usługi dostępu do danych CLR w celu pobrania rekordu kontekstu skojarzonego z procesem docelowym.</span><span class="sxs-lookup"><span data-stu-id="e2dab-110">Called by the CLR data access services to retrieve the context record associated with the target process.</span></span>|  
|[<span data-ttu-id="e2dab-111">Metoda GetExceptionThreadID</span><span class="sxs-lookup"><span data-stu-id="e2dab-111">GetExceptionThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-getexceptionthreadid-method.md)|<span data-ttu-id="e2dab-112">Metoda wywoływana przez usługi dostępu do danych CLR można uzyskać Identyfikatora wątku, który zgłosił wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e2dab-112">Called by the CLR data access services to get the ID of the thread that threw the exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2dab-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e2dab-113">Remarks</span></span>  
 <span data-ttu-id="e2dab-114">Klient API (tzn. debuger) musi implementować ten interfejs stosownie do określonego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="e2dab-114">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="e2dab-115">Na przykład żywy proces miałby inną implementację od tej ze zrzutu pamięci.</span><span class="sxs-lookup"><span data-stu-id="e2dab-115">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="e2dab-116">Cel może nie obsługiwać modyfikacji regionów pamięci.</span><span class="sxs-lookup"><span data-stu-id="e2dab-116">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2dab-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e2dab-117">Requirements</span></span>  
 <span data-ttu-id="e2dab-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2dab-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2dab-119">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="e2dab-119">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="e2dab-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2dab-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2dab-121">**Wersje programu .NET framework:**[!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2dab-121">**.NET Framework Versions:** [!INCLUDE[v451_update](../../../../includes/v451-update-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2dab-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e2dab-122">See Also</span></span>  
 [<span data-ttu-id="e2dab-123">ICLRDataTarget — interfejs</span><span class="sxs-lookup"><span data-stu-id="e2dab-123">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="e2dab-124">ICLRDataTarget2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="e2dab-124">ICLRDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 [<span data-ttu-id="e2dab-125">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="e2dab-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)