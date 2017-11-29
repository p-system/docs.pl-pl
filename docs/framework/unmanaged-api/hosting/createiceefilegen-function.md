---
title: "CreateICeeFileGen — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CreateICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type: COM
f1_keywords: CreateICeeFileGen
helpviewer_keywords: CreateICeeFileGen function [.NET Framework hosting]
ms.assetid: e36e1fd8-8456-4359-bdc3-3ec1765f041f
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9162da1b48348da745f8616b5cc643bf3dee97fe
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="createiceefilegen-function"></a><span data-ttu-id="00bb9-102">CreateICeeFileGen — Funkcja</span><span class="sxs-lookup"><span data-stu-id="00bb9-102">CreateICeeFileGen Function</span></span>
<span data-ttu-id="00bb9-103">Tworzy [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="00bb9-103">Creates an [ICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="00bb9-104">Ta funkcja jest przestarzała w [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="00bb9-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00bb9-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="00bb9-105">Syntax</span></span>  
  
```  
HRESULT CreateICeeFileGen (  
    [out] ICeeFileGen  **ceeFileGen  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00bb9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="00bb9-106">Parameters</span></span>  
 `ceeFileGen`  
 <span data-ttu-id="00bb9-107">[out] Wskaźnik do nowego adresu `ICeeFileGen` obiektu.</span><span class="sxs-lookup"><span data-stu-id="00bb9-107">[out] A pointer to the address of a new `ICeeFileGen` object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="00bb9-108">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="00bb9-108">Return Value</span></span>  
 <span data-ttu-id="00bb9-109">Ta metoda zwraca standardowe kody błędów COM.</span><span class="sxs-lookup"><span data-stu-id="00bb9-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00bb9-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00bb9-110">Remarks</span></span>  
 <span data-ttu-id="00bb9-111">`ICeeFileGen` Obiekt jest używany do tworzenia wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) przenośny plik wykonywalny (PE) plików.</span><span class="sxs-lookup"><span data-stu-id="00bb9-111">The `ICeeFileGen` object is used to create common language runtime (CLR) portable executable (PE) files.</span></span>  
  
 <span data-ttu-id="00bb9-112">Wywołanie [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) funkcji do zniszczenia `ICeeFileGen` obiekt po zakończeniu.</span><span class="sxs-lookup"><span data-stu-id="00bb9-112">Call the [DestroyICeeFileGen](../../../../docs/framework/unmanaged-api/hosting/destroyiceefilegen-function.md) function to destroy the `ICeeFileGen` object when finished.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00bb9-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00bb9-113">Requirements</span></span>  
 <span data-ttu-id="00bb9-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00bb9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00bb9-115">**Nagłówek:** ICeeFileGen.h</span><span class="sxs-lookup"><span data-stu-id="00bb9-115">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="00bb9-116">**Biblioteka:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="00bb9-116">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="00bb9-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00bb9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00bb9-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="00bb9-118">See Also</span></span>  
 [<span data-ttu-id="00bb9-119">Przestarzałe funkcje hostingu środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="00bb9-119">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)