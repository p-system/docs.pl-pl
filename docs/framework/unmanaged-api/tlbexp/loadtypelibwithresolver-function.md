---
title: "LoadTypeLibWithResolver — Funkcja"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: LoadTypeLibWithResolver
api_location: TlbRef.dll
api_type: DLLExport
f1_keywords: LoadTypeLibWithResolver
helpviewer_keywords: LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0241745396ab01a777eef6e3b88e4c12bdd8b429
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="b3a5e-102">LoadTypeLibWithResolver — Funkcja</span><span class="sxs-lookup"><span data-stu-id="b3a5e-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="b3a5e-103">Ładuje bibliotekę typów i używa podane [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) rozwiązywać żadnych bibliotek typu wewnętrznie występującego w odwołaniu.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-103">Loads a type library and uses the supplied [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3a5e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3a5e-104">Syntax</span></span>  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3a5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3a5e-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="b3a5e-106">[in] Ścieżka do pliku biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="b3a5e-107">[in] A [wyliczenie REGKIND](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx) flagę, która kontroluje sposób zrejestrowanej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-107">[in] A [REGKIND enumeration](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx) flag that controls how the type library is registered.</span></span> <span data-ttu-id="b3a5e-108">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="b3a5e-108">Its possible values are:</span></span>  
  
-   <span data-ttu-id="b3a5e-109">`REGKIND_DEFAULT`: Użyj domyślnego zachowania rejestracji.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-109">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
-   <span data-ttu-id="b3a5e-110">`REGKIND_REGISTER`: Zarejestrować tej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-110">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
-   <span data-ttu-id="b3a5e-111">`REGKIND_NONE`: Nie rejestruj tej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-111">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="b3a5e-112">[in] Wskaźnik do wykonania [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b3a5e-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="b3a5e-113">[out] Odwołanie do biblioteki typów, który jest ładowany.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3a5e-114">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b3a5e-114">Return Value</span></span>  
 <span data-ttu-id="b3a5e-115">Jedna z wartości HRESULT wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="b3a5e-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="b3a5e-116">Return value</span></span>|<span data-ttu-id="b3a5e-117">Znaczenie</span><span class="sxs-lookup"><span data-stu-id="b3a5e-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="b3a5e-118">Powodzenie.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="b3a5e-119">Za mało pamięci.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="b3a5e-120">Co najmniej jeden wskaźniki są nieprawidłowe.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="b3a5e-121">Co najmniej jeden z argumentów jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="b3a5e-122">Funkcja nie można zapisać do pliku.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="b3a5e-123">Nie można otworzyć bazy danych rejestracji systemu.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="b3a5e-124">Nie można otworzyć biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="b3a5e-125">Nie można załadować biblioteki typów lub DLL.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3a5e-126">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b3a5e-126">Remarks</span></span>  
 <span data-ttu-id="b3a5e-127">[Tlbexp.exe (Eksporter biblioteki typów)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) wywołania `LoadTypeLibWithResolver` funkcji podczas procesu konwersji zestawu do typu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-127">The [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="b3a5e-128">Ta funkcja ładuje określonej biblioteki typów minimalnego dostępu do rejestru.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="b3a5e-129">Funkcja następnie sprawdza, czy biblioteki typów dla typu wewnętrznie występującego w odwołaniu biblioteki, z których każdy musi być załadowany i dodawane do biblioteki typu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="b3a5e-130">Przed załadowaniem przywoływanej biblioteki typów, ścieżki pliku odniesienia można rozwiązać pełną ścieżkę.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="b3a5e-131">Jest to realizowane przez [ResolveTypeLib — metoda](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) dostarczanym przez [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), który jest przekazywany w `pTlbResolver` parametru.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-131">This is accomplished through the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="b3a5e-132">Gdy znany jest pełna ścieżka pliku biblioteki typów do którego istnieje odwołanie, `LoadTypeLibWithResolver` funkcja ładuje i dodaje do biblioteki typu nadrzędnego, tworzenia biblioteki Scalonej typu głównego przywoływanej biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="b3a5e-133">Po funkcja rozpoznaje i ładuje wszystkie biblioteki typu wewnętrznie występującego w odwołaniu, zwraca odwołanie do biblioteki typów rozpoznać wzorca w `pptlib` parametru.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="b3a5e-134">`LoadTypeLibWithResolver` Funkcja jest zazwyczaj wywoływana przez [Tlbexp.exe (Eksporter biblioteki typów)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), który dostarcza własnego wewnętrznego [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementacja `pTlbResolver` parametr.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="b3a5e-135">Jeśli należy wywołać `LoadTypeLibWithResolver` bezpośrednio, należy podać własne [itypelibresolver — interfejs](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementacji.</span><span class="sxs-lookup"><span data-stu-id="b3a5e-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3a5e-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b3a5e-136">Requirements</span></span>  
 <span data-ttu-id="b3a5e-137">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3a5e-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3a5e-138">**Nagłówek:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="b3a5e-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="b3a5e-139">**Biblioteka:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="b3a5e-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="b3a5e-140">**Wersja platformy .NET framework:** 3.5, 3.0, 2.0</span><span class="sxs-lookup"><span data-stu-id="b3a5e-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a5e-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3a5e-141">See Also</span></span>  
 [<span data-ttu-id="b3a5e-142">Tlbexp — funkcje pomocy</span><span class="sxs-lookup"><span data-stu-id="b3a5e-142">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="b3a5e-143">[Funkcja LoadTypeLibEx](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)</span><span class="sxs-lookup"><span data-stu-id="b3a5e-143">[LoadTypeLibEx Function](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)</span></span>