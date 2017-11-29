---
title: "ICorDebugType::EnumerateTypeParameters — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.EnumerateTypeParameters
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::EnumerateTypeParameters
helpviewer_keywords:
- EnumerateTypeParameters method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::EnumerateTypeParameters method [.NET Framework debugging]
ms.assetid: 1ee1f6e6-1bd7-4ebb-83b8-ff9a08ca03de
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e9dd00b0a5f28821112621a54c97551c71e1acc6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugtypeenumeratetypeparameters-method"></a><span data-ttu-id="817d2-102">ICorDebugType::EnumerateTypeParameters — Metoda</span><span class="sxs-lookup"><span data-stu-id="817d2-102">ICorDebugType::EnumerateTypeParameters Method</span></span>
<span data-ttu-id="817d2-103">Pobiera wskaźnika interfejsu do ICorDebugTypeEnum, który zawiera <xref:System.Type> parametry odwołuje się ten ICorDebugType klasy.</span><span class="sxs-lookup"><span data-stu-id="817d2-103">Gets an interface pointer to an ICorDebugTypeEnum that contains the <xref:System.Type> parameters of the class referenced by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="817d2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="817d2-104">Syntax</span></span>  
  
```  
HRESULT EnumerateTypeParameters (  
    [out] ICorDebugTypeEnum   **ppTyParEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="817d2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="817d2-105">Parameters</span></span>  
 `ppTyParEnum`  
 <span data-ttu-id="817d2-106">[out] Wskaźnik do adresu `ICorDebugTypeEnum` zawiera parametry typu.</span><span class="sxs-lookup"><span data-stu-id="817d2-106">[out] A pointer to the address of an `ICorDebugTypeEnum` that contains the parameters of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="817d2-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="817d2-107">Remarks</span></span>  
 <span data-ttu-id="817d2-108">Można użyć `EnumerateTypeParameters` Jeśli CorElementType wartość zwracana przez [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) po elemencie ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, element ELEMENT_TYPE_ PTR lub ELEMENT_TYPE_FNPTR.</span><span class="sxs-lookup"><span data-stu-id="817d2-108">You can use `EnumerateTypeParameters` if the CorElementType value returned by [ICorDebugType::GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) is ELEMENT_TYPE_CLASS, ELEMENT_TYPE_VALUETYPE, ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, ELEMENT_TYPE_PTR, or ELEMENT_TYPE_FNPTR.</span></span> <span data-ttu-id="817d2-109">Liczba parametrów i ich kolejność, zależy od typu:</span><span class="sxs-lookup"><span data-stu-id="817d2-109">The number of parameters and their order depends on the type:</span></span>  
  
-   <span data-ttu-id="817d2-110">Po elemencie ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE: liczba parametrów typu zawartych w `ICorDebugTypeEnum` ta metoda zwraca, zależy od liczby parametrów typu formalnego dla odpowiedniej klasy.</span><span class="sxs-lookup"><span data-stu-id="817d2-110">ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE: The number of type parameters contained in the `ICorDebugTypeEnum` that this method returns, will depend on the number of formal type parameters for the corresponding class.</span></span> <span data-ttu-id="817d2-111">Na przykład, jeśli typ jest `class Dict<String,int32>`, następnie `EnumerateTypeParameters` zwróci `ICorDebugTypeEnum` zawierający obiekty reprezentujące `String` i `int32` w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="817d2-111">For example, if the type is `class Dict<String,int32>`, then `EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains objects representing `String` and `int32` in sequence.</span></span>  
  
-   <span data-ttu-id="817d2-112">ELEMENT_TYPE_FNPTR: Liczba parametrów typu zawartych w `ICorDebugTypeEnum` będzie jeden większa niż liczba argumentów akceptowanych przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="817d2-112">ELEMENT_TYPE_FNPTR: The number of type parameters contained in the `ICorDebugTypeEnum` will be one greater than the number of arguments accepted by the function.</span></span> <span data-ttu-id="817d2-113">Pierwszy parametr typu zawartych w `ICorDebugTypeEnum` jest typ zwracany funkcji i parametrów typu kolejne parametry funkcji.</span><span class="sxs-lookup"><span data-stu-id="817d2-113">The first type parameter contained in the `ICorDebugTypeEnum` is the return type for the function, and the subsequent type parameters are the function's parameters.</span></span>  
  
-   <span data-ttu-id="817d2-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF lub poprawności elementu ELEMENT_TYPE_PTR: zostanie zwrócony jeden parametr typu.</span><span class="sxs-lookup"><span data-stu-id="817d2-114">ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, ELEMENT_TYPE_BYREF, or ELEMENT_TYPE_PTR: One type parameter will be returned.</span></span> <span data-ttu-id="817d2-115">Na przykład, jeśli typ jest typem tablicowym `int32[]`,`EnumerateTypeParameters` zwróci `ICorDebugTypeEnum` zawiera obiekt reprezentujący `int32`.</span><span class="sxs-lookup"><span data-stu-id="817d2-115">For example, if the type is an array type such as `int32[]`,`EnumerateTypeParameters` will return an `ICorDebugTypeEnum` that contains an object representing `int32`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="817d2-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="817d2-116">Requirements</span></span>  
 <span data-ttu-id="817d2-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="817d2-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="817d2-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="817d2-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="817d2-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="817d2-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="817d2-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="817d2-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>