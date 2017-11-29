---
title: "IDebuggerThreadControl::ThreadIsBlockingForDebugger — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location: mscoree.dll
api_type: COM
f1_keywords: ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5b14818f06fec78cfc2cff9ea66548c9ee87bb4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="549f4-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger — Metoda</span><span class="sxs-lookup"><span data-stu-id="549f4-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="549f4-103">Powiadamia hosta, którego dotyczy wątku, który wysyła to wywołanie zwrotne do bloku, w ramach usług debugowania.</span><span class="sxs-lookup"><span data-stu-id="549f4-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="549f4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="549f4-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="549f4-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="549f4-105">Remarks</span></span>  
 <span data-ttu-id="549f4-106">`ThreadIsBlockingForDebugger` Zawsze metoda zostanie wywołana w wątku czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="549f4-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="549f4-107">`ThreadIsBlockingForDebugger` Metoda daje hosta możliwość wykonania innej akcji podczas bloki wątku.</span><span class="sxs-lookup"><span data-stu-id="549f4-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="549f4-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="549f4-108">Requirements</span></span>  
 <span data-ttu-id="549f4-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="549f4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="549f4-110">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="549f4-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="549f4-111">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="549f4-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="549f4-112">**NET Framework w wersji:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="549f4-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="549f4-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="549f4-113">See Also</span></span>  
 [<span data-ttu-id="549f4-114">IDebuggerThreadControl — interfejs</span><span class="sxs-lookup"><span data-stu-id="549f4-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)