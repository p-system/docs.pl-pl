---
title: "IMetaDataEmit::SetTypeDefProps — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataEmit.SetTypeDefProps
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataEmit::SetTypeDefProps
helpviewer_keywords:
- SetTypeDefProps method [.NET Framework metadata]
- IMetaDataEmit::SetTypeDefProps method [.NET Framework metadata]
ms.assetid: 480d596a-759f-4d29-ac1a-3dbff8f3544d
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 50f92d0ff307621695887ee7a0af2d4d19985f51
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataemitsettypedefprops-method"></a><span data-ttu-id="5dd90-102">IMetaDataEmit::SetTypeDefProps — Metoda</span><span class="sxs-lookup"><span data-stu-id="5dd90-102">IMetaDataEmit::SetTypeDefProps Method</span></span>
<span data-ttu-id="5dd90-103">Zestawy funkcji zdefiniowanych przez poprzednie wywołanie [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="5dd90-103">Sets features of a type defined by a prior call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5dd90-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5dd90-104">Syntax</span></span>  
  
```  
HRESULT SetTypeDefProps (  
    [in]  mdTypeDef   td,   
    [in]  DWORD       dwTypeDefFlags,   
    [in]  mdToken     tkExtends,   
    [in]  mdToken     rtkImplements[]   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5dd90-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5dd90-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="5dd90-106">[in] `mdTypeDef` Tokenu uzyskanego z oryginalnego wywołania [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span><span class="sxs-lookup"><span data-stu-id="5dd90-106">[in] An `mdTypeDef` token obtained from original call to [IMetaDataEmit::DefineTypeDef](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-definetypedef-method.md).</span></span>  
  
 `dwTypeDefFlags`  
 <span data-ttu-id="5dd90-107">[in] `TypeDef` atrybutów.</span><span class="sxs-lookup"><span data-stu-id="5dd90-107">[in] `TypeDef` attributes.</span></span> <span data-ttu-id="5dd90-108">To jest maską bitów z `CorTypeAttr` wartości.</span><span class="sxs-lookup"><span data-stu-id="5dd90-108">This is a bitmask of `CorTypeAttr` values.</span></span>  
  
 `tkExtends`  
 <span data-ttu-id="5dd90-109">[in] `mdToken` Klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="5dd90-109">[in] The `mdToken` of the base class.</span></span> <span data-ttu-id="5dd90-110">Uzyskane z poprzedniego wywołania [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), lub `null`.</span><span class="sxs-lookup"><span data-stu-id="5dd90-110">Obtained from a previous call to [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md), or `null`.</span></span>  
  
 `rtkImplements[]`  
 <span data-ttu-id="5dd90-111">[in] Tablica dla interfejsów, które implementuje tego typu.</span><span class="sxs-lookup"><span data-stu-id="5dd90-111">[in] An array of tokens for the interfaces that this type implements.</span></span> <span data-ttu-id="5dd90-112">Te `mdTypeRef` tokeny są uzyskiwane przy użyciu [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span><span class="sxs-lookup"><span data-stu-id="5dd90-112">These `mdTypeRef` tokens are obtained using [IMetaDataEmit::DefineImportType](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-defineimporttype-method.md).</span></span> <span data-ttu-id="5dd90-113">Jest ostatnim elemencie tablicy musi być `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="5dd90-113">The last element of the array is must be `mdTokenNil`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5dd90-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5dd90-114">Requirements</span></span>  
 <span data-ttu-id="5dd90-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5dd90-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5dd90-116">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5dd90-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5dd90-117">**Biblioteka:** używany jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="5dd90-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5dd90-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5dd90-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dd90-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5dd90-119">See Also</span></span>  
 [<span data-ttu-id="5dd90-120">IMetaDataEmit — interfejs</span><span class="sxs-lookup"><span data-stu-id="5dd90-120">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="5dd90-121">IMetaDataEmit2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="5dd90-121">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)