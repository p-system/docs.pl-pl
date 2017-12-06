---
title: "ICLRErrorReportingManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRErrorReportingManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRErrorReportingManager
helpviewer_keywords: ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 590cd87d6a566e9c8c3819fd1b250997938e9c35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="160da-102">ICLRErrorReportingManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="160da-102">ICLRErrorReportingManager Interface</span></span>
<span data-ttu-id="160da-103">Udostępnia metody umożliwiające hosta skonfigurować zrzuty stosu niestandardowych dla usługi raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="160da-103">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="160da-104">Metody</span><span class="sxs-lookup"><span data-stu-id="160da-104">Methods</span></span>  
  
|<span data-ttu-id="160da-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="160da-105">Method</span></span>|<span data-ttu-id="160da-106">Opis</span><span class="sxs-lookup"><span data-stu-id="160da-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="160da-107">BeginCustomDump — metoda</span><span class="sxs-lookup"><span data-stu-id="160da-107">BeginCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="160da-108">Określa konfigurację zrzuty stosu niestandardowych dla usługi raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="160da-108">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="160da-109">EndCustomDump — metoda</span><span class="sxs-lookup"><span data-stu-id="160da-109">EndCustomDump Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="160da-110">Czyści konfiguracji zrzutu niestandardowych stos został ustawiony przez wywołanie wcześniejszych `BeginCustomDump`.</span><span class="sxs-lookup"><span data-stu-id="160da-110">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="160da-111">GetBucketParametersForCurrentException — metoda</span><span class="sxs-lookup"><span data-stu-id="160da-111">GetBucketParametersForCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="160da-112">Pobiera bieżący wyjątek w wątku wywołującym pakiet programu Watson.</span><span class="sxs-lookup"><span data-stu-id="160da-112">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="160da-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="160da-113">Remarks</span></span>  
 <span data-ttu-id="160da-114">`BeginCustomDump` Metoda ustawia Konfiguracja zrzutu stosu niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="160da-114">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="160da-115">`EndCustomDump` Metody spowoduje wyczyszczenie stosu niestandardowej konfiguracji zrzutu i zwalnia każdy stan skojarzony.</span><span class="sxs-lookup"><span data-stu-id="160da-115">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="160da-116">Należy wywołać po wykonaniu zrzutu niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="160da-116">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="160da-117">Nie można wywołać `EndCustomDump` powoduje, że nastąpił przeciek pamięci.</span><span class="sxs-lookup"><span data-stu-id="160da-117">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="160da-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="160da-118">Requirements</span></span>  
 <span data-ttu-id="160da-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="160da-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="160da-120">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="160da-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="160da-121">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="160da-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="160da-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="160da-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="160da-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="160da-123">See Also</span></span>  
 [<span data-ttu-id="160da-124">ECustomDumpItemKind — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="160da-124">ECustomDumpItemKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/ecustomdumpitemkind-enumeration.md)  
 [<span data-ttu-id="160da-125">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="160da-125">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)