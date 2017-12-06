---
title: "IMetaDataImport::EnumMethodsWithName — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.EnumMethodsWithName
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::EnumMethodsWithName
helpviewer_keywords:
- IMetaDataImport::EnumMethodsWithName method [.NET Framework metadata]
- EnumMethodsWithName method [.NET Framework metadata]
ms.assetid: a8624913-2e23-46ad-a0c1-bb8eccbbf20f
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dadff8be283160ddc6049d0d2f8b78052e5c8ec5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportenummethodswithname-method"></a><span data-ttu-id="85abb-102">IMetaDataImport::EnumMethodsWithName — Metoda</span><span class="sxs-lookup"><span data-stu-id="85abb-102">IMetaDataImport::EnumMethodsWithName Method</span></span>
<span data-ttu-id="85abb-103">Wylicza metody tym, które są definiowane przez typ odwołuje się określony token TypeDef określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="85abb-103">Enumerates methods that have the specified name and that are defined by the type referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85abb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="85abb-104">Syntax</span></span>  
  
```  
HRESULT EnumMethodsWithName (  
   [in, out] HCORENUM    *phEnum,  
   [in]  mdTypeDef       cl,  
   [in]  LPCWSTR         szName,  
   [out] mdMethodDef     rMethods[],  
   [in]  ULONG           cMax,  
   [out] ULONG           *pcTokens  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85abb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85abb-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="85abb-106">[w, out] Wskaźnik do modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="85abb-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="85abb-107">Musi to być wartość NULL dla pierwsze wywołanie tej metody.</span><span class="sxs-lookup"><span data-stu-id="85abb-107">This must be NULL for the first call of this method.</span></span>  
  
 `cl`  
 <span data-ttu-id="85abb-108">[in] TypeDef token reprezentujący typ, której metody wyliczania.</span><span class="sxs-lookup"><span data-stu-id="85abb-108">[in] A TypeDef token representing the type whose methods to enumerate.</span></span>  
  
 `szName`  
 <span data-ttu-id="85abb-109">[in] Nazwa, która ogranicza zakres wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="85abb-109">[in] The name that limits the scope of the enumeration.</span></span>  
  
 `rMethods`  
 <span data-ttu-id="85abb-110">[out] Tablica używany do przechowywania tokenów MethodDef.</span><span class="sxs-lookup"><span data-stu-id="85abb-110">[out] The array used to store the MethodDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="85abb-111">[in] Maksymalny rozmiar `rMethods` tablicy.</span><span class="sxs-lookup"><span data-stu-id="85abb-111">[in] The maximum size of the `rMethods` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="85abb-112">[out] Liczba tokenów MethodDef zwracane w `rMethods`.</span><span class="sxs-lookup"><span data-stu-id="85abb-112">[out] The number of MethodDef tokens returned in `rMethods`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85abb-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="85abb-113">Remarks</span></span>  
 <span data-ttu-id="85abb-114">Ta metoda wylicza pól i metod, ale nie do właściwości lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="85abb-114">This method enumerates fields and methods, but not properties or events.</span></span> <span data-ttu-id="85abb-115">W odróżnieniu od [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` odrzuca wszystkie tokeny metody, które nie mają określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="85abb-115">Unlike [IMetaDataImport::EnumMethods](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enummethods-method.md), `EnumMethodsWithName` discards all method tokens that do not have the specified name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85abb-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="85abb-116">Return Value</span></span>  
  
|<span data-ttu-id="85abb-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="85abb-117">HRESULT</span></span>|<span data-ttu-id="85abb-118">Opis</span><span class="sxs-lookup"><span data-stu-id="85abb-118">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="85abb-119">`EnumMethodsWithName`zwrócona pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="85abb-119">`EnumMethodsWithName` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="85abb-120">Nie ma żadnych tokenów do wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="85abb-120">There are no tokens to enumerate.</span></span> <span data-ttu-id="85abb-121">W takim przypadku `pcTokens` wynosi zero.</span><span class="sxs-lookup"><span data-stu-id="85abb-121">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85abb-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85abb-122">Requirements</span></span>  
 <span data-ttu-id="85abb-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85abb-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85abb-124">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="85abb-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85abb-125">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="85abb-125">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="85abb-126">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85abb-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85abb-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85abb-127">See Also</span></span>  
 [<span data-ttu-id="85abb-128">IMetaDataImport — interfejs</span><span class="sxs-lookup"><span data-stu-id="85abb-128">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="85abb-129">IMetaDataImport2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="85abb-129">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)