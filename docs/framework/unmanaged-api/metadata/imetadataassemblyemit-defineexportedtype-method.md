---
title: IMetaDataAssemblyEmit::DefineExportedType — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.DefineExportedType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::DefineExportedType
helpviewer_keywords:
- IMetaDataAssemblyEmit::DefineExportedType method [.NET Framework metadata]
- DefineExportedType method [.NET Framework metadata]
ms.assetid: fad01d7a-3178-4c8c-9f0a-4641e3701c9b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2eb894a8bac702c30826d1e965c91cae9b259ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33448563"
---
# <a name="imetadataassemblyemitdefineexportedtype-method"></a>IMetaDataAssemblyEmit::DefineExportedType — Metoda
Tworzy `ExportedType` struktury zawierający metadane dla określonej wyeksportowanego typu i zwraca token skojarzone metadane.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT DefineExportedType (  
    [in]  LPCWSTR             szName,  
    [in]  mdToken             tkImplementation,   
    [in]  mdTypeDef           tkTypeDef,  
    [in]  DWORD               dwExportedTypeFlags,  
    [out] mdExportedType      *pmdct  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szName`  
 [in] Nazwa typu do wyeksportowania. Dla środowiska CLR, nazwa typu wyeksportowanego w wersji 1.1 musi dokładnie odpowiadać nazwie podanej w `TypeDef` dla typu.  
  
 `tkImplementation`  
 [in] Token określający, gdzie wyeksportowanego typu jest zaimplementowana. Prawidłowe wartości i ich znaczenie skojarzone są:  
  
-   `mdFile` Typ jest zaimplementowana w innym pliku w tym zestawie.  
  
-   `mdAssemblyRef` Typ jest zaimplementowana w innym zestawie.  
  
-   `mdExportedTYpe` Typ jest zagnieżdżony w ramach innego typu.  
  
-   `mdFileNil` Typ jest w tym samym pliku jako manifest i nie jest typem zagnieżdżonym.  
  
 `tkTypeDef`  
 [in] Token określający typ do wyeksportowania metadanych. Ta wartość jest wprowadzana w `TypeDef` tabeli w pliku, który implementuje typ i ma zastosowanie tylko wtedy, gdy ten plik jest w tym zestawie.  
  
 `dwExportedTypeFlags`  
 [in] Bitowe połączenie [CorTypeAttr](../../../../docs/framework/unmanaged-api/metadata/cortypeattr-enumeration.md) wartości wyliczenia, które definiują ustawienia właściwości wyeksportowanego typu.  
  
 `pmdct`  
 [out] Wskaźnik do tokenu zwrócone metadane, który wskazuje wyeksportowanego typu.  
  
## <a name="remarks"></a>Uwagi  
 `ExportedType` Struktura metadanych musi być zdefiniowana dla każdego typu, który jest udostępniany przez ten zestaw i wykonywane w module innego niż ten, zawierający manifestu.  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** używany jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IMetaDataAssemblyEmit, interfejs](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyemit-interface.md)
